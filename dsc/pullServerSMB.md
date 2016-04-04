# 设置 DSC SMB 请求服务器

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

DSC SMB 请求服务器是 SMB 文件共享，可在目标节点请求 DSC 配置文件和/或
DSC 资源时，向这些节点提供它们。

若要将 SMB 请求服务器用于 DSC，必须执行以下操作：
- 在运行 PowerShell 4.0 或更高版本的服务器上设置一个 SMB 文件共享
- 配置运行 PowerShell 4.0 或更高版本的客户端以从该 SMB 共享进行请求

## 使用 xSmbShare 资源创建 SMB 文件共享

可通过多种方法来设置 SMB 文件共享，不过我们来了解一下如何使用 DSC 来实现此目标。

### 安装 xSmbShare 资源

调用 Install-Module cmdlet 以安装 xSmbShare 模块。
>注意：Install-Module 包含在 PowerShellGet 模块中，后者纳入 PowerShell 5.0。 可在以下位置下载适用于 PowerShell 3.0 和 4.0 的 PowerShellGet：
>PackageManagement PowerShell 模块预览。 xSmbShare 包含 DSC 资源 xSmbShare，后者可以用于
创建 SMB 文件共享。

### 创建目录和文件共享

下面的配置使用 File 资源为共享创建目录，并使用 xSmbShare 资源设置 SMB 共享：

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }
        
    }
 
}
```

该配置会创建目录 `C:\DscSmbShare`（如果尚未存在），随后将该目录用作 SMB 文件共享。 FullAccess 应授予给任何
需要写入文件共享或从中进行删除的帐户，而 ReadAccess 必须授予给任何将从共享获取配置和/或 DSC 资源的客户端节点（
这是因为 DSC 在默认情况下作为系统帐户来运行，因此计算机本身必须有权访问共享）。


### 向请求客户端授予文件系统访问权限

向某个客户端节点授予 ReadAccess 可允许该节点访问 SMB 共享，但不可访问该共享中的文件或文件夹。 必须向客户端节点显式授予对 SMB 共享文件夹和子文件夹
的访问权限。 可以通过使用 cNtfsPermissionEntry 资源（它包含在 CNtfsAccessControl 模块中）进行添加，对 DSC
执行此操作。 下面的配置添加一个 cNtfsPermissionEntry 块，该块向请求客户端授予 ReadAndExecute 访问权限：

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }

        cNtfsPermissionEntry PermissionSet1 {
            
        Ensure = 'Present'
        Path = 'C:\DSCSMB'
        Principal = 'myDomain\Contoso-Server$'
        AccessControlInformation = @(
            cNtfsAccessControlInformation
            {
                AccessControlType = 'Allow'
                FileSystemRights = 'ReadAndExecute'
                Inheritance = 'ThisFolderSubfoldersAndFiles'
                NoPropagateInherit = $false
            }
        )
        DependsOn = '[File]CreateFolder'
        
        }
 
        
    }
 
}
```

## 放置配置和资源

将希望客户端节点请求的所有配置 MOF 文件和/或 DSC 资源保存在 SMB 共享文件夹中。

任何配置 MOF 文件都必须命名为 ConfigurationID.mof，其中 ConfigurationID 是目标节点上 LCM 的 ConfigurationID 属性值。 有关以下内容的详细信息
设置请求客户端，请参阅使用配置 ID 设置请求客户端。

>注意：如果使用 SMB 请求服务器，则必须使用配置 ID。 SMB 不支持配置名称。

客户端所需的任何资源都必须作为已存档的 `.zip` 文件置于 SMB 共享文件夹中。  

## 创建 MOF 校验和
配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。 
若要创建校验和，请调用 New-DSCCheckSum cmdlet。 该 cmdlet 将接受 Path 参数，该参数指定了 
配置 MOF 所在的文件夹。 该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。 
如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。

校验和文件与配置 MOF 文件必须位于同一目录中（默认为 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`）且具有相同名称（校验文件附加有 `.checksum` 扩展名）。

>注意：如果以任何方式更改配置 MOF 文件，则也必须重新创建校验和文件。

## 致谢

特别感谢以下人员：

- Mike F. Robbins，其有关将 SMB 用于 DSC 的文章帮助告知本主题中的内容。 其博客地址是 Mike F Robbins。
- Serge Nikalaichyk，他是 cNtfsAccessControl 模块的作者。 此模块的源代码位于 https://github.com/SNikalaichyk/cNtfsAccessControl。

## 另请参阅
- [Windows PowerShell Desired State Configuration 概述](overview.md)
- [执行配置](enactingConfigurations.md)
- [使用配置 ID 设置请求客户端](pullClientConfigID.md)

 

<!--HONumber=Mar16_HO2-->



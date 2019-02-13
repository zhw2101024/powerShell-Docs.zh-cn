---
ms.date: 04/11/2018
keywords: dsc,powershell,配置,安装程序
title: 设置 DSC SMB 请求服务器
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676185"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>设置 DSC SMB 请求服务器

适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) 请求服务器是计算机托管 SMB 文件共享，可在目标节点提出请求时向它们提供 DSC 配置文件和 DSC 资源。

若要将 SMB 请求服务器用于 DSC，必须执行以下操作：

- 在运行 PowerShell 4.0 或更高版本的服务器上设置一个 SMB 文件共享
- 配置运行 PowerShell 4.0 或更高版本的客户端以从该 SMB 共享进行请求

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>使用 xSmbShare 资源创建 SMB 文件共享

可通过多种方法来设置 SMB 文件共享，不过我们来了解一下如何使用 DSC 来实现此目标。

### <a name="install-the-xsmbshare-resource"></a>安装 xSmbShare 资源

调用 [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet 可以安装 **xSmbShare** 模块。

> [!NOTE]
> `Install-Module` 包含在 PowerShellGet 模块中，后者纳入 PowerShell 5.0。 可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。
> **xSmbShare** 包含 DSC 资源 **xSmbShare**，后者可用于创建 SMB 文件共享。

### <a name="create-the-directory-and-file-share"></a>创建目录和文件共享

下面的配置使用 **File** 资源创建共享目录，并使用 **xSmbShare** 资源创建 SMB 共享：

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
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

此配置会创建该目录`C:\DscSmbShare`，如果它尚不存在，然后将该目录用作 SMB 文件共享。 **FullAccess**应授予给任何需要写入或从文件共享中删除的帐户。 **ReadAccess**必须授予给所有从共享获取配置和/或 DSC 资源的客户端节点。

> [!NOTE]
> DSC 以系统帐户默认运行，因此计算机本身必须有权访问共享。

### <a name="give-file-system-access-to-the-pull-client"></a>向请求客户端授予文件系统访问权限

向客户端节点授予 **ReadAccess** 可允许该节点访问 SMB 共享，但不允许其访问此共享中的文件或文件夹。 你必须显式授予客户端节点访问 SMB 共享文件夹和子文件夹。 我们可以使用 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 模块中包含的 **cNtfsPermissionEntry** 资源进行添加，对 DSC 执行此操作。 下面的配置添加了 **cNtfsPermissionEntry** 块，用于向请求客户端授予 ReadAndExecute 访问权限：

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
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

## <a name="placing-configurations-and-resources"></a>放置配置和资源

将希望客户端节点请求的所有配置 MOF 文件和/或 DSC 资源保存在 SMB 共享文件夹中。

所有配置 MOF 文件都必须命名为 *ConfigurationID*.mof，其中 *ConfigurationID* 是目标节点的 LCM 的 **ConfigurationID** 属性值。 若要详细了解如何设置请求客户端，请参阅[使用配置 ID 设置请求客户端](pullClientConfigID.md)。

> [!NOTE]
> 如果你使用的是 SMB 请求服务器，则必须使用配置 ID。 SMB 不支持配置名称。

每个资源模块都需要进行压缩并按照 `{Module Name}_{Module Version}.zip` 模式进行命名。 例如，一个名为 xWebAdminstration 并且模块版本为 3.1.2.0 的模块会命名为“xWebAdministration_3.2.1.0.zip”。 每个版本的模块都必须包含在单个 zip 文件中。 不支持单独的 zip 文件中的模块的版本。 在打包 DSC 资源模块以便用于请求服务器之前, 需要对目录结构进行少量更改。

包含 WMF 5.0 中 DSC 资源的模块的默认格式为 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`。

为请求服务器打包前，只需删除 `{Module version}` 文件夹，以使路径变为 `{Module Folder}\DscResources\{DSC Resource Folder}\`。 进行此更改之后，按上文所述压缩文件夹，并将这些 zip 文件置于 SMB 共享文件夹中。

## <a name="creating-the-mof-checksum"></a>创建 MOF 校验和

配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。
若要创建校验和，请调用 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet。 该 cmdlet 将采用 `Path` 参数，指定配置 MOF 所在的文件夹。 该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。
如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。

校验和文件与配置 MOF 文件必须位于同一目录中（默认为 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`）且具有相同名称（校验文件附加有 `.checksum` 扩展名）。

> [!NOTE]
> 如果以任何方式更改配置 MOF 文件，则还必须重新创建校验和文件。

## <a name="setting-up-a-pull-client-for-smb"></a>设置 SMB 请求客户端

若要设置从 SMB 共享请求获取配置和/或资源的客户端，可使用指定从哪个共享中请求获取配置和 DSC 资源的 **ConfigurationRepositoryShare** 和 **ResourceRepositoryShare** 代码块，配置客户端的本地配置管理器 (LCM)。

有关配置 LCM 的详细信息，请参阅[使用配置 ID 设置请求客户端](pullClientConfigID.md)。

> [!NOTE]
> 为简单起见，此示例使用 PSDscAllowPlainTextPassword，以允许将明文密码传递到 Credential 参数。 有关更安全传递凭据的信息，请参阅[配置数据中的凭据选项](../configurations/configDataCredentials.md)。
>
> 即使仅请求资源，也必须在 SMB 请求服务器的 metaconfiguration“设置”块中指定“ConfigurationID”。

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a>致谢

特别感谢下列人员：

- Mike F. Robbins，其有关将 SMB 用于 DSC 的文章帮助告知本主题中的内容。 他的博客是 [Mike F Robbins](http://mikefrobbins.com/)。
- Serge Nikalaichyk，他是 **cNtfsAccessControl** 模块的作者。 此模块的来源位于 [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl)。

## <a name="see-also"></a>另请参阅

[Windows PowerShell Desired State Configuration 概述](../overview/overview.md)

[执行配置](enactingConfigurations.md)

[使用配置 ID 设置请求客户端](pullClientConfigID.md)

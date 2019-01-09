---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 应用、获取并测试节点上的配置
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400854"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>应用、获取并测试节点上的配置

本指南将演示如何使用配置目标节点上。 本指南将分解为以下步骤：

## <a name="apply-a-configuration"></a>应用配置

若要应用并管理配置，我们需要生成一个".mof"文件。 下面的代码将表示将本指南中使用的简单配置。

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

编译此配置会产生两个".mof"文件。

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

若要应用配置，请使用[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet。 `-Path`参数指定".mof"的文件所在的目录。 如果没有`-Computername`指定，则`Start-DSCConfiguration`会尝试将每个配置应用于.mof 文件的名称指定的计算机名称 (\<computername\>.mof)。 指定`-Verbose`到`Start-DSCConfiguration`若要查看更详细的输出。

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

如果`-Wait`未指定，请参阅创建一个作业。 创建的作业会有一个**ChildJob**对于每个".mof"文件处理的`Start-DSCConfiguration`。

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

如果配置需要很长时间，并且你想要停止它，可以使用[Stop-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)本地节点上停止应用程序。

```powershell
Stop-DSCConfiguration -Force
```

完成后，您可以查看作业通过返回的作业对象的状态[Get-job](/powershell/module/microsoft.powershell.core/get-job)。

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

若要查看**Verbose**输出，请使用以下命令来查看**Verbose**每个流**ChildJob**。 有关 PowerShell 作业的详细信息，请参阅[about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

从 PowerShell 5.0 中，开始`-UseExisting`参数已添加到`Start-DSCConfiguration`。 通过指定`-UseExisting`，指示 cmdlet 而不是一个由指定使用现有应用的配置`-Path`参数。

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>测试配置

你可以测试目前已应用的配置使用[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。 `Test-DSCConfiguration` 将返回`True`符合要求，节点是否和`False`如果不是。

```powershell
Test-DSCConfiguration
```

从 PowerShell 5.0 中，开始`-Detailed`参数已添加它返回具有集合的对象**ResourcesInDesiredState**和**ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

从 PowerShell 5.0 开始，您可以测试配置，而不应用它。 `-ReferenceConfiguration`参数接受".mof"文件，以测试针对的节点的路径。 否**设置**针对节点执行操作。 在 PowerShell 4.0 中，有解决方法来测试配置，而不应用它，但这里不对其进行讨论。

## <a name="get-configuration-values"></a>获取配置值

[Get-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 返回在当前应用的配置中的任何已配置的资源的当前值。

```powershell
Get-DSCConfiguration
```

如果已成功应用，从我们的示例配置的输出将类似如下。

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>获取配置状态

从 PowerShell 5.0 开始[Get-dscconfigurationstatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet 允许您查看应用到的节点配置的历史记录。 跟踪应用中的最后一个 {{N}} 配置的 PowerShell DSC**推送**或**拉取**模式。 这包括任何*一致性*检查由 LCM 进行执行。 默认情况下，`Get-DSCConfigurationStatus`演示的最后一个历史记录条目。

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

使用`-All`参数，以查看所有配置状态历史记录。

> [!NOTE]
> 为简洁起见，输出将被截断。

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>管理配置文档

LCM 使用由管理的节点配置**配置文档**。 这些".mof"文件位于"C:\Windows\System32\Configuration"目录中。

从 PowerShell 5.0 开始[Remove-dscconfigurationdocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) ，可删除".mof"文件以停止将来一致性检查或删除有错误时应用的配置。 `-Stage`参数可以指定你想要删除哪个".mof"文件。

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> 在 PowerShell 4.0 中，可以仍删除直接使用这些".mof"文件[Remove-item](/powershell/module/microsoft.powershell.management/remove-item)。

## <a name="publish-configurations"></a>发布配置

从 PowerShell 5.0 中，开始[Publish-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet 已添加。 此 cmdlet，可将".mof"文件发布到远程计算机，而不应用它。

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>另请参阅

- [获取、测试并设置](../resources/get-test-set.md)

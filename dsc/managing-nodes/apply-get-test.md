---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 应用、获取并测试节点上的配置
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079704"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>应用、获取并测试节点上的配置

本指南将演示如何处理目标节点上的配置。 本指南分为以下几个步骤：

## <a name="apply-a-configuration"></a>应用配置

为了应用和管理配置，我们需要生成一个“.mof”文件。 下面的代码表示将在整个指南中使用的一个简单配置。

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

编译此配置将产生两个“.mof”文件。

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

若要应用配置，请使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet。 参数 `-Path` 指定“.mof”文件所在的目录。 如果未指定 `-Computername`，`Start-DSCConfiguration` 将尝试将每个配置应用于由“.mof”文件（\<computername \>.mof）的名称指定的计算机名称。 将 `-Verbose` 指定为 `Start-DSCConfiguration`，以查看更详细的输出。

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

如果未指定 `-Wait`，你将看到创建了一个作业。 创建的作业将为每个由 `Start-DSCConfiguration` 处理的“.mof”文件提供一个 ChildJob。

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

如果配置需要很长时间，并且你想要停止它，则可以使用 [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) 来停止本地节点上的应用程序。

```powershell
Stop-DSCConfiguration -Force
```

完成后，可以通过由 [Get-Job](/powershell/module/microsoft.powershell.core/get-job) 返回的作业对象查看作业状态。

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

要查看详细输出，请使用以下命令查看每个 ChildJob 的详细流。 有关 PowerShell 作业的详细信息，请参阅 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。

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

从 PowerShell 5.0 开始，`-UseExisting` 参数已添加到 `Start-DSCConfiguration`。 通过指定 `-UseExisting`，可以指示 cmdlet 使用现有的已应用配置，而不使用由 `-Path` 参数指定的配置。

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>测试配置

可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 测试当前应用的配置。 如果节点兼容，`Test-DSCConfiguration` 将返回 `True`；如果不兼容，则返回 `False`。

```powershell
Test-DSCConfiguration
```

从 PowerShell 5.0 开始，添加了 `-Detailed` 参数，该参数返回一个对象，其中包含 ResourcesInDesiredState 和 ResourcesNotInDesiredState 的集合

```powershell
Test-DSCConfiguration -Detailed
```

从 PowerShell 5.0 开始，可以在不应用配置的情况下对其进行测试。 `-ReferenceConfiguration` 参数接受要对其测试节点的“.mof”文件的路径。 没有对节点执行任何设置操作。 在 PowerShell 4.0 中，有一些解决方法可在不应用配置的情况下对其进行测试，但在这里不予讨论。

## <a name="get-configuration-values"></a>获取配置值

[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 返回当前应用的配置中任何已配置资源的当前值。

```powershell
Get-DSCConfiguration
```

如果应用成功，示例配置的输出将如下所示。

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

从 PowerShell 5.0 开始，借助 [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet，用户可查看节点的已应用配置的历史记录。 PowerShell DSC 跟踪在推送或拉取模式下应用的最后 {{N}} 个配置。 这包括 LCM 执行的任何一致性检查。 默认情况下，`Get-DSCConfigurationStatus` 只显示最后一个历史记录条目。

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

使用 `-All` 参数查看所有配置状态历史记录。

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

LCM 通过处理配置文档来管理节点配置。 这些“.mof”文件驻留在“C:\Windows\System32\Configuration”目录中。

从 PowerShell 5.0 开始，借助 [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)用户可删除“.mof”文件来停止未来的一致性检查，或删除应用时出现错误的配置。 `-Stage` 参数允许用户指定要删除的“.mof”文件。

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> 在 PowerShell 4.0 中，仍可以使用 [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) 来直接删除这些“.mof”文件。

## <a name="publish-configurations"></a>发布配置

从 PowerShell 5.0 开始，添加了 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet。 可通过此 cmdlet 将“.mof”文件发布到远程计算机，而无需应用它。

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>另请参阅

- [获取、测试并设置](../resources/get-test-set.md)

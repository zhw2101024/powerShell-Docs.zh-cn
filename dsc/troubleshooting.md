# DSC 故障排除

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

本主题介绍使 Desired State Configuration (DSC) 的脚本正确运行的方法。 通过有效使用日志跟踪错误和了解如何回收缓存以查看资源更改的直接结果，你将能够更有效地对 DSC 进行故障排除。 以下两节中讨论了这些技术：

* 脚本不运行：**使用 DSC 日志来诊断脚本错误**
* 资源不更新：**如何重置缓存**

## 脚本不运行：使用 DSC 日志来诊断脚本错误

与所有 Windows 软件一样，DSC 将错误和事件记录在[日志](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx)中，可以通过[事件查看器](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer)查看。 检查这些日志可以帮助你了解某一特定操作失败的原因，以及如何防止将来出现故障。 编写配置脚本可能会很棘手，因此，为了在创作时更轻松地跟踪错误，请在 DSC Analytic 事件日志中使用 DSC Log 资源跟踪配置的进度。

## DSC 事件日志在哪里？

在事件查看器中，DSC 事件位于：**Applications and Services Logs/Microsoft/Windows/Desired State Configuration**

也可以运行相应的 PowerShell cmdlet ([Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx)) 以查看事件日志：

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

如上所示，DSC 的主日志名称为 **Microsoft->Windows->DSC**（为简洁起见，此处未显示 Windows 下的其他日志名称）。 将主名称追加到通道名称，以创建完整的日志名称。 DSC 引擎主要写入三种类型的日志：[运行、分析和调试日志](https://technet.microsoft.com/library/cc722404.aspx)。 分析和调试日志默认处于关闭状态，因此你应该在事件查看器中启用它们。 若要进行此操作，请在 Windows PowerShell 中输入 Show-EventLog 以打开事件查看器，或依次单击“开始”、“控制面板”、“管理工具”以及“事件查看器”。**************** 在事件查看器中的“查看”菜单上，单击“显示分析和调试日志”。 分析通道的日志名称为 **Microsoft-Windows-Dsc/Analytic**，而调试通道为 **Microsoft-Windows-Dsc/Debug**。 你还可以通过 [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) 实用程序启用日志，如下面的示例中所示。

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## DSC 日志包含哪些内容？

根据消息的重要性，将 DSC 日志拆分到三个日志通道。 DSC 中的运行日志包含所有错误消息，可用于确定问题。 分析日志包含更多事件，可确定错误出现的位置。 此通道还包含详细消息（若有）。 调试日志包含的日志可帮助你了解错误出现的过程。 DSC 事件消息的构成方式是，每个事件消息以表示唯一 DSC 操作的作业 ID 开头。 下面的示例尝试从记录到 DSC 操作日志的第一个事件获取消息。

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

以特定结构记录 DSC 事件，该结构让用户可以通过一个 DSC 作业聚合事件。 该结构如下所示：

**作业 ID：<Guid>**
**<Event Message>**

## 通过单个 DSC 操作收集事件

DSC 事件日志包含由各种 DSC 操作生成的事件。 但是，你通常只关心某一特定操作的详细信息。 可按作业 ID 属性对所有 DSC 日志进行分组，作业 ID 对每个 DSC 操作来说是唯一的。 作业 ID 显示为所有 DSC 事件中的第一个属性值。 下列步骤说明如何在一个分组数组结构中累计所有事件。

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}  
```

此处，变量 `$SeparateDscOperations` 包含按作业 ID 分组的日志。 此变量的每个数组元素表示由不同的 DSC 操作记录的一组事件，让你可以访问有关日志的更多信息。

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

可以用 [Where-object](https://technet.microsoft.com/library/ee177028.aspx) 提取变量 `$SeparateDscOperations` 中的数据。 在以下五种情况下，可能需要提取数据以解决 DSC 问题：

### 1：操作故障

所有事件都具有[严重性级别](https://msdn.microsoft.com/library/dd996917(v=vs.85))。 此信息可用于标识错误事件：

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2：过去半小时内所运行操作的详细信息

每个 Windows 事件都具有 `TimeCreated` 属性，它表明创建该事件的时间。 可通过将此属性与特定日期/时间对象进行比较来筛选所有事件：

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3：来自最新操作的消息

最新操作存储在数组组 `$SeparateDscOperations` 的第一个索引中。 查询索引 0 的组消息将返回最新操作的所有消息：

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### 4：为最近的失败操作记录到的错误消息

`$SeparateDscOperations[0].Group` 包含最新操作的一组事件。 运行 `Where-Object` cmdlet 可根据事件级别显示名称对筛选事件。 结果将存储在 `$myFailedEvent` 变量中，可以进一步细化以获取事件消息：

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### 5：为特定作业 ID 生成的所有事件。

`$SeparateDscOperations` 是一个组数组，其中每个组的名称即其唯一作业 ID。 通过运行 `Where-Object` cmdlet，你可以提取这些具有特定作业 ID 的事件组：

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## 使用 xDscDiagnostics 分析 DSC 日志

**xDscDiagnostics** 是由两个简单函数组成的 PowerShell 模块，这两个函数（`Get-xDscOperation` 和 `Trace-xDscOperation`）可以帮助你分析计算机上的 DSC 失败。 这些函数可以帮助你确定因过去的 DSC 操作而起的所有本地事件，或（具有有效凭据的）远程计算机上的 DSC 事件。 此处使用了“DSC 操作”这一术语来定义单个唯一的 DSC 执行过程。 例如，`Test-DscConfiguration` 将是一个单独的 DSC 操作。 同样，DSC 中每个其他 cmdlet （如 `Get-DscConfiguration`、`Start-DscConfiguration` 等）可各自识别为单独的 DSC 操作。 以下 [xDscDiagnostics](https://powershellgallery.com/packages/xDscDiagnostics) PowerShell 模块（DSC 资源工具包）中更详细地解释了这两个函数。 可通过运行 `Get-Help <cmdlet name>` 获取帮助。

## Get-xDscOperation

可通过此函数查找在一台或多台计算机上运行的 DSC 操作的结果，并返回一个包含每个 DSC 操作所产生事件的集合的对象。 例如，在下面的输出中，运行了三个命令。 第一个命令成功，另外两个失败。 在 `Get-xDscOperation` 的输出中总结了这些结果。

TODO：替换显示 Get-xDscOperation 输出的图像

### 参数

* **Newest**：采用整数值指示要显示的操作数。 默认情况下，它将返回 10 个最新的操作。 例如，
  TODO：显示 Get-xDscOperation -Newest 5
* **ComputerName**：接受字符串数组的参数，这些字符串各包含你想要从中收集 DSC 事件日志数据的计算机的名称。 默认情况下，它从本地计算机收集数据。 若要启用此功能，必须在提升模式下在远程计算机上运行以下命令，以允许收集事件
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* **Credential**：类型为 PSCredential 的参数，可帮助访问 ComputerName 参数中指定的计算机。

### 返回的对象

该 cmdlet 返回 **Microsoft.PowerShell.xDscDiagnostics.GroupedEvents** 类型对象的数组。 此数组中的每个对象各与不同 DSC 操作有关。 此对象的默认显示具有以下属性
* **SequenceID**：根据时间指定分配给 DSC 操作的递增编号。 例如，最后执行的操作的 SequenceID 为 1，倒数第二个 DSC 操作的 SequenceID 为 2，以此类推。 此编号是返回的数组中每个对象的另一个标识符。
* **TimeCreated**：用于指示 DSC 操作开始时间的 DateTime 值。
* **ComputerName**：从其上聚合结果的计算机的名称。
* **Result**：包含 **Failure** 或 **Success** 值的字符串，这两个值分别指示该 DSC 操作是否出错。
* **AllEvents**：表示由 DSC 操作所生成事件的集合的对象。

例如，下面的输出显示来自多台计算机的上一个操作的结果：
  TODO：替换 Get-xDscOperation 的图片以显示远程计算机日志

## Trace-xDscOperation

此 cmdlet 将返回一个对象，其中包含事件集合、其事件类型以及特定 DSC 操作生成的消息输出。 通常情况下，使用 `Get-xDscOperation` 在任何操作中查找故障时，将跟踪该操作以查明导致故障的事件。

### 参数

* **SequenceID**：这是分配给任意操作的整数值，与特定计算机相关。 通过指定序列 ID（比如说 4），将输出倒数第 4 个 DSC 操作的跟踪信息

指定了序列 ID 的 Trace-xDscOperation
* **JobID**：这是由 LCM xDscOperation 分配用于唯一标识操作的 GUID 值。 指定 JobID 后，将输出相应 DSC 操作的跟踪信息。
  TODO：替换将 JobID 用作参数的 Trace-xDscOperation 的图片
* **ComputerName** 和 **Credential**：这些参数允许从远程计算机收集跟踪信息：
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  TODO：替换在不同计算机上运行的 Trace-xDscOperation 的图片

请注意，由于 `Trace-xDscOperation` 聚合来自分析、调试和运行日志的事件，因此它将提示你启用这些日志，如上所述。

### 返回的对象

此 cmdlet 将返回一个 `Microsoft.PowerShell.xDscDiagnostics.TraceOutput` 类型对象的数组。 此数组中的每个对象包含以下字段：
* **ComputerName**：从中收集日志的计算机的名称。
* **EventType**：这是一个枚举器类型字段，其中包含事件类型的信息。 事件可为以下任一类型：
  - *Operational*：来自运行日志的事件。
  - *Analytic*：来自分析日志的事件。
  - *Debug*：来自调试日志的事件。
  - *Verbose*：执行过程中作为详细消息输出的事件。 通过详细消息，可轻松标识已发布事件的顺序。
  - *Error*：错误事件。 通过查找错误事件，通常可以快速查明故障的原因。
* **TimeCreated**：表明 DSC 记录该事件的时间的 DateTime 值。
* **Message**：由 DSC 记录到事件日志的消息。

此对象中的以下字段可用于获取有关事件的详细信息，但默认情况下未显示这些字段：

* **JobID**：特定于该 DSC 操作的作业 ID（GUID 格式）。
* **SequenceID**：该计算机中该 DSC 操作特有的 SequenceID。
* **Event**：这是 DSC 记录的实际事件，类型为 `System.Diagnostics.Eventing.Reader.EventLogRecord`。 也可以通过运行 cmdlet `Get-WinEvent` 获取它。 它包含任务、事件 ID 和事件的级别等详细信息。

或者，你可以通过将 `Trace-xDscOperation` 的输出保存到变量中来收集关于事件的信息。 可使用以下命令显示特定 DSC 操作的所有事件：

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

此操作将显示与 `Get-WinEvent` cmdlet 相同的结果，例如以下输出中的结果：
  TODO：输出内容是什么？

理想情况下，你将首先使用 `Get-xDscOperation` 列出在计算机上运行的最后几个 DSC 配置。 此后，可以通过 `Trace-xDscOperation` 检查任意单个操作（使用其 SequenceID 或 JobID）以发现它在后台进行的活动。

## 资源不更新：如何重置缓存

出于效率考虑，DSC 引擎将缓存作为 PowerShell 模块实现的资源。 但是，当你同时创作和测试资源时，这可能导致问题，因为在重启进程前，DSC 将始终加载缓存的版本。 使 DSC 加载较新版本的唯一方法是显式终止承载 DSC 引擎的进程。

同样，当你运行 `Start-DscConfiguration` 时，在添加和修改自定义资源之后，重启计算机之前可能无法执行修改。 这是因为 DSC 在 WMI 提供程序主机进程 (WmiPrvSE) 中运行，且通常情况下将有 WmiPrvSE 的多个实例同时运行。 重启时，将重新启动主机进程并清除缓存。

若要在不重启的情况下成功回收配置并清除缓存，必须停止并重新启动主机进程。 可按实例逐一进行此操作，在这些实例中标识、停止和重新启动该进程。 或者，你可以使用 `DebugMode` 来重新加载 PowerShell DSC 资源，如下所示。

若要确定承载 DSC 引擎的进程并按实例逐一停止它们，你可以列出承载 DSC 引擎的 WmiPrvSE 的进程 ID。 然后，若要更新提供程序，请使用以下命令停止 WmiPrvSE 进程，并再次运行 **Start-DscConfiguration**。

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## 使用 DebugMode

可将 DSC 本地配置管理器 (LCM) 配置为使用 `DebugMode`，以便在重新启动主机进程时始终清除缓存。 当设置为 **TRUE**，它将使引擎始终重新加载 PowerShell DSC 资源。 编写完资源后，可将其设置回 **FALSE**，引擎将恢复到其缓存模块的行为。

下列演示表明了 `DebugMode` 可以如何自动刷新缓存。 首先，让我们看一下默认配置：

```
PS C:\> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

你可以看到 `DebugMode` 设置为 **FALSE**。

若要设置 `DebugMode` 演示，请使用以下 PowerShell 资源：

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

现在，使用上述名为 `TestProviderDebugMode` 的资源创作配置：

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

你将看到文件“**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**”的内容为 **1**。

现在，使用以下脚本更新提供程序代码：

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

此脚本将生成一个随机数，并相应地更新提供程序代码。 将 `DebugMode` 设置为 false 后，文件“**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**”的内容未发生更改。

现在，在配置脚本中将 `DebugMode` 设置为 **TRUE**：

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

再次运行上述脚本时，你将看到该文件的内容每次都不同。 （可运行 `Get-DscConfiguration` 以对其进行检查）。 以下是两次额外运行的结果（当你运行脚本时，结果可能不同）：

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14                                      localhost
```

## 另请参阅

### 引用
* [DSC Log 资源](logResource.md)

### 概念
* [构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)

### 其他资源
* [Windows PowerShell Desired State Configuration Cmdlet](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)


<!--HONumber=Mar16_HO1-->



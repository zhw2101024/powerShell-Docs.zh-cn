# 统一且一致的状态和状态表示形式

在此版本中，增加了一系列自动化构建 LCM 状态和 DSC 状态的增强功能。 其中包括统一且一致的状态和状态表示形式：Get-DscConfigurationStatus cmdlet 所返回状态对象的可管理日期时间属性和 Get-DscLocalConfigurationManager cmdlet 所返回增强的 LCM 状态详细信息属性。

根据下列规则再次访问并统一了 LCM 状态和 DSC 操作状态的表示形式：
1.  Notprocessed 资源不会影响 LCM 状态和 DSC 状态。
2.  一旦 LCM 遇到请求重新启动的资源，它将停止处理更多资源。
3.  直到实重新启动实际发生，请求重新启动的资源才处于所需状态。
4.  出现失败的资源后，LCM 将继续处理更多资源（只要这些资源不依赖于失败的资源）。
5.  Get-DscConfigurationStatus cmdlet 返回的总体状态是所有资源状态的超集。
6.  PendingReboot 状态是 PendingConfiguration 状态的超集。

下表说明了在使用典型方案时产生的状态和与状态关联属性。

| **方案**                    | **LCMState\***       | **状态** | **请求重新启动**  | **ResourcesInDesiredState**  | **ResourcesNotInDesiredState** |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | 空闲                 | Success    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | 失败    | $false        | $null                        | F                              |
| S、F                             | PendingConfiguration | 失败    | $false        | S                            | F                              |
| F、S                             | PendingConfiguration | 失败    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | 失败    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | 失败    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S、r                            | PendingReboot        | Success    | $true         | S                            | r                              |
| F、r                            | PendingReboot        | 失败    | $true         | $null                        | F、r                           |
| r、S                            | PendingReboot        | Success    | $true         | $null                        | r                              |
| r、F                            | PendingReboot        | Success    | $true         | $null                        | r                              |

^
S<sub>i</sub>：一系列成功应用 F<sub>i</sub> 的资源：一系列成功应用 r 的资源 ：需要重新启动的资源
\*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## Get-DscConfigurationStatus cmdlet 中的增强功能

在此版本中，对 Get DscConfigurationStatus cmdlet 进行了几处改进。 以前，该 cmdlet 返回的对象的 StartDate 属性是 String 类型。 现在，它是 Datetime 类型，从而可以根据 Datetime 对象的内部属性更轻松地进行复杂选择和筛选。
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

以下示例返回与今天处于一周中同一天的日子里产生的所有 DSC 操作记录。
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

将消除不更改节点配置的操作（即只读操作）的记录。 因此，Test-DscConfiguration、Get-DscConfiguration 操作将不再掺杂在从 Get-DscConfigurationStatus cmdlet 返回的对象中。
元配置设置操作的记录将添加到 Get-DscConfigurationStatus cmdlet 的返回结果中。

下面是从 Get-DscConfigurationStatus –All cmdlet 返回结果的示例。
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## Get-DscLocalConfigurationManager cmdlet 中的增强功能
新字段 LCMStateDetail 已添加到从 Get-DscLocalConfigurationManager cmdlet 返回的对象。 LCMState 为“忙碌”时，填充此字段。 它可以通过以下 cmdlet 来检索：
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

下面是对需要两次重新启动远程节点的配置所进行持续监视的示例输出。
```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```


<!--HONumber=Jun16_HO4-->



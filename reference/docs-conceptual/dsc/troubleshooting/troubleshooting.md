---
ms.date: 10/30/2018
keywords: dsc,powershell,配置,安装程序
title: DSC 故障排除
ms.openlocfilehash: 5cbe6496a6e0b9940f4b69e13d1e19e43b3915f0
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402404"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="162bf-103">DSC 故障排除</span><span class="sxs-lookup"><span data-stu-id="162bf-103">Troubleshooting DSC</span></span>

<span data-ttu-id="162bf-104">适用于：_Windows PowerShell 4.0 和 Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="162bf-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="162bf-105">本主题介绍出现问题时 DSC 故障排除的方法。</span><span class="sxs-lookup"><span data-stu-id="162bf-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="162bf-106">WinRM 依赖关系</span><span class="sxs-lookup"><span data-stu-id="162bf-106">WinRM Dependency</span></span>

<span data-ttu-id="162bf-107">Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。</span><span class="sxs-lookup"><span data-stu-id="162bf-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="162bf-108">在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="162bf-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="162bf-109">若要启用 WinRM，在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="162bf-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="162bf-110">使用 Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="162bf-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="162bf-111">[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet 从目标节点中获取有关配置状态的信息。</span><span class="sxs-lookup"><span data-stu-id="162bf-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="162bf-112">将返一个回富对象，它包含有关配置运行成功与否的高级信息。</span><span class="sxs-lookup"><span data-stu-id="162bf-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="162bf-113">你可以深入探究该对象，以查明有关配置运行的详细信息，例如：</span><span class="sxs-lookup"><span data-stu-id="162bf-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="162bf-114">失败的所有资源</span><span class="sxs-lookup"><span data-stu-id="162bf-114">All of the resources that failed</span></span>
- <span data-ttu-id="162bf-115">请求重新启动的任何资源</span><span class="sxs-lookup"><span data-stu-id="162bf-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="162bf-116">配置运行时的元配置设置</span><span class="sxs-lookup"><span data-stu-id="162bf-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="162bf-117">等。</span><span class="sxs-lookup"><span data-stu-id="162bf-117">Etc.</span></span>

<span data-ttu-id="162bf-118">下面的参数集将返回上次配置运行的状态信息：</span><span class="sxs-lookup"><span data-stu-id="162bf-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="162bf-119">下面的参数集将返回之前所有配置运行的状态信息：</span><span class="sxs-lookup"><span data-stu-id="162bf-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="162bf-120">示例</span><span class="sxs-lookup"><span data-stu-id="162bf-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="162bf-121">脚本不运行：使用 DSC 日志来诊断脚本错误</span><span class="sxs-lookup"><span data-stu-id="162bf-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="162bf-122">与所有 Windows 软件一样，DSC 将错误和事件记录在[日志](/windows/desktop/EventLog/about-event-logging)中，可以通过[事件查看器](https://support.microsoft.com/hub/4338813/windows-help)查看。</span><span class="sxs-lookup"><span data-stu-id="162bf-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="162bf-123">检查这些日志可以帮助你了解某一特定操作失败的原因，以及如何防止将来出现故障。</span><span class="sxs-lookup"><span data-stu-id="162bf-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="162bf-124">编写配置脚本可能会很棘手，因此，为了在创作时更轻松地跟踪错误，请在 DSC Analytic 事件日志中使用 DSC Log 资源跟踪配置的进度。</span><span class="sxs-lookup"><span data-stu-id="162bf-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="162bf-125">DSC 事件日志在哪里？</span><span class="sxs-lookup"><span data-stu-id="162bf-125">Where are DSC event logs?</span></span>

<span data-ttu-id="162bf-126">在事件查看器中，DSC 事件位于：**Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="162bf-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="162bf-127">也可以运行相应的 PowerShell cmdlet ([Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)) 以查看事件日志：</span><span class="sxs-lookup"><span data-stu-id="162bf-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="162bf-128">如上所示，DSC 的主日志名称为 Microsoft->Windows->DSC  （为简洁起见，此处未显示 Windows 下的其他日志名称）。</span><span class="sxs-lookup"><span data-stu-id="162bf-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="162bf-129">将主名称追加到通道名称，以创建完整的日志名称。</span><span class="sxs-lookup"><span data-stu-id="162bf-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="162bf-130">DSC 引擎主要写入三种类型的日志：[运行、分析和调试日志](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="162bf-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="162bf-131">分析和调试日志默认处于关闭状态，因此你应该在事件查看器中启用它们。</span><span class="sxs-lookup"><span data-stu-id="162bf-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="162bf-132">若要进行此操作，请在 Windows PowerShell 中输入 Show-EventLog 以打开事件查看器，或依次单击“开始”、“控制面板”、“管理工具”以及“事件查看器”。    </span><span class="sxs-lookup"><span data-stu-id="162bf-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="162bf-133">在事件查看器中的“查看”菜单上，单击“显示分析和调试日志”。  </span><span class="sxs-lookup"><span data-stu-id="162bf-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="162bf-134">分析通道的日志名称为 **Microsoft-Windows-Dsc/Analytic**，而调试通道为 **Microsoft-Windows-Dsc/Debug**。</span><span class="sxs-lookup"><span data-stu-id="162bf-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="162bf-135">你还可以通过 [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) 实用程序启用日志，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="162bf-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="162bf-136">DSC 日志包含哪些内容？</span><span class="sxs-lookup"><span data-stu-id="162bf-136">What do DSC logs contain?</span></span>

<span data-ttu-id="162bf-137">根据消息的重要性，将 DSC 日志拆分到三个日志通道。</span><span class="sxs-lookup"><span data-stu-id="162bf-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="162bf-138">DSC 中的运行日志包含所有错误消息，可用于确定问题。</span><span class="sxs-lookup"><span data-stu-id="162bf-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="162bf-139">分析日志包含更多事件，可确定错误出现的位置。</span><span class="sxs-lookup"><span data-stu-id="162bf-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="162bf-140">此通道还包含详细消息（若有）。</span><span class="sxs-lookup"><span data-stu-id="162bf-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="162bf-141">调试日志包含的日志可帮助你了解错误出现的过程。</span><span class="sxs-lookup"><span data-stu-id="162bf-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="162bf-142">DSC 事件消息的构成方式是，每个事件消息以表示唯一 DSC 操作的作业 ID 开头。</span><span class="sxs-lookup"><span data-stu-id="162bf-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="162bf-143">下面的示例尝试从记录到 DSC 操作日志的第一个事件获取消息。</span><span class="sxs-lookup"><span data-stu-id="162bf-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="162bf-144">以特定结构记录 DSC 事件，该结构让用户可以通过一个 DSC 作业聚合事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="162bf-145">结构如下：</span><span class="sxs-lookup"><span data-stu-id="162bf-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="162bf-146">通过单个 DSC 操作收集事件</span><span class="sxs-lookup"><span data-stu-id="162bf-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="162bf-147">DSC 事件日志包含由各种 DSC 操作生成的事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="162bf-148">但是，你通常只关心某一特定操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="162bf-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="162bf-149">可按作业 ID 属性对所有 DSC 日志进行分组，作业 ID 对每个 DSC 操作来说是唯一的。</span><span class="sxs-lookup"><span data-stu-id="162bf-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="162bf-150">作业 ID 显示为所有 DSC 事件中的第一个属性值。</span><span class="sxs-lookup"><span data-stu-id="162bf-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="162bf-151">下列步骤说明如何在一个分组数组结构中累计所有事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

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

<span data-ttu-id="162bf-152">此处，变量 `$SeparateDscOperations` 包含按作业 ID 分组的日志。</span><span class="sxs-lookup"><span data-stu-id="162bf-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="162bf-153">此变量的每个数组元素表示由不同的 DSC 操作记录的一组事件，让你可以访问有关日志的更多信息。</span><span class="sxs-lookup"><span data-stu-id="162bf-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="162bf-154">可以用 [Where-object](/powershell/module/microsoft.powershell.core/where-object) 提取变量 `$SeparateDscOperations` 中的数据。</span><span class="sxs-lookup"><span data-stu-id="162bf-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="162bf-155">在以下五种情况下，可能需要提取数据以解决 DSC 问题：</span><span class="sxs-lookup"><span data-stu-id="162bf-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="162bf-156">1：操作失败</span><span class="sxs-lookup"><span data-stu-id="162bf-156">1: Operations failures</span></span>

<span data-ttu-id="162bf-157">所有事件都具有[严重性级别](/windows/desktop/WES/defining-severity-levels)。</span><span class="sxs-lookup"><span data-stu-id="162bf-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="162bf-158">此信息可用于标识错误事件：</span><span class="sxs-lookup"><span data-stu-id="162bf-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="162bf-159">2:过去半小时内所运行操作的详细信息</span><span class="sxs-lookup"><span data-stu-id="162bf-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="162bf-160">每个 Windows 事件都具有 `TimeCreated` 属性，它表明创建该事件的时间。</span><span class="sxs-lookup"><span data-stu-id="162bf-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="162bf-161">可通过将此属性与特定日期/时间对象进行比较来筛选所有事件：</span><span class="sxs-lookup"><span data-stu-id="162bf-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="162bf-162">3：来自最新操作的消息</span><span class="sxs-lookup"><span data-stu-id="162bf-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="162bf-163">最新操作存储在数组组 `$SeparateDscOperations` 的第一个索引中。</span><span class="sxs-lookup"><span data-stu-id="162bf-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="162bf-164">查询索引 0 的组消息将返回最新操作的所有消息：</span><span class="sxs-lookup"><span data-stu-id="162bf-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="162bf-165">4：为最近的失败操作记录到的错误消息</span><span class="sxs-lookup"><span data-stu-id="162bf-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="162bf-166">`$SeparateDscOperations[0].Group` 包含最新操作的一组事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="162bf-167">运行 `Where-Object` cmdlet 可根据事件级别显示名称对筛选事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="162bf-168">结果将存储在 `$myFailedEvent` 变量中，可以进一步细化以获取事件消息：</span><span class="sxs-lookup"><span data-stu-id="162bf-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="162bf-169">5：为特定作业 ID 生成的所有事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="162bf-170">`$SeparateDscOperations` 是一个组数组，其中每个组的名称即其唯一作业 ID。</span><span class="sxs-lookup"><span data-stu-id="162bf-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="162bf-171">通过运行 `Where-Object` cmdlet，你可以提取这些具有特定作业 ID 的事件组：</span><span class="sxs-lookup"><span data-stu-id="162bf-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="162bf-172">使用 xDscDiagnostics 分析 DSC 日志</span><span class="sxs-lookup"><span data-stu-id="162bf-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="162bf-173">**xDscDiagnostics** 是由几个函数组成的 PowerShell 模块，这些函数可以帮助你分析计算机上的 DSC 失败。</span><span class="sxs-lookup"><span data-stu-id="162bf-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="162bf-174">这些函数可以帮助你确定因过去的 DSC 操作而起的所有本地事件，或（具有有效凭据的）远程计算机上的 DSC 事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="162bf-175">此处使用了“DSC 操作”这一术语来定义单个唯一的 DSC 执行过程。</span><span class="sxs-lookup"><span data-stu-id="162bf-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="162bf-176">例如，`Test-DscConfiguration` 将是一个单独的 DSC 操作。</span><span class="sxs-lookup"><span data-stu-id="162bf-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="162bf-177">同样，DSC 中每个其他 cmdlet （如 `Get-DscConfiguration`、`Start-DscConfiguration` 等）可各自识别为单独的 DSC 操作。</span><span class="sxs-lookup"><span data-stu-id="162bf-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="162bf-178">在 [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics) 中对函数进行了解释。</span><span class="sxs-lookup"><span data-stu-id="162bf-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="162bf-179">可通过运行 `Get-Help <cmdlet name>` 获取帮助。</span><span class="sxs-lookup"><span data-stu-id="162bf-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="162bf-180">获取 DSC 操作的详细信息</span><span class="sxs-lookup"><span data-stu-id="162bf-180">Getting details of DSC operations</span></span>

<span data-ttu-id="162bf-181">可通过 `Get-xDscOperation` 函数查找在一台或多台计算机上运行的 DSC 操作的结果，并返回一个包含每个 DSC 操作所产生事件的集合的对象。</span><span class="sxs-lookup"><span data-stu-id="162bf-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="162bf-182">例如，在下面的输出中，运行了三个命令。</span><span class="sxs-lookup"><span data-stu-id="162bf-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="162bf-183">第一个命令成功，另外两个失败。</span><span class="sxs-lookup"><span data-stu-id="162bf-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="162bf-184">在 `Get-xDscOperation` 的输出中总结了这些结果。</span><span class="sxs-lookup"><span data-stu-id="162bf-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="162bf-185">也可通过使用 `Newest` 参数指定你只需要最近操作的结果：</span><span class="sxs-lookup"><span data-stu-id="162bf-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="162bf-186">获取 DSC 事件的详细信息</span><span class="sxs-lookup"><span data-stu-id="162bf-186">Getting details of DSC events</span></span>

<span data-ttu-id="162bf-187">`Trace-xDscOperation` cmdlet 将返回一个对象，其中包含事件集合、其事件类型以及特定 DSC 操作生成的消息输出。</span><span class="sxs-lookup"><span data-stu-id="162bf-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="162bf-188">通常情况下，使用 `Get-xDscOperation` 在任何操作中查找故障时，将跟踪该操作以查明导致故障的事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="162bf-189">使用 `SequenceID` 参数以获取某个特定计算机的某个特定操作的事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="162bf-190">例如，如果你指定 9 的 `SequenceID`，则 `Trace-xDscOperaion` 获取 DSC 操作的跟踪（自上一次操作的第 9 个）：</span><span class="sxs-lookup"><span data-stu-id="162bf-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="162bf-191">传递分配给特定 DSC 操作（由 `Get-xDscOperation` cmdlet 返回）的 GUID  以获取 DSC 操作的事件详细信息：</span><span class="sxs-lookup"><span data-stu-id="162bf-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="162bf-192">请注意，由于 `Trace-xDscOperation` 聚合来自分析、调试和运行日志的事件，因此它将提示你启用这些日志，如上所述。</span><span class="sxs-lookup"><span data-stu-id="162bf-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="162bf-193">或者，你可以通过将 `Trace-xDscOperation` 的输出保存到变量中来收集关于事件的信息。</span><span class="sxs-lookup"><span data-stu-id="162bf-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="162bf-194">可使用以下命令显示特定 DSC 操作的所有事件。</span><span class="sxs-lookup"><span data-stu-id="162bf-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="162bf-195">此操作将显示与 `Get-WinEvent` cmdlet 相同的结果，例如以下输出中的结果：</span><span class="sxs-lookup"><span data-stu-id="162bf-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="162bf-196">理想情况下，你将首先使用 `Get-xDscOperation` 列出在计算机上运行的最后几个 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="162bf-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="162bf-197">此后，可以通过 `Trace-xDscOperation` 检查任意单个操作（使用其 SequenceID 或 JobID）以发现它在后台进行的活动。</span><span class="sxs-lookup"><span data-stu-id="162bf-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="162bf-198">获取远程计算机的事件</span><span class="sxs-lookup"><span data-stu-id="162bf-198">Getting events for a remote computer</span></span>

<span data-ttu-id="162bf-199">使用 `ComputerName` cmdlet 的 `Trace-xDscOperation` 参数以获取远程计算机上的事件详细信息。</span><span class="sxs-lookup"><span data-stu-id="162bf-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="162bf-200">执行此操作前，你需要创建一个防火墙规则，以允许在远程计算机上进行远程管理：</span><span class="sxs-lookup"><span data-stu-id="162bf-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="162bf-201">现在可以在你的调用中将计算机指定到 `Trace-xDscOperation`：</span><span class="sxs-lookup"><span data-stu-id="162bf-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="162bf-202">资源不更新：如何重置缓存</span><span class="sxs-lookup"><span data-stu-id="162bf-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="162bf-203">出于效率考虑，DSC 引擎将缓存作为 PowerShell 模块实现的资源。</span><span class="sxs-lookup"><span data-stu-id="162bf-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="162bf-204">但是，当你同时创作和测试资源时，这可能导致问题，因为在重启进程前，DSC 将始终加载缓存的版本。</span><span class="sxs-lookup"><span data-stu-id="162bf-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="162bf-205">使 DSC 加载较新版本的唯一方法是显式终止承载 DSC 引擎的进程。</span><span class="sxs-lookup"><span data-stu-id="162bf-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="162bf-206">同样，当你运行 `Start-DscConfiguration` 时，在添加和修改自定义资源之后，重启计算机之前可能无法执行修改。</span><span class="sxs-lookup"><span data-stu-id="162bf-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="162bf-207">这是因为 DSC 在 WMI 提供程序主机进程 (WmiPrvSE) 中运行，且通常情况下将有 WmiPrvSE 的多个实例同时运行。</span><span class="sxs-lookup"><span data-stu-id="162bf-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="162bf-208">重启时，将重新启动主机进程并清除缓存。</span><span class="sxs-lookup"><span data-stu-id="162bf-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="162bf-209">若要在不重启的情况下成功回收配置并清除缓存，必须停止并重新启动主机进程。</span><span class="sxs-lookup"><span data-stu-id="162bf-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="162bf-210">可按实例逐一进行此操作，在这些实例中标识、停止和重新启动该进程。</span><span class="sxs-lookup"><span data-stu-id="162bf-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="162bf-211">或者，你可以使用 `DebugMode` 来重新加载 PowerShell DSC 资源，如下所示。</span><span class="sxs-lookup"><span data-stu-id="162bf-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="162bf-212">若要确定承载 DSC 引擎的进程并按实例逐一停止它们，你可以列出承载 DSC 引擎的 WmiPrvSE 的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="162bf-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="162bf-213">然后，若要更新提供程序，请使用以下命令停止 WmiPrvSE 进程，并再次运行 **Start-DscConfiguration**。</span><span class="sxs-lookup"><span data-stu-id="162bf-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="162bf-214">使用 DebugMode</span><span class="sxs-lookup"><span data-stu-id="162bf-214">Using DebugMode</span></span>

<span data-ttu-id="162bf-215">可将 DSC 本地配置管理器 (LCM) 配置为使用 `DebugMode`，以便在重新启动主机进程时始终清除缓存。</span><span class="sxs-lookup"><span data-stu-id="162bf-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="162bf-216">当设置为 **TRUE**，它将使引擎始终重新加载 PowerShell DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="162bf-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="162bf-217">编写完资源后，可将其设置回 **FALSE**，引擎将恢复到其缓存模块的行为。</span><span class="sxs-lookup"><span data-stu-id="162bf-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="162bf-218">下列演示表明了 `DebugMode` 可以如何自动刷新缓存。</span><span class="sxs-lookup"><span data-stu-id="162bf-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="162bf-219">首先，让我们看一下默认配置：</span><span class="sxs-lookup"><span data-stu-id="162bf-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="162bf-220">可以看到 `DebugMode` 设置为“无”  。</span><span class="sxs-lookup"><span data-stu-id="162bf-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="162bf-221">若要设置 `DebugMode` 演示，请使用以下 PowerShell 资源：</span><span class="sxs-lookup"><span data-stu-id="162bf-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="162bf-222">现在，使用上述名为 `TestProviderDebugMode` 的资源创作配置：</span><span class="sxs-lookup"><span data-stu-id="162bf-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="162bf-223">你将看到文件的内容：`$env:SystemDrive\OutputFromTestProviderDebugMode.txt` 为 1  。</span><span class="sxs-lookup"><span data-stu-id="162bf-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="162bf-224">现在，使用以下脚本更新提供程序代码：</span><span class="sxs-lookup"><span data-stu-id="162bf-224">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="162bf-225">此脚本将生成一个随机数，并相应地更新提供程序代码。</span><span class="sxs-lookup"><span data-stu-id="162bf-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="162bf-226">将 `DebugMode` 设置为 false 后，文件“$env:SystemDrive\OutputFromTestProviderDebugMode.txt”  的内容未发生更改。</span><span class="sxs-lookup"><span data-stu-id="162bf-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="162bf-227">现在，在配置脚本中将 `DebugMode` 设置为“ForceModuleImport”  ：</span><span class="sxs-lookup"><span data-stu-id="162bf-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="162bf-228">再次运行上述脚本时，你将看到该文件的内容每次都不同。</span><span class="sxs-lookup"><span data-stu-id="162bf-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="162bf-229">（可运行 `Get-DscConfiguration` 以对其进行检查）。</span><span class="sxs-lookup"><span data-stu-id="162bf-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="162bf-230">以下是两次额外运行的结果（当你运行脚本时，结果可能不同）：</span><span class="sxs-lookup"><span data-stu-id="162bf-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a><span data-ttu-id="162bf-231">注册 Windows 拉取服务器时，DSC 返回“意外的响应代码 InternalServerError”</span><span class="sxs-lookup"><span data-stu-id="162bf-231">DSC returns "unexpected response code InternalServerError" when registering with Windows Pull Server</span></span>

<span data-ttu-id="162bf-232">将元配置应用于服务器以将其注册到 Windows 拉取服务器实例时，可能遇到以下错误。</span><span class="sxs-lookup"><span data-stu-id="162bf-232">When applying a metaconfiguration to a server to register it with an instance of Windows Pull Server, you might encounter the following error.</span></span>

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

<span data-ttu-id="162bf-233">当服务器上用于加密流量的证书公用名称 (CN) 不同于节点用于解析 URL 的 DNS 名称时，可能发生此情况。</span><span class="sxs-lookup"><span data-stu-id="162bf-233">This can occur when the certificate used on the server to encrypt traffic has a common name (CN) that is different than the DNS name used by the node to resolve the URL.</span></span>
<span data-ttu-id="162bf-234">更新 Windows 拉取服务器实例，使用名称正确的证书。</span><span class="sxs-lookup"><span data-stu-id="162bf-234">Update the Windows Pull Server instance to use a certificate with a corrected name.</span></span>

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a><span data-ttu-id="162bf-235">在应用 DSC 配置后应用 Sysprep 时出错</span><span class="sxs-lookup"><span data-stu-id="162bf-235">Error when running Sysprep after applying a DSC Configuration</span></span>

<span data-ttu-id="162bf-236">应用 DSC 配置后尝试运行 Sysprep 来通用化 Windows Server 时，你可能会遇到以下问题。</span><span class="sxs-lookup"><span data-stu-id="162bf-236">When attempting to run Sysprep to generalize a Windows Server after applying a DSC configuration, you might encounter the following error.</span></span>

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

<span data-ttu-id="162bf-237">不支持在使用 Windows PowerShell Desired State Configuration 配置后通用化服务器。</span><span class="sxs-lookup"><span data-stu-id="162bf-237">Generalizing a server after it has been configured using Windows PowerShell Desired State Configuration is not a supported scenario.</span></span>  <span data-ttu-id="162bf-238">转而，请在完成 Windows 设置的通用化阶段后将配置应用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="162bf-238">Instead, apply configurations to Windows after the Specialize phase of Windows Setup has completed.</span></span>

## <a name="see-also"></a><span data-ttu-id="162bf-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="162bf-239">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="162bf-240">概念</span><span class="sxs-lookup"><span data-stu-id="162bf-240">Concepts</span></span>

- [<span data-ttu-id="162bf-241">构建自定义 Windows PowerShell Desired State Configuration 资源</span><span class="sxs-lookup"><span data-stu-id="162bf-241">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="162bf-242">其他资源</span><span class="sxs-lookup"><span data-stu-id="162bf-242">Other Resources</span></span>

- [<span data-ttu-id="162bf-243">Windows PowerShell Desired State Configuration Cmdlet</span><span class="sxs-lookup"><span data-stu-id="162bf-243">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)

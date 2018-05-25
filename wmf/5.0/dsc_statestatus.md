---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 7b4e4dbeaf9c3c48e7b2dfc74435dfa2cd9c7ea7
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="500d7-102">统一且一致的状态和状态表示形式</span><span class="sxs-lookup"><span data-stu-id="500d7-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="500d7-103">在此版本中，增加了一系列自动化构建 LCM 状态和 DSC 状态的增强功能。</span><span class="sxs-lookup"><span data-stu-id="500d7-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="500d7-104">其中包括统一且一致的状态和状态表示形式：Get-DscConfigurationStatus cmdlet 所返回状态对象的可管理日期时间属性和 Get-DscLocalConfigurationManager cmdlet 所返回增强的 LCM 状态详细信息属性。</span><span class="sxs-lookup"><span data-stu-id="500d7-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by Get-DscConfigurationStatus cmdlet and enhanced LCM state details property returned by Get-DscLocalConfigurationManager cmdlet.</span></span>

<span data-ttu-id="500d7-105">根据下列规则再次访问并统一了 LCM 状态和 DSC 操作状态的表示形式：</span><span class="sxs-lookup"><span data-stu-id="500d7-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>
1.  <span data-ttu-id="500d7-106">Notprocessed 资源不会影响 LCM 状态和 DSC 状态。</span><span class="sxs-lookup"><span data-stu-id="500d7-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2.  <span data-ttu-id="500d7-107">一旦 LCM 遇到请求重新启动的资源，它将停止处理更多资源。</span><span class="sxs-lookup"><span data-stu-id="500d7-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3.  <span data-ttu-id="500d7-108">直到实重新启动实际发生，请求重新启动的资源才处于所需状态。</span><span class="sxs-lookup"><span data-stu-id="500d7-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4.  <span data-ttu-id="500d7-109">出现失败的资源后，LCM 将继续处理更多资源（只要这些资源不依赖于失败的资源）。</span><span class="sxs-lookup"><span data-stu-id="500d7-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5.  <span data-ttu-id="500d7-110">Get-DscConfigurationStatus cmdlet 返回的总体状态是所有资源状态的超集。</span><span class="sxs-lookup"><span data-stu-id="500d7-110">The overall status returned by Get-DscConfigurationStatus cmdlet is the super set of all resources' status.</span></span>
6.  <span data-ttu-id="500d7-111">PendingReboot 状态是 PendingConfiguration 状态的超集。</span><span class="sxs-lookup"><span data-stu-id="500d7-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="500d7-112">下表说明了在使用典型方案时产生的状态和与状态关联属性。</span><span class="sxs-lookup"><span data-stu-id="500d7-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="500d7-113">方案</span><span class="sxs-lookup"><span data-stu-id="500d7-113">Scenario</span></span>                    | <span data-ttu-id="500d7-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="500d7-114">LCMState</span></span>       | <span data-ttu-id="500d7-115">状态</span><span class="sxs-lookup"><span data-stu-id="500d7-115">Status</span></span> | <span data-ttu-id="500d7-116">请求重新启动</span><span class="sxs-lookup"><span data-stu-id="500d7-116">Reboot Requested</span></span>  | <span data-ttu-id="500d7-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="500d7-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="500d7-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="500d7-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="500d7-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="500d7-119">S**^**</span></span>                          | <span data-ttu-id="500d7-120">空闲</span><span class="sxs-lookup"><span data-stu-id="500d7-120">Idle</span></span>                 | <span data-ttu-id="500d7-121">Success</span><span class="sxs-lookup"><span data-stu-id="500d7-121">Success</span></span>    | <span data-ttu-id="500d7-122">$false</span><span class="sxs-lookup"><span data-stu-id="500d7-122">$false</span></span>        | <span data-ttu-id="500d7-123">S</span><span class="sxs-lookup"><span data-stu-id="500d7-123">S</span></span>                            | <span data-ttu-id="500d7-124">$null</span><span class="sxs-lookup"><span data-stu-id="500d7-124">$null</span></span>                          |
| <span data-ttu-id="500d7-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="500d7-125">F**^**</span></span>                          | <span data-ttu-id="500d7-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="500d7-126">PendingConfiguration</span></span> | <span data-ttu-id="500d7-127">失败</span><span class="sxs-lookup"><span data-stu-id="500d7-127">Failure</span></span>    | <span data-ttu-id="500d7-128">$false</span><span class="sxs-lookup"><span data-stu-id="500d7-128">$false</span></span>        | <span data-ttu-id="500d7-129">$null</span><span class="sxs-lookup"><span data-stu-id="500d7-129">$null</span></span>                        | <span data-ttu-id="500d7-130">F</span><span class="sxs-lookup"><span data-stu-id="500d7-130">F</span></span>                              |
| <span data-ttu-id="500d7-131">S、F</span><span class="sxs-lookup"><span data-stu-id="500d7-131">S,F</span></span>                             | <span data-ttu-id="500d7-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="500d7-132">PendingConfiguration</span></span> | <span data-ttu-id="500d7-133">失败</span><span class="sxs-lookup"><span data-stu-id="500d7-133">Failure</span></span>    | <span data-ttu-id="500d7-134">$false</span><span class="sxs-lookup"><span data-stu-id="500d7-134">$false</span></span>        | <span data-ttu-id="500d7-135">S</span><span class="sxs-lookup"><span data-stu-id="500d7-135">S</span></span>                            | <span data-ttu-id="500d7-136">F</span><span class="sxs-lookup"><span data-stu-id="500d7-136">F</span></span>                              |
| <span data-ttu-id="500d7-137">F、S</span><span class="sxs-lookup"><span data-stu-id="500d7-137">F,S</span></span>                             | <span data-ttu-id="500d7-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="500d7-138">PendingConfiguration</span></span> | <span data-ttu-id="500d7-139">失败</span><span class="sxs-lookup"><span data-stu-id="500d7-139">Failure</span></span>    | <span data-ttu-id="500d7-140">$false</span><span class="sxs-lookup"><span data-stu-id="500d7-140">$false</span></span>        | <span data-ttu-id="500d7-141">S</span><span class="sxs-lookup"><span data-stu-id="500d7-141">S</span></span>                            | <span data-ttu-id="500d7-142">F</span><span class="sxs-lookup"><span data-stu-id="500d7-142">F</span></span>                              |
| <span data-ttu-id="500d7-143">S<sub>1</sub>、F、S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="500d7-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="500d7-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="500d7-144">PendingConfiguration</span></span> | <span data-ttu-id="500d7-145">失败</span><span class="sxs-lookup"><span data-stu-id="500d7-145">Failure</span></span>    | <span data-ttu-id="500d7-146">$false</span><span class="sxs-lookup"><span data-stu-id="500d7-146">$false</span></span>        | <span data-ttu-id="500d7-147">S<sub>1</sub>、S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="500d7-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="500d7-148">F</span><span class="sxs-lookup"><span data-stu-id="500d7-148">F</span></span>                              |
| <span data-ttu-id="500d7-149">F<sub>1</sub>、S、F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="500d7-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="500d7-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="500d7-150">PendingConfiguration</span></span> | <span data-ttu-id="500d7-151">失败</span><span class="sxs-lookup"><span data-stu-id="500d7-151">Failure</span></span>    | <span data-ttu-id="500d7-152">$false</span><span class="sxs-lookup"><span data-stu-id="500d7-152">$false</span></span>        | <span data-ttu-id="500d7-153">S</span><span class="sxs-lookup"><span data-stu-id="500d7-153">S</span></span>                            | <span data-ttu-id="500d7-154">F<sub>1</sub>、F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="500d7-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="500d7-155">S、r</span><span class="sxs-lookup"><span data-stu-id="500d7-155">S, r</span></span>                            | <span data-ttu-id="500d7-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="500d7-156">PendingReboot</span></span>        | <span data-ttu-id="500d7-157">Success</span><span class="sxs-lookup"><span data-stu-id="500d7-157">Success</span></span>    | <span data-ttu-id="500d7-158">$true</span><span class="sxs-lookup"><span data-stu-id="500d7-158">$true</span></span>         | <span data-ttu-id="500d7-159">S</span><span class="sxs-lookup"><span data-stu-id="500d7-159">S</span></span>                            | <span data-ttu-id="500d7-160">r</span><span class="sxs-lookup"><span data-stu-id="500d7-160">r</span></span>                              |
| <span data-ttu-id="500d7-161">F、r</span><span class="sxs-lookup"><span data-stu-id="500d7-161">F, r</span></span>                            | <span data-ttu-id="500d7-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="500d7-162">PendingReboot</span></span>        | <span data-ttu-id="500d7-163">失败</span><span class="sxs-lookup"><span data-stu-id="500d7-163">Failure</span></span>    | <span data-ttu-id="500d7-164">$true</span><span class="sxs-lookup"><span data-stu-id="500d7-164">$true</span></span>         | <span data-ttu-id="500d7-165">$null</span><span class="sxs-lookup"><span data-stu-id="500d7-165">$null</span></span>                        | <span data-ttu-id="500d7-166">F、r</span><span class="sxs-lookup"><span data-stu-id="500d7-166">F, r</span></span>                           |
| <span data-ttu-id="500d7-167">r、S</span><span class="sxs-lookup"><span data-stu-id="500d7-167">r, S</span></span>                            | <span data-ttu-id="500d7-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="500d7-168">PendingReboot</span></span>        | <span data-ttu-id="500d7-169">Success</span><span class="sxs-lookup"><span data-stu-id="500d7-169">Success</span></span>    | <span data-ttu-id="500d7-170">$true</span><span class="sxs-lookup"><span data-stu-id="500d7-170">$true</span></span>         | <span data-ttu-id="500d7-171">$null</span><span class="sxs-lookup"><span data-stu-id="500d7-171">$null</span></span>                        | <span data-ttu-id="500d7-172">r</span><span class="sxs-lookup"><span data-stu-id="500d7-172">r</span></span>                              |
| <span data-ttu-id="500d7-173">r、F</span><span class="sxs-lookup"><span data-stu-id="500d7-173">r, F</span></span>                            | <span data-ttu-id="500d7-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="500d7-174">PendingReboot</span></span>        | <span data-ttu-id="500d7-175">Success</span><span class="sxs-lookup"><span data-stu-id="500d7-175">Success</span></span>    | <span data-ttu-id="500d7-176">$true</span><span class="sxs-lookup"><span data-stu-id="500d7-176">$true</span></span>         | <span data-ttu-id="500d7-177">$null</span><span class="sxs-lookup"><span data-stu-id="500d7-177">$null</span></span>                        | <span data-ttu-id="500d7-178">r</span><span class="sxs-lookup"><span data-stu-id="500d7-178">r</span></span>                              |

<span data-ttu-id="500d7-179">^ S<sub>i</sub>：一系列成功应用的资源 F<sub>i</sub>：一系列应用失败的资源 r：要求重启的资源 \*</span><span class="sxs-lookup"><span data-stu-id="500d7-179">^ S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="500d7-180">Get-DscConfigurationStatus cmdlet 中的增强功能</span><span class="sxs-lookup"><span data-stu-id="500d7-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="500d7-181">在此版本中，对 Get DscConfigurationStatus cmdlet 进行了几处改进。</span><span class="sxs-lookup"><span data-stu-id="500d7-181">A few enhancements have been made to Get-DscConfigurationStatus cmdlet in this release.</span></span> <span data-ttu-id="500d7-182">以前，该 cmdlet 返回的对象的 StartDate 属性是 String 类型。</span><span class="sxs-lookup"><span data-stu-id="500d7-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="500d7-183">现在，它是 Datetime 类型，从而可以根据 Datetime 对象的内部属性更轻松地进行复杂选择和筛选。</span><span class="sxs-lookup"><span data-stu-id="500d7-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | fl *
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

<span data-ttu-id="500d7-184">以下示例返回与今天处于一周中同一天的日子里产生的所有 DSC 操作记录。</span><span class="sxs-lookup"><span data-stu-id="500d7-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | where { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="500d7-185">将消除不更改节点配置的操作（即只读操作）的记录。</span><span class="sxs-lookup"><span data-stu-id="500d7-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="500d7-186">因此，Test-DscConfiguration、Get-DscConfiguration 操作将不再掺杂在从 Get-DscConfigurationStatus cmdlet 返回的对象中。</span><span class="sxs-lookup"><span data-stu-id="500d7-186">Therefore, Test-DscConfiguration, Get-DscConfiguration operations are no longer adulterated in returned objects from Get-DscConfigurationStatus cmdlet.</span></span>
<span data-ttu-id="500d7-187">元配置设置操作的记录将添加到 Get-DscConfigurationStatus cmdlet 的返回结果中。</span><span class="sxs-lookup"><span data-stu-id="500d7-187">Records of meta configuration setting operation is added to the return of Get-DscConfigurationStatus cmdlet.</span></span>

<span data-ttu-id="500d7-188">下面是从 Get-DscConfigurationStatus –All cmdlet 返回结果的示例。</span><span class="sxs-lookup"><span data-stu-id="500d7-188">Following is an example of result returned from Get-DscConfigurationStatus –All cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="500d7-189">Get-DscLocalConfigurationManager cmdlet 中的增强功能</span><span class="sxs-lookup"><span data-stu-id="500d7-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="500d7-190">新字段 LCMStateDetail 已添加到从 Get-DscLocalConfigurationManager cmdlet 返回的对象。</span><span class="sxs-lookup"><span data-stu-id="500d7-190">A new field of LCMStateDetail is added to the object returned from Get-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="500d7-191">LCMState 为“忙碌”时，填充此字段。</span><span class="sxs-lookup"><span data-stu-id="500d7-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="500d7-192">它可以通过以下 cmdlet 来检索：</span><span class="sxs-lookup"><span data-stu-id="500d7-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="500d7-193">下面是对需要两次重新启动远程节点的配置所进行持续监视的示例输出。</span><span class="sxs-lookup"><span data-stu-id="500d7-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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

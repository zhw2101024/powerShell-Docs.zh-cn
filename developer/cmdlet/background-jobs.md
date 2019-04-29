---
title: 后台作业 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068666"
---
# <a name="background-jobs"></a><span data-ttu-id="7b2cb-102">后台作业</span><span class="sxs-lookup"><span data-stu-id="7b2cb-102">Background Jobs</span></span>

<span data-ttu-id="7b2cb-103">在内部或者作为 Windows PowerShell，Cmdlet 可以执行其操作*后台作业*。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="7b2cb-104">Cmdlet 运行时作为后台作业，则会在其自己独立于使用该 cmdlet 的管道线程的线程以异步方式完成工作。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="7b2cb-105">从用户角度来看，当一个 cmdlet 作为后台作业，在运行时命令提示符下立即返回即使作业需要花费一段较的长的时间才能完成，并且该作业运行时，用户可以继续而不发生中断。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="7b2cb-106">后台作业、 子作业和作业存储库</span><span class="sxs-lookup"><span data-stu-id="7b2cb-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="7b2cb-107">支持后台作业的 cmdlet 返回的作业对象定义的作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="7b2cb-108">( [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet 也会返回作业对象。)在此定义中包含的作业，用于指定作业、 状态信息，以及子作业的标识符名称。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="7b2cb-109">该作业不执行任何工作。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-109">The job does not perform any of the work.</span></span> <span data-ttu-id="7b2cb-110">每个后台作业具有至少一个子作业，因为子作业执行的实际工作。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="7b2cb-111">当您运行某个 cmdlet，以便作为后台作业执行工作时，该 cmdlet 必须添加作业和子作业到公共存储库，称为*作业存储库*。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="7b2cb-112">有关如何在命令行处理后台作业的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="7b2cb-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="7b2cb-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="7b2cb-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="7b2cb-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="7b2cb-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="7b2cb-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="7b2cb-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="7b2cb-116">编写 Cmdlet 作为后台作业运行</span><span class="sxs-lookup"><span data-stu-id="7b2cb-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="7b2cb-117">若要编写可作为后台作业运行的 cmdlet，必须完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="7b2cb-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="7b2cb-118">定义`asJob`切换参数，以便用户可以决定是否要运行该 cmdlet 作为后台作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="7b2cb-119">创建派生的对象[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)类。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="7b2cb-120">此对象可以是自定义作业对象或作业对象提供通过 Windows PowerShell 中，如[System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob)对象。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="7b2cb-121">在记录的处理方法中，添加`if`检测到该 cmdlet 是否应作为后台作业运行的语句。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="7b2cb-122">对于自定义作业的对象，实现作业类。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="7b2cb-123">返回相应的对象，具体取决于是否作为后台作业运行该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="7b2cb-124">有关代码示例，请参阅[如何支持作业](./how-to-support-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="7b2cb-125">后台作业相关的 Api</span><span class="sxs-lookup"><span data-stu-id="7b2cb-125">Background Job-Related APIs</span></span>

<span data-ttu-id="7b2cb-126">以下 Api 提供了 Windows PowerShell 来管理后台作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="7b2cb-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)派生自定义作业对象。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="7b2cb-128">这是一个抽象类。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-128">This is an abstract class.</span></span>

<span data-ttu-id="7b2cb-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository)管理，并提供有关当前活动的后台作业的信息。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="7b2cb-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState)定义后台作业的状态。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="7b2cb-131">状态包括启动、 正在运行，且已停止。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="7b2cb-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo)提供有关后台作业的状态信息，并且如果最后一个状态更改错误导致的，该作业进入其当前状态的原因。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="7b2cb-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs)提供后台作业更改状态时引发的事件参数。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="7b2cb-134">Windows PowerShell 作业 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7b2cb-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="7b2cb-135">以下 cmdlet 提供了 Windows PowerShell 来管理后台作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="7b2cb-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="7b2cb-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="7b2cb-137">获取在当前会话中运行的 Windows PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="7b2cb-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="7b2cb-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="7b2cb-139">获取当前会话中的 Windows PowerShell 后台作业的结果。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="7b2cb-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="7b2cb-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="7b2cb-141">删除 Windows PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7b2cb-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="7b2cb-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="7b2cb-143">启动 Windows PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7b2cb-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="7b2cb-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="7b2cb-145">停止 Windows PowerShell 后台作业。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7b2cb-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="7b2cb-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="7b2cb-147">禁止显示命令提示符，直到在会话中运行的一个或全部 Windows PowerShell 后台作业完成。</span><span class="sxs-lookup"><span data-stu-id="7b2cb-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b2cb-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b2cb-148">See Also</span></span>

[<span data-ttu-id="7b2cb-149">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7b2cb-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

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
# <a name="background-jobs"></a>后台作业

在内部或者作为 Windows PowerShell，Cmdlet 可以执行其操作*后台作业*。 Cmdlet 运行时作为后台作业，则会在其自己独立于使用该 cmdlet 的管道线程的线程以异步方式完成工作。 从用户角度来看，当一个 cmdlet 作为后台作业，在运行时命令提示符下立即返回即使作业需要花费一段较的长的时间才能完成，并且该作业运行时，用户可以继续而不发生中断。

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>后台作业、 子作业和作业存储库

支持后台作业的 cmdlet 返回的作业对象定义的作业。 ( [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet 也会返回作业对象。)在此定义中包含的作业，用于指定作业、 状态信息，以及子作业的标识符名称。 该作业不执行任何工作。 每个后台作业具有至少一个子作业，因为子作业执行的实际工作。 当您运行某个 cmdlet，以便作为后台作业执行工作时，该 cmdlet 必须添加作业和子作业到公共存储库，称为*作业存储库*。

有关如何在命令行处理后台作业的详细信息，请参阅：

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>编写 Cmdlet 作为后台作业运行

若要编写可作为后台作业运行的 cmdlet，必须完成以下任务：

- 定义`asJob`切换参数，以便用户可以决定是否要运行该 cmdlet 作为后台作业。

- 创建派生的对象[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)类。 此对象可以是自定义作业对象或作业对象提供通过 Windows PowerShell 中，如[System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob)对象。

- 在记录的处理方法中，添加`if`检测到该 cmdlet 是否应作为后台作业运行的语句。

- 对于自定义作业的对象，实现作业类。

- 返回相应的对象，具体取决于是否作为后台作业运行该 cmdlet。

有关代码示例，请参阅[如何支持作业](./how-to-support-jobs.md)。

## <a name="background-job-related-apis"></a>后台作业相关的 Api

以下 Api 提供了 Windows PowerShell 来管理后台作业。

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)派生自定义作业对象。 这是一个抽象类。

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository)管理，并提供有关当前活动的后台作业的信息。

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState)定义后台作业的状态。 状态包括启动、 正在运行，且已停止。

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo)提供有关后台作业的状态信息，并且如果最后一个状态更改错误导致的，该作业进入其当前状态的原因。

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs)提供后台作业更改状态时引发的事件参数。

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell 作业 Cmdlet

以下 cmdlet 提供了 Windows PowerShell 来管理后台作业。

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

获取在当前会话中运行的 Windows PowerShell 后台作业。

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

获取当前会话中的 Windows PowerShell 后台作业的结果。

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

删除 Windows PowerShell 后台作业。

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

启动 Windows PowerShell 后台作业。

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

停止 Windows PowerShell 后台作业。

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

禁止显示命令提示符，直到在会话中运行的一个或全部 Windows PowerShell 后台作业完成。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

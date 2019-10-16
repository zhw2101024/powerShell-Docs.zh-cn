---
title: Cmdlet 输入处理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369866"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="115a4-102">Cmdlet 输入处理方法</span><span class="sxs-lookup"><span data-stu-id="115a4-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="115a4-103">Cmdlet 必须重写本主题中描述的一个或多个输入处理方法，以执行其工作。</span><span class="sxs-lookup"><span data-stu-id="115a4-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="115a4-104">这些方法允许 cmdlet 执行预处理、输入处理和后期处理操作。</span><span class="sxs-lookup"><span data-stu-id="115a4-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="115a4-105">这些方法还允许你停止 cmdlet 处理。</span><span class="sxs-lookup"><span data-stu-id="115a4-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="115a4-106">有关如何使用这些方法的更详细示例，请参阅[SelectStr 教程](selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="115a4-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="115a4-107">预处理操作</span><span class="sxs-lookup"><span data-stu-id="115a4-107">Pre-Processing Operations</span></span>

<span data-ttu-id="115a4-108">Cmdlet 应重写[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，以添加对将在以后由 Cmdlet 处理的所有记录有效的任何预处理操作。</span><span class="sxs-lookup"><span data-stu-id="115a4-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="115a4-109">当 PowerShell 处理命令管道时，PowerShell 将为管道中的每个 cmdlet 实例调用一次此方法。</span><span class="sxs-lookup"><span data-stu-id="115a4-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="115a4-110">有关 PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="115a4-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="115a4-111">下面的代码演示 BeginProcessing 方法的实现。</span><span class="sxs-lookup"><span data-stu-id="115a4-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="115a4-112">输入处理操作</span><span class="sxs-lookup"><span data-stu-id="115a4-112">Input Processing Operations</span></span>

<span data-ttu-id="115a4-113">Cmdlet 可以重写[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以处理发送到 Cmdlet 的输入的。</span><span class="sxs-lookup"><span data-stu-id="115a4-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="115a4-114">当 PowerShell 处理命令管道时，PowerShell 将为 cmdlet 处理的每个输入记录调用此方法。</span><span class="sxs-lookup"><span data-stu-id="115a4-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="115a4-115">有关 PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="115a4-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="115a4-116">下面的代码演示 ProcessRecord 方法的实现。</span><span class="sxs-lookup"><span data-stu-id="115a4-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="115a4-117">后处理操作</span><span class="sxs-lookup"><span data-stu-id="115a4-117">Post-Processing Operations</span></span>

<span data-ttu-id="115a4-118">Cmdlet 应重写[system.exception 方法，](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)以添加对 Cmdlet 所处理的所有记录有效的任何后续处理后操作。</span><span class="sxs-lookup"><span data-stu-id="115a4-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="115a4-119">例如，你的 cmdlet 可能需要在完成处理后清理对象变量。</span><span class="sxs-lookup"><span data-stu-id="115a4-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="115a4-120">当 PowerShell 处理命令管道时，PowerShell 将为管道中的每个 cmdlet 实例调用一次此方法。</span><span class="sxs-lookup"><span data-stu-id="115a4-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="115a4-121">但是，请务必记住，如果通过其输入处理中途取消 cmdlet，或者在 cmdlet 的任何部分中发生终止错误，则 PowerShell 运行时将不会调用 EndProcessing 方法。</span><span class="sxs-lookup"><span data-stu-id="115a4-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="115a4-122">出于此原因，需要对象清理的 cmdlet 应该实现完整的[IDisposable](/dotnet/api/System.IDisposable)模式（包括一个终结器），以便运行时可以在末尾调用 EndProcessing 和 IDisposable 方法[。](/dotnet/api/System.IDisposable.Dispose)字处理.</span><span class="sxs-lookup"><span data-stu-id="115a4-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="115a4-123">有关 PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](/previous-versions/ms714429(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="115a4-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="115a4-124">下面的代码演示了 EndProcessing 方法的实现。</span><span class="sxs-lookup"><span data-stu-id="115a4-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="115a4-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="115a4-125">See Also</span></span>

[<span data-ttu-id="115a4-126">"BeginProcessing"。</span><span class="sxs-lookup"><span data-stu-id="115a4-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="115a4-127">"ProcessRecord"。</span><span class="sxs-lookup"><span data-stu-id="115a4-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="115a4-128">System.web. EndProcessing. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="115a4-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="115a4-129">SelectStr 教程</span><span class="sxs-lookup"><span data-stu-id="115a4-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="115a4-130">IDisposable</span><span class="sxs-lookup"><span data-stu-id="115a4-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="115a4-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="115a4-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)

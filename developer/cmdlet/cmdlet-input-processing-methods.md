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
ms.openlocfilehash: dfaaa19fd3d4eb65a3fd335fb984a69874688f27
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861483"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="dfa33-102">Cmdlet 输入处理方法</span><span class="sxs-lookup"><span data-stu-id="dfa33-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="dfa33-103">一个或多个输入处理方法来执行其工作本主题中所述，必须重写 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dfa33-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="dfa33-104">这些方法允许 cmdlet 来执行预处理操作、 输入处理操作和后期处理操作。</span><span class="sxs-lookup"><span data-stu-id="dfa33-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="dfa33-105">这些方法还允许您停止 cmdlet 处理。</span><span class="sxs-lookup"><span data-stu-id="dfa33-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="dfa33-106">预处理任务</span><span class="sxs-lookup"><span data-stu-id="dfa33-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="dfa33-107">Cmdlet 应重写[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法中添加任何有效的该 cmdlet 将更高版本处理的所有记录的预处理操作。</span><span class="sxs-lookup"><span data-stu-id="dfa33-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="dfa33-108">当 Windows PowerShell 处理命令管道时，Windows PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。</span><span class="sxs-lookup"><span data-stu-id="dfa33-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="dfa33-109">有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="dfa33-110">下面的代码演示一种实现[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="dfa33-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="dfa33-111">有关如何使用的更多详细示例[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法，请参阅[SelectStr 教程](./selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="dfa33-112">在本教程中，**选择 Str** cmdlet 使用[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法生成用于搜索的输入处理记录的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="dfa33-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="dfa33-113">输入处理任务</span><span class="sxs-lookup"><span data-stu-id="dfa33-113">Input Processing Tasks</span></span>

<span data-ttu-id="dfa33-114">Cmdlet 可以重写[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法来处理发送到该 cmdlet 的输入。</span><span class="sxs-lookup"><span data-stu-id="dfa33-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="dfa33-115">当 Windows PowerShell 处理命令管道时，Windows PowerShell cmdlet 处理每个输入记录调用此方法。</span><span class="sxs-lookup"><span data-stu-id="dfa33-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="dfa33-116">有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>
<span data-ttu-id="dfa33-117">Cmdlet 可以重写[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法来处理发送到该 cmdlet 的输入。</span><span class="sxs-lookup"><span data-stu-id="dfa33-117">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="dfa33-118">当 Windows PowerShell 处理命令管道时，Windows PowerShell cmdlet 处理每个输入记录调用此方法。</span><span class="sxs-lookup"><span data-stu-id="dfa33-118">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="dfa33-119">有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-119">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="dfa33-120">下面的代码演示一种实现[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="dfa33-120">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="dfa33-121">有关如何使用的更多详细示例[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，请参阅[SelectStr 教程](./selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-121">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="dfa33-122">后续处理任务</span><span class="sxs-lookup"><span data-stu-id="dfa33-122">Post-Processing Tasks</span></span>

<span data-ttu-id="dfa33-123">Cmdlet 应重写[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法添加有效的 cmdlet 已处理的所有记录的任何后续处理操作。</span><span class="sxs-lookup"><span data-stu-id="dfa33-123">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="dfa33-124">例如，你的 cmdlet 可能需要在完成后清理对象变量处理。</span><span class="sxs-lookup"><span data-stu-id="dfa33-124">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="dfa33-125">当 Windows PowerShell 处理命令管道时，Windows PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。</span><span class="sxs-lookup"><span data-stu-id="dfa33-125">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="dfa33-126">但是，务必记住，Windows PowerShell 运行时将不会调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法，如果该 cmdlet 通过其输入处理正中取消或如果终止该 cmdlet 的任何部分中会发生错误。</span><span class="sxs-lookup"><span data-stu-id="dfa33-126">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="dfa33-127">出于此原因，应实现完整的 cmdlet，需要对象清理[System.Idisposable](/dotnet/api/System.IDisposable)模式，包括一个终结器，以便在运行时可以同时调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)并[System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)末尾的处理方法。</span><span class="sxs-lookup"><span data-stu-id="dfa33-127">For this reason, a cmdlet that requires object cleanup should implement the complete [System.Idisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="dfa33-128">有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-128">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>
<span data-ttu-id="dfa33-129">当 Windows PowerShell 处理命令管道时，Windows PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。</span><span class="sxs-lookup"><span data-stu-id="dfa33-129">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="dfa33-130">但是，务必记住，Windows PowerShell 运行时将不会调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法，如果该 cmdlet 通过其输入处理正中取消或如果终止该 cmdlet 的任何部分中会发生错误。</span><span class="sxs-lookup"><span data-stu-id="dfa33-130">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="dfa33-131">出于此原因，应实现完整的 cmdlet，需要对象清理[System.Idisposable](/dotnet/api/System.IDisposable)模式，包括一个终结器，以便在运行时可以同时调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)并[System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)末尾的处理方法。</span><span class="sxs-lookup"><span data-stu-id="dfa33-131">For this reason, a cmdlet that requires object cleanup should implement the complete [System.Idisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="dfa33-132">有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-132">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="dfa33-133">下面的代码演示一种实现[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="dfa33-133">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="dfa33-134">有关如何使用的更多详细示例[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，请参阅[SelectStr 教程](./selectstr-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="dfa33-134">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa33-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dfa33-135">See Also</span></span>

[<span data-ttu-id="dfa33-136">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="dfa33-136">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="dfa33-137">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="dfa33-137">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="dfa33-138">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="dfa33-138">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="dfa33-139">System.Idisposable</span><span class="sxs-lookup"><span data-stu-id="dfa33-139">System.Idisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="dfa33-140">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="dfa33-140">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)

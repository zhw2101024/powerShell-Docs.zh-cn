---
title: Cmdlet 错误报告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986318"
---
# <a name="cmdlet-error-reporting"></a><span data-ttu-id="49564-102">Cmdlet 错误报告</span><span class="sxs-lookup"><span data-stu-id="49564-102">Cmdlet error reporting</span></span>

<span data-ttu-id="49564-103">根据错误是终止错误还是非终止错误, cmdlet 应以不同的方式报告错误。</span><span class="sxs-lookup"><span data-stu-id="49564-103">Cmdlets should report errors differently depending on whether the errors are terminating errors or nonterminating errors.</span></span> <span data-ttu-id="49564-104">终止错误是导致管道立即终止的错误, 或在没有理由继续处理时所发生的错误。</span><span class="sxs-lookup"><span data-stu-id="49564-104">Terminating errors are errors that cause the pipeline to be terminated immediately, or errors that occur when there's no reason to continue processing.</span></span> <span data-ttu-id="49564-105">非终止错误是报告当前错误情况的错误, 但该 cmdlet 可以继续处理输入对象。</span><span class="sxs-lookup"><span data-stu-id="49564-105">Nonterminating errors are those errors that report a current error condition, but the cmdlet can continue to process input objects.</span></span> <span data-ttu-id="49564-106">对于非终止错误, 用户通常会收到有关问题的通知, 但 cmdlet 会继续处理下一个输入对象。</span><span class="sxs-lookup"><span data-stu-id="49564-106">With nonterminating errors, the user is typically notified of the problem, but the cmdlet continues to process the next input object.</span></span>

## <a name="terminating-and-nonterminating-errors"></a><span data-ttu-id="49564-107">终止和非终止错误</span><span class="sxs-lookup"><span data-stu-id="49564-107">Terminating and nonterminating errors</span></span>

<span data-ttu-id="49564-108">以下准则可用于确定错误条件是终止错误还是非终止错误。</span><span class="sxs-lookup"><span data-stu-id="49564-108">The following guidelines can be used to determine if an error condition is a terminating error or a nonterminating error.</span></span>

- <span data-ttu-id="49564-109">错误情况是否会阻止 cmdlet 成功处理任何其他输入对象？</span><span class="sxs-lookup"><span data-stu-id="49564-109">Does the error condition prevent your cmdlet from successfully processing any further input objects?</span></span> <span data-ttu-id="49564-110">如果是这样, 则这是一个终止错误。</span><span class="sxs-lookup"><span data-stu-id="49564-110">If so, this is a terminating error.</span></span>

- <span data-ttu-id="49564-111">与特定输入对象或输入对象的子集相关的错误条件？</span><span class="sxs-lookup"><span data-stu-id="49564-111">Is the error condition related to a specific input object or a subset of input objects?</span></span> <span data-ttu-id="49564-112">如果是这样, 则这是一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="49564-112">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="49564-113">Cmdlet 是否接受多个输入对象, 以便处理可以在另一个输入对象上成功进行？</span><span class="sxs-lookup"><span data-stu-id="49564-113">Does the cmdlet accept multiple input objects, such that processing may succeed on another input object?</span></span> <span data-ttu-id="49564-114">如果是这样, 则这是一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="49564-114">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="49564-115">可以接受多个输入对象的 cmdlet 应在什么是终止和非终止错误之间做出决定, 即使特定情况仅适用于单个输入对象也是如此。</span><span class="sxs-lookup"><span data-stu-id="49564-115">Cmdlets that can accept multiple input objects should decide between what are terminating and nonterminating errors, even when a particular situation applies to only a single input object.</span></span>

- <span data-ttu-id="49564-116">在引发终止异常之前, cmdlet 可以接收任意数量的输入对象并发送任意数量的 success 或 error 对象。</span><span class="sxs-lookup"><span data-stu-id="49564-116">Cmdlets can receive any number of input objects and send any number of success or error objects before throwing a terminating exception.</span></span> <span data-ttu-id="49564-117">收到的输入对象数与发送的成功和错误对象数之间没有关系。</span><span class="sxs-lookup"><span data-stu-id="49564-117">There's no relationship between the number of input objects received and the number of success and error objects sent.</span></span>

- <span data-ttu-id="49564-118">仅可接受0-1 输入对象并仅生成0-1 输出对象的 cmdlet 应将错误视为终止错误并生成终止异常。</span><span class="sxs-lookup"><span data-stu-id="49564-118">Cmdlets that can accept only 0-1 input objects and generate only 0-1 output objects should treat errors as terminating errors and generate terminating exceptions.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="49564-119">报告非终止错误</span><span class="sxs-lookup"><span data-stu-id="49564-119">Reporting nonterminating errors</span></span>

<span data-ttu-id="49564-120">报告非终止错误的操作应始终在 cmdlet 的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法 ( [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法) 的实现中完成, 或为, 则不应如此。[system.web. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法的方法。</span><span class="sxs-lookup"><span data-stu-id="49564-120">The reporting of a nonterminating error should always be done within the cmdlet's implementation of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, or the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="49564-121">这些类型的错误通过调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法进行报告, 后者会将错误记录发送到错误流。</span><span class="sxs-lookup"><span data-stu-id="49564-121">These types of errors are reported by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method that in turn sends an error record to the error stream.</span></span>

## <a name="reporting-terminating-errors"></a><span data-ttu-id="49564-122">报告终止错误</span><span class="sxs-lookup"><span data-stu-id="49564-122">Reporting terminating errors</span></span>

<span data-ttu-id="49564-123">通过引发异常或通过调用[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法来报告终止错误。</span><span class="sxs-lookup"><span data-stu-id="49564-123">Terminating errors are reported by throwing exceptions or by calling the [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="49564-124">请注意, cmdlet 还可以捕获并重新引发异常 (如**OutOfMemory**), 但是, 它们不需要重新引发异常, 因为 PowerShell 运行时也会捕获它们。</span><span class="sxs-lookup"><span data-stu-id="49564-124">Be aware that cmdlets can also catch and rethrow exceptions such as **OutOfMemory**, however, they aren't required to rethrow exceptions as the PowerShell runtime will catch them as well.</span></span>

<span data-ttu-id="49564-125">你还可以为特定于你的情况的问题定义自己的异常, 或使用其错误记录向现有异常添加其他信息。</span><span class="sxs-lookup"><span data-stu-id="49564-125">You can also define your own exceptions for issues specific to your situation, or add additional information to an existing exception using its error record.</span></span>

## <a name="error-records"></a><span data-ttu-id="49564-126">错误记录</span><span class="sxs-lookup"><span data-stu-id="49564-126">Error records</span></span>

<span data-ttu-id="49564-127">PowerShell 介绍了[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象的非终止错误条件。</span><span class="sxs-lookup"><span data-stu-id="49564-127">PowerShell describes a nonterminating error condition with [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objects.</span></span> <span data-ttu-id="49564-128">每个对象提供错误类别信息、可选的目标对象以及有关错误情况的详细信息。</span><span class="sxs-lookup"><span data-stu-id="49564-128">Each object provides error category information, an optional target object, and details about the error condition.</span></span>

### <a name="error-identifiers"></a><span data-ttu-id="49564-129">错误标识符</span><span class="sxs-lookup"><span data-stu-id="49564-129">Error identifiers</span></span>

<span data-ttu-id="49564-130">错误标识符是一个简单的字符串, 用于标识 cmdlet 内的错误条件。</span><span class="sxs-lookup"><span data-stu-id="49564-130">The error identifier is a simple string that identifies the error condition within the cmdlet.</span></span>
<span data-ttu-id="49564-131">PowerShell 将此标识符与 cmdlet 标识符组合在一起, 创建完全限定的错误标识符, 稍后在筛选错误流或记录错误时、响应特定错误时或与其他用户特定活动一起使用。</span><span class="sxs-lookup"><span data-stu-id="49564-131">PowerShell combines this identifier with a cmdlet identifier to create a fully qualified error identifier that can be used later when filtering error streams or logging errors, when responding to specific errors, or with other user-specific activities.</span></span>

<span data-ttu-id="49564-132">指定错误标识符时, 应遵循以下准则:</span><span class="sxs-lookup"><span data-stu-id="49564-132">The following guidelines should be followed when specifying error identifiers:</span></span>

- <span data-ttu-id="49564-133">将不同的、高度特定的错误标识符分配给不同的代码路径。</span><span class="sxs-lookup"><span data-stu-id="49564-133">Assign different, highly specific, error identifiers to different code paths.</span></span> <span data-ttu-id="49564-134">调用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)的每个代码路径都应具有其自己的错误标识符的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="49564-134">Each code path that calls [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) or [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) should have its own error identifier.</span></span>

- <span data-ttu-id="49564-135">错误标识符对于终止和非终止错误应是公共语言运行时 (CLR) 异常类型所特有的。</span><span class="sxs-lookup"><span data-stu-id="49564-135">Error identifiers should be unique to Common Language Runtime (CLR) exception types for both terminating and nonterminating errors.</span></span>

- <span data-ttu-id="49564-136">请勿更改 cmdlet 或 PowerShell 提供程序版本之间的错误标识符的语义。</span><span class="sxs-lookup"><span data-stu-id="49564-136">Don't change the semantics of an error identifier between versions of your cmdlet or PowerShell provider.</span></span> <span data-ttu-id="49564-137">建立错误标识符的语义后, 它应在 cmdlet 的整个生命周期中保持不变。</span><span class="sxs-lookup"><span data-stu-id="49564-137">After the semantics of an error identifier is established, it should remain constant throughout the lifecycle of your cmdlet.</span></span>

- <span data-ttu-id="49564-138">对于终止错误, 请为特定的 CLR 异常类型使用唯一的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="49564-138">For terminating errors, use a unique error identifier for a particular CLR exception type.</span></span> <span data-ttu-id="49564-139">如果异常类型发生更改, 请使用新的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="49564-139">If the exception type changes, use a new error identifier.</span></span>

- <span data-ttu-id="49564-140">对于非终止错误, 请使用特定输入对象的特定错误标识符。</span><span class="sxs-lookup"><span data-stu-id="49564-140">For nonterminating errors, use a specific error identifier for a specific input object.</span></span>

- <span data-ttu-id="49564-141">选择 tersely 与所报告错误相对应的标识符文本。</span><span class="sxs-lookup"><span data-stu-id="49564-141">Choose text for the identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="49564-142">不要使用空格或标点。</span><span class="sxs-lookup"><span data-stu-id="49564-142">Don't use white space or punctuation.</span></span>

- <span data-ttu-id="49564-143">不要生成不可重复的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="49564-143">Don't generate error identifiers that aren't reproducible.</span></span> <span data-ttu-id="49564-144">例如, 不生成包含进程标识符的标识符。</span><span class="sxs-lookup"><span data-stu-id="49564-144">For example, don't generate identifiers that include a process identifier.</span></span> <span data-ttu-id="49564-145">仅当错误标识符对应于遇到相同问题的其他用户所见的标识符时, 错误标识符才有用。</span><span class="sxs-lookup"><span data-stu-id="49564-145">Error identifiers are useful only when they correspond to identifiers that are seen by other users who are experiencing the same problem.</span></span>

### <a name="error-categories"></a><span data-ttu-id="49564-146">错误类别</span><span class="sxs-lookup"><span data-stu-id="49564-146">Error categories</span></span>

<span data-ttu-id="49564-147">错误类别用于对用户的错误进行分组。</span><span class="sxs-lookup"><span data-stu-id="49564-147">Error categories are used to group errors for the user.</span></span> <span data-ttu-id="49564-148">PowerShell 定义这些类别和 cmdlet, 并且 PowerShell 提供程序在生成错误记录时必须在它们之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="49564-148">PowerShell defines these categories and cmdlets and PowerShell providers must choose between them when generating the error record.</span></span>

<span data-ttu-id="49564-149">有关可用的错误类别的说明, 请参阅[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。</span><span class="sxs-lookup"><span data-stu-id="49564-149">For a description of the error categories that are available, see the [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="49564-150">通常, 应尽可能避免使用**NoError**、 **UndefinedError**和**GenericError** 。</span><span class="sxs-lookup"><span data-stu-id="49564-150">In general, you should avoid using **NoError**, **UndefinedError**, and **GenericError** whenever possible.</span></span>

<span data-ttu-id="49564-151">用户可以根据类别设置`$ErrorView`为 " **CategoryView**" 查看错误。</span><span class="sxs-lookup"><span data-stu-id="49564-151">Users can view errors based on category when they set `$ErrorView` to **CategoryView**.</span></span>

## <a name="see-also"></a><span data-ttu-id="49564-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49564-152">See also</span></span>

[<span data-ttu-id="49564-153">Cmdlet 概述</span><span class="sxs-lookup"><span data-stu-id="49564-153">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="49564-154">Cmdlet 输出的类型</span><span class="sxs-lookup"><span data-stu-id="49564-154">Types of Cmdlet Output</span></span>](./types-of-cmdlet-output.md)

[<span data-ttu-id="49564-155">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="49564-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

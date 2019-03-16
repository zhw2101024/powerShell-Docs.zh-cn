---
title: Cmdlet 的错误报告 |Microsoft Docs
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
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057937"
---
# <a name="cmdlet-error-reporting"></a><span data-ttu-id="62f2c-102">Cmdlet 错误报告</span><span class="sxs-lookup"><span data-stu-id="62f2c-102">Cmdlet Error Reporting</span></span>

<span data-ttu-id="62f2c-103">Cmdlet 应报告以不同的方式根据错误是否终止错误的错误或非终止错误。</span><span class="sxs-lookup"><span data-stu-id="62f2c-103">Cmdlets should report errors differently depending on whether the errors are terminating errors or nonterminating errors.</span></span> <span data-ttu-id="62f2c-104">终止错误会导致立即终止，将管道的错误或无需继续进行处理时，可能发生的错误。</span><span class="sxs-lookup"><span data-stu-id="62f2c-104">Terminating errors are errors that cause the pipeline to be terminated immediately, or errors that occur when there is no reason to continue processing.</span></span> <span data-ttu-id="62f2c-105">非终止错误，报告当前的错误条件，这些错误，但该 cmdlet 可以继续处理输入的对象。</span><span class="sxs-lookup"><span data-stu-id="62f2c-105">Nonterminating errors are those errors that report a current error condition, but the cmdlet can continue to process input objects.</span></span> <span data-ttu-id="62f2c-106">与非终止错误的问题，通常会通知用户，但该 cmdlet 将继续处理下一步的输入的对象。</span><span class="sxs-lookup"><span data-stu-id="62f2c-106">With nonterminating errors, the user is typically notified of the problem, but the cmdlet continues to process the next input object.</span></span>

## <a name="terminating-and-nonterminating-errors"></a><span data-ttu-id="62f2c-107">终止性和非终止错误</span><span class="sxs-lookup"><span data-stu-id="62f2c-107">Terminating and Nonterminating Errors</span></span>

<span data-ttu-id="62f2c-108">可以使用以下准则，以确定错误条件是否终止错误或非终止错误。</span><span class="sxs-lookup"><span data-stu-id="62f2c-108">The following guidelines can be used to determine if an error condition is a terminating error or a nonterminating error.</span></span>

- <span data-ttu-id="62f2c-109">错误条件是否已成功处理任何进一步输入的对象阻止 cmdlet？</span><span class="sxs-lookup"><span data-stu-id="62f2c-109">Does the error condition prevent your cmdlet from successfully processing any further input objects?</span></span> <span data-ttu-id="62f2c-110">如果是这样，这是一个终止错误。</span><span class="sxs-lookup"><span data-stu-id="62f2c-110">If so, this is a terminating error.</span></span>

- <span data-ttu-id="62f2c-111">与特定的输入的对象或输入对象的一个子集相关的错误条件？</span><span class="sxs-lookup"><span data-stu-id="62f2c-111">Is the error condition related to a specific input object or a subset of input objects?</span></span> <span data-ttu-id="62f2c-112">如果是这样，这是一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="62f2c-112">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="62f2c-113">该 cmdlet 是否接受多个输入的对象，此类处理可能会在另一个输入对象上成功？</span><span class="sxs-lookup"><span data-stu-id="62f2c-113">Does the cmdlet accept multiple input objects, such that processing may succeed on another input object?</span></span> <span data-ttu-id="62f2c-114">如果是这样，这是一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="62f2c-114">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="62f2c-115">即使在特定情况下适用于单个输入对象时，可以接受多个输入的对象的 Cmdlet 应确定什么终止和非终止错误之间。</span><span class="sxs-lookup"><span data-stu-id="62f2c-115">Cmdlets that can accept multiple input objects should decide between what are terminating and nonterminating errors, even when a particular situation applies to only a single input object.</span></span>

- <span data-ttu-id="62f2c-116">Cmdlet 可以接收任意数量的输入对象，并引发了终止异常之前发送任意数量的成功或错误的对象。</span><span class="sxs-lookup"><span data-stu-id="62f2c-116">Cmdlets can receive any number of input objects and send any number of success or error objects before throwing a terminating exception.</span></span> <span data-ttu-id="62f2c-117">收到的输入对象的数量和发送的 success 和 error 对象数之间没有关系。</span><span class="sxs-lookup"><span data-stu-id="62f2c-117">There is no relationship between the number of input objects received and the number of success and error objects sent.</span></span>

- <span data-ttu-id="62f2c-118">Cmdlet 可接受 0 到 1 输入对象，并生成 0 到 1 的输出对象应将错误视为终止错误并生成终止的异常。</span><span class="sxs-lookup"><span data-stu-id="62f2c-118">Cmdlets that can accept only 0-1 input objects and generate only 0-1 output objects should treat errors as terminating errors and generate terminating exceptions.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="62f2c-119">报告非终止错误</span><span class="sxs-lookup"><span data-stu-id="62f2c-119">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="62f2c-120">非终止错误的报告应始终进行中的 cmdlet 的实现[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="62f2c-120">The reporting of a nonterminating error should always be done within the cmdlet's implementation of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, or the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="62f2c-121">这些类型的错误报告通过调用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)反过来将错误记录发送到错误流的方法。</span><span class="sxs-lookup"><span data-stu-id="62f2c-121">These types of errors are reported by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method that in turn sends an error record to the error stream.</span></span>

## <a name="reporting-terminating-errors"></a><span data-ttu-id="62f2c-122">报告的终止错误</span><span class="sxs-lookup"><span data-stu-id="62f2c-122">Reporting Terminating Errors</span></span>

<span data-ttu-id="62f2c-123">通过引发异常或通过调用报告的终止错误[System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。</span><span class="sxs-lookup"><span data-stu-id="62f2c-123">Terminating errors are reported by throwing exceptions or by calling the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="62f2c-124">请注意，cmdlet 还可以捕获并重新引发如 OutOfMemory 异常，但是，它们不需要重新引发异常，如 Windows PowerShell 运行时将同时捕获它们。</span><span class="sxs-lookup"><span data-stu-id="62f2c-124">Be aware that cmdlets can also catch and re-throw exceptions such as OutOfMemory, however, they are not required to re-throw exceptions as the Windows PowerShell runtime will catch them as well.</span></span>

<span data-ttu-id="62f2c-125">此外可以定义自己的特定问题的异常情况，或将其他信息添加到现有异常使用其错误记录。</span><span class="sxs-lookup"><span data-stu-id="62f2c-125">You can also define your own exceptions for issues specific to your situation, or add additional information to an existing exception using its error record.</span></span>

## <a name="error-records"></a><span data-ttu-id="62f2c-126">错误记录</span><span class="sxs-lookup"><span data-stu-id="62f2c-126">Error Records</span></span>

<span data-ttu-id="62f2c-127">Windows PowerShell 描述使用非终止错误条件[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象。</span><span class="sxs-lookup"><span data-stu-id="62f2c-127">Windows PowerShell describes a nonterminating error condition through the use of [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objects.</span></span> <span data-ttu-id="62f2c-128">每个[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)对象提供错误类别信息、 可选目标对象，以及有关错误条件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="62f2c-128">Each [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object provides error category information, an optional target object, and details about the error condition.</span></span>

### <a name="error-identifiers"></a><span data-ttu-id="62f2c-129">错误标识符</span><span class="sxs-lookup"><span data-stu-id="62f2c-129">Error Identifiers</span></span>

<span data-ttu-id="62f2c-130">错误标识符是一个简单字符串，标识 cmdlet 中的错误情况。</span><span class="sxs-lookup"><span data-stu-id="62f2c-130">The error identifier is a simple string that identifies the error condition within the cmdlet.</span></span> <span data-ttu-id="62f2c-131">Windows PowerShell 将合并此标识符与创建时，可以使用更高版本筛选错误流或日志记录错误，具体的错误，在响应时的完全限定的错误标识符的 cmdlet 标识符或其他特定于用户的活动。</span><span class="sxs-lookup"><span data-stu-id="62f2c-131">Windows PowerShell combines this identifier with a cmdlet identifier to create a fully qualified error identifier that can be used later when filtering error streams or logging errors, when responding to specific errors, or with other user-specific activities.</span></span>

<span data-ttu-id="62f2c-132">指定错误标识符时，应遵循以下准则。</span><span class="sxs-lookup"><span data-stu-id="62f2c-132">The following guidelines should be followed when specifying error identifiers.</span></span>

- <span data-ttu-id="62f2c-133">不同且非常具体的错误标识符分配到不同的代码路径。</span><span class="sxs-lookup"><span data-stu-id="62f2c-133">Assign different, highly specific, error identifiers to different code paths.</span></span> <span data-ttu-id="62f2c-134">调用每个代码路径[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)应具有其自己的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="62f2c-134">Each code path that calls [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) or [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) should have its own error identifier.</span></span>

- <span data-ttu-id="62f2c-135">错误标识符应是唯一的 CLR 异常类型的终止性和非终止错误。</span><span class="sxs-lookup"><span data-stu-id="62f2c-135">Error identifiers should be unique to CLR exception types for both terminating and nonterminating errors.</span></span>

- <span data-ttu-id="62f2c-136">不要更改 cmdlet 或 Windows PowerShell 提供程序的不同版本之间的错误标识符的语义。</span><span class="sxs-lookup"><span data-stu-id="62f2c-136">Do not change the semantics of an error identifier between versions of your cmdlet or Windows PowerShell provider.</span></span> <span data-ttu-id="62f2c-137">错误标识符的语义建立后，它应保留常量整个生命周期的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62f2c-137">After the semantics of an error identifier is established, it should remain constant throughout the life cycle of your cmdlet.</span></span>

- <span data-ttu-id="62f2c-138">对于终止错误，为特定的 CLR 异常类型使用唯一的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="62f2c-138">For terminating errors, use a unique error identifier for a particular CLR exception type.</span></span> <span data-ttu-id="62f2c-139">如果异常类型发生更改，使用新的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="62f2c-139">If the exception type changes, use a new error identifier.</span></span>

- <span data-ttu-id="62f2c-140">对于非终止错误，使用一个特定的输入对象特定的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="62f2c-140">For nonterminating errors, use a specific error identifier for a specific input object.</span></span>

- <span data-ttu-id="62f2c-141">选择文本 tersely 与所报告的错误相对应的标识符。</span><span class="sxs-lookup"><span data-stu-id="62f2c-141">Choose text for the identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="62f2c-142">不要使用空格或标点。</span><span class="sxs-lookup"><span data-stu-id="62f2c-142">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="62f2c-143">不会生成不是可重现的错误标识符。</span><span class="sxs-lookup"><span data-stu-id="62f2c-143">Do not generate error identifiers that are not reproducible.</span></span> <span data-ttu-id="62f2c-144">例如，不生成标识符，其中包括进程标识符。</span><span class="sxs-lookup"><span data-stu-id="62f2c-144">For example, do not generate identifiers that include a process identifier.</span></span> <span data-ttu-id="62f2c-145">仅当它们对应于遇到相同问题的其他用户看到的标识符时，错误标识符是非常有用。</span><span class="sxs-lookup"><span data-stu-id="62f2c-145">Error identifiers are useful only when they correspond to identifiers that are seen by other users who are experiencing the same problem.</span></span>

### <a name="error-categories"></a><span data-ttu-id="62f2c-146">错误类别</span><span class="sxs-lookup"><span data-stu-id="62f2c-146">Error Categories</span></span>

<span data-ttu-id="62f2c-147">错误类别用于为最终用户的错误进行分组。</span><span class="sxs-lookup"><span data-stu-id="62f2c-147">Error categories are used to group errors for the end-user.</span></span> <span data-ttu-id="62f2c-148">Windows PowerShell 定义了这些类别和 cmdlet 和 Windows PowerShell 提供程序必须选择时生成的错误记录在它们之间。</span><span class="sxs-lookup"><span data-stu-id="62f2c-148">Windows PowerShell defines these categories and cmdlets and Windows PowerShell providers must choose between them when generating the error record.</span></span>

<span data-ttu-id="62f2c-149">可将错误类别的说明，请参阅[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。</span><span class="sxs-lookup"><span data-stu-id="62f2c-149">For a description of the error categories that are available, see the [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="62f2c-150">一般情况下，应避免使用 NoError、 UndefinedError 和 GenericError 只要有可能。</span><span class="sxs-lookup"><span data-stu-id="62f2c-150">In general, you should avoid using NoError, UndefinedError, and GenericError whenever possible.</span></span>

<span data-ttu-id="62f2c-151">用户可以查看基于类别，这些设置时的错误"`$ErrorView`"到"CategoryView"。</span><span class="sxs-lookup"><span data-stu-id="62f2c-151">Users can view errors based on category when they set "`$ErrorView`" to "CategoryView".</span></span>

## <a name="see-also"></a><span data-ttu-id="62f2c-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62f2c-152">See Also</span></span>

[<span data-ttu-id="62f2c-153">Windows PowerShell Cmdlets</span><span class="sxs-lookup"><span data-stu-id="62f2c-153">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="62f2c-154">Cmdlet Output</span><span class="sxs-lookup"><span data-stu-id="62f2c-154">Cmdlet Output</span></span>](./types-of-cmdlet-output.md)

[<span data-ttu-id="62f2c-155">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="62f2c-155">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)

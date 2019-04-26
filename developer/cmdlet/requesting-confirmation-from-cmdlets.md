---
title: 从 Cmdlet 请求确认 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067478"
---
# <a name="requesting-confirmation-from-cmdlets"></a><span data-ttu-id="4ce7f-102">请求 Cmdlet 确认</span><span class="sxs-lookup"><span data-stu-id="4ce7f-102">Requesting Confirmation from Cmdlets</span></span>

<span data-ttu-id="4ce7f-103">它们是以对 Windows PowerShell 环境外部的系统进行更改时，Cmdlet 应请求确认。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-103">Cmdlets should request confirmation when they are about to make a change to the system that is outside of the Windows PowerShell environment.</span></span> <span data-ttu-id="4ce7f-104">例如，如果 cmdlet 是要添加的用户帐户或停止的进程，该 cmdlet 应要求来自用户的确认之前它将继续进行。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-104">For example, if a cmdlet is about to add a user account or stop a process, the cmdlet should require confirmation from the user before it proceeds.</span></span> <span data-ttu-id="4ce7f-105">与此相反，如果某个 cmdlet 来更改 Windows PowerShell 变量，该 cmdlet 不会不需要要求进行确认。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-105">In contrast, if a cmdlet is about to change a Windows PowerShell variable, the cmdlet does not need to require confirmation.</span></span>

<span data-ttu-id="4ce7f-106">为了使确认请求，该 cmdlet 必须指示，它支持确认请求，并且它必须调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) （可选） 若要显示一条确认请求消息的方法。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-106">In order to make a confirmation request, the cmdlet must indicate that it supports confirmation requests, and it must call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (optional) methods to display a confirmation request message.</span></span>

## <a name="supporting-confirmation-requests"></a><span data-ttu-id="4ce7f-107">支持的确认请求</span><span class="sxs-lookup"><span data-stu-id="4ce7f-107">Supporting Confirmation Requests</span></span>

<span data-ttu-id="4ce7f-108">若要支持确认请求，该 cmdlet 必须设置`SupportsShouldProcess`Cmdlet 将属性与参数`true`。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-108">To support confirmation requests, the cmdlet must set the `SupportsShouldProcess` parameter of the Cmdlet attribute to `true`.</span></span> <span data-ttu-id="4ce7f-109">这使得`Confirm`和`WhatIf`所提供的 Windows PowerShell cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-109">This enables the `Confirm` and `WhatIf` cmdlet parameters that are provided by Windows PowerShell.</span></span> <span data-ttu-id="4ce7f-110">`Confirm`参数允许用户控制是否显示确认请求。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-110">The `Confirm` parameter allows the user to control whether the confirmation request is displayed.</span></span> <span data-ttu-id="4ce7f-111">`WhatIf`参数允许用户以确定该 cmdlet 应显示一条消息，还是执行其操作。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-111">The `WhatIf` parameter allows the user to determine whether the cmdlet should display a message or perform its action.</span></span> <span data-ttu-id="4ce7f-112">手动添加`Confirm`和`WhatIf`给某个 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-112">Do not manually add the `Confirm` and `WhatIf` parameters to a cmdlet.</span></span>

<span data-ttu-id="4ce7f-113">下面的示例演示了一个支持确认请求的 Cmdlet 属性声明。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-113">The following example shows a Cmdlet attribute declaration that supports confirmation requests.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a><span data-ttu-id="4ce7f-114">调用确认请求方法</span><span class="sxs-lookup"><span data-stu-id="4ce7f-114">Calling the Confirmation request methods</span></span>

<span data-ttu-id="4ce7f-115">在 cmdlet 代码中，调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前执行更改系统的操作。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-115">In the cmdlet code, call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the operation that changes the system is performed.</span></span> <span data-ttu-id="4ce7f-116">设计该 cmdlet，因此，如果在调用返回的值为`false`，无法执行的操作，并处理下一步操作。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-116">Design the cmdlet so that if the call returns a value of `false`, the operation is not performed, and the cmdlet processes the next operation.</span></span>

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="4ce7f-117">调用 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="4ce7f-117">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="4ce7f-118">大多数 cmdlet 请求确认仅使用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-118">Most cmdlets request confirmation using only the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="4ce7f-119">但是，某些情况下可能需要额外的确认信息。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-119">However, some cases might require additional confirmation.</span></span> <span data-ttu-id="4ce7f-120">这些情况下，对补充[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用通过调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-120">For these cases, supplement the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call with a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method.</span></span> <span data-ttu-id="4ce7f-121">这允许 cmdlet 或提供程序来更精细地控制的作用域**全是**响应确认提示。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-121">This allows the cmdlet or provider to more finely control the scope of the **Yes to all** response to the confirmation prompt.</span></span>

<span data-ttu-id="4ce7f-122">如果某个 cmdlet 调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，该 cmdlet 还必须提供`Force`开关参数。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-122">If a cmdlet calls the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method, the cmdlet must also provide a `Force` switch parameter.</span></span> <span data-ttu-id="4ce7f-123">如果用户指定`Force`当用户调用该 cmdlet，该 cmdlet 仍应调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，但它应绕过对调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-123">If the user specifies `Force` when the user invokes the cmdlet, the cmdlet should still call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), but it should bypass the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

<span data-ttu-id="4ce7f-124">[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)调用从非交互式环境会提示用户不能将引发异常。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-124">[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) will throw an exception when it is called from a non-interactive environment where the user cannot be prompted.</span></span> <span data-ttu-id="4ce7f-125">添加`Force`参数可确保在非交互式环境中调用时仍可以执行该命令。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-125">Adding a `Force` parameter ensures that the command can still be performed when it is invoked in a non-interactive environment.</span></span>

<span data-ttu-id="4ce7f-126">下面的示例演示如何调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-126">The following example shows how to call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

<span data-ttu-id="4ce7f-127">行为[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用可以在其中调用该 cmdlet 的环境而异。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-127">The behavior of a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call can vary depending on the environment in which the cmdlet is invoked.</span></span> <span data-ttu-id="4ce7f-128">使用上一准则将有助于确保该 cmdlet 行为一致地与其他 cmdlet，而不考虑主机环境。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-128">Using the previous guidelines will help ensure that the cmdlet behaves consistently with other cmdlets, regardless of the host environment.</span></span>

<span data-ttu-id="4ce7f-129">有关调用的示例[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，请参阅[如何请求确认](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-129">For an example of calling the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specify-the-impact-level"></a><span data-ttu-id="4ce7f-130">指定影响级别</span><span class="sxs-lookup"><span data-stu-id="4ce7f-130">Specify the Impact Level</span></span>

<span data-ttu-id="4ce7f-131">在创建 cmdlet 时，指定更改的影响级别 （严重性）。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-131">When you create the cmdlet, specify the impact level (the severity) of the change.</span></span> <span data-ttu-id="4ce7f-132">若要执行此操作，设置的值`ConfirmImpact`高、 中或低将 Cmdlet 属性的参数。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-132">To do this, set the value of the `ConfirmImpact` parameter of the Cmdlet attribute to High, Medium, or Low.</span></span> <span data-ttu-id="4ce7f-133">可以指定的值`ConfirmImpact`仅当还指定`SupportsShouldProcess`cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-133">You can specify a value for `ConfirmImpact` only when you also specify the `SupportsShouldProcess` parameter for the cmdlet.</span></span>

<span data-ttu-id="4ce7f-134">对于大多数 cmdlet，你不必显式指定`ConfirmImpact`。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-134">For most cmdlets, you do not have to explicitly specify `ConfirmImpact`.</span></span>  <span data-ttu-id="4ce7f-135">相反，使用默认设置的参数，这为 Medium。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-135">Instead, use the default setting of the parameter, which is Medium.</span></span> <span data-ttu-id="4ce7f-136">如果您设置`ConfirmImpact`为高，该操作将确认默认情况下。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-136">If you set `ConfirmImpact` to High, the operation will be confirmed by default.</span></span> <span data-ttu-id="4ce7f-137">保留此设置为高度破坏性操作，例如重新格式化硬盘卷。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-137">Reserve this setting for highly disruptive actions, such as reformatting a hard-disk volume.</span></span>

## <a name="calling-non-confirmation-methods"></a><span data-ttu-id="4ce7f-138">调用非确认方法</span><span class="sxs-lookup"><span data-stu-id="4ce7f-138">Calling Non-Confirmation Methods</span></span>

<span data-ttu-id="4ce7f-139">如果 cmdlet 或提供程序必须发送一条消息，但不是请求确认，它可以调用以下三种方法。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-139">If the cmdlet or provider must send a message but not request confirmation, it can call the following three methods.</span></span> <span data-ttu-id="4ce7f-140">避免使用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法来发送这些类型的消息，因为[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)混合输出cmdlet 或提供程序的正常输出，这就可将脚本写入困难。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-140">Avoid using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to send messages of these types because [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) output is intermingled with the normal output of your cmdlet or provider, which makes script writing difficult.</span></span>

- <span data-ttu-id="4ce7f-141">若要提醒用户，并继续执行操作，cmdlet 或提供程序可以调用[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-141">To caution the user and continue with the operation, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

- <span data-ttu-id="4ce7f-142">若要提供用户可以检索使用的其他信息`Verbose`参数，cmdlet 或提供程序可以调用[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-142">To provide additional information that the user can retrieve using the `Verbose` parameter, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span>

- <span data-ttu-id="4ce7f-143">若要对其他开发人员或获取产品支持提供调试级别的详细信息，该 cmdlet 或提供程序可以调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-143">To provide debugging-level detail for other developers or for product support, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span> <span data-ttu-id="4ce7f-144">用户可以检索此信息使用`Debug`参数。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-144">The user can retrieve this information using the `Debug` parameter.</span></span>

<span data-ttu-id="4ce7f-145">Cmdlet 和提供程序首先调用以下方法来尝试执行操作的更改在 Windows PowerShell 之外的系统之前请求确认：</span><span class="sxs-lookup"><span data-stu-id="4ce7f-145">Cmdlets and providers first call the following methods to request confirmation before they attempt to perform an operation that changes a system outside of Windows PowerShell:</span></span>

- [<span data-ttu-id="4ce7f-146">System.Management.Automation.Cmdlet.Shouldprocess</span><span class="sxs-lookup"><span data-stu-id="4ce7f-146">System.Management.Automation.Cmdlet.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [<span data-ttu-id="4ce7f-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span><span class="sxs-lookup"><span data-stu-id="4ce7f-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

<span data-ttu-id="4ce7f-148">在此，通过调用[System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，它会提示用户确认操作基于用户调用该命令的方式。</span><span class="sxs-lookup"><span data-stu-id="4ce7f-148">They do so by calling the [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which prompts the user to confirm the operation based on how the user invoked the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ce7f-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ce7f-149">See Also</span></span>

[<span data-ttu-id="4ce7f-150">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4ce7f-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

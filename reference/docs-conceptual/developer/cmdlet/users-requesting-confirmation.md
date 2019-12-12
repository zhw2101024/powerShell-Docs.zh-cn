---
title: 请求确认的用户 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369246"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="d517a-102">请求确认的用户</span><span class="sxs-lookup"><span data-stu-id="d517a-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="d517a-103">为 Cmdlet 特性声明的 `SupportsShouldProcess` 参数指定 `true` 值时，用户可以在命令提示符处指定 `Confirm` 参数。</span><span class="sxs-lookup"><span data-stu-id="d517a-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="d517a-104">在默认环境中，用户可以指定 `Confirm` 参数或 `"-Confirm:$true`，以便在调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法时请求确认。</span><span class="sxs-lookup"><span data-stu-id="d517a-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="d517a-105">这会绕过[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)确认请求，即使对于影响很大的操作也是如此。</span><span class="sxs-lookup"><span data-stu-id="d517a-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="d517a-106">如果未指定 `Confirm`，则当 `$ConfirmPreference` 首选项变量等于或大于 Cmdlet 或提供程序的 `ConfirmImpact` 设置时， [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求确认。</span><span class="sxs-lookup"><span data-stu-id="d517a-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="d517a-107">`$ConfirmPreference` 的默认设置为 "高"。</span><span class="sxs-lookup"><span data-stu-id="d517a-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="d517a-108">因此，在默认环境中，只有指定了影响很大的操作请求确认的 cmdlet 和提供程序。</span><span class="sxs-lookup"><span data-stu-id="d517a-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="d517a-109">如果 `Confirm` 为 false 或指定 `"-Confirm:$false`，则[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求从用户处确认，`$ConfirmPreference` shell 变量将被忽略。</span><span class="sxs-lookup"><span data-stu-id="d517a-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="d517a-110">备注</span><span class="sxs-lookup"><span data-stu-id="d517a-110">Remarks</span></span>

- <span data-ttu-id="d517a-111">对于指定 `SupportsShouldProcess`而不是 `ConfirmImpact`的 cmdlet 和提供程序，这些操作将作为 "中影响" 操作进行处理，并且默认情况下不会提示。</span><span class="sxs-lookup"><span data-stu-id="d517a-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="d517a-112">其影响级别小于 `$ConfirmPreference` 首选项变量的默认设置。</span><span class="sxs-lookup"><span data-stu-id="d517a-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="d517a-113">如果用户指定了 `Verbose` 参数，则即使不提示用户进行确认，也会收到有关该操作的通知。</span><span class="sxs-lookup"><span data-stu-id="d517a-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="d517a-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d517a-114">See Also</span></span>

[<span data-ttu-id="d517a-115">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d517a-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

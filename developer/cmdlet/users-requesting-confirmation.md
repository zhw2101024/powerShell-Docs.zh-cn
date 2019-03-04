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
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856233"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="f1035-102">请求确认的用户</span><span class="sxs-lookup"><span data-stu-id="f1035-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="f1035-103">指定的值时`true`有关`SupportsShouldProcess`Cmdlet 特性声明的参数，用户可以指定`Confirm`参数在命令提示符处。</span><span class="sxs-lookup"><span data-stu-id="f1035-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="f1035-104">在默认环境中，用户可以指定`Confirm`参数或`"-Confirm:$true`，以便请求确认时[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用方法。</span><span class="sxs-lookup"><span data-stu-id="f1035-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="f1035-105">这将绕过[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)确认请求，即使对于影响较大的操作。</span><span class="sxs-lookup"><span data-stu-id="f1035-105">This bypasses [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="f1035-106">如果`Confirm`未指定，则[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求确认，如果`$ConfirmPreference`首选项变量是等于或大于`ConfirmImpact`的设置cmdlet 或提供程序。</span><span class="sxs-lookup"><span data-stu-id="f1035-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="f1035-107">默认设置`$ConfirmPreference`是高。</span><span class="sxs-lookup"><span data-stu-id="f1035-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="f1035-108">因此，在默认环境中，唯一的 cmdlet 和提供程序用于指定影响较大的操作请求确认。</span><span class="sxs-lookup"><span data-stu-id="f1035-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="f1035-109">如果`Confirm`为 false 或者如果`"-Confirm:$false`指定，则[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用请求用户，确认和`$ConfirmPreference`shell 变量将被忽略。</span><span class="sxs-lookup"><span data-stu-id="f1035-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1035-110">备注</span><span class="sxs-lookup"><span data-stu-id="f1035-110">Remarks</span></span>

- <span data-ttu-id="f1035-111">为 cmdlet 和指定的提供商`SupportsShouldProcess`，但不是`ConfirmImpact`，这些操作处理为"中等程度的影响"操作，它们将不会提示默认情况下。</span><span class="sxs-lookup"><span data-stu-id="f1035-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="f1035-112">其影响级别低于的默认设置`$ConfirmPreference`首选项变量。</span><span class="sxs-lookup"><span data-stu-id="f1035-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="f1035-113">如果用户指定`Verbose`参数，他们将会收到通知操作即使它们不会提示进行确认。</span><span class="sxs-lookup"><span data-stu-id="f1035-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1035-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1035-114">See Also</span></span>

[<span data-ttu-id="f1035-115">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f1035-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

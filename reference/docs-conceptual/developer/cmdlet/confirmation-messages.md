---
title: 确认消息 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365726"
---
# <a name="confirmation-messages"></a><span data-ttu-id="798de-102">确认消息</span><span class="sxs-lookup"><span data-stu-id="798de-102">Confirmation Messages</span></span>

<span data-ttu-id="798de-103">下面是一些不同的确认消息，可以根据所调用的[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的变体来显示这些消息，具体取决于。</span><span class="sxs-lookup"><span data-stu-id="798de-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="798de-104">有关演示如何请求确认的示例代码，请参阅[如何请求确认](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="798de-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="798de-105">指定资源</span><span class="sxs-lookup"><span data-stu-id="798de-105">Specifying the Resource</span></span>

<span data-ttu-id="798de-106">你可以通过调用 Shouldprocess% 2A 来指定要更改的资源（& i） [？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="798de-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="798de-107">在这种情况下，请使用方法的 @no__t 参数提供资源，并由 Windows PowerShell 添加操作。</span><span class="sxs-lookup"><span data-stu-id="798de-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="798de-108">在下面的消息中，文本 "MyResource" 是操作资源，操作是执行调用的命令的名称。</span><span class="sxs-lookup"><span data-stu-id="798de-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="798de-109">如果用户为确认请求选择 **"是"** 或 **"全部"** （如以下示例中所示），则会调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，这将导致第二条确认消息会.</span><span class="sxs-lookup"><span data-stu-id="798de-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="798de-110">指定操作和资源</span><span class="sxs-lookup"><span data-stu-id="798de-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="798de-111">你可以通过调用 Shouldprocess% 2A 来指定要更改的资源，以及该命令将要执行的操作（& e） [？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="798de-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="798de-112">在这种情况下，请使用 @no__t 参数和操作通过使用 `target` 参数提供资源。</span><span class="sxs-lookup"><span data-stu-id="798de-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="798de-113">在下面的消息中，文本 "MyResource" 是操作资源，而 "MyAction" 是要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="798de-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="798de-114">如果用户选择 **"是"** 或 **"全部"** 作为上一条消息，则会调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，这将导致显示第二条确认消息。</span><span class="sxs-lookup"><span data-stu-id="798de-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="798de-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="798de-115">See Also</span></span>

[<span data-ttu-id="798de-116">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="798de-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

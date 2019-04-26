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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068362"
---
# <a name="confirmation-messages"></a><span data-ttu-id="06c50-102">确认消息</span><span class="sxs-lookup"><span data-stu-id="06c50-102">Confirmation Messages</span></span>

<span data-ttu-id="06c50-103">以下是可以根据的变体显示的不同的确认消息[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)调用的方法。</span><span class="sxs-lookup"><span data-stu-id="06c50-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06c50-104">有关演示如何请求确认的示例代码，请参阅[如何请求确认](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="06c50-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="06c50-105">指定的资源</span><span class="sxs-lookup"><span data-stu-id="06c50-105">Specifying the Resource</span></span>

<span data-ttu-id="06c50-106">可以指定将通过调用更改资源[System.Management.Automation.Cmdlet.Shouldprocess%2A？Displayproperty =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="06c50-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="06c50-107">在这种情况下，使用提供该资源`target`通过 Windows PowerShell 添加的方法，并在操作的参数。</span><span class="sxs-lookup"><span data-stu-id="06c50-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="06c50-108">在下面的消息中，"MyResource"的文本是所作用于的资源和操作是调用命令的名称。</span><span class="sxs-lookup"><span data-stu-id="06c50-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="06c50-109">如果用户选择**是**或**全部**确认请求 （如下面的示例所示），调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法进行，这将导致第二个要在显示确认消息。</span><span class="sxs-lookup"><span data-stu-id="06c50-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="06c50-110">指定的操作和资源</span><span class="sxs-lookup"><span data-stu-id="06c50-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="06c50-111">你可以指定将要更改的资源和命令时通过调用来执行该操作[System.Management.Automation.Cmdlet.Shouldprocess%2A？Displayproperty =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="06c50-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="06c50-112">在这种情况下，使用提供的资源`target`参数，并且通过使用操作`target`参数。</span><span class="sxs-lookup"><span data-stu-id="06c50-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="06c50-113">在下面的消息中，"MyResource"的文本是所作用于的资源，并"命名为 MyAction"是要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="06c50-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="06c50-114">如果用户选择**是**或**全部**到前面的消息调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法进行，这将导致若要显示的第二个确认消息。</span><span class="sxs-lookup"><span data-stu-id="06c50-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="06c50-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06c50-115">See Also</span></span>

[<span data-ttu-id="06c50-116">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="06c50-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

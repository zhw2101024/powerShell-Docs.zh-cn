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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365726"
---
# <a name="confirmation-messages"></a>确认消息

下面是一些不同的确认消息，可以根据所调用的[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的变体来显示这些消息，具体取决于。

> [!IMPORTANT]
> 有关演示如何请求确认的示例代码，请参阅[如何请求确认](./how-to-request-confirmations.md)。

## <a name="specifying-the-resource"></a>指定资源

你可以通过调用 Shouldprocess% 2A 来指定要更改的资源（& i） [？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在这种情况下，请使用方法的 `target` 参数提供资源，并由 Windows PowerShell 添加操作。 在下面的消息中，文本 "MyResource" 是操作资源，操作是执行调用的命令的名称。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果用户为确认请求选择 **"是"** 或 **"全部"** （如以下示例中所示），则会调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，这将导致显示第二条确认消息。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>指定操作和资源

你可以通过调用 Shouldprocess% 2A 来指定要更改的资源，以及该命令将要执行的操作（& e） [？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在这种情况下，请使用 `target` 参数和操作通过使用 `target` 参数提供资源。 在下面的消息中，文本 "MyResource" 是操作资源，而 "MyAction" 是要执行的操作。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果用户选择 **"是"** 或 **"全部"** 作为上一条消息，则会调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，这将导致显示第二条确认消息。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

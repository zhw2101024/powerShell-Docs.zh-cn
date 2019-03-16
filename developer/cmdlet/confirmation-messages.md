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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059467"
---
# <a name="confirmation-messages"></a>确认消息

以下是可以根据的变体显示的不同的确认消息[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)调用的方法。

> [!IMPORTANT]
> 有关演示如何请求确认的示例代码，请参阅[如何请求确认](./how-to-request-confirmations.md)。

## <a name="specifying-the-resource"></a>指定的资源

可以指定将通过调用更改资源[System.Management.Automation.Cmdlet.Shouldprocess%2A？Displayproperty =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在这种情况下，使用提供该资源`target`通过 Windows PowerShell 添加的方法，并在操作的参数。 在下面的消息中，"MyResource"的文本是所作用于的资源和操作是调用命令的名称。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果用户选择**是**或**全部**确认请求 （如下面的示例所示），调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法进行，这将导致第二个要在显示确认消息。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>指定的操作和资源

你可以指定将要更改的资源和命令时通过调用来执行该操作[System.Management.Automation.Cmdlet.Shouldprocess%2A？Displayproperty =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在这种情况下，使用提供的资源`target`参数，并且通过使用操作`target`参数。 在下面的消息中，"MyResource"的文本是所作用于的资源，并"命名为 MyAction"是要执行的操作。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果用户选择**是**或**全部**到前面的消息调用[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法进行，这将导致若要显示的第二个确认消息。

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

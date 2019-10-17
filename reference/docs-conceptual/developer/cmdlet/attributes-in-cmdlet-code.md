---
title: Cmdlet 代码中的属性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369996"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 代码中的属性

若要使用 Windows PowerShell 提供的通用功能，请使用属性修饰 cmdlet 代码中定义的类和公共属性。 例如，下面的类定义使用 Cmdlet 特性来标识实现了**get-help** Cmdlet 的 Microsoft .NET 框架类。 （本文档中使用此 cmdlet，它类似于 Windows PowerShell 提供的 `Get-Process` cmdlet。）

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

这些属性被视为元数据，因为它们的实现与 cmdlet 代码的实现不同。 当 Windows PowerShell 运行时运行该 cmdlet 时，它会识别这些属性，然后针对每个属性执行相应的操作。

尽管你可能想要实现这些属性提供的功能版本，但良好的 cmdlet 设计则使用这些常见功能。

有关可在 cmdlet 中声明的不同属性的详细信息，请参阅[属性类型](./attribute-types.md)。

## <a name="see-also"></a>另请参阅

[特性类型](./attribute-types.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

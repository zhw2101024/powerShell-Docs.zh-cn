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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068667"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 代码中的属性

若要使用提供的 Windows PowerShell 的常见功能，类和 cmdlet 代码中定义的公共属性进行修饰的属性。 例如，以下类定义使用 Cmdlet 属性来标识在其中的 Microsoft.NET Framework 类**Get-proc** cmdlet 实现。 (此 cmdlet 用作示例，请参见本文档中，它类似于`Get-Process`提供的 Windows PowerShell cmdlet。)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

这些属性被视为元数据，因为它们的实现是独立于实现的 cmdlet 代码。 Windows PowerShell 运行时在该 cmdlet，它将识别特性，然后为每个属性执行适当的操作。

虽然你可能想要实现自己的这些属性提供的功能版本，但好 cmdlet 设计使用这些常见的功能。

有关可以在 cmdlet 中声明的不同属性的详细信息，请参阅[属性类型](./attribute-types.md)。

## <a name="see-also"></a>另请参阅

[属性类型](./attribute-types.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

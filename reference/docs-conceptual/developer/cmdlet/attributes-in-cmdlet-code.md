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
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="b6c4a-102">Cmdlet 代码中的属性</span><span class="sxs-lookup"><span data-stu-id="b6c4a-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="b6c4a-103">若要使用 Windows PowerShell 提供的通用功能，请使用属性修饰 cmdlet 代码中定义的类和公共属性。</span><span class="sxs-lookup"><span data-stu-id="b6c4a-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="b6c4a-104">例如，下面的类定义使用 Cmdlet 特性来标识实现了**get-help** Cmdlet 的 Microsoft .NET 框架类。</span><span class="sxs-lookup"><span data-stu-id="b6c4a-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="b6c4a-105">（本文档中使用此 cmdlet，它类似于 Windows PowerShell 提供的 `Get-Process` cmdlet。）</span><span class="sxs-lookup"><span data-stu-id="b6c4a-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="b6c4a-106">这些属性被视为元数据，因为它们的实现与 cmdlet 代码的实现不同。</span><span class="sxs-lookup"><span data-stu-id="b6c4a-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="b6c4a-107">当 Windows PowerShell 运行时运行该 cmdlet 时，它会识别这些属性，然后针对每个属性执行相应的操作。</span><span class="sxs-lookup"><span data-stu-id="b6c4a-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="b6c4a-108">尽管你可能想要实现这些属性提供的功能版本，但良好的 cmdlet 设计则使用这些常见功能。</span><span class="sxs-lookup"><span data-stu-id="b6c4a-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="b6c4a-109">有关可在 cmdlet 中声明的不同属性的详细信息，请参阅[属性类型](./attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b6c4a-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6c4a-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6c4a-110">See Also</span></span>

[<span data-ttu-id="b6c4a-111">特性类型</span><span class="sxs-lookup"><span data-stu-id="b6c4a-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="b6c4a-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6c4a-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

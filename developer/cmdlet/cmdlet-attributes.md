---
title: Cmdlet 属性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055166"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="524e3-102">Cmdlet 属性</span><span class="sxs-lookup"><span data-stu-id="524e3-102">Cmdlet Attributes</span></span>

<span data-ttu-id="524e3-103">Windows PowerShell 定义可用于将常见功能添加到 cmdlet，而无需实现你自己的代码中的该功能的多个属性。</span><span class="sxs-lookup"><span data-stu-id="524e3-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="524e3-104">这包括 Cmdlet 属性，用于标识 Microsoft.NET Framework 类作为的 cmdlet，指定该 cmdlet，将公共属性标识为 cmdlet 的参数属性返回的.NET Framework 类型的 OutputType 特性参数和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="524e3-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="524e3-105">本部分内容</span><span class="sxs-lookup"><span data-stu-id="524e3-105">In This Section</span></span>

<span data-ttu-id="524e3-106">[Cmdlet 代码中的属性](./attributes-in-cmdlet-code.md)介绍 cmdlet 代码中使用属性的好处。</span><span class="sxs-lookup"><span data-stu-id="524e3-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="524e3-107">[属性类型](./attribute-types.md)介绍可以修饰 cmdlet 类的各种属性。</span><span class="sxs-lookup"><span data-stu-id="524e3-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="524e3-108">[别名属性声明](./alias-attribute-declaration.md)介绍如何定义的 cmdlet 参数名称的别名。</span><span class="sxs-lookup"><span data-stu-id="524e3-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="524e3-109">[Cmdlet 属性声明](./cmdlet-attribute-declaration.md)介绍如何为 cmdlet 定义.NET Framework 类。</span><span class="sxs-lookup"><span data-stu-id="524e3-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="524e3-110">[凭据属性声明](./credential-attribute-declaration.md)介绍了如何添加用于将转换到的字符串输入的支持[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)对象。</span><span class="sxs-lookup"><span data-stu-id="524e3-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="524e3-111">[OutputType 属性声明](./outputtype-attribute-declaration.md)介绍如何指定该 cmdlet 返回的.NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="524e3-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="524e3-112">[参数特性声明](./parameter-attribute-declaration.md)介绍如何定义一个 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="524e3-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="524e3-113">[ValidateCount 特性声明](./validatecount-attribute-declaration.md)介绍如何定义为参数允许使用多少参数。</span><span class="sxs-lookup"><span data-stu-id="524e3-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="524e3-114">[ValidateLength 特性声明](./validatelength-attribute-declaration.md)介绍如何定义参数自变量的长度 （以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="524e3-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="524e3-115">[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)介绍如何定义参数自变量的有效模式。</span><span class="sxs-lookup"><span data-stu-id="524e3-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="524e3-116">[ValidateRange 特性声明](./validaterange-attribute-declaration.md)介绍如何定义参数自变量的有效范围。</span><span class="sxs-lookup"><span data-stu-id="524e3-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="524e3-117">[ValidateSet 特性声明](./validateset-attribute-declaration.md)介绍如何定义参数自变量的可能值。</span><span class="sxs-lookup"><span data-stu-id="524e3-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="524e3-118">引用</span><span class="sxs-lookup"><span data-stu-id="524e3-118">Reference</span></span>

[<span data-ttu-id="524e3-119">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="524e3-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

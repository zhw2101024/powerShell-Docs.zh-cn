---
title: ValidateSet 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364276"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="f31ae-102">ValidateSet 属性声明</span><span class="sxs-lookup"><span data-stu-id="f31ae-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="f31ae-103">ValidateSetAttribute 属性为 cmdlet 参数参数指定一组可能的值。</span><span class="sxs-lookup"><span data-stu-id="f31ae-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="f31ae-104">此属性也可由 Windows PowerShell 函数使用。</span><span class="sxs-lookup"><span data-stu-id="f31ae-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="f31ae-105">如果指定此属性，则 Windows PowerShell 运行时将确定 cmdlet 参数的提供参数是否与提供的元素集中的元素匹配。</span><span class="sxs-lookup"><span data-stu-id="f31ae-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="f31ae-106">仅当参数参数与集中的元素匹配时，才运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f31ae-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="f31ae-107">如果未找到匹配项，则 Windows PowerShell 运行时将引发错误。</span><span class="sxs-lookup"><span data-stu-id="f31ae-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="f31ae-108">语法</span><span class="sxs-lookup"><span data-stu-id="f31ae-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="f31ae-109">参数</span><span class="sxs-lookup"><span data-stu-id="f31ae-109">Parameters</span></span>

<span data-ttu-id="f31ae-110">需要 `ValidValues` （[system.string](/dotnet/api/System.String)）。</span><span class="sxs-lookup"><span data-stu-id="f31ae-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="f31ae-111">指定有效的参数元素值。</span><span class="sxs-lookup"><span data-stu-id="f31ae-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="f31ae-112">下面的示例演示如何指定一个或多个元素。</span><span class="sxs-lookup"><span data-stu-id="f31ae-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="f31ae-113">`IgnoreCase` （[system.string](/dotnet/api/System.Boolean)）可选命名参数。</span><span class="sxs-lookup"><span data-stu-id="f31ae-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f31ae-114">`true` 的默认值指示忽略大小写。</span><span class="sxs-lookup"><span data-stu-id="f31ae-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="f31ae-115">`false` 的值使 cmdlet 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="f31ae-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="f31ae-116">备注</span><span class="sxs-lookup"><span data-stu-id="f31ae-116">Remarks</span></span>

- <span data-ttu-id="f31ae-117">此属性仅可用于每个参数一次。</span><span class="sxs-lookup"><span data-stu-id="f31ae-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="f31ae-118">如果参数值为数组，则数组的每个元素都必须与属性集的元素匹配。</span><span class="sxs-lookup"><span data-stu-id="f31ae-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="f31ae-119">ValidateSetAttribute 特性是由[ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)类定义的。</span><span class="sxs-lookup"><span data-stu-id="f31ae-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f31ae-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f31ae-120">See Also</span></span>

[<span data-ttu-id="f31ae-121">System.web. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="f31ae-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="f31ae-122">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f31ae-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

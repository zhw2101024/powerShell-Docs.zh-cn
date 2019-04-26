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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067054"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="6240b-102">ValidateSet 属性声明</span><span class="sxs-lookup"><span data-stu-id="6240b-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="6240b-103">ValidateSetAttribute 属性指定一组的可能值的 cmdlet 参数自变量。</span><span class="sxs-lookup"><span data-stu-id="6240b-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="6240b-104">Windows PowerShell 函数还可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="6240b-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="6240b-105">当指定此属性时，Windows PowerShell 运行时确定 cmdlet 参数提供的参数是否与中提供的元素集的元素相匹配。</span><span class="sxs-lookup"><span data-stu-id="6240b-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="6240b-106">参数自变量与匹配集中的元素时才运行该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6240b-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="6240b-107">如果不找到任何匹配项，则是由 Windows PowerShell 运行时引发错误。</span><span class="sxs-lookup"><span data-stu-id="6240b-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="6240b-108">语法</span><span class="sxs-lookup"><span data-stu-id="6240b-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="6240b-109">参数</span><span class="sxs-lookup"><span data-stu-id="6240b-109">Parameters</span></span>

<span data-ttu-id="6240b-110">`ValidValues` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="6240b-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="6240b-111">指定有效的参数元素值。</span><span class="sxs-lookup"><span data-stu-id="6240b-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="6240b-112">下面的示例演示如何指定一个元素或多个元素。</span><span class="sxs-lookup"><span data-stu-id="6240b-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="6240b-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="6240b-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="6240b-114">默认值`true`指示忽略大小写。</span><span class="sxs-lookup"><span data-stu-id="6240b-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="6240b-115">值为`false`使该 cmdlet 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="6240b-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="6240b-116">备注</span><span class="sxs-lookup"><span data-stu-id="6240b-116">Remarks</span></span>

- <span data-ttu-id="6240b-117">此属性可以使用仅一次，每个参数。</span><span class="sxs-lookup"><span data-stu-id="6240b-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="6240b-118">如果参数值是一个数组，数组的每个元素必须匹配的元素的属性集。</span><span class="sxs-lookup"><span data-stu-id="6240b-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="6240b-119">通过定义 ValidateSetAttribute 特性[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="6240b-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="6240b-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6240b-120">See Also</span></span>

[<span data-ttu-id="6240b-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="6240b-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="6240b-122">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6240b-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

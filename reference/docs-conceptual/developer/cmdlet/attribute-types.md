---
title: 属性类型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364576"
---
# <a name="attribute-types"></a><span data-ttu-id="c7581-102">属性类型</span><span class="sxs-lookup"><span data-stu-id="c7581-102">Attribute Types</span></span>

<span data-ttu-id="c7581-103">Cmdlet 属性可以按功能分组。</span><span class="sxs-lookup"><span data-stu-id="c7581-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="c7581-104">以下各节介绍了可用的属性，并说明了在调用特性时运行时的作用。</span><span class="sxs-lookup"><span data-stu-id="c7581-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="c7581-105">Cmdlet 属性</span><span class="sxs-lookup"><span data-stu-id="c7581-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="c7581-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c7581-106">Cmdlet</span></span>

<span data-ttu-id="c7581-107">将 .NET Framework 类标识为 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c7581-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="c7581-108">这是必需的基本属性。</span><span class="sxs-lookup"><span data-stu-id="c7581-108">This is the required base attribute.</span></span>
<span data-ttu-id="c7581-109">有关详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="c7581-110">参数特性</span><span class="sxs-lookup"><span data-stu-id="c7581-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="c7581-111">参数</span><span class="sxs-lookup"><span data-stu-id="c7581-111">Parameter</span></span>

<span data-ttu-id="c7581-112">将 cmdlet 类中的公共属性标识为 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="c7581-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="c7581-113">有关详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="c7581-114">Alias</span><span class="sxs-lookup"><span data-stu-id="c7581-114">Alias</span></span>

<span data-ttu-id="c7581-115">指定参数的一个或多个别名。</span><span class="sxs-lookup"><span data-stu-id="c7581-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="c7581-116">有关详细信息，请参阅[Alias 特性声明](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="c7581-117">参数验证特性</span><span class="sxs-lookup"><span data-stu-id="c7581-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="c7581-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="c7581-118">ValidateCount</span></span>

<span data-ttu-id="c7581-119">指定 cmdlet 参数允许的最小和最大参数数量。</span><span class="sxs-lookup"><span data-stu-id="c7581-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="c7581-120">有关详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="c7581-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="c7581-121">ValidateLength</span></span>

<span data-ttu-id="c7581-122">指定 cmdlet 参数参数的最小和最大字符数。</span><span class="sxs-lookup"><span data-stu-id="c7581-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c7581-123">有关详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="c7581-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="c7581-124">ValidatePattern</span></span>

<span data-ttu-id="c7581-125">指定 cmdlet 参数参数必须匹配的正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="c7581-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="c7581-126">有关详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="c7581-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="c7581-127">ValidateRange</span></span>

<span data-ttu-id="c7581-128">指定 cmdlet 参数参数的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="c7581-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c7581-129">有关详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="c7581-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="c7581-130">ValidateSet</span></span>

<span data-ttu-id="c7581-131">为 cmdlet 参数参数指定一组有效值。</span><span class="sxs-lookup"><span data-stu-id="c7581-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="c7581-132">有关详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7581-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7581-133">See Also</span></span>

[<span data-ttu-id="c7581-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c7581-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

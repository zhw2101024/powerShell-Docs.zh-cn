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
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863803"
---
# <a name="attribute-types"></a><span data-ttu-id="f03ce-102">属性类型</span><span class="sxs-lookup"><span data-stu-id="f03ce-102">Attribute Types</span></span>

<span data-ttu-id="f03ce-103">Cmdlet 属性可以按功能分组。</span><span class="sxs-lookup"><span data-stu-id="f03ce-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="f03ce-104">以下各节描述了可用的属性，并描述调用该属性时，运行时的作用。</span><span class="sxs-lookup"><span data-stu-id="f03ce-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="f03ce-105">Cmdlet 属性</span><span class="sxs-lookup"><span data-stu-id="f03ce-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="f03ce-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f03ce-106">Cmdlet</span></span>

<span data-ttu-id="f03ce-107">将.NET Framework 类标识为一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f03ce-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="f03ce-108">这是必需的基本属性。</span><span class="sxs-lookup"><span data-stu-id="f03ce-108">This is the required base attribute.</span></span>
<span data-ttu-id="f03ce-109">有关详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="f03ce-110">参数特性</span><span class="sxs-lookup"><span data-stu-id="f03ce-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="f03ce-111">参数</span><span class="sxs-lookup"><span data-stu-id="f03ce-111">Parameter</span></span>

<span data-ttu-id="f03ce-112">标识作为 cmdlet 参数在 cmdlet 类中的公共属性。</span><span class="sxs-lookup"><span data-stu-id="f03ce-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="f03ce-113">有关详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="f03ce-114">Alias</span><span class="sxs-lookup"><span data-stu-id="f03ce-114">Alias</span></span>

<span data-ttu-id="f03ce-115">指定为参数的一个或多个别名。</span><span class="sxs-lookup"><span data-stu-id="f03ce-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="f03ce-116">有关详细信息，请参阅[别名属性声明](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="f03ce-117">参数验证属性</span><span class="sxs-lookup"><span data-stu-id="f03ce-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="f03ce-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="f03ce-118">ValidateCount</span></span>

<span data-ttu-id="f03ce-119">指定参数为 cmdlet 参数允许的最小值和最大数目。</span><span class="sxs-lookup"><span data-stu-id="f03ce-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="f03ce-120">有关详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="f03ce-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="f03ce-121">ValidateLength</span></span>

<span data-ttu-id="f03ce-122">指定最小和最大的 cmdlet 参数自变量的字符数。</span><span class="sxs-lookup"><span data-stu-id="f03ce-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f03ce-123">有关详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="f03ce-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="f03ce-124">ValidatePattern</span></span>

<span data-ttu-id="f03ce-125">指定 cmdlet 参数自变量必须与匹配的正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="f03ce-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="f03ce-126">有关详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="f03ce-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="f03ce-127">ValidateRange</span></span>

<span data-ttu-id="f03ce-128">指定 cmdlet 参数自变量的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="f03ce-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f03ce-129">有关详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="f03ce-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="f03ce-130">ValidateSet</span></span>

<span data-ttu-id="f03ce-131">指定一组 cmdlet 参数自变量的有效值。</span><span class="sxs-lookup"><span data-stu-id="f03ce-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="f03ce-132">有关详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f03ce-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f03ce-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f03ce-133">See Also</span></span>

[<span data-ttu-id="f03ce-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f03ce-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

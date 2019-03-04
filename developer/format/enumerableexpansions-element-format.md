---
title: EnumerableExpansions 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860253"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="37370-102">EnumerableExpansions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="37370-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="37370-103">定义显示在视图中时如何展开.NET 集合对象。</span><span class="sxs-lookup"><span data-stu-id="37370-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="37370-104">配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="37370-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37370-105">语法</span><span class="sxs-lookup"><span data-stu-id="37370-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37370-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="37370-106">Attributes and Elements</span></span>

<span data-ttu-id="37370-107">以下各节描述了特性、 子元素和父元素的`EnumerableExpansions`元素。</span><span class="sxs-lookup"><span data-stu-id="37370-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="37370-108">可以使用的子元素的数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="37370-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="37370-109">特性</span><span class="sxs-lookup"><span data-stu-id="37370-109">Attributes</span></span>

<span data-ttu-id="37370-110">无。</span><span class="sxs-lookup"><span data-stu-id="37370-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37370-111">子元素</span><span class="sxs-lookup"><span data-stu-id="37370-111">Child Elements</span></span>

|<span data-ttu-id="37370-112">元素</span><span class="sxs-lookup"><span data-stu-id="37370-112">Element</span></span>|<span data-ttu-id="37370-113">描述</span><span class="sxs-lookup"><span data-stu-id="37370-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37370-114">EnumerableExpansion 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="37370-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="37370-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="37370-115">Optional element.</span></span><br /><br /> <span data-ttu-id="37370-116">定义显示在视图中时进行扩展的特定.NET 集合对象。</span><span class="sxs-lookup"><span data-stu-id="37370-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="37370-117">父元素</span><span class="sxs-lookup"><span data-stu-id="37370-117">Parent Elements</span></span>

|<span data-ttu-id="37370-118">元素</span><span class="sxs-lookup"><span data-stu-id="37370-118">Element</span></span>|<span data-ttu-id="37370-119">描述</span><span class="sxs-lookup"><span data-stu-id="37370-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37370-120">DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="37370-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="37370-121">定义应用于的格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="37370-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37370-122">备注</span><span class="sxs-lookup"><span data-stu-id="37370-122">Remarks</span></span>

<span data-ttu-id="37370-123">此元素用于定义如何显示集合对象和集合中的对象。</span><span class="sxs-lookup"><span data-stu-id="37370-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="37370-124">在这种情况下，集合对象是指任何支持的对象**System.Collections.ICollection**接口。</span><span class="sxs-lookup"><span data-stu-id="37370-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="37370-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37370-125">See Also</span></span>

[<span data-ttu-id="37370-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="37370-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

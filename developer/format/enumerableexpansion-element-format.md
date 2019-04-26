---
title: EnumerableExpansion 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066135"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="68626-102">EnumerableExpansion Element (Format)</span><span class="sxs-lookup"><span data-stu-id="68626-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="68626-103">定义如何特定对象在视图中显示时进行扩展的.NET 集合。</span><span class="sxs-lookup"><span data-stu-id="68626-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="68626-104">配置元素 （格式） DefaultSettings 元素 （格式） EnumerableExpansions 元素 （格式） EnumerableExpansion 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="68626-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68626-105">语法</span><span class="sxs-lookup"><span data-stu-id="68626-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68626-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="68626-106">Attributes and Elements</span></span>

<span data-ttu-id="68626-107">以下各节描述了特性、 子元素和父元素的`EnumerableExpansion`元素。</span><span class="sxs-lookup"><span data-stu-id="68626-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68626-108">属性</span><span class="sxs-lookup"><span data-stu-id="68626-108">Attributes</span></span>

<span data-ttu-id="68626-109">无。</span><span class="sxs-lookup"><span data-stu-id="68626-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68626-110">子元素</span><span class="sxs-lookup"><span data-stu-id="68626-110">Child Elements</span></span>

|<span data-ttu-id="68626-111">元素</span><span class="sxs-lookup"><span data-stu-id="68626-111">Element</span></span>|<span data-ttu-id="68626-112">说明</span><span class="sxs-lookup"><span data-stu-id="68626-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68626-113">EnumerableExpansion （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="68626-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="68626-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="68626-114">Optional element.</span></span><br /><br /> <span data-ttu-id="68626-115">定义此定义的扩展的.NET 集合对象。</span><span class="sxs-lookup"><span data-stu-id="68626-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="68626-116">展开元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="68626-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="68626-117">指定如何为此定义扩展的集合对象。</span><span class="sxs-lookup"><span data-stu-id="68626-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="68626-118">父元素</span><span class="sxs-lookup"><span data-stu-id="68626-118">Parent Elements</span></span>

|<span data-ttu-id="68626-119">元素</span><span class="sxs-lookup"><span data-stu-id="68626-119">Element</span></span>|<span data-ttu-id="68626-120">说明</span><span class="sxs-lookup"><span data-stu-id="68626-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68626-121">EnumerableExpansions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="68626-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="68626-122">该对象在视图中显示时进行扩展的.NET 集合定义的不同方式。</span><span class="sxs-lookup"><span data-stu-id="68626-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="68626-123">备注</span><span class="sxs-lookup"><span data-stu-id="68626-123">Remarks</span></span>

<span data-ttu-id="68626-124">此元素用于定义如何显示集合对象和集合中的对象。</span><span class="sxs-lookup"><span data-stu-id="68626-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="68626-125">在这种情况下，集合对象是指任何支持的对象**System.Collections.ICollection**接口。</span><span class="sxs-lookup"><span data-stu-id="68626-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="68626-126">默认行为是仅显示属性的对象的集合中。</span><span class="sxs-lookup"><span data-stu-id="68626-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="68626-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68626-127">See Also</span></span>

[<span data-ttu-id="68626-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="68626-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

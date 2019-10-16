---
title: EnumerableExpansion 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368746"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="4eba1-102">EnumerableExpansion Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4eba1-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="4eba1-103">定义特定 .NET 集合对象在视图中显示的方式。</span><span class="sxs-lookup"><span data-stu-id="4eba1-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="4eba1-104">配置元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4eba1-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4eba1-105">语法</span><span class="sxs-lookup"><span data-stu-id="4eba1-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4eba1-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4eba1-106">Attributes and Elements</span></span>

<span data-ttu-id="4eba1-107">以下各节介绍了 `EnumerableExpansion` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4eba1-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4eba1-108">属性</span><span class="sxs-lookup"><span data-stu-id="4eba1-108">Attributes</span></span>

<span data-ttu-id="4eba1-109">无。</span><span class="sxs-lookup"><span data-stu-id="4eba1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4eba1-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4eba1-110">Child Elements</span></span>

|<span data-ttu-id="4eba1-111">元素</span><span class="sxs-lookup"><span data-stu-id="4eba1-111">Element</span></span>|<span data-ttu-id="4eba1-112">描述</span><span class="sxs-lookup"><span data-stu-id="4eba1-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4eba1-113">EnumerableExpansion 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4eba1-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="4eba1-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="4eba1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="4eba1-115">定义通过此定义扩展哪些 .NET 集合对象。</span><span class="sxs-lookup"><span data-stu-id="4eba1-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="4eba1-116">Expand 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4eba1-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="4eba1-117">指定为此定义扩展集合对象的方式。</span><span class="sxs-lookup"><span data-stu-id="4eba1-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4eba1-118">父元素</span><span class="sxs-lookup"><span data-stu-id="4eba1-118">Parent Elements</span></span>

|<span data-ttu-id="4eba1-119">元素</span><span class="sxs-lookup"><span data-stu-id="4eba1-119">Element</span></span>|<span data-ttu-id="4eba1-120">描述</span><span class="sxs-lookup"><span data-stu-id="4eba1-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4eba1-121">EnumerableExpansions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4eba1-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="4eba1-122">定义 .NET 集合对象在视图中显示时的扩展方式。</span><span class="sxs-lookup"><span data-stu-id="4eba1-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4eba1-123">备注</span><span class="sxs-lookup"><span data-stu-id="4eba1-123">Remarks</span></span>

<span data-ttu-id="4eba1-124">此元素用于定义集合对象和集合中的对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="4eba1-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="4eba1-125">在这种情况下，集合对象引用支持**system.object**接口的任何对象。</span><span class="sxs-lookup"><span data-stu-id="4eba1-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="4eba1-126">默认行为是只显示集合中对象的属性。</span><span class="sxs-lookup"><span data-stu-id="4eba1-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="4eba1-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4eba1-127">See Also</span></span>

[<span data-ttu-id="4eba1-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4eba1-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

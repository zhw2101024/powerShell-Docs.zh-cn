---
title: Expand 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368736"
---
# <a name="expand-element-format"></a><span data-ttu-id="9f832-102">Expand Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9f832-102">Expand Element (Format)</span></span>

<span data-ttu-id="9f832-103">指定为此定义扩展集合对象的方式。</span><span class="sxs-lookup"><span data-stu-id="9f832-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="9f832-104">配置元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式） Expand 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9f832-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f832-105">语法</span><span class="sxs-lookup"><span data-stu-id="9f832-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f832-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9f832-106">Attributes and Elements</span></span>

<span data-ttu-id="9f832-107">以下各节介绍了 `Expand` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9f832-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f832-108">属性</span><span class="sxs-lookup"><span data-stu-id="9f832-108">Attributes</span></span>

<span data-ttu-id="9f832-109">无。</span><span class="sxs-lookup"><span data-stu-id="9f832-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f832-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9f832-110">Child Elements</span></span>

<span data-ttu-id="9f832-111">无。</span><span class="sxs-lookup"><span data-stu-id="9f832-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f832-112">父元素</span><span class="sxs-lookup"><span data-stu-id="9f832-112">Parent Elements</span></span>

|<span data-ttu-id="9f832-113">元素</span><span class="sxs-lookup"><span data-stu-id="9f832-113">Element</span></span>|<span data-ttu-id="9f832-114">描述</span><span class="sxs-lookup"><span data-stu-id="9f832-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f832-115">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9f832-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="9f832-116">定义特定 .NET 集合对象在视图中显示的方式。</span><span class="sxs-lookup"><span data-stu-id="9f832-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9f832-117">文本值</span><span class="sxs-lookup"><span data-stu-id="9f832-117">Text Value</span></span>

<span data-ttu-id="9f832-118">指定下列值之一：</span><span class="sxs-lookup"><span data-stu-id="9f832-118">Specify one of the following values:</span></span>

- <span data-ttu-id="9f832-119">EnumOnly：仅显示集合中对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9f832-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="9f832-120">CoreOnly：仅显示集合对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9f832-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="9f832-121">Both：显示集合中的对象的属性和集合对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9f832-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f832-122">备注</span><span class="sxs-lookup"><span data-stu-id="9f832-122">Remarks</span></span>

<span data-ttu-id="9f832-123">此元素用于定义集合对象和集合中的对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="9f832-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="9f832-124">在这种情况下，集合对象引用支持**system.object**接口的任何对象。</span><span class="sxs-lookup"><span data-stu-id="9f832-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="9f832-125">默认行为是只显示集合中对象的属性。</span><span class="sxs-lookup"><span data-stu-id="9f832-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f832-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f832-126">See Also</span></span>

[<span data-ttu-id="9f832-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9f832-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

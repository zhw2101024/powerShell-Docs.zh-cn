---
title: SelectionSets 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063755"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="1c589-102">SelectionSets Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1c589-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="1c589-103">定义可以使用的格式设置文件的所有视图的.NET 对象的公用集。</span><span class="sxs-lookup"><span data-stu-id="1c589-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="1c589-104">视图和控件的格式设置文件可以通过使用仅所选内容集的名称引用对象的完整的集合。</span><span class="sxs-lookup"><span data-stu-id="1c589-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="1c589-105">配置元素 SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="1c589-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="1c589-106">语法</span><span class="sxs-lookup"><span data-stu-id="1c589-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c589-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1c589-107">Attributes and Elements</span></span>

<span data-ttu-id="1c589-108">以下各节描述的特性、 子元素和父元素的`SelectionSets`元素。</span><span class="sxs-lookup"><span data-stu-id="1c589-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="1c589-109">每个子元素定义一组的集的名称，可以引用的对象。</span><span class="sxs-lookup"><span data-stu-id="1c589-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="1c589-110">子元素的顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="1c589-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c589-111">属性</span><span class="sxs-lookup"><span data-stu-id="1c589-111">Attributes</span></span>

<span data-ttu-id="1c589-112">无。</span><span class="sxs-lookup"><span data-stu-id="1c589-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c589-113">子元素</span><span class="sxs-lookup"><span data-stu-id="1c589-113">Child Elements</span></span>

|<span data-ttu-id="1c589-114">元素</span><span class="sxs-lookup"><span data-stu-id="1c589-114">Element</span></span>|<span data-ttu-id="1c589-115">说明</span><span class="sxs-lookup"><span data-stu-id="1c589-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c589-116">SelectionSet 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="1c589-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="1c589-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="1c589-117">Required element.</span></span><br /><br /> <span data-ttu-id="1c589-118">定义集的名称，可以引用.NET 对象的单个组。</span><span class="sxs-lookup"><span data-stu-id="1c589-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c589-119">父元素</span><span class="sxs-lookup"><span data-stu-id="1c589-119">Parent Elements</span></span>

|<span data-ttu-id="1c589-120">元素</span><span class="sxs-lookup"><span data-stu-id="1c589-120">Element</span></span>|<span data-ttu-id="1c589-121">说明</span><span class="sxs-lookup"><span data-stu-id="1c589-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c589-122">配置元素</span><span class="sxs-lookup"><span data-stu-id="1c589-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="1c589-123">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="1c589-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c589-124">备注</span><span class="sxs-lookup"><span data-stu-id="1c589-124">Remarks</span></span>

<span data-ttu-id="1c589-125">当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。</span><span class="sxs-lookup"><span data-stu-id="1c589-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="1c589-126">在定义您的视图时，可以通过使用所选内容，而不是列出每个视图中的所有对象设置的名称中指定对象的集。</span><span class="sxs-lookup"><span data-stu-id="1c589-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="1c589-127">常见的选项集，由其名称定义的格式设置文件的视图或视图的定义时指定。</span><span class="sxs-lookup"><span data-stu-id="1c589-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="1c589-128">在这些情况下，`SelectionSetName`的子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集。</span><span class="sxs-lookup"><span data-stu-id="1c589-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="1c589-129">有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="1c589-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c589-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c589-130">See Also</span></span>

[<span data-ttu-id="1c589-131">配置元素</span><span class="sxs-lookup"><span data-stu-id="1c589-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="1c589-132">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="1c589-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1c589-133">SelectionSet 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="1c589-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="1c589-134">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="1c589-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: SelectionSets 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361866"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="57fb4-102">SelectionSets Element (Format)</span><span class="sxs-lookup"><span data-stu-id="57fb4-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="57fb4-103">定义可供格式设置文件的所有视图使用的常用 .NET 对象集。</span><span class="sxs-lookup"><span data-stu-id="57fb4-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="57fb4-104">格式设置文件的视图和控件可以只使用选择集的名称来引用完整的对象集。</span><span class="sxs-lookup"><span data-stu-id="57fb4-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="57fb4-105">配置元素 SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="57fb4-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="57fb4-106">语法</span><span class="sxs-lookup"><span data-stu-id="57fb4-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57fb4-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="57fb4-107">Attributes and Elements</span></span>

<span data-ttu-id="57fb4-108">以下各节介绍 `SelectionSets` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="57fb4-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="57fb4-109">每个子元素定义一组可由集名称引用的对象。</span><span class="sxs-lookup"><span data-stu-id="57fb4-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="57fb4-110">子元素的顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="57fb4-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="57fb4-111">属性</span><span class="sxs-lookup"><span data-stu-id="57fb4-111">Attributes</span></span>

<span data-ttu-id="57fb4-112">无。</span><span class="sxs-lookup"><span data-stu-id="57fb4-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57fb4-113">子元素</span><span class="sxs-lookup"><span data-stu-id="57fb4-113">Child Elements</span></span>

|<span data-ttu-id="57fb4-114">元素</span><span class="sxs-lookup"><span data-stu-id="57fb4-114">Element</span></span>|<span data-ttu-id="57fb4-115">描述</span><span class="sxs-lookup"><span data-stu-id="57fb4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57fb4-116">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="57fb4-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="57fb4-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="57fb4-117">Required element.</span></span><br /><br /> <span data-ttu-id="57fb4-118">定义一组可由集名称引用的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="57fb4-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="57fb4-119">父元素</span><span class="sxs-lookup"><span data-stu-id="57fb4-119">Parent Elements</span></span>

|<span data-ttu-id="57fb4-120">元素</span><span class="sxs-lookup"><span data-stu-id="57fb4-120">Element</span></span>|<span data-ttu-id="57fb4-121">描述</span><span class="sxs-lookup"><span data-stu-id="57fb4-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57fb4-122">配置元素</span><span class="sxs-lookup"><span data-stu-id="57fb4-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="57fb4-123">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="57fb4-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="57fb4-124">备注</span><span class="sxs-lookup"><span data-stu-id="57fb4-124">Remarks</span></span>

<span data-ttu-id="57fb4-125">如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。</span><span class="sxs-lookup"><span data-stu-id="57fb4-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="57fb4-126">定义视图时，可以使用选择集的名称（而不是列出每个视图中的所有对象）来指定对象集。</span><span class="sxs-lookup"><span data-stu-id="57fb4-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="57fb4-127">常用选择集在定义格式设置文件的视图或视图定义时由其名称指定。</span><span class="sxs-lookup"><span data-stu-id="57fb4-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="57fb4-128">在这些情况下，@no__t 的 @no__t 子元素和 @no__t 2 元素指定要使用的集。</span><span class="sxs-lookup"><span data-stu-id="57fb4-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="57fb4-129">有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="57fb4-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57fb4-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57fb4-130">See Also</span></span>

[<span data-ttu-id="57fb4-131">配置元素</span><span class="sxs-lookup"><span data-stu-id="57fb4-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="57fb4-132">定义选择集</span><span class="sxs-lookup"><span data-stu-id="57fb4-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="57fb4-133">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="57fb4-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="57fb4-134">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="57fb4-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: SelectionSet 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368376"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="87b0c-102">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="87b0c-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="87b0c-103">定义一组可由集名称引用的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="87b0c-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="87b0c-104">配置元素（格式） SelectionSets 元素（format） SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="87b0c-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87b0c-105">语法</span><span class="sxs-lookup"><span data-stu-id="87b0c-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87b0c-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="87b0c-106">Attributes and Elements</span></span>

<span data-ttu-id="87b0c-107">以下各节介绍了 `SelectionSet` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="87b0c-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="87b0c-108">每个选项集都必须具有一个名称，并且必须指定该集的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="87b0c-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="87b0c-109">特性</span><span class="sxs-lookup"><span data-stu-id="87b0c-109">Attributes</span></span>

<span data-ttu-id="87b0c-110">无。</span><span class="sxs-lookup"><span data-stu-id="87b0c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87b0c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="87b0c-111">Child Elements</span></span>

|<span data-ttu-id="87b0c-112">元素</span><span class="sxs-lookup"><span data-stu-id="87b0c-112">Element</span></span>|<span data-ttu-id="87b0c-113">描述</span><span class="sxs-lookup"><span data-stu-id="87b0c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87b0c-114">SelectionSet 的 Name 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="87b0c-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="87b0c-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="87b0c-115">Required element.</span></span><br /><br /> <span data-ttu-id="87b0c-116">指定用于引用选项集的名称。</span><span class="sxs-lookup"><span data-stu-id="87b0c-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="87b0c-117">Types 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="87b0c-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="87b0c-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="87b0c-118">Required element.</span></span><br /><br /> <span data-ttu-id="87b0c-119">定义选择集中的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="87b0c-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87b0c-120">父元素</span><span class="sxs-lookup"><span data-stu-id="87b0c-120">Parent Elements</span></span>

|<span data-ttu-id="87b0c-121">元素</span><span class="sxs-lookup"><span data-stu-id="87b0c-121">Element</span></span>|<span data-ttu-id="87b0c-122">描述</span><span class="sxs-lookup"><span data-stu-id="87b0c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87b0c-123">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="87b0c-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="87b0c-124">定义可供格式设置文件的所有视图使用的常用 .NET 对象集。</span><span class="sxs-lookup"><span data-stu-id="87b0c-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87b0c-125">备注</span><span class="sxs-lookup"><span data-stu-id="87b0c-125">Remarks</span></span>

<span data-ttu-id="87b0c-126">如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。</span><span class="sxs-lookup"><span data-stu-id="87b0c-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="87b0c-127">定义视图时，可以使用选择集的名称（而不是列出每个视图中的所有对象）来指定对象集。</span><span class="sxs-lookup"><span data-stu-id="87b0c-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="87b0c-128">常用选择集在定义格式设置文件的视图或视图定义时由其名称指定。</span><span class="sxs-lookup"><span data-stu-id="87b0c-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="87b0c-129">在这些情况下，`ViewSelectedBy` 和 `EntrySelectedBy` 元素的 `SelectionSetName` 子元素指定要使用的集。</span><span class="sxs-lookup"><span data-stu-id="87b0c-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="87b0c-130">有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="87b0c-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="87b0c-131">示例</span><span class="sxs-lookup"><span data-stu-id="87b0c-131">Example</span></span>

<span data-ttu-id="87b0c-132">下面的示例演示一个定义四个 .NET 类型的 `SelectionSet` 元素。</span><span class="sxs-lookup"><span data-stu-id="87b0c-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="87b0c-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87b0c-133">See Also</span></span>

[<span data-ttu-id="87b0c-134">定义选择集</span><span class="sxs-lookup"><span data-stu-id="87b0c-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="87b0c-135">SelectionSet 的 Name 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="87b0c-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="87b0c-136">SelectionSets 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="87b0c-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="87b0c-137">Types 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="87b0c-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="87b0c-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="87b0c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

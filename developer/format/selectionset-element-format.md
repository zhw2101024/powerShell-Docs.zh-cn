---
title: SelectionSet 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861153"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="f8553-102">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f8553-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="f8553-103">定义一组的集的名称，可以引用.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="f8553-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="f8553-104">配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="f8553-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8553-105">语法</span><span class="sxs-lookup"><span data-stu-id="f8553-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8553-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="f8553-106">Attributes and Elements</span></span>

<span data-ttu-id="f8553-107">以下各节描述了特性、 子元素和父元素的`SelectionSet`元素。</span><span class="sxs-lookup"><span data-stu-id="f8553-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="f8553-108">每个所选内容集必须具有一个名称，并且它必须指定集的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="f8553-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8553-109">特性</span><span class="sxs-lookup"><span data-stu-id="f8553-109">Attributes</span></span>

<span data-ttu-id="f8553-110">无。</span><span class="sxs-lookup"><span data-stu-id="f8553-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8553-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f8553-111">Child Elements</span></span>

|<span data-ttu-id="f8553-112">元素</span><span class="sxs-lookup"><span data-stu-id="f8553-112">Element</span></span>|<span data-ttu-id="f8553-113">描述</span><span class="sxs-lookup"><span data-stu-id="f8553-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8553-114">SelectionSet （格式） 的名称元素</span><span class="sxs-lookup"><span data-stu-id="f8553-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="f8553-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="f8553-115">Required element.</span></span><br /><br /> <span data-ttu-id="f8553-116">指定用来引用所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="f8553-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="f8553-117">类型元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="f8553-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="f8553-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="f8553-118">Required element.</span></span><br /><br /> <span data-ttu-id="f8553-119">定义集内所选内容的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="f8553-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8553-120">父元素</span><span class="sxs-lookup"><span data-stu-id="f8553-120">Parent Elements</span></span>

|<span data-ttu-id="f8553-121">元素</span><span class="sxs-lookup"><span data-stu-id="f8553-121">Element</span></span>|<span data-ttu-id="f8553-122">描述</span><span class="sxs-lookup"><span data-stu-id="f8553-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8553-123">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="f8553-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="f8553-124">定义可以使用的格式设置文件的所有视图的.NET 对象的公用集。</span><span class="sxs-lookup"><span data-stu-id="f8553-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f8553-125">备注</span><span class="sxs-lookup"><span data-stu-id="f8553-125">Remarks</span></span>

<span data-ttu-id="f8553-126">当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。</span><span class="sxs-lookup"><span data-stu-id="f8553-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="f8553-127">在定义您的视图时，可以通过使用所选内容，而不是列出每个视图中的所有对象设置的名称中指定对象的集。</span><span class="sxs-lookup"><span data-stu-id="f8553-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="f8553-128">常见的选项集，由其名称定义的格式设置文件的视图或视图的定义时指定。</span><span class="sxs-lookup"><span data-stu-id="f8553-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="f8553-129">在这些情况下，`SelectionSetName`的子元素`ViewSelectedBy`和`EntrySelectedBy`元素指定要使用的集。</span><span class="sxs-lookup"><span data-stu-id="f8553-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="f8553-130">有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f8553-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8553-131">示例</span><span class="sxs-lookup"><span data-stu-id="f8553-131">Example</span></span>

<span data-ttu-id="f8553-132">下面的示例演示`SelectionSet`定义四种.NET 类型的元素。</span><span class="sxs-lookup"><span data-stu-id="f8553-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f8553-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8553-133">See Also</span></span>

[<span data-ttu-id="f8553-134">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="f8553-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f8553-135">Name 元素的 SelectionSet （格式）</span><span class="sxs-lookup"><span data-stu-id="f8553-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="f8553-136">SelectionSets 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="f8553-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="f8553-137">类型元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="f8553-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="f8553-138">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="f8553-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

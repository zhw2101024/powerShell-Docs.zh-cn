---
title: TypeName 元素的类型 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853573"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="c7900-102">TypeName Element for Types (Format)</span><span class="sxs-lookup"><span data-stu-id="c7900-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="c7900-103">指定属于所选内容集的对象的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="c7900-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="c7900-104">配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式） 类型元素 （格式） 类型名称元素的类型 （格式）</span><span class="sxs-lookup"><span data-stu-id="c7900-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7900-105">语法</span><span class="sxs-lookup"><span data-stu-id="c7900-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7900-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c7900-106">Attributes and Elements</span></span>

<span data-ttu-id="c7900-107">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="c7900-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="c7900-108">至少一个`TypeName`元素必须包含在选择集中。</span><span class="sxs-lookup"><span data-stu-id="c7900-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7900-109">特性</span><span class="sxs-lookup"><span data-stu-id="c7900-109">Attributes</span></span>

<span data-ttu-id="c7900-110">无。</span><span class="sxs-lookup"><span data-stu-id="c7900-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7900-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c7900-111">Child Elements</span></span>

<span data-ttu-id="c7900-112">无。</span><span class="sxs-lookup"><span data-stu-id="c7900-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c7900-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c7900-113">Parent Elements</span></span>

|<span data-ttu-id="c7900-114">元素</span><span class="sxs-lookup"><span data-stu-id="c7900-114">Element</span></span>|<span data-ttu-id="c7900-115">描述</span><span class="sxs-lookup"><span data-stu-id="c7900-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7900-116">类型元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="c7900-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="c7900-117">定义集内所选内容的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="c7900-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c7900-118">文本值</span><span class="sxs-lookup"><span data-stu-id="c7900-118">Text Value</span></span>

<span data-ttu-id="c7900-119">指定.NET 类型的完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="c7900-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7900-120">备注</span><span class="sxs-lookup"><span data-stu-id="c7900-120">Remarks</span></span>

<span data-ttu-id="c7900-121">当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。</span><span class="sxs-lookup"><span data-stu-id="c7900-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="c7900-122">在定义您的视图时，可以通过使用所选内容，而不是列出每个视图中的所有对象设置的名称中指定对象的集。</span><span class="sxs-lookup"><span data-stu-id="c7900-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="c7900-123">常见的选项集，由其名称定义的格式设置文件的视图时指定。</span><span class="sxs-lookup"><span data-stu-id="c7900-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="c7900-124">在这些情况下，`SelectionSetName`的子元素`ViewSelectedBy`元素为视图指定组。</span><span class="sxs-lookup"><span data-stu-id="c7900-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="c7900-125">但是，视图的不同项还可以指定适用于只有该视图的项的选择集。</span><span class="sxs-lookup"><span data-stu-id="c7900-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="c7900-126">有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c7900-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="c7900-127">示例</span><span class="sxs-lookup"><span data-stu-id="c7900-127">Example</span></span>

<span data-ttu-id="c7900-128">下面的示例演示`SelectionSet`定义四种.NET 类型的元素。</span><span class="sxs-lookup"><span data-stu-id="c7900-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="c7900-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7900-129">See Also</span></span>

[<span data-ttu-id="c7900-130">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="c7900-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c7900-131">SelectionSet 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="c7900-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="c7900-132">SelectionSets 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="c7900-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="c7900-133">类型元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="c7900-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="c7900-134">编写 Windows PowDefining 的一组 ObjecterShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="c7900-134">Writing a Windows PowDefining Sets of ObjecterShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

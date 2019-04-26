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
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083784"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="77153-102">TypeName Element for Types (Format)</span><span class="sxs-lookup"><span data-stu-id="77153-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="77153-103">指定属于所选内容集的对象的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="77153-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="77153-104">配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式） 类型元素 （格式） 类型名称元素的类型 （格式）</span><span class="sxs-lookup"><span data-stu-id="77153-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77153-105">语法</span><span class="sxs-lookup"><span data-stu-id="77153-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77153-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="77153-106">Attributes and Elements</span></span>

<span data-ttu-id="77153-107">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="77153-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="77153-108">至少一个`TypeName`元素必须包含在选择集中。</span><span class="sxs-lookup"><span data-stu-id="77153-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="77153-109">属性</span><span class="sxs-lookup"><span data-stu-id="77153-109">Attributes</span></span>

<span data-ttu-id="77153-110">无。</span><span class="sxs-lookup"><span data-stu-id="77153-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77153-111">子元素</span><span class="sxs-lookup"><span data-stu-id="77153-111">Child Elements</span></span>

<span data-ttu-id="77153-112">无。</span><span class="sxs-lookup"><span data-stu-id="77153-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="77153-113">父元素</span><span class="sxs-lookup"><span data-stu-id="77153-113">Parent Elements</span></span>

|<span data-ttu-id="77153-114">元素</span><span class="sxs-lookup"><span data-stu-id="77153-114">Element</span></span>|<span data-ttu-id="77153-115">说明</span><span class="sxs-lookup"><span data-stu-id="77153-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77153-116">类型元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="77153-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="77153-117">定义集内所选内容的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="77153-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="77153-118">文本值</span><span class="sxs-lookup"><span data-stu-id="77153-118">Text Value</span></span>

<span data-ttu-id="77153-119">指定.NET 类型的完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="77153-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="77153-120">备注</span><span class="sxs-lookup"><span data-stu-id="77153-120">Remarks</span></span>

<span data-ttu-id="77153-121">当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。</span><span class="sxs-lookup"><span data-stu-id="77153-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="77153-122">在定义您的视图时，可以通过使用所选内容，而不是列出每个视图中的所有对象设置的名称中指定对象的集。</span><span class="sxs-lookup"><span data-stu-id="77153-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="77153-123">常见的选项集，由其名称定义的格式设置文件的视图时指定。</span><span class="sxs-lookup"><span data-stu-id="77153-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="77153-124">在这些情况下，`SelectionSetName`的子元素`ViewSelectedBy`元素为视图指定组。</span><span class="sxs-lookup"><span data-stu-id="77153-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="77153-125">但是，视图的不同项还可以指定适用于只有该视图的项的选择集。</span><span class="sxs-lookup"><span data-stu-id="77153-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="77153-126">有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="77153-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="77153-127">示例</span><span class="sxs-lookup"><span data-stu-id="77153-127">Example</span></span>

<span data-ttu-id="77153-128">下面的示例演示`SelectionSet`定义四种.NET 类型的元素。</span><span class="sxs-lookup"><span data-stu-id="77153-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="77153-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77153-129">See Also</span></span>

[<span data-ttu-id="77153-130">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="77153-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="77153-131">SelectionSet 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="77153-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="77153-132">SelectionSets 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="77153-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="77153-133">类型元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="77153-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="77153-134">编写 Windows PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="77153-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

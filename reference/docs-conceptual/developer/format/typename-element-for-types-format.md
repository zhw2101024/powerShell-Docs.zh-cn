---
title: 类型的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368026"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="9c0cc-102">TypeName Element for Types (Format)</span><span class="sxs-lookup"><span data-stu-id="9c0cc-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="9c0cc-103">指定属于选择集的对象的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="9c0cc-104">配置元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式）类型元素（格式）类型的类型名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9c0cc-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c0cc-105">语法</span><span class="sxs-lookup"><span data-stu-id="9c0cc-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c0cc-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9c0cc-106">Attributes and Elements</span></span>

<span data-ttu-id="9c0cc-107">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="9c0cc-108">选择集中必须包含至少一个 `TypeName` 元素。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c0cc-109">特性</span><span class="sxs-lookup"><span data-stu-id="9c0cc-109">Attributes</span></span>

<span data-ttu-id="9c0cc-110">无。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c0cc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9c0cc-111">Child Elements</span></span>

<span data-ttu-id="9c0cc-112">无。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c0cc-113">父元素</span><span class="sxs-lookup"><span data-stu-id="9c0cc-113">Parent Elements</span></span>

|<span data-ttu-id="9c0cc-114">元素</span><span class="sxs-lookup"><span data-stu-id="9c0cc-114">Element</span></span>|<span data-ttu-id="9c0cc-115">描述</span><span class="sxs-lookup"><span data-stu-id="9c0cc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c0cc-116">Types 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9c0cc-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="9c0cc-117">定义选择集中的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9c0cc-118">文本值</span><span class="sxs-lookup"><span data-stu-id="9c0cc-118">Text Value</span></span>

<span data-ttu-id="9c0cc-119">指定 .NET 类型的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c0cc-120">备注</span><span class="sxs-lookup"><span data-stu-id="9c0cc-120">Remarks</span></span>

<span data-ttu-id="9c0cc-121">如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="9c0cc-122">定义视图时，可以使用选择集的名称（而不是列出每个视图中的所有对象）来指定对象集。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="9c0cc-123">常用选择集在定义格式设置文件的视图时由其名称指定。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="9c0cc-124">在这些情况下，视图的 `ViewSelectedBy` 元素的 `SelectionSetName` 子元素将指定集。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="9c0cc-125">但是，视图的不同项还可以指定仅适用于该视图项的选择集。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="9c0cc-126">有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="9c0cc-127">示例</span><span class="sxs-lookup"><span data-stu-id="9c0cc-127">Example</span></span>

<span data-ttu-id="9c0cc-128">下面的示例演示一个定义四个 .NET 类型的 `SelectionSet` 元素。</span><span class="sxs-lookup"><span data-stu-id="9c0cc-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9c0cc-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c0cc-129">See Also</span></span>

[<span data-ttu-id="9c0cc-130">定义选择集</span><span class="sxs-lookup"><span data-stu-id="9c0cc-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9c0cc-131">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9c0cc-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="9c0cc-132">SelectionSets 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9c0cc-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="9c0cc-133">Types 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9c0cc-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="9c0cc-134">编写 Windows PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9c0cc-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: SelectionSet 的类型元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367956"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="c9330-102">Types Element for SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="c9330-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="c9330-103">定义选择集中的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="c9330-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="c9330-104">配置元素（格式） SelectionSets 元素（格式） SelectionSet 元素（格式）类型元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9330-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9330-105">语法</span><span class="sxs-lookup"><span data-stu-id="c9330-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9330-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c9330-106">Attributes and Elements</span></span>

<span data-ttu-id="c9330-107">以下各节介绍了 `Types` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c9330-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="c9330-108">必须至少有一个子元素，但对于可添加的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="c9330-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9330-109">属性</span><span class="sxs-lookup"><span data-stu-id="c9330-109">Attributes</span></span>

<span data-ttu-id="c9330-110">无。</span><span class="sxs-lookup"><span data-stu-id="c9330-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9330-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c9330-111">Child Elements</span></span>

|<span data-ttu-id="c9330-112">元素</span><span class="sxs-lookup"><span data-stu-id="c9330-112">Element</span></span>|<span data-ttu-id="c9330-113">描述</span><span class="sxs-lookup"><span data-stu-id="c9330-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9330-114">类型的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9330-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="c9330-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="c9330-115">Required element.</span></span><br /><br /> <span data-ttu-id="c9330-116">指定属于选择集的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="c9330-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c9330-117">父元素</span><span class="sxs-lookup"><span data-stu-id="c9330-117">Parent Elements</span></span>

|<span data-ttu-id="c9330-118">元素</span><span class="sxs-lookup"><span data-stu-id="c9330-118">Element</span></span>|<span data-ttu-id="c9330-119">描述</span><span class="sxs-lookup"><span data-stu-id="c9330-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9330-120">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9330-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="c9330-121">定义一组可由集名称引用的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="c9330-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9330-122">备注</span><span class="sxs-lookup"><span data-stu-id="c9330-122">Remarks</span></span>

<span data-ttu-id="c9330-123">此元素定义的对象构成一个选项集，该选项集可由视图、视图定义（视图可以有多个定义）或指定选择条件时使用。</span><span class="sxs-lookup"><span data-stu-id="c9330-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="c9330-124">有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c9330-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="c9330-125">示例</span><span class="sxs-lookup"><span data-stu-id="c9330-125">Example</span></span>

<span data-ttu-id="c9330-126">此示例演示一个定义四个 .NET 类型的 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="c9330-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c9330-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9330-127">See Also</span></span>

[<span data-ttu-id="c9330-128">定义对象集</span><span class="sxs-lookup"><span data-stu-id="c9330-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c9330-129">SelectionSet 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9330-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="c9330-130">类型的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9330-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="c9330-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="c9330-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

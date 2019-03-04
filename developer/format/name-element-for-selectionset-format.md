---
title: SelectionSet （格式） 的名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858163"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="96659-102">Name Element for SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="96659-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="96659-103">指定用来引用所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="96659-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="96659-104">配置元素 （格式） SelectionSets 元素 （格式） SelectionSet 元素 （格式） 的名称元素更改为的 SelectionSet （格式）</span><span class="sxs-lookup"><span data-stu-id="96659-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96659-105">语法</span><span class="sxs-lookup"><span data-stu-id="96659-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96659-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="96659-106">Attributes and Elements</span></span>

<span data-ttu-id="96659-107">以下各节描述的特性、 子元素和父元素的`Name`元素。</span><span class="sxs-lookup"><span data-stu-id="96659-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96659-108">特性</span><span class="sxs-lookup"><span data-stu-id="96659-108">Attributes</span></span>

<span data-ttu-id="96659-109">无。</span><span class="sxs-lookup"><span data-stu-id="96659-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96659-110">子元素</span><span class="sxs-lookup"><span data-stu-id="96659-110">Child Elements</span></span>

<span data-ttu-id="96659-111">无。</span><span class="sxs-lookup"><span data-stu-id="96659-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="96659-112">父元素</span><span class="sxs-lookup"><span data-stu-id="96659-112">Parent Elements</span></span>

|<span data-ttu-id="96659-113">元素</span><span class="sxs-lookup"><span data-stu-id="96659-113">Element</span></span>|<span data-ttu-id="96659-114">描述</span><span class="sxs-lookup"><span data-stu-id="96659-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96659-115">SelectionSet 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="96659-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="96659-116">定义集的名称，可以引用.NET 对象的单个组。</span><span class="sxs-lookup"><span data-stu-id="96659-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="96659-117">文本值</span><span class="sxs-lookup"><span data-stu-id="96659-117">Text Value</span></span>

<span data-ttu-id="96659-118">指定要引用所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="96659-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="96659-119">有可以使用哪些字符没有限制。</span><span class="sxs-lookup"><span data-stu-id="96659-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="96659-120">备注</span><span class="sxs-lookup"><span data-stu-id="96659-120">Remarks</span></span>

<span data-ttu-id="96659-121">此处指定的名称中使用`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="96659-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="96659-122">可由视图定义的视图的选项集 （视图可以具有多个定义），或指定选择条件时。</span><span class="sxs-lookup"><span data-stu-id="96659-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="96659-123">有关所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="96659-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="96659-124">示例</span><span class="sxs-lookup"><span data-stu-id="96659-124">Example</span></span>

<span data-ttu-id="96659-125">此示例显示了`SelectionSet`定义四种.NET 类型的元素。</span><span class="sxs-lookup"><span data-stu-id="96659-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="96659-126">所选内容集的名称是"FileSystemTypes"。</span><span class="sxs-lookup"><span data-stu-id="96659-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="96659-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96659-127">See Also</span></span>

[<span data-ttu-id="96659-128">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="96659-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="96659-129">SelectionSet 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="96659-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="96659-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="96659-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

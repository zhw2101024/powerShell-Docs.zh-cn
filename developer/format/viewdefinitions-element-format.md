---
title: ViewDefinitions 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083699"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="9154f-102">ViewDefinitions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9154f-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="9154f-103">定义用于显示.NET 对象的视图。</span><span class="sxs-lookup"><span data-stu-id="9154f-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="9154f-104">这些视图可以显示在表格格式、 列表格式、 宽格式和自定义控件格式的属性和对象的脚本值。</span><span class="sxs-lookup"><span data-stu-id="9154f-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="9154f-105">配置元素 （格式） ViewDefinitions （XML 格式） 元素</span><span class="sxs-lookup"><span data-stu-id="9154f-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="9154f-106">语法</span><span class="sxs-lookup"><span data-stu-id="9154f-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9154f-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9154f-107">Attributes and Elements</span></span>

<span data-ttu-id="9154f-108">以下各节描述的特性、 子元素和父元素的`ViewDefinitions`元素。</span><span class="sxs-lookup"><span data-stu-id="9154f-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="9154f-109">没有可以在格式设置文件中定义的视图数目没有限制，可以按任意顺序添加它们。</span><span class="sxs-lookup"><span data-stu-id="9154f-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="9154f-110">属性</span><span class="sxs-lookup"><span data-stu-id="9154f-110">Attributes</span></span>

<span data-ttu-id="9154f-111">无。</span><span class="sxs-lookup"><span data-stu-id="9154f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9154f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9154f-112">Child Elements</span></span>

|<span data-ttu-id="9154f-113">元素</span><span class="sxs-lookup"><span data-stu-id="9154f-113">Element</span></span>|<span data-ttu-id="9154f-114">说明</span><span class="sxs-lookup"><span data-stu-id="9154f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9154f-115">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="9154f-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="9154f-116">定义用于显示一个或多个.NET 对象的视图。</span><span class="sxs-lookup"><span data-stu-id="9154f-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9154f-117">父元素</span><span class="sxs-lookup"><span data-stu-id="9154f-117">Parent Elements</span></span>

|<span data-ttu-id="9154f-118">元素</span><span class="sxs-lookup"><span data-stu-id="9154f-118">Element</span></span>|<span data-ttu-id="9154f-119">说明</span><span class="sxs-lookup"><span data-stu-id="9154f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9154f-120">配置元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="9154f-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="9154f-121">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="9154f-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9154f-122">备注</span><span class="sxs-lookup"><span data-stu-id="9154f-122">Remarks</span></span>

<span data-ttu-id="9154f-123">有关不同类型的视图组件的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="9154f-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="9154f-124">创建表视图</span><span class="sxs-lookup"><span data-stu-id="9154f-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="9154f-125">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="9154f-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="9154f-126">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="9154f-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="9154f-127">自定义控件</span><span class="sxs-lookup"><span data-stu-id="9154f-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="9154f-128">示例</span><span class="sxs-lookup"><span data-stu-id="9154f-128">Example</span></span>

<span data-ttu-id="9154f-129">此示例显示了`ViewDefinitions`元素，其中包含有关表视图和列表视图的父元素。</span><span class="sxs-lookup"><span data-stu-id="9154f-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="9154f-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9154f-130">See Also</span></span>

[<span data-ttu-id="9154f-131">配置元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="9154f-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="9154f-132">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="9154f-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="9154f-133">创建表视图</span><span class="sxs-lookup"><span data-stu-id="9154f-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9154f-134">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="9154f-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9154f-135">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="9154f-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9154f-136">自定义控件</span><span class="sxs-lookup"><span data-stu-id="9154f-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="9154f-137">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9154f-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

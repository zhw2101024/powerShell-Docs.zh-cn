---
title: ViewSelectedBy 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083818"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="3b0f0-102">ViewSelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3b0f0-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="3b0f0-103">定义视图所显示的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="3b0f0-104">每个视图都必须指定至少一个.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="3b0f0-105">ViewDefinitions 元素 （格式） 视图元素 （格式） ViewSelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="3b0f0-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3b0f0-106">语法</span><span class="sxs-lookup"><span data-stu-id="3b0f0-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b0f0-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-107">Attributes and Elements</span></span>

<span data-ttu-id="3b0f0-108">以下各节描述的特性、 子元素和父元素的`ViewSelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="3b0f0-109">此元素必须包含至少一个`TypeName`或`SelectionSetName`子元素。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="3b0f0-110">可以指定的子元素的数目没有限制也不是其顺序重要。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b0f0-111">属性</span><span class="sxs-lookup"><span data-stu-id="3b0f0-111">Attributes</span></span>

<span data-ttu-id="3b0f0-112">无。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3b0f0-113">子元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-113">Child Elements</span></span>

|<span data-ttu-id="3b0f0-114">元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-114">Element</span></span>|<span data-ttu-id="3b0f0-115">说明</span><span class="sxs-lookup"><span data-stu-id="3b0f0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b0f0-116">ViewSelectedBy （格式） 的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="3b0f0-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3b0f0-118">指定视图显示的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="3b0f0-119">ViewSelectedBy （格式） 的 SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="3b0f0-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3b0f0-121">指定一组.NET 对象所显示的视图。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3b0f0-122">父元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-122">Parent Elements</span></span>

|<span data-ttu-id="3b0f0-123">元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-123">Element</span></span>|<span data-ttu-id="3b0f0-124">说明</span><span class="sxs-lookup"><span data-stu-id="3b0f0-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b0f0-125">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="3b0f0-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="3b0f0-126">定义一个视图，显示一个或多个.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3b0f0-127">备注</span><span class="sxs-lookup"><span data-stu-id="3b0f0-127">Remarks</span></span>

<span data-ttu-id="3b0f0-128">有关如何在不同的视图中使用此元素的详细信息，请参阅[表视图组件](./creating-a-table-view.md)，[列表视图组件](./creating-a-list-view.md)，[宽视图组件](./creating-a-wide-view.md)，以及[自定义控件组件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="3b0f0-129">`SelectionSetName`时的格式设置文件定义的对象的多个视图将显示一组使用元素。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="3b0f0-130">有关如何定义和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3b0f0-131">示例</span><span class="sxs-lookup"><span data-stu-id="3b0f0-131">Example</span></span>

<span data-ttu-id="3b0f0-132">下面的示例演示如何指定[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)列表视图的对象。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="3b0f0-133">相同的架构用于表中，宽，和自定义视图。</span><span class="sxs-lookup"><span data-stu-id="3b0f0-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="3b0f0-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b0f0-134">See Also</span></span>

[<span data-ttu-id="3b0f0-135">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="3b0f0-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3b0f0-136">创建表视图</span><span class="sxs-lookup"><span data-stu-id="3b0f0-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3b0f0-137">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="3b0f0-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3b0f0-138">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="3b0f0-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="3b0f0-139">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="3b0f0-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3b0f0-140">ViewSelectedBy （格式） 的 SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="3b0f0-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="3b0f0-141">类型名称元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="3b0f0-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="3b0f0-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="3b0f0-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

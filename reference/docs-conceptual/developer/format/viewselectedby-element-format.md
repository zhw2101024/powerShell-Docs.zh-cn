---
title: ViewSelectedBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367966"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="3c537-102">ViewSelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c537-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="3c537-103">定义视图显示的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3c537-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="3c537-104">每个视图必须至少指定一个 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3c537-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="3c537-105">ViewDefinitions 元素（格式） View 元素（Format） ViewSelectedBy 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="3c537-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c537-106">语法</span><span class="sxs-lookup"><span data-stu-id="3c537-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c537-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="3c537-107">Attributes and Elements</span></span>

<span data-ttu-id="3c537-108">以下各节介绍 `ViewSelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3c537-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="3c537-109">此元素必须包含至少一个 `TypeName` 或 `SelectionSetName` 子元素。</span><span class="sxs-lookup"><span data-stu-id="3c537-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="3c537-110">对于可以指定的子元素数没有限制，也没有其顺序。</span><span class="sxs-lookup"><span data-stu-id="3c537-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c537-111">特性</span><span class="sxs-lookup"><span data-stu-id="3c537-111">Attributes</span></span>

<span data-ttu-id="3c537-112">无。</span><span class="sxs-lookup"><span data-stu-id="3c537-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c537-113">子元素</span><span class="sxs-lookup"><span data-stu-id="3c537-113">Child Elements</span></span>

|<span data-ttu-id="3c537-114">元素</span><span class="sxs-lookup"><span data-stu-id="3c537-114">Element</span></span>|<span data-ttu-id="3c537-115">描述</span><span class="sxs-lookup"><span data-stu-id="3c537-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c537-116">ViewSelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="3c537-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="3c537-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3c537-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3c537-118">指定视图显示的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3c537-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="3c537-119">ViewSelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3c537-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="3c537-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3c537-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3c537-121">指定视图显示的一组 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3c537-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c537-122">父元素</span><span class="sxs-lookup"><span data-stu-id="3c537-122">Parent Elements</span></span>

|<span data-ttu-id="3c537-123">元素</span><span class="sxs-lookup"><span data-stu-id="3c537-123">Element</span></span>|<span data-ttu-id="3c537-124">描述</span><span class="sxs-lookup"><span data-stu-id="3c537-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c537-125">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3c537-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="3c537-126">定义一个视图，该视图显示一个或多个 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3c537-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c537-127">备注</span><span class="sxs-lookup"><span data-stu-id="3c537-127">Remarks</span></span>

<span data-ttu-id="3c537-128">有关此元素在不同视图中的使用方式的详细信息，请参阅[表视图组件](./creating-a-table-view.md)、[列表视图](./creating-a-list-view.md)组件、[宽视图组件](./creating-a-wide-view.md)和[自定义控件组件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="3c537-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="3c537-129">当格式文件定义一组由多个视图显示的对象时，将使用 `SelectionSetName` 元素。</span><span class="sxs-lookup"><span data-stu-id="3c537-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="3c537-130">有关如何定义和引用选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="3c537-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c537-131">示例</span><span class="sxs-lookup"><span data-stu-id="3c537-131">Example</span></span>

<span data-ttu-id="3c537-132">下面的示例演示如何为列表视图指定[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="3c537-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="3c537-133">表、宽视图和自定义视图使用相同的架构。</span><span class="sxs-lookup"><span data-stu-id="3c537-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="3c537-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c537-134">See Also</span></span>

[<span data-ttu-id="3c537-135">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="3c537-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3c537-136">创建表视图</span><span class="sxs-lookup"><span data-stu-id="3c537-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3c537-137">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="3c537-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3c537-138">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="3c537-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="3c537-139">定义选择集</span><span class="sxs-lookup"><span data-stu-id="3c537-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3c537-140">ViewSelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3c537-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="3c537-141">TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3c537-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="3c537-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="3c537-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

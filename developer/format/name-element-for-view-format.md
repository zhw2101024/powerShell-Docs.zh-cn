---
title: 视图 （格式） 的名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859503"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="fcbeb-102">Name Element for View (Format)</span><span class="sxs-lookup"><span data-stu-id="fcbeb-102">Name Element for View (Format)</span></span>

<span data-ttu-id="fcbeb-103">指定用于标识该视图的名称。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="fcbeb-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 名称元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="fcbeb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fcbeb-105">语法</span><span class="sxs-lookup"><span data-stu-id="fcbeb-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fcbeb-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="fcbeb-106">Attributes and Elements</span></span>

<span data-ttu-id="fcbeb-107">以下各节描述了特性、 子元素和父元素的`Name`元素。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="fcbeb-108">只有一个`Name`元素允许为每个视图。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="fcbeb-109">特性</span><span class="sxs-lookup"><span data-stu-id="fcbeb-109">Attributes</span></span>

<span data-ttu-id="fcbeb-110">无。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fcbeb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="fcbeb-111">Child Elements</span></span>

<span data-ttu-id="fcbeb-112">无。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fcbeb-113">父元素</span><span class="sxs-lookup"><span data-stu-id="fcbeb-113">Parent Elements</span></span>

|<span data-ttu-id="fcbeb-114">元素</span><span class="sxs-lookup"><span data-stu-id="fcbeb-114">Element</span></span>|<span data-ttu-id="fcbeb-115">描述</span><span class="sxs-lookup"><span data-stu-id="fcbeb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fcbeb-116">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="fcbeb-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="fcbeb-117">定义一个视图，它用于显示一个或多个.NET 对象的成员。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fcbeb-118">文本值</span><span class="sxs-lookup"><span data-stu-id="fcbeb-118">Text Value</span></span>

<span data-ttu-id="fcbeb-119">指定视图的唯一友好名称。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="fcbeb-120">此名称可以包含对哪些对象或一组对象使用的视图中，哪些命令将返回对象或这些项的组合 （如表视图或列表视图） 视图的类型的引用。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcbeb-121">备注</span><span class="sxs-lookup"><span data-stu-id="fcbeb-121">Remarks</span></span>

<span data-ttu-id="fcbeb-122">有关不同类型的视图的详细信息，请参阅以下主题：[表视图](./creating-a-table-view.md)，[列表视图](./creating-a-list-view.md)，[宽视图](./creating-a-wide-view.md)，并且[自定义视图](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="fcbeb-123">示例</span><span class="sxs-lookup"><span data-stu-id="fcbeb-123">Example</span></span>

<span data-ttu-id="fcbeb-124">下面的示例演示`View`定义的表视图元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="fcbeb-125">视图的名称为"service"。</span><span class="sxs-lookup"><span data-stu-id="fcbeb-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="fcbeb-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcbeb-126">See Also</span></span>

[<span data-ttu-id="fcbeb-127">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="fcbeb-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fcbeb-128">创建表视图</span><span class="sxs-lookup"><span data-stu-id="fcbeb-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fcbeb-129">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="fcbeb-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fcbeb-130">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="fcbeb-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="fcbeb-131">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="fcbeb-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="fcbeb-132">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="fcbeb-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

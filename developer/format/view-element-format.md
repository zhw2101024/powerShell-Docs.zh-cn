---
title: 查看元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856143"
---
# <a name="view-element-format"></a><span data-ttu-id="b148a-102">View Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b148a-102">View Element (Format)</span></span>

<span data-ttu-id="b148a-103">定义一个视图，显示一个或多个.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="b148a-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="b148a-104">可在格式设置文件中定义的视图数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="b148a-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="b148a-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b148a-106">语法</span><span class="sxs-lookup"><span data-stu-id="b148a-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b148a-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b148a-107">Attributes and Elements</span></span>

<span data-ttu-id="b148a-108">以下各节描述了特性、 子元素和父元素的`View`元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="b148a-109">必须指定一个且只有一个控件子元素，并且必须指定的视图和使用视图的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="b148a-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="b148a-110">定义自定义控件，如何对分组对象，并指定是否该视图带外都是可选的。</span><span class="sxs-lookup"><span data-stu-id="b148a-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="b148a-111">特性</span><span class="sxs-lookup"><span data-stu-id="b148a-111">Attributes</span></span>

<span data-ttu-id="b148a-112">无。</span><span class="sxs-lookup"><span data-stu-id="b148a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b148a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="b148a-113">Child Elements</span></span>

|<span data-ttu-id="b148a-114">元素</span><span class="sxs-lookup"><span data-stu-id="b148a-114">Element</span></span>|<span data-ttu-id="b148a-115">描述</span><span class="sxs-lookup"><span data-stu-id="b148a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b148a-116">视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="b148a-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="b148a-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b148a-118">定义一组可以按其从视图中的名称引用的控件。</span><span class="sxs-lookup"><span data-stu-id="b148a-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="b148a-119">CustomControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="b148a-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b148a-121">定义自定义控件的视图格式。</span><span class="sxs-lookup"><span data-stu-id="b148a-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="b148a-122">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="b148a-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="b148a-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b148a-124">定义如何对.NET 对象的成员进行分组。</span><span class="sxs-lookup"><span data-stu-id="b148a-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="b148a-125">ListControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="b148a-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b148a-127">定义视图以列表格式。</span><span class="sxs-lookup"><span data-stu-id="b148a-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="b148a-128">视图 （格式） 的名称元素</span><span class="sxs-lookup"><span data-stu-id="b148a-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="b148a-129">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-129">Required element.</span></span><br /><br /> <span data-ttu-id="b148a-130">指定用来引用该视图的名称。</span><span class="sxs-lookup"><span data-stu-id="b148a-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="b148a-131">TableControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="b148a-132">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-132">Optional element.</span></span><br /><br /> <span data-ttu-id="b148a-133">定义视图以表格格式。</span><span class="sxs-lookup"><span data-stu-id="b148a-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="b148a-134">视图 （格式） 的 ViewSelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="b148a-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="b148a-135">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-135">Required element.</span></span><br /><br /> <span data-ttu-id="b148a-136">定义此视图显示的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="b148a-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="b148a-137">WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="b148a-138">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b148a-138">Optional element.</span></span><br /><br /> <span data-ttu-id="b148a-139">定义范围内 （单个值） 的视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="b148a-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b148a-140">父元素</span><span class="sxs-lookup"><span data-stu-id="b148a-140">Parent Elements</span></span>

|<span data-ttu-id="b148a-141">元素</span><span class="sxs-lookup"><span data-stu-id="b148a-141">Element</span></span>|<span data-ttu-id="b148a-142">描述</span><span class="sxs-lookup"><span data-stu-id="b148a-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b148a-143">ViewDefinitions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="b148a-144">定义用于显示对象的视图。</span><span class="sxs-lookup"><span data-stu-id="b148a-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b148a-145">备注</span><span class="sxs-lookup"><span data-stu-id="b148a-145">Remarks</span></span>

<span data-ttu-id="b148a-146">有关不同的视图和自定义控件的组件的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="b148a-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="b148a-147">表视图组件</span><span class="sxs-lookup"><span data-stu-id="b148a-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="b148a-148">列表视图组件</span><span class="sxs-lookup"><span data-stu-id="b148a-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="b148a-149">宽的视图组件</span><span class="sxs-lookup"><span data-stu-id="b148a-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="b148a-150">自定义控件</span><span class="sxs-lookup"><span data-stu-id="b148a-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="b148a-151">示例</span><span class="sxs-lookup"><span data-stu-id="b148a-151">Example</span></span>

<span data-ttu-id="b148a-152">此示例演示`View`定义的表视图元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="b148a-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="b148a-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b148a-153">See Also</span></span>

[<span data-ttu-id="b148a-154">ViewDefinitions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="b148a-155">视图 （格式） 的名称元素</span><span class="sxs-lookup"><span data-stu-id="b148a-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="b148a-156">ViewSelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="b148a-157">视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="b148a-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="b148a-158">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="b148a-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="b148a-159">TableControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="b148a-160">ListControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="b148a-161">WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="b148a-162">CustomControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b148a-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="b148a-163">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b148a-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: View 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361456"
---
# <a name="view-element-format"></a><span data-ttu-id="335dd-102">View Element (Format)</span><span class="sxs-lookup"><span data-stu-id="335dd-102">View Element (Format)</span></span>

<span data-ttu-id="335dd-103">定义一个视图，该视图显示一个或多个 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="335dd-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="335dd-104">对于可在格式设置文件中定义的视图数没有限制。</span><span class="sxs-lookup"><span data-stu-id="335dd-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="335dd-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="335dd-106">语法</span><span class="sxs-lookup"><span data-stu-id="335dd-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="335dd-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="335dd-107">Attributes and Elements</span></span>

<span data-ttu-id="335dd-108">以下各节介绍了 `View` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="335dd-109">您必须指定一个且仅有一个控件子元素，并且您必须指定视图的名称和使用视图的对象。</span><span class="sxs-lookup"><span data-stu-id="335dd-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="335dd-110">定义自定义控件，如何对对象分组，并指定视图是否带外是可选的。</span><span class="sxs-lookup"><span data-stu-id="335dd-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="335dd-111">属性</span><span class="sxs-lookup"><span data-stu-id="335dd-111">Attributes</span></span>

<span data-ttu-id="335dd-112">无。</span><span class="sxs-lookup"><span data-stu-id="335dd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="335dd-113">子元素</span><span class="sxs-lookup"><span data-stu-id="335dd-113">Child Elements</span></span>

|<span data-ttu-id="335dd-114">元素</span><span class="sxs-lookup"><span data-stu-id="335dd-114">Element</span></span>|<span data-ttu-id="335dd-115">描述</span><span class="sxs-lookup"><span data-stu-id="335dd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="335dd-116">View 的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="335dd-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="335dd-118">定义一组可从视图中的名称引用的控件。</span><span class="sxs-lookup"><span data-stu-id="335dd-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="335dd-119">CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="335dd-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="335dd-121">定义视图的自定义控件格式。</span><span class="sxs-lookup"><span data-stu-id="335dd-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="335dd-122">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="335dd-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-123">Optional element.</span></span><br /><br /> <span data-ttu-id="335dd-124">定义 .NET 对象成员的分组方式。</span><span class="sxs-lookup"><span data-stu-id="335dd-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="335dd-125">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="335dd-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-126">Optional element.</span></span><br /><br /> <span data-ttu-id="335dd-127">定义视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="335dd-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="335dd-128">View 的 Name 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="335dd-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="335dd-129">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-129">Required element.</span></span><br /><br /> <span data-ttu-id="335dd-130">指定用于引用视图的名称。</span><span class="sxs-lookup"><span data-stu-id="335dd-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="335dd-131">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="335dd-132">可选元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-132">Optional element.</span></span><br /><br /> <span data-ttu-id="335dd-133">定义视图的表格格式。</span><span class="sxs-lookup"><span data-stu-id="335dd-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="335dd-134">View 的 ViewSelectedBy 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="335dd-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="335dd-135">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-135">Required element.</span></span><br /><br /> <span data-ttu-id="335dd-136">定义此视图显示的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="335dd-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="335dd-137">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="335dd-138">可选元素。</span><span class="sxs-lookup"><span data-stu-id="335dd-138">Optional element.</span></span><br /><br /> <span data-ttu-id="335dd-139">定义视图的宽（单值）列表格式。</span><span class="sxs-lookup"><span data-stu-id="335dd-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="335dd-140">父元素</span><span class="sxs-lookup"><span data-stu-id="335dd-140">Parent Elements</span></span>

|<span data-ttu-id="335dd-141">元素</span><span class="sxs-lookup"><span data-stu-id="335dd-141">Element</span></span>|<span data-ttu-id="335dd-142">描述</span><span class="sxs-lookup"><span data-stu-id="335dd-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="335dd-143">ViewDefinitions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="335dd-144">定义用于显示对象的视图。</span><span class="sxs-lookup"><span data-stu-id="335dd-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="335dd-145">备注</span><span class="sxs-lookup"><span data-stu-id="335dd-145">Remarks</span></span>

<span data-ttu-id="335dd-146">有关不同视图和自定义控件的组件的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="335dd-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="335dd-147">表视图组件</span><span class="sxs-lookup"><span data-stu-id="335dd-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="335dd-148">列表视图组件</span><span class="sxs-lookup"><span data-stu-id="335dd-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="335dd-149">宽视图组件</span><span class="sxs-lookup"><span data-stu-id="335dd-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="335dd-150">自定义控件</span><span class="sxs-lookup"><span data-stu-id="335dd-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="335dd-151">示例</span><span class="sxs-lookup"><span data-stu-id="335dd-151">Example</span></span>

<span data-ttu-id="335dd-152">此示例演示了一个 `View` 元素，该元素定义[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象的表视图。</span><span class="sxs-lookup"><span data-stu-id="335dd-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="335dd-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="335dd-153">See Also</span></span>

[<span data-ttu-id="335dd-154">ViewDefinitions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="335dd-155">View 的 Name 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="335dd-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="335dd-156">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="335dd-157">View 的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="335dd-158">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="335dd-159">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="335dd-160">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="335dd-161">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="335dd-162">CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="335dd-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="335dd-163">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="335dd-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

---
title: WideControl 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859823"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="b86c1-102">WideControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b86c1-102">WideControl Element (Format)</span></span>

<span data-ttu-id="b86c1-103">定义范围内 （单个值） 的视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="b86c1-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="b86c1-104">此视图显示单个属性值或为每个对象的脚本值。</span><span class="sxs-lookup"><span data-stu-id="b86c1-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="b86c1-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b86c1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b86c1-106">语法</span><span class="sxs-lookup"><span data-stu-id="b86c1-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b86c1-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-107">Attributes and Elements</span></span>

<span data-ttu-id="b86c1-108">以下各节描述的特性、 子元素和父元素的`WideControl`元素。</span><span class="sxs-lookup"><span data-stu-id="b86c1-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="b86c1-109">不能指定`AutoSize`和`ColumnNumber`元素出现在同一时间。</span><span class="sxs-lookup"><span data-stu-id="b86c1-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="b86c1-110">特性</span><span class="sxs-lookup"><span data-stu-id="b86c1-110">Attributes</span></span>

<span data-ttu-id="b86c1-111">无。</span><span class="sxs-lookup"><span data-stu-id="b86c1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b86c1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-112">Child Elements</span></span>

|<span data-ttu-id="b86c1-113">元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-113">Element</span></span>|<span data-ttu-id="b86c1-114">描述</span><span class="sxs-lookup"><span data-stu-id="b86c1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b86c1-115">WideControl （格式） 的自动调整大小元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="b86c1-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b86c1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b86c1-117">指定列的大小和列数会调整基于数据的大小。</span><span class="sxs-lookup"><span data-stu-id="b86c1-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="b86c1-118">ColumnNumber WideControl （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="b86c1-119">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b86c1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b86c1-120">指定宽视图中显示的列数。</span><span class="sxs-lookup"><span data-stu-id="b86c1-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="b86c1-121">WideEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b86c1-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="b86c1-122">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="b86c1-122">Required element.</span></span><br /><br /> <span data-ttu-id="b86c1-123">提供了宽的视图的定义。</span><span class="sxs-lookup"><span data-stu-id="b86c1-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b86c1-124">父元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-124">Parent Elements</span></span>

|<span data-ttu-id="b86c1-125">元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-125">Element</span></span>|<span data-ttu-id="b86c1-126">描述</span><span class="sxs-lookup"><span data-stu-id="b86c1-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b86c1-127">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b86c1-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="b86c1-128">定义用于显示一个或多个.NET 对象的视图。</span><span class="sxs-lookup"><span data-stu-id="b86c1-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b86c1-129">备注</span><span class="sxs-lookup"><span data-stu-id="b86c1-129">Remarks</span></span>

<span data-ttu-id="b86c1-130">在定义较宽的视图，你可以添加`AutoSize`元素或`ColumnNumber`但不能添加两者。</span><span class="sxs-lookup"><span data-stu-id="b86c1-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="b86c1-131">在大多数情况下，只有一个定义需要为每个宽的视图，但可以有多个定义，如果你想要使用相同的视图以显示不同的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="b86c1-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="b86c1-132">在这些情况下，可以为每个对象或对象集提供一个单独的定义。</span><span class="sxs-lookup"><span data-stu-id="b86c1-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="b86c1-133">有关较宽的视图的组件的详细信息，请参阅[宽视图组件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b86c1-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b86c1-134">示例</span><span class="sxs-lookup"><span data-stu-id="b86c1-134">Example</span></span>

<span data-ttu-id="b86c1-135">下面的示例演示`WideControl`用来显示的属性的元素[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="b86c1-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="b86c1-136">有关较宽的视图的完整示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="b86c1-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b86c1-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b86c1-137">See Also</span></span>

[<span data-ttu-id="b86c1-138">WideControl （格式） 的自动调整大小元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="b86c1-139">ColumnNumber WideControl （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="b86c1-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="b86c1-140">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b86c1-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="b86c1-141">WideEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b86c1-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="b86c1-142">宽的视图 (Basic)</span><span class="sxs-lookup"><span data-stu-id="b86c1-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="b86c1-143">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="b86c1-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b86c1-144">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b86c1-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

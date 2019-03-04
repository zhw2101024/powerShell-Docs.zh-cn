---
title: 创建较宽的视图 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858493"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="4f456-102">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="4f456-102">Creating a Wide View</span></span>

<span data-ttu-id="4f456-103">较宽的视图显示每个对象显示单个值。</span><span class="sxs-lookup"><span data-stu-id="4f456-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="4f456-104">显示的值可以是.NET 对象属性的值或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="4f456-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="4f456-105">默认情况下，没有标签或此视图的标头。</span><span class="sxs-lookup"><span data-stu-id="4f456-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="4f456-106">宽的视图显示</span><span class="sxs-lookup"><span data-stu-id="4f456-106">A Wide View Display</span></span>

<span data-ttu-id="4f456-107">下面的示例演示如何显示 Windows PowerShell [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)返回的对象[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 时其输出通过管道传递给[Format-wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f456-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="4f456-108">(默认情况下[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 返回的表视图。)在此示例中，两个列用于显示有关每个返回的对象的进程名称。</span><span class="sxs-lookup"><span data-stu-id="4f456-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="4f456-109">不显示对象的属性的名称，仅属性的值。</span><span class="sxs-lookup"><span data-stu-id="4f456-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="4f456-110">定义宽视图</span><span class="sxs-lookup"><span data-stu-id="4f456-110">Defining the Wide View</span></span>

<span data-ttu-id="4f456-111">下面的 XML 演示的宽视图架构[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="4f456-112">以下 XML 元素用于定义较宽的视图：</span><span class="sxs-lookup"><span data-stu-id="4f456-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="4f456-113">[视图](./view-element-format.md)元素是宽视图的父元素。</span><span class="sxs-lookup"><span data-stu-id="4f456-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="4f456-114">（这是表、 列表和自定义控件视图的相同父元素）。</span><span class="sxs-lookup"><span data-stu-id="4f456-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="4f456-115">[名称](./name-element-for-view-format.md)元素指定的视图的名称。</span><span class="sxs-lookup"><span data-stu-id="4f456-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="4f456-116">此元素是必需的所有视图。</span><span class="sxs-lookup"><span data-stu-id="4f456-116">This element is required for all views.</span></span>

- <span data-ttu-id="4f456-117">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="4f456-118">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="4f456-118">This element is required.</span></span>

- <span data-ttu-id="4f456-119">[GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新组的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="4f456-120">特定属性或脚本的值发生更改时启动新的组。</span><span class="sxs-lookup"><span data-stu-id="4f456-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="4f456-121">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-121">This element is optional.</span></span>

- <span data-ttu-id="4f456-122">[控件](./controls-element-for-view-format.md)元素定义宽视图定义的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="4f456-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="4f456-123">控件提供了一种方法，以便进一步指定如何显示数据。</span><span class="sxs-lookup"><span data-stu-id="4f456-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="4f456-124">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-124">This element is optional.</span></span> <span data-ttu-id="4f456-125">视图可以定义自己的自定义控件或它可以使用可由任意视图中的格式设置文件的公共控件。</span><span class="sxs-lookup"><span data-stu-id="4f456-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="4f456-126">有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="4f456-127">[WideControl](./widecontrol-element-format.md)元素及其子元素定义的视图中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="4f456-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="4f456-128">在前面的示例中，视图设计用于显示[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性。</span><span class="sxs-lookup"><span data-stu-id="4f456-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="4f456-129">有关完整的格式设置文件，用于定义较宽的简单视图的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="4f456-130">提供宽视图的定义</span><span class="sxs-lookup"><span data-stu-id="4f456-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="4f456-131">宽视图可以通过使用的子元素提供一个或多个定义[WideControl](./widecontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="4f456-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="4f456-132">通常情况下，视图将具有只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="4f456-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="4f456-133">在以下示例中，此视图提供单个的定义显示的值[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性。</span><span class="sxs-lookup"><span data-stu-id="4f456-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="4f456-134">较宽的视图可以显示属性的值或脚本 （在示例中未显示） 的值。</span><span class="sxs-lookup"><span data-stu-id="4f456-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="4f456-135">以下 XML 元素可以用于提供较宽的视图的定义：</span><span class="sxs-lookup"><span data-stu-id="4f456-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="4f456-136">[WideControl](./widecontrol-element-format.md)元素及其子元素定义的视图中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="4f456-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="4f456-137">[AutoSize](./autosize-element-for-widecontrol-format.md)元素指定列的大小和列数会调整基于数据的大小。</span><span class="sxs-lookup"><span data-stu-id="4f456-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="4f456-138">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-138">This element is optional.</span></span>

- <span data-ttu-id="4f456-139">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素指定宽视图中显示的列数。</span><span class="sxs-lookup"><span data-stu-id="4f456-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="4f456-140">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-140">This element is optional.</span></span>

- <span data-ttu-id="4f456-141">[WideEntries](./wideentries-element-for-widecontrol-format.md)元素提供了该视图的定义。</span><span class="sxs-lookup"><span data-stu-id="4f456-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="4f456-142">在大多数情况下，将具有只有一个定义的视图。</span><span class="sxs-lookup"><span data-stu-id="4f456-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="4f456-143">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="4f456-143">This element is required.</span></span>

- <span data-ttu-id="4f456-144">[WideEntry](./wideentry-element-for-widecontrol-format.md)元素提供视图的定义。</span><span class="sxs-lookup"><span data-stu-id="4f456-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="4f456-145">至少一个[WideEntry](./wideentry-element-for-widecontrol-format.md)是必需的; 但是，没有任何可以添加的元素数目的最大限制。</span><span class="sxs-lookup"><span data-stu-id="4f456-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="4f456-146">在大多数情况下，将具有只有一个定义的视图。</span><span class="sxs-lookup"><span data-stu-id="4f456-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="4f456-147">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素指定所显示的特定定义的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="4f456-148">此元素是可选的仅当定义多个需要[WideEntry](./wideentry-element-for-widecontrol-format.md)元素，用于显示不同的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="4f456-149">[WideItem](./wideitem-element-for-widecontrol-format.md)元素指定由该视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4f456-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="4f456-150">相比其他类型的视图，宽控件可以显示只有一项。</span><span class="sxs-lookup"><span data-stu-id="4f456-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="4f456-151">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定由该视图显示其值的属性。</span><span class="sxs-lookup"><span data-stu-id="4f456-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="4f456-152">必须指定一个属性或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4f456-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="4f456-153">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素指定由该视图显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="4f456-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="4f456-154">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4f456-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="4f456-155">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)元素指定用于显示数据的模式。</span><span class="sxs-lookup"><span data-stu-id="4f456-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="4f456-156">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-156">This element is optional.</span></span>

<span data-ttu-id="4f456-157">有关完整的格式设置文件中定义的宽的视图定义示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="4f456-158">定义使用宽的视图的对象</span><span class="sxs-lookup"><span data-stu-id="4f456-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="4f456-159">有两种方法定义的.NET 对象使用宽的视图。</span><span class="sxs-lookup"><span data-stu-id="4f456-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="4f456-160">可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可显示的视图，或者您的所有定义的对象可以使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素来定义将显示哪些对象将视图的特定定义。</span><span class="sxs-lookup"><span data-stu-id="4f456-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="4f456-161">在大多数情况下，视图具有只有一个定义，因此对象通常由定义[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="4f456-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="4f456-162">下面的示例演示如何定义宽视图使用显示的对象[ViewSelectedBy](./viewselectedby-element-format.md)并[TypeName](./typename-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="4f456-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="4f456-163">数量没有限制[TypeName](./typename-element-for-viewselectedby-format.md)元素可以指定和其顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="4f456-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="4f456-164">以下 XML 元素可以用于指定由宽的视图的对象：</span><span class="sxs-lookup"><span data-stu-id="4f456-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="4f456-165">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="4f456-166">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的.NET。</span><span class="sxs-lookup"><span data-stu-id="4f456-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="4f456-167">完全限定的.NET 类型名称是必需的。</span><span class="sxs-lookup"><span data-stu-id="4f456-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="4f456-168">必须指定至少一个类型或所选内容设置对于视图，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="4f456-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="4f456-169">有关完整的格式设置文件的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="4f456-170">下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)并[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="4f456-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="4f456-171">使用的选项集，其中有一组相关的相同对象使用多个视图，例如何时定义较宽的视图和表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="4f456-172">有关如何创建选项集的详细信息，请参阅[定义的选项集，](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="4f456-173">以下 XML 元素可以用于指定由宽的视图的对象：</span><span class="sxs-lookup"><span data-stu-id="4f456-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="4f456-174">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="4f456-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定一组视图可以显示的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="4f456-176">必须指定至少一个选择集或类型视图，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="4f456-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="4f456-177">下面的示例演示如何定义宽视图使用的特定定义所显示的对象[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="4f456-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="4f456-178">使用此元素，可以指定将对象、 选择一组对象或选择条件，指定当使用定义的.NET 类型名称。</span><span class="sxs-lookup"><span data-stu-id="4f456-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="4f456-179">有关如何创建所选条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="4f456-180">以下 XML 元素可以用于指定使用特定的宽的视图定义的对象：</span><span class="sxs-lookup"><span data-stu-id="4f456-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="4f456-181">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素定义在定义将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="4f456-182">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定显示定义的.NET。</span><span class="sxs-lookup"><span data-stu-id="4f456-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="4f456-183">在使用此元素的完全限定的.NET 类型名称是必需。</span><span class="sxs-lookup"><span data-stu-id="4f456-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="4f456-184">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="4f456-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="4f456-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素 （未显示） 指定一组可显示的此定义的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="4f456-186">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="4f456-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="4f456-187">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素 （未显示） 指定要使用此定义中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="4f456-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="4f456-188">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="4f456-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="4f456-189">有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="4f456-190">在较宽的视图中显示的对象的组</span><span class="sxs-lookup"><span data-stu-id="4f456-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="4f456-191">可以分隔成组宽的视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="4f456-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="4f456-192">这并不意味着定义组，仅特定属性或脚本的值发生更改时，Windows PowerShell 启动新的组。</span><span class="sxs-lookup"><span data-stu-id="4f456-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="4f456-193">在以下示例中，启动新的组时的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性更改。</span><span class="sxs-lookup"><span data-stu-id="4f456-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="4f456-194">以下 XML 元素用于定义一组启动时：</span><span class="sxs-lookup"><span data-stu-id="4f456-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="4f456-195">[GroupBy](./groupby-element-for-view-format.md)元素定义的属性或启动新的组，并定义如何显示组的脚本。</span><span class="sxs-lookup"><span data-stu-id="4f456-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="4f456-196">[PropertyName](./propertyname-element-for-groupby-format.md)元素指定它的值发生更改时启动新的组的属性。</span><span class="sxs-lookup"><span data-stu-id="4f456-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="4f456-197">必须指定属性或脚本以启动组，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4f456-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="4f456-198">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素指定它的值发生更改时启动新的组的脚本。</span><span class="sxs-lookup"><span data-stu-id="4f456-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="4f456-199">必须指定脚本或属性来启动组，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4f456-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="4f456-200">[标签](./label-element-for-groupby-format.md)元素定义每个组的起始处显示标签。</span><span class="sxs-lookup"><span data-stu-id="4f456-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="4f456-201">除了指定此元素的文本，Windows PowerShell 显示触发的新组并添加一个空行之前和之后标签的值。</span><span class="sxs-lookup"><span data-stu-id="4f456-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="4f456-202">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-202">This element is optional.</span></span>

- <span data-ttu-id="4f456-203">[CustomControl](./customcontrol-element-for-groupby-format.md)元素定义用于显示数据的控件。</span><span class="sxs-lookup"><span data-stu-id="4f456-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="4f456-204">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-204">This element is optional.</span></span>

- <span data-ttu-id="4f456-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素指定一种常见或视图用于显示数据的控件。</span><span class="sxs-lookup"><span data-stu-id="4f456-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="4f456-206">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="4f456-206">This element is optional.</span></span>

<span data-ttu-id="4f456-207">有关定义组的完整格式设置文件的示例，请参阅[宽的视图 (GroupBy)](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="4f456-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="4f456-208">使用格式字符串</span><span class="sxs-lookup"><span data-stu-id="4f456-208">Using Format Strings</span></span>

<span data-ttu-id="4f456-209">格式设置字符串可以添加到较宽的视图来进一步定义数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="4f456-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="4f456-210">下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。</span><span class="sxs-lookup"><span data-stu-id="4f456-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="4f456-211">可以使用以下 XML 元素来指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="4f456-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="4f456-212">[WideItem](./wideitem-element-for-widecontrol-format.md)元素指定由该视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4f456-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="4f456-213">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定由该视图显示其值的属性。</span><span class="sxs-lookup"><span data-stu-id="4f456-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="4f456-214">必须指定一个属性或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4f456-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="4f456-215">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)元素指定的格式模式，它定义如何在视图中显示的属性或脚本的值</span><span class="sxs-lookup"><span data-stu-id="4f456-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="4f456-216">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。</span><span class="sxs-lookup"><span data-stu-id="4f456-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="4f456-217">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4f456-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="4f456-218">在以下示例中，`ToString`调用方法来设置脚本的值的格式。</span><span class="sxs-lookup"><span data-stu-id="4f456-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="4f456-219">脚本可以调用一个对象的任何方法。</span><span class="sxs-lookup"><span data-stu-id="4f456-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="4f456-220">因此，如果对象具有一种方法，如`ToString`，具有格式设置参数，该脚本可以调用该方法，以设置脚本的输出值的格式。</span><span class="sxs-lookup"><span data-stu-id="4f456-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="4f456-221">下面的 XML 元素可用于调用`ToString`方法：</span><span class="sxs-lookup"><span data-stu-id="4f456-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="4f456-222">[WideItem](./wideitem-element-for-widecontrol-format.md)元素指定由该视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="4f456-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="4f456-223">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。</span><span class="sxs-lookup"><span data-stu-id="4f456-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="4f456-224">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4f456-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f456-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f456-225">See Also</span></span>

[<span data-ttu-id="4f456-226">宽的视图 (Basic)</span><span class="sxs-lookup"><span data-stu-id="4f456-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="4f456-227">宽的视图 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="4f456-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="4f456-228">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="4f456-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

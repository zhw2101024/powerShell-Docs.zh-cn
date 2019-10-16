---
title: 创建宽视图 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368946"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="ec779-102">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="ec779-102">Creating a Wide View</span></span>

<span data-ttu-id="ec779-103">宽视图为显示的每个对象显示单个值。</span><span class="sxs-lookup"><span data-stu-id="ec779-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="ec779-104">显示的值可以是 .NET 对象属性的值或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="ec779-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="ec779-105">默认情况下，此视图没有标签或标题。</span><span class="sxs-lookup"><span data-stu-id="ec779-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="ec779-106">宽视图显示</span><span class="sxs-lookup"><span data-stu-id="ec779-106">A Wide View Display</span></span>

<span data-ttu-id="ec779-107">下面的示例演示了 Windows PowerShell 如何显示在将其输出传送到[格式范围](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide)cmdlet 时由[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 返回的[system.object](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="ec779-108">（默认情况下，[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 返回表视图。）在此示例中，两个列用于显示每个返回对象的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="ec779-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="ec779-109">不显示对象属性的名称，只显示属性的值。</span><span class="sxs-lookup"><span data-stu-id="ec779-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="ec779-110">定义宽视图</span><span class="sxs-lookup"><span data-stu-id="ec779-110">Defining the Wide View</span></span>

<span data-ttu-id="ec779-111">下面的 XML 显示了[system.object](/dotnet/api/System.Diagnostics.Process)对象的宽视图架构。</span><span class="sxs-lookup"><span data-stu-id="ec779-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="ec779-112">以下 XML 元素用于定义宽视图：</span><span class="sxs-lookup"><span data-stu-id="ec779-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="ec779-113">[View](./view-element-format.md)元素是宽视图的父元素。</span><span class="sxs-lookup"><span data-stu-id="ec779-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="ec779-114">（这是表、列表和自定义控件视图的相同父元素。）</span><span class="sxs-lookup"><span data-stu-id="ec779-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="ec779-115">[Name](./name-element-for-view-format.md)元素指定视图的名称。</span><span class="sxs-lookup"><span data-stu-id="ec779-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="ec779-116">此元素对于所有视图都是必需的。</span><span class="sxs-lookup"><span data-stu-id="ec779-116">This element is required for all views.</span></span>

- <span data-ttu-id="ec779-117">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="ec779-118">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="ec779-118">This element is required.</span></span>

- <span data-ttu-id="ec779-119">[GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新的对象组。</span><span class="sxs-lookup"><span data-stu-id="ec779-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="ec779-120">每当特定属性或脚本的值发生更改时，就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="ec779-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ec779-121">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-121">This element is optional.</span></span>

- <span data-ttu-id="ec779-122">[Controls](./controls-element-for-view-format.md)元素定义由宽视图定义的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="ec779-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="ec779-123">控件使您可以进一步指定数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="ec779-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="ec779-124">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-124">This element is optional.</span></span> <span data-ttu-id="ec779-125">视图可以定义自己的自定义控件，也可以使用可由格式设置文件中的任何视图使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="ec779-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="ec779-126">有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="ec779-127">[WideControl](./widecontrol-element-format.md)元素及其子元素定义视图中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="ec779-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="ec779-128">在前面的示例中，视图设计为显示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性。</span><span class="sxs-lookup"><span data-stu-id="ec779-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="ec779-129">有关定义简单宽视图的完整格式化文件的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="ec779-130">为宽视图提供定义</span><span class="sxs-lookup"><span data-stu-id="ec779-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="ec779-131">宽视图可以通过使用[WideControl](./widecontrol-element-format.md)元素的子元素来提供一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="ec779-132">通常，视图将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="ec779-133">在下面的示例中，视图提供了一个显示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性值的定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="ec779-134">宽视图可以显示属性的值或脚本的值（示例中未显示）。</span><span class="sxs-lookup"><span data-stu-id="ec779-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="ec779-135">以下 XML 元素可用于为宽视图提供定义：</span><span class="sxs-lookup"><span data-stu-id="ec779-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="ec779-136">[WideControl](./widecontrol-element-format.md)元素及其子元素定义视图中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="ec779-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="ec779-137">[AutoSize](./autosize-element-for-widecontrol-format.md)元素指定是否根据数据大小调整列大小和列数。</span><span class="sxs-lookup"><span data-stu-id="ec779-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="ec779-138">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-138">This element is optional.</span></span>

- <span data-ttu-id="ec779-139">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素指定在宽视图中显示的列数。</span><span class="sxs-lookup"><span data-stu-id="ec779-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="ec779-140">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-140">This element is optional.</span></span>

- <span data-ttu-id="ec779-141">[WideEntries](./wideentries-element-for-widecontrol-format.md)元素提供视图的定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="ec779-142">在大多数情况下，视图将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="ec779-143">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="ec779-143">This element is required.</span></span>

- <span data-ttu-id="ec779-144">[WideEntry](./wideentry-element-for-widecontrol-format.md)元素提供视图的定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="ec779-145">至少需要一个[WideEntry](./wideentry-element-for-widecontrol-format.md) ;但是，可以添加的元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="ec779-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="ec779-146">在大多数情况下，视图将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="ec779-147">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素指定由特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="ec779-148">此元素是可选的，仅当定义显示不同对象的多个[WideEntry](./wideentry-element-for-widecontrol-format.md)元素时才需要此元素。</span><span class="sxs-lookup"><span data-stu-id="ec779-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="ec779-149">[WideItem](./wideitem-element-for-widecontrol-format.md)元素指定视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ec779-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="ec779-150">与其他类型的视图不同，范围广泛的控件只能显示一项。</span><span class="sxs-lookup"><span data-stu-id="ec779-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="ec779-151">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定其值由视图显示的属性。</span><span class="sxs-lookup"><span data-stu-id="ec779-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="ec779-152">您必须指定属性或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ec779-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ec779-153">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素指定其值由视图显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="ec779-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ec779-154">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ec779-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="ec779-155">"[格式字符串](./formatstring-element-for-wideitem-for-widecontrol-format.md)" 元素指定用于显示数据的模式。</span><span class="sxs-lookup"><span data-stu-id="ec779-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="ec779-156">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-156">This element is optional.</span></span>

<span data-ttu-id="ec779-157">有关定义宽视图定义的完整格式化文件的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="ec779-158">定义使用大视图的对象</span><span class="sxs-lookup"><span data-stu-id="ec779-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="ec779-159">可以通过两种方法来定义哪些 .NET 对象使用宽视图。</span><span class="sxs-lookup"><span data-stu-id="ec779-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="ec779-160">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可由视图的所有定义显示的对象，也可以使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素来定义由视图的特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="ec779-161">在大多数情况下，视图只有一个定义，因此对象通常由[ViewSelectedBy](./viewselectedby-element-format.md)元素定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="ec779-162">下面的示例演示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定义宽视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ec779-163">对于您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素的数量没有限制，它们的顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="ec779-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="ec779-164">以下 XML 元素可用于指定宽视图使用的对象：</span><span class="sxs-lookup"><span data-stu-id="ec779-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="ec779-165">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="ec779-166">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的 .net。</span><span class="sxs-lookup"><span data-stu-id="ec779-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="ec779-167">完全限定的 .NET 类型名称是必需的。</span><span class="sxs-lookup"><span data-stu-id="ec779-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="ec779-168">您必须为视图指定至少一个类型或选择集，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="ec779-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ec779-169">有关完整格式化文件的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="ec779-170">下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ec779-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ec779-171">使用选择集，其中有一组使用多个视图显示的相关对象，例如为同一对象定义宽视图和表视图。</span><span class="sxs-lookup"><span data-stu-id="ec779-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="ec779-172">有关如何创建选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="ec779-173">以下 XML 元素可用于指定宽视图使用的对象：</span><span class="sxs-lookup"><span data-stu-id="ec779-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="ec779-174">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="ec779-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定可由视图显示的一组对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="ec779-176">您必须为视图指定至少一个选择集或类型，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="ec779-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ec779-177">下面的示例演示如何使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素定义由宽视图的特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="ec779-178">使用此元素，可以指定对象的 .NET 类型名称、对象的选择集或指定何时使用定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="ec779-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="ec779-179">有关如何创建选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="ec779-180">以下 XML 元素可用于指定由大视图的特定定义使用的对象：</span><span class="sxs-lookup"><span data-stu-id="ec779-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="ec779-181">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素定义由定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="ec779-182">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定由定义显示的 .net。</span><span class="sxs-lookup"><span data-stu-id="ec779-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="ec779-183">使用此元素时，需要完全限定的 .NET 类型名称。</span><span class="sxs-lookup"><span data-stu-id="ec779-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="ec779-184">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="ec779-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ec779-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素（未显示）指定可由此定义显示的一组对象。</span><span class="sxs-lookup"><span data-stu-id="ec779-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="ec779-186">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="ec779-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ec779-187">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素（未显示）指定必须存在的条件才能使用此定义。</span><span class="sxs-lookup"><span data-stu-id="ec779-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ec779-188">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="ec779-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="ec779-189">有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="ec779-190">以宽视图显示对象组</span><span class="sxs-lookup"><span data-stu-id="ec779-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="ec779-191">您可以将由宽视图显示的对象划分为多个组。</span><span class="sxs-lookup"><span data-stu-id="ec779-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="ec779-192">这并不意味着你要定义一个组，只要特定属性或脚本的值发生变化，Windows PowerShell 就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="ec779-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ec779-193">在下面的示例中，只要[system.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性的值发生更改，就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="ec779-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="ec779-194">以下 XML 元素用于定义组的启动时间：</span><span class="sxs-lookup"><span data-stu-id="ec779-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="ec779-195">[GroupBy](./groupby-element-for-view-format.md)元素定义用于启动新组和定义组显示方式的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="ec779-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="ec779-196">[PropertyName](./propertyname-element-for-groupby-format.md)元素指定在其值更改时启动新组的属性。</span><span class="sxs-lookup"><span data-stu-id="ec779-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="ec779-197">您必须指定一个属性或脚本来启动组，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ec779-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="ec779-198">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素指定在其值更改时启动新组的脚本。</span><span class="sxs-lookup"><span data-stu-id="ec779-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="ec779-199">您必须指定脚本或属性以启动组，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ec779-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="ec779-200">[标签](./label-element-for-groupby-format.md)元素定义在每个组的开头显示的标签。</span><span class="sxs-lookup"><span data-stu-id="ec779-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="ec779-201">除了此元素指定的文本，Windows PowerShell 还显示触发新组的值，并在标签之前和之后添加一个空白行。</span><span class="sxs-lookup"><span data-stu-id="ec779-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="ec779-202">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-202">This element is optional.</span></span>

- <span data-ttu-id="ec779-203">[CustomControl](./customcontrol-element-for-groupby-format.md)元素定义用于显示数据的控件。</span><span class="sxs-lookup"><span data-stu-id="ec779-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="ec779-204">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-204">This element is optional.</span></span>

- <span data-ttu-id="ec779-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素指定用于显示数据的通用控件或视图控件。</span><span class="sxs-lookup"><span data-stu-id="ec779-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="ec779-206">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ec779-206">This element is optional.</span></span>

<span data-ttu-id="ec779-207">有关定义组的完整格式化文件的示例，请参阅[宽视图（GroupBy）](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="ec779-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="ec779-208">使用格式字符串</span><span class="sxs-lookup"><span data-stu-id="ec779-208">Using Format Strings</span></span>

<span data-ttu-id="ec779-209">可以将字符串的格式添加到宽视图，进一步定义数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="ec779-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="ec779-210">下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。</span><span class="sxs-lookup"><span data-stu-id="ec779-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="ec779-211">以下 XML 元素可用于指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="ec779-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="ec779-212">[WideItem](./wideitem-element-for-widecontrol-format.md)元素指定视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ec779-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="ec779-213">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定其值由视图显示的属性。</span><span class="sxs-lookup"><span data-stu-id="ec779-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="ec779-214">您必须指定属性或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ec779-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ec779-215">"格式[字符串](./formatstring-element-for-wideitem-for-widecontrol-format.md)" 元素指定定义属性或脚本值在视图中显示方式的格式模式</span><span class="sxs-lookup"><span data-stu-id="ec779-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="ec779-216">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素（未显示）指定其值由视图显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="ec779-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ec779-217">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ec779-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="ec779-218">在下面的示例中，调用 `ToString` 方法来设置脚本的值的格式。</span><span class="sxs-lookup"><span data-stu-id="ec779-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="ec779-219">脚本可以调用对象的任何方法。</span><span class="sxs-lookup"><span data-stu-id="ec779-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="ec779-220">因此，如果对象有一个具有格式参数的方法（如 `ToString`），则脚本可以调用该方法来设置脚本的输出值的格式。</span><span class="sxs-lookup"><span data-stu-id="ec779-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="ec779-221">以下 XML 元素可用于调用 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="ec779-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="ec779-222">[WideItem](./wideitem-element-for-widecontrol-format.md)元素指定视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ec779-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="ec779-223">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素（未显示）指定其值由视图显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="ec779-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="ec779-224">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="ec779-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec779-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec779-225">See Also</span></span>

[<span data-ttu-id="ec779-226">宽视图（基本）</span><span class="sxs-lookup"><span data-stu-id="ec779-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="ec779-227">宽视图（GroupBy）</span><span class="sxs-lookup"><span data-stu-id="ec779-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="ec779-228">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="ec779-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

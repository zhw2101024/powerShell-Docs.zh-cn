---
title: 创建列表视图 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861573"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="5f967-102">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="5f967-102">Creating a List View</span></span>

<span data-ttu-id="5f967-103">列表视图 （按先后顺序） 的单个列中显示数据。</span><span class="sxs-lookup"><span data-stu-id="5f967-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="5f967-104">在列表中显示的数据可以是.NET 属性的值或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="5f967-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="5f967-105">列表视图显示</span><span class="sxs-lookup"><span data-stu-id="5f967-105">A List View Display</span></span>

<span data-ttu-id="5f967-106">以下输出显示了 Windows PowerShell 如何显示的属性[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f967-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="5f967-107">在此示例中，返回了三个对象，其中从上述对象由一个空行分隔每个对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="5f967-108">定义列表视图</span><span class="sxs-lookup"><span data-stu-id="5f967-108">Defining the List View</span></span>

<span data-ttu-id="5f967-109">下面的 XML 演示用于显示的多个属性的列表视图架构[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="5f967-110">必须指定想要在列表视图中显示每个属性。</span><span class="sxs-lookup"><span data-stu-id="5f967-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="5f967-111">以下 XML 元素用于定义列表视图：</span><span class="sxs-lookup"><span data-stu-id="5f967-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="5f967-112">[视图](./view-element-format.md)元素是列表视图的父元素。</span><span class="sxs-lookup"><span data-stu-id="5f967-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="5f967-113">（这是对于表，，和自定义控件的视图相同的父元素）。</span><span class="sxs-lookup"><span data-stu-id="5f967-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="5f967-114">[名称](./name-element-for-view-format.md)元素指定的视图的名称。</span><span class="sxs-lookup"><span data-stu-id="5f967-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="5f967-115">此元素是必需的所有视图。</span><span class="sxs-lookup"><span data-stu-id="5f967-115">This element is required for all views.</span></span>

- <span data-ttu-id="5f967-116">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="5f967-117">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="5f967-117">This element is required.</span></span>

- <span data-ttu-id="5f967-118">[GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新组的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="5f967-119">特定属性或脚本的值发生更改时启动新的组。</span><span class="sxs-lookup"><span data-stu-id="5f967-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="5f967-120">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-120">This element is optional.</span></span>

- <span data-ttu-id="5f967-121">[控件](./controls-element-for-view-format.md)元素定义由列表视图中定义的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="5f967-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="5f967-122">控件提供了一种方法，以便进一步指定如何显示数据。</span><span class="sxs-lookup"><span data-stu-id="5f967-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="5f967-123">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-123">This element is optional.</span></span> <span data-ttu-id="5f967-124">视图可以定义自己的自定义控件或它可以使用可由任意视图中的格式设置文件的公共控件。</span><span class="sxs-lookup"><span data-stu-id="5f967-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="5f967-125">有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="5f967-126">[ListControl](./listcontrol-element-format.md)元素定义的视图中显示的内容和它的格式。</span><span class="sxs-lookup"><span data-stu-id="5f967-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="5f967-127">与所有其他视图类似，列表视图可以显示对象属性的值或值生成的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="5f967-128">有关定义简单列表视图的完整格式设置文件的示例，请参阅[列表视图 （基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="5f967-129">提供在列表视图的定义</span><span class="sxs-lookup"><span data-stu-id="5f967-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="5f967-130">列表视图可以通过使用的子元素提供一个或多个定义[ListControl](./listcontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5f967-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="5f967-131">通常情况下，视图将具有只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="5f967-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="5f967-132">在以下示例中，视图提供了显示的多个属性的单个定义[System.Diagnostics.Process？Displayproperty =](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="5f967-133">列表视图可以显示属性的值或脚本 （在示例中未显示） 的值。</span><span class="sxs-lookup"><span data-stu-id="5f967-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="5f967-134">以下 XML 元素可以用于提供列表视图的定义：</span><span class="sxs-lookup"><span data-stu-id="5f967-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="5f967-135">[ListControl](./listcontrol-element-format.md)元素及其子元素定义的视图中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="5f967-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="5f967-136">[ListEntries](./listentries-element-for-listcontrol-format.md)元素提供了该视图的定义。</span><span class="sxs-lookup"><span data-stu-id="5f967-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="5f967-137">在大多数情况下，将具有只有一个定义的视图。</span><span class="sxs-lookup"><span data-stu-id="5f967-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="5f967-138">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="5f967-138">This element is required.</span></span>

- <span data-ttu-id="5f967-139">[ListEntry](./listentry-element-for-listcontrol-format.md)元素提供视图的定义。</span><span class="sxs-lookup"><span data-stu-id="5f967-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="5f967-140">至少一个[ListEntry](./listentry-element-for-listcontrol-format.md)是必需的; 但是，没有任何可以添加的元素数目的最大限制。</span><span class="sxs-lookup"><span data-stu-id="5f967-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="5f967-141">在大多数情况下，将具有只有一个定义的视图。</span><span class="sxs-lookup"><span data-stu-id="5f967-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="5f967-142">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素指定所显示的特定定义的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="5f967-143">此元素是可选的仅当定义多个需要[ListEntry](./listentry-element-for-listcontrol-format.md)元素，用于显示不同的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="5f967-144">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)元素指定的属性和其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="5f967-145">[ListItem](./listitems-element-for-listentry-for-listcontrol-format.md)元素指定的属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="5f967-146">列表视图必须指定至少一个属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="5f967-147">可以指定的行数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="5f967-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="5f967-148">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定的行中显示其值的属性。</span><span class="sxs-lookup"><span data-stu-id="5f967-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="5f967-149">必须指定一个属性或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="5f967-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="5f967-150">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素指定其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="5f967-151">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="5f967-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="5f967-152">[标签](./label-element-for-listitem-for-listcontrol-format.md)元素指定的行中的属性或脚本的值的左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="5f967-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="5f967-153">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-153">This element is optional.</span></span> <span data-ttu-id="5f967-154">如果未指定一个标签，显示属性或脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="5f967-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="5f967-155">有关完整示例，请参阅[列表视图 （标签）](./list-view-labels.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="5f967-156">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)元素指定要显示的行中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5f967-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="5f967-157">有关将条件添加到列表视图的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="5f967-158">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-158">This element is optional.</span></span>

- <span data-ttu-id="5f967-159">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)元素指定用于显示属性或脚本的值的模式。</span><span class="sxs-lookup"><span data-stu-id="5f967-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="5f967-160">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-160">This element is optional.</span></span>

<span data-ttu-id="5f967-161">有关定义简单列表视图的完整格式设置文件的示例，请参阅[列表视图 （基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="5f967-162">定义使用列表视图的对象</span><span class="sxs-lookup"><span data-stu-id="5f967-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="5f967-163">有两种方法定义的.NET 对象使用列表视图。</span><span class="sxs-lookup"><span data-stu-id="5f967-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="5f967-164">可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可显示的视图，或者您的所有定义的对象可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义将显示哪些对象将视图的特定定义。</span><span class="sxs-lookup"><span data-stu-id="5f967-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="5f967-165">在大多数情况下，视图具有只有一个定义，因此对象通常由定义[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5f967-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="5f967-166">下面的示例演示如何定义显示列表视图使用的对象[ViewSelectedBy](./viewselectedby-element-format.md)并[TypeName](./typename-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5f967-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="5f967-167">数量没有限制[TypeName](./typename-element-for-viewselectedby-format.md)元素可以指定和其顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="5f967-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="5f967-168">以下 XML 元素可以用于指定使用列表视图的对象：</span><span class="sxs-lookup"><span data-stu-id="5f967-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="5f967-169">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="5f967-170">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定.NET 对象，该视图显示对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="5f967-171">完全限定的.NET 类型名称是必需的。</span><span class="sxs-lookup"><span data-stu-id="5f967-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="5f967-172">必须指定至少一个类型或所选内容设置对于视图，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="5f967-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="5f967-173">有关完整的格式设置文件的示例，请参阅[列表视图 （基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="5f967-174">下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)并[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5f967-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="5f967-175">使用的选项集，其中有一组相关的相同对象使用多个视图，例如何时定义列表视图和表视图，显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="5f967-176">有关如何创建选项集的详细信息，请参阅[定义的选项集，](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="5f967-177">以下 XML 元素可以用于指定使用列表视图的对象：</span><span class="sxs-lookup"><span data-stu-id="5f967-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="5f967-178">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="5f967-179">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定一组视图可以显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="5f967-180">必须指定至少一个选择集或类型视图，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="5f967-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="5f967-181">下面的示例演示如何定义使用列表视图的特定定义所显示的对象[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5f967-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="5f967-182">使用此元素，可以指定将对象、 选择一组对象或选择条件，指定当使用定义的.NET 类型名称。</span><span class="sxs-lookup"><span data-stu-id="5f967-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="5f967-183">有关如何创建所选条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="5f967-184">以下 XML 元素可以用于指定使用特定的列表视图中定义的对象：</span><span class="sxs-lookup"><span data-stu-id="5f967-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="5f967-185">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素定义在定义将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="5f967-186">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定显示定义的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="5f967-187">使用此元素，完全限定的.NET 类型名称时，所需。</span><span class="sxs-lookup"><span data-stu-id="5f967-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="5f967-188">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="5f967-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="5f967-189">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定一组可显示的此定义的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="5f967-190">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="5f967-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="5f967-191">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定要使用此定义中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5f967-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="5f967-192">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="5f967-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="5f967-193">有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="5f967-194">在列表视图中显示的对象的组</span><span class="sxs-lookup"><span data-stu-id="5f967-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="5f967-195">可以分隔成组的列表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5f967-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="5f967-196">这并不意味着定义组，仅特定属性或脚本的值发生更改时，Windows PowerShell 启动新的组。</span><span class="sxs-lookup"><span data-stu-id="5f967-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="5f967-197">在以下示例中，启动新的组时的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性更改。</span><span class="sxs-lookup"><span data-stu-id="5f967-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="5f967-198">以下 XML 元素用于定义一组启动时：</span><span class="sxs-lookup"><span data-stu-id="5f967-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="5f967-199">[GroupBy](./groupby-element-for-view-format.md)元素定义的属性或启动新的组，并定义如何显示组的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="5f967-200">[PropertyName](./propertyname-element-for-groupby-format.md)元素指定它的值发生更改时启动新的组的属性。</span><span class="sxs-lookup"><span data-stu-id="5f967-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="5f967-201">必须指定属性或脚本以启动组，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="5f967-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="5f967-202">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素指定它的值发生更改时启动新的组的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="5f967-203">必须指定脚本或属性来启动组，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="5f967-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="5f967-204">[标签](./label-element-for-groupby-format.md)元素定义每个组的起始处显示标签。</span><span class="sxs-lookup"><span data-stu-id="5f967-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="5f967-205">除了指定此元素的文本，Windows PowerShell 显示触发的新组并添加一个空行之前和之后标签的值。</span><span class="sxs-lookup"><span data-stu-id="5f967-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="5f967-206">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-206">This element is optional.</span></span>

- <span data-ttu-id="5f967-207">[CustomControl](./customcontrol-element-for-groupby-format.md)元素定义用于显示数据的控件。</span><span class="sxs-lookup"><span data-stu-id="5f967-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="5f967-208">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-208">This element is optional.</span></span>

- <span data-ttu-id="5f967-209">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素指定一种常见或视图用于显示数据的控件。</span><span class="sxs-lookup"><span data-stu-id="5f967-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="5f967-210">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f967-210">This element is optional.</span></span>

<span data-ttu-id="5f967-211">有关定义组的完整格式设置文件的示例，请参阅[列表视图 (GroupBy)](./list-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="5f967-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="5f967-212">使用格式字符串</span><span class="sxs-lookup"><span data-stu-id="5f967-212">Using Format Strings</span></span>

<span data-ttu-id="5f967-213">可以为视图，以进一步定义数据的显示方式添加格式设置字符串。</span><span class="sxs-lookup"><span data-stu-id="5f967-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="5f967-214">下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。</span><span class="sxs-lookup"><span data-stu-id="5f967-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="5f967-215">可以使用以下 XML 元素来指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="5f967-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="5f967-216">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素指定由该视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="5f967-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="5f967-217">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定由该视图显示其值的属性。</span><span class="sxs-lookup"><span data-stu-id="5f967-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="5f967-218">必须指定一个属性或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="5f967-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="5f967-219">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)元素指定的格式模式，它定义如何在视图中显示的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="5f967-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="5f967-220">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="5f967-221">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="5f967-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="5f967-222">在以下示例中，`ToString`调用方法来设置脚本的值的格式。</span><span class="sxs-lookup"><span data-stu-id="5f967-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="5f967-223">脚本可以调用一个对象的任何方法。</span><span class="sxs-lookup"><span data-stu-id="5f967-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="5f967-224">因此，如果对象具有一种方法，如`ToString`，具有格式设置参数，该脚本可以调用该方法，以设置脚本的输出值的格式。</span><span class="sxs-lookup"><span data-stu-id="5f967-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="5f967-225">下面的 XML 元素可用于调用`ToString`方法：</span><span class="sxs-lookup"><span data-stu-id="5f967-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="5f967-226">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素指定由该视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="5f967-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="5f967-227">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。</span><span class="sxs-lookup"><span data-stu-id="5f967-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="5f967-228">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="5f967-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f967-229">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f967-229">See Also</span></span>

[<span data-ttu-id="5f967-230">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f967-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)

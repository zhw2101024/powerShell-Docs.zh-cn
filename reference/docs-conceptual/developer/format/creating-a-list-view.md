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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368976"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="5b98f-102">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="5b98f-102">Creating a List View</span></span>

<span data-ttu-id="5b98f-103">列表视图以单个列的顺序（按顺序）显示数据。</span><span class="sxs-lookup"><span data-stu-id="5b98f-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="5b98f-104">列表中显示的数据可以是 .NET 属性的值或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="5b98f-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="5b98f-105">列表视图显示</span><span class="sxs-lookup"><span data-stu-id="5b98f-105">A List View Display</span></span>

<span data-ttu-id="5b98f-106">以下输出显示了 Windows PowerShell 如何显示[system.serviceprocess. Servicecontroller 的属性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[get-help](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 返回的 Fullname 对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="5b98f-107">在此示例中，返回了三个对象，每个对象都由一个空行与前面的对象隔开。</span><span class="sxs-lookup"><span data-stu-id="5b98f-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="5b98f-108">定义列表视图</span><span class="sxs-lookup"><span data-stu-id="5b98f-108">Defining the List View</span></span>

<span data-ttu-id="5b98f-109">下面的 XML 演示了用于显示[system.serviceprocess. Servicecontroller 的多个属性的列表视图架构。Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="5b98f-110">您必须指定要在列表视图中显示的每个属性。</span><span class="sxs-lookup"><span data-stu-id="5b98f-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="5b98f-111">以下 XML 元素用于定义列表视图：</span><span class="sxs-lookup"><span data-stu-id="5b98f-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="5b98f-112">[View](./view-element-format.md)元素是列表视图的父元素。</span><span class="sxs-lookup"><span data-stu-id="5b98f-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="5b98f-113">（这是表、宽和自定义控件视图的相同父元素。）</span><span class="sxs-lookup"><span data-stu-id="5b98f-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="5b98f-114">[Name](./name-element-for-view-format.md)元素指定视图的名称。</span><span class="sxs-lookup"><span data-stu-id="5b98f-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="5b98f-115">此元素对于所有视图都是必需的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-115">This element is required for all views.</span></span>

- <span data-ttu-id="5b98f-116">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="5b98f-117">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-117">This element is required.</span></span>

- <span data-ttu-id="5b98f-118">[GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新的对象组。</span><span class="sxs-lookup"><span data-stu-id="5b98f-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="5b98f-119">每当特定属性或脚本的值发生更改时，就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="5b98f-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="5b98f-120">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-120">This element is optional.</span></span>

- <span data-ttu-id="5b98f-121">[Controls](./controls-element-for-view-format.md)元素定义由列表视图定义的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="5b98f-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="5b98f-122">控件使您可以进一步指定数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="5b98f-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="5b98f-123">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-123">This element is optional.</span></span> <span data-ttu-id="5b98f-124">视图可以定义自己的自定义控件，也可以使用可由格式设置文件中的任何视图使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="5b98f-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="5b98f-125">有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="5b98f-126">[ListControl](./listcontrol-element-format.md)元素定义视图中显示的内容以及如何设置它的格式。</span><span class="sxs-lookup"><span data-stu-id="5b98f-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="5b98f-127">与所有其他视图类似，列表视图可以显示对象属性的值或脚本生成的值。</span><span class="sxs-lookup"><span data-stu-id="5b98f-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="5b98f-128">有关定义简单列表视图的完整格式化文件的示例，请参阅[列表视图（基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="5b98f-129">为列表视图提供定义</span><span class="sxs-lookup"><span data-stu-id="5b98f-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="5b98f-130">列表视图可以通过使用[ListControl](./listcontrol-element-format.md)元素的子元素来提供一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="5b98f-131">通常，视图将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="5b98f-132">在下面的示例中，视图提供了一个定义，用于显示系统的多个属性[。Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="5b98f-133">列表视图可以显示属性的值或脚本的值（在此示例中未显示）。</span><span class="sxs-lookup"><span data-stu-id="5b98f-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="5b98f-134">以下 XML 元素可用于为列表视图提供定义：</span><span class="sxs-lookup"><span data-stu-id="5b98f-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="5b98f-135">[ListControl](./listcontrol-element-format.md)元素及其子元素定义视图中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="5b98f-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="5b98f-136">[ListEntries](./listentries-element-for-listcontrol-format.md)元素提供视图的定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="5b98f-137">在大多数情况下，视图将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="5b98f-138">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-138">This element is required.</span></span>

- <span data-ttu-id="5b98f-139">[ListEntry](./listentry-element-for-listcontrol-format.md)元素提供视图的定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="5b98f-140">至少需要一个[ListEntry](./listentry-element-for-listcontrol-format.md) ;但是，可以添加的元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="5b98f-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="5b98f-141">在大多数情况下，视图将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="5b98f-142">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素指定由特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="5b98f-143">此元素是可选的，仅当定义显示不同对象的多个[ListEntry](./listentry-element-for-listcontrol-format.md)元素时才需要此元素。</span><span class="sxs-lookup"><span data-stu-id="5b98f-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="5b98f-144">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)元素指定其值显示在列表视图的行中的属性和脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="5b98f-145">"[列表](./listitems-element-for-listentry-for-listcontrol-format.md)元素" 指定其值显示在列表视图的行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="5b98f-146">列表视图必须至少指定一个属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="5b98f-147">对于可以指定的行数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="5b98f-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="5b98f-148">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定其值显示在行中的属性。</span><span class="sxs-lookup"><span data-stu-id="5b98f-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="5b98f-149">您必须指定属性或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5b98f-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="5b98f-150">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素指定其值在行中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="5b98f-151">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5b98f-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="5b98f-152">[Label](./label-element-for-listitem-for-listcontrol-format.md)元素指定在行中的属性或脚本值左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="5b98f-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="5b98f-153">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-153">This element is optional.</span></span> <span data-ttu-id="5b98f-154">如果未指定标签，则显示属性或脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="5b98f-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="5b98f-155">有关完整示例，请参阅[列表视图（标签）](./list-view-labels.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="5b98f-156">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)元素指定要显示的行必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5b98f-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="5b98f-157">有关向列表视图添加条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="5b98f-158">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-158">This element is optional.</span></span>

- <span data-ttu-id="5b98f-159">[格式字符串](./formatstring-element-for-listitem-for-listcontrol-format.md)元素指定用于显示属性或脚本的值的模式。</span><span class="sxs-lookup"><span data-stu-id="5b98f-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="5b98f-160">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-160">This element is optional.</span></span>

<span data-ttu-id="5b98f-161">有关定义简单列表视图的完整格式化文件的示例，请参阅[列表视图（基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="5b98f-162">定义使用列表视图的对象</span><span class="sxs-lookup"><span data-stu-id="5b98f-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="5b98f-163">可以通过两种方法来定义哪些 .NET 对象使用列表视图。</span><span class="sxs-lookup"><span data-stu-id="5b98f-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="5b98f-164">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可由视图的所有定义显示的对象，也可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义由视图的特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="5b98f-165">在大多数情况下，视图只有一个定义，因此对象通常由[ViewSelectedBy](./viewselectedby-element-format.md)元素定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="5b98f-166">下面的示例演示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定义列表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="5b98f-167">对于您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素的数量没有限制，它们的顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="5b98f-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="5b98f-168">以下 XML 元素可用于指定列表视图所使用的对象：</span><span class="sxs-lookup"><span data-stu-id="5b98f-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="5b98f-169">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="5b98f-170">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的 .net 对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="5b98f-171">完全限定的 .NET 类型名称是必需的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="5b98f-172">您必须为视图指定至少一个类型或选择集，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="5b98f-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="5b98f-173">有关完整格式化文件的示例，请参阅[列表视图（基本）](./list-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="5b98f-174">下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5b98f-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="5b98f-175">使用选择集，其中有一组使用多个视图显示的相关对象，例如为同一对象定义列表视图和表视图。</span><span class="sxs-lookup"><span data-stu-id="5b98f-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="5b98f-176">有关如何创建选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="5b98f-177">以下 XML 元素可用于指定列表视图所使用的对象：</span><span class="sxs-lookup"><span data-stu-id="5b98f-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="5b98f-178">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="5b98f-179">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定可由视图显示的一组对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="5b98f-180">您必须为视图指定至少一个选择集或类型，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="5b98f-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="5b98f-181">下面的示例演示如何使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素定义由列表视图的特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="5b98f-182">使用此元素，可以指定对象的 .NET 类型名称、对象的选择集或指定何时使用定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="5b98f-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="5b98f-183">有关如何创建选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="5b98f-184">以下 XML 元素可用于指定列表视图的特定定义所使用的对象：</span><span class="sxs-lookup"><span data-stu-id="5b98f-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="5b98f-185">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素定义由定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="5b98f-186">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定由定义显示的 .net 对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="5b98f-187">使用此元素时，必须提供完全限定的 .NET 类型名称。</span><span class="sxs-lookup"><span data-stu-id="5b98f-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="5b98f-188">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="5b98f-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="5b98f-189">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定可由此定义显示的一组对象。</span><span class="sxs-lookup"><span data-stu-id="5b98f-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="5b98f-190">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="5b98f-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="5b98f-191">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定必须存在的条件才能使用此定义。</span><span class="sxs-lookup"><span data-stu-id="5b98f-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="5b98f-192">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="5b98f-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="5b98f-193">有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="5b98f-194">在列表视图中显示对象组</span><span class="sxs-lookup"><span data-stu-id="5b98f-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="5b98f-195">可以将列表视图显示的对象划分为多个组。</span><span class="sxs-lookup"><span data-stu-id="5b98f-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="5b98f-196">这并不意味着你要定义一个组，只要特定属性或脚本的值发生变化，Windows PowerShell 就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="5b98f-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="5b98f-197">在下面的示例中，只要[system.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性的值发生更改，就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="5b98f-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="5b98f-198">以下 XML 元素用于定义组的启动时间：</span><span class="sxs-lookup"><span data-stu-id="5b98f-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="5b98f-199">[GroupBy](./groupby-element-for-view-format.md)元素定义用于启动新组和定义组显示方式的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="5b98f-200">[PropertyName](./propertyname-element-for-groupby-format.md)元素指定在其值更改时启动新组的属性。</span><span class="sxs-lookup"><span data-stu-id="5b98f-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="5b98f-201">您必须指定一个属性或脚本来启动组，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5b98f-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="5b98f-202">[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素指定在其值更改时启动新组的脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="5b98f-203">您必须指定脚本或属性以启动组，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5b98f-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="5b98f-204">[标签](./label-element-for-groupby-format.md)元素定义在每个组的开头显示的标签。</span><span class="sxs-lookup"><span data-stu-id="5b98f-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="5b98f-205">除了此元素指定的文本，Windows PowerShell 还显示触发新组的值，并在标签之前和之后添加一个空白行。</span><span class="sxs-lookup"><span data-stu-id="5b98f-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="5b98f-206">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-206">This element is optional.</span></span>

- <span data-ttu-id="5b98f-207">[CustomControl](./customcontrol-element-for-groupby-format.md)元素定义用于显示数据的控件。</span><span class="sxs-lookup"><span data-stu-id="5b98f-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="5b98f-208">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-208">This element is optional.</span></span>

- <span data-ttu-id="5b98f-209">[CustomControlName](./customcontrolname-element-for-groupby-format.md)元素指定用于显示数据的通用控件或视图控件。</span><span class="sxs-lookup"><span data-stu-id="5b98f-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="5b98f-210">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5b98f-210">This element is optional.</span></span>

<span data-ttu-id="5b98f-211">有关定义组的完整格式化文件的示例，请参阅[列表视图（GroupBy）](./list-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="5b98f-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="5b98f-212">使用格式字符串</span><span class="sxs-lookup"><span data-stu-id="5b98f-212">Using Format Strings</span></span>

<span data-ttu-id="5b98f-213">可以将字符串的格式添加到视图中，以便进一步定义数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="5b98f-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="5b98f-214">下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。</span><span class="sxs-lookup"><span data-stu-id="5b98f-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="5b98f-215">以下 XML 元素可用于指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="5b98f-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="5b98f-216">"[出现](./listitem-element-for-listitems-for-listcontrol-format.md)类型" 元素指定视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="5b98f-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="5b98f-217">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定其值由视图显示的属性。</span><span class="sxs-lookup"><span data-stu-id="5b98f-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="5b98f-218">您必须指定属性或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5b98f-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="5b98f-219">"格式[字符串](./formatstring-element-for-listitem-for-listcontrol-format.md)" 元素指定定义属性或脚本值在视图中显示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="5b98f-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="5b98f-220">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素（未显示）指定其值由视图显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="5b98f-221">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5b98f-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="5b98f-222">在下面的示例中，调用 `ToString` 方法来设置脚本的值的格式。</span><span class="sxs-lookup"><span data-stu-id="5b98f-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="5b98f-223">脚本可以调用对象的任何方法。</span><span class="sxs-lookup"><span data-stu-id="5b98f-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="5b98f-224">因此，如果对象有一个具有格式参数的方法（如 `ToString`），则脚本可以调用该方法来设置脚本的输出值的格式。</span><span class="sxs-lookup"><span data-stu-id="5b98f-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="5b98f-225">以下 XML 元素可用于调用 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="5b98f-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="5b98f-226">"[出现](./listitem-element-for-listitems-for-listcontrol-format.md)类型" 元素指定视图显示的数据。</span><span class="sxs-lookup"><span data-stu-id="5b98f-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="5b98f-227">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素（未显示）指定其值由视图显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="5b98f-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="5b98f-228">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5b98f-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b98f-229">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b98f-229">See Also</span></span>

[<span data-ttu-id="5b98f-230">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b98f-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)

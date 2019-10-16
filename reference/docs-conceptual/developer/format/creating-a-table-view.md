---
title: 创建表视图 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363406"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="36c3d-102">创建表视图</span><span class="sxs-lookup"><span data-stu-id="36c3d-102">Creating a Table View</span></span>

<span data-ttu-id="36c3d-103">表视图在一个或多个列中显示数据。</span><span class="sxs-lookup"><span data-stu-id="36c3d-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="36c3d-104">表中的每一行都表示一个 .NET 对象，表中的每一列都表示该对象的一个属性或一个脚本值。</span><span class="sxs-lookup"><span data-stu-id="36c3d-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="36c3d-105">您可以定义显示对象的所有属性或对象的属性子集的表视图。</span><span class="sxs-lookup"><span data-stu-id="36c3d-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="36c3d-106">表格视图显示</span><span class="sxs-lookup"><span data-stu-id="36c3d-106">A Table View Display</span></span>

<span data-ttu-id="36c3d-107">下面的示例演示 Windows PowerShell 如何显示由[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) [Cmdlet 返回](/powershell/module/microsoft.powershell.management/get-service)的 system.serviceprocess 对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="36c3d-108">对于此对象，Windows PowerShell 定义了一个显示 `Status` 属性的表视图，`Name` 属性（此属性是 @no__t 2 属性的别名属性）和 @no__t。</span><span class="sxs-lookup"><span data-stu-id="36c3d-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="36c3d-109">表中的每一行表示该 cmdlet 返回的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="36c3d-110">定义表视图</span><span class="sxs-lookup"><span data-stu-id="36c3d-110">Defining the Table View</span></span>

<span data-ttu-id="36c3d-111">下面的 XML 演示用于显示[system.serviceprocess. Servicecontroller 的表视图架构。Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="36c3d-112">您必须指定要在表视图中显示的每个属性。</span><span class="sxs-lookup"><span data-stu-id="36c3d-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="36c3d-113">以下 XML 元素用于定义列表视图：</span><span class="sxs-lookup"><span data-stu-id="36c3d-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="36c3d-114">[View](./view-element-format.md)元素是表视图的父元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="36c3d-115">（这是列表、宽控件和自定义控件视图的相同父元素。）</span><span class="sxs-lookup"><span data-stu-id="36c3d-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="36c3d-116">[Name](./name-element-for-view-format.md)元素指定视图的名称。</span><span class="sxs-lookup"><span data-stu-id="36c3d-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="36c3d-117">此元素对于所有视图都是必需的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-117">This element is required for all views.</span></span>

- <span data-ttu-id="36c3d-118">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="36c3d-119">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-119">This element is required.</span></span>

- <span data-ttu-id="36c3d-120">[GroupBy](./groupby-element-for-view-format.md)元素（在本示例中未显示）定义显示新的对象组的时间。</span><span class="sxs-lookup"><span data-stu-id="36c3d-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="36c3d-121">每当特定属性或脚本的值发生更改时，就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="36c3d-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="36c3d-122">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-122">This element is optional.</span></span>

- <span data-ttu-id="36c3d-123">[Controls](./controls-element-for-view-format.md)元素（在本示例中未显示）定义表视图定义的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="36c3d-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="36c3d-124">控件使您可以进一步指定数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="36c3d-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="36c3d-125">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-125">This element is optional.</span></span> <span data-ttu-id="36c3d-126">视图可以定义自己的自定义控件，也可以使用可由格式设置文件中的任何视图使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="36c3d-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="36c3d-127">有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="36c3d-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="36c3d-128">[HideTableHeaders](./hidetableheaders-element-format.md)元素（在本示例中不显示）指定表将不会在表的顶部显示任何标签。</span><span class="sxs-lookup"><span data-stu-id="36c3d-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="36c3d-129">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-129">This element is optional.</span></span>

- <span data-ttu-id="36c3d-130">定义表的标头和行信息的[TableControl](./tablecontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="36c3d-131">与所有其他视图类似，表视图可以显示对象属性的值或脚本生成的值。</span><span class="sxs-lookup"><span data-stu-id="36c3d-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="36c3d-132">定义列标题</span><span class="sxs-lookup"><span data-stu-id="36c3d-132">Defining Column Headers</span></span>

1. <span data-ttu-id="36c3d-133">[TableHeaders](./tableheaders-element-format.md)元素及其子元素定义在表顶部显示的内容。</span><span class="sxs-lookup"><span data-stu-id="36c3d-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="36c3d-134">[TableColumnHeader](./tablecolumnheader-element-format.md)元素定义在表的列顶部显示的内容。</span><span class="sxs-lookup"><span data-stu-id="36c3d-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="36c3d-135">按您希望标题显示的顺序指定这些元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="36c3d-136">您可以使用的这些元素的数量没有限制，但表视图中的[TableColumnHeader](./tablecolumnheader-element-format.md)元素数目必须等于您使用的[TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)元素的数目。</span><span class="sxs-lookup"><span data-stu-id="36c3d-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="36c3d-137">[Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定显示的文本。</span><span class="sxs-lookup"><span data-stu-id="36c3d-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="36c3d-138">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-138">This element is optional.</span></span>

4. <span data-ttu-id="36c3d-139">[Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定列的宽度（以字符为字符）。</span><span class="sxs-lookup"><span data-stu-id="36c3d-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="36c3d-140">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-140">This element is optional.</span></span>

5. <span data-ttu-id="36c3d-141">[对齐](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定如何显示标签。</span><span class="sxs-lookup"><span data-stu-id="36c3d-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="36c3d-142">标签可以左对齐、右对齐或居中对齐。</span><span class="sxs-lookup"><span data-stu-id="36c3d-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="36c3d-143">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="36c3d-144">定义表行</span><span class="sxs-lookup"><span data-stu-id="36c3d-144">Defining the Table Rows</span></span>

<span data-ttu-id="36c3d-145">表视图可以提供一个或多个定义，这些定义通过使用[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素的子元素来指定在表的行中显示哪些数据。</span><span class="sxs-lookup"><span data-stu-id="36c3d-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="36c3d-146">请注意，您可以为表中的行指定多个定义，但无论使用哪种行定义，行的标头都保持不变。</span><span class="sxs-lookup"><span data-stu-id="36c3d-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="36c3d-147">通常，表只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="36c3d-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="36c3d-148">在下面的示例中，视图提供了一个定义，用于显示系统的多个属性的值[。Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="36c3d-149">表视图可以在其行中显示属性的值或脚本的值（不在示例中显示）。</span><span class="sxs-lookup"><span data-stu-id="36c3d-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="36c3d-150">以下 XML 元素可用于为行提供定义：</span><span class="sxs-lookup"><span data-stu-id="36c3d-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="36c3d-151">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素及其子元素定义在表的行中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="36c3d-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="36c3d-152">[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素提供行的定义。</span><span class="sxs-lookup"><span data-stu-id="36c3d-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="36c3d-153">至少需要一个[TableRowEntry](./listentry-element-for-listcontrol-format.md) ;但是，可以添加的元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="36c3d-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="36c3d-154">在大多数情况下，视图将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="36c3d-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="36c3d-155">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素指定由特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="36c3d-156">此元素是可选的，仅当定义显示不同对象的多个[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素时才需要此元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="36c3d-157">[Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)元素指定超出列宽的文本显示在下一行。</span><span class="sxs-lookup"><span data-stu-id="36c3d-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="36c3d-158">默认情况下，超过列宽的文本将被截断。</span><span class="sxs-lookup"><span data-stu-id="36c3d-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="36c3d-159">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)元素定义其值显示在行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="36c3d-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="36c3d-160">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义其值显示在行的列中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="36c3d-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="36c3d-161">行的每个列都需要一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="36c3d-162">第一项显示在第一列中，第二项显示在第二列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="36c3d-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="36c3d-163">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示在行中的属性。</span><span class="sxs-lookup"><span data-stu-id="36c3d-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="36c3d-164">您必须指定属性或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="36c3d-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="36c3d-165">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值在行中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="36c3d-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="36c3d-166">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="36c3d-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="36c3d-167">"格式[字符串](./label-element-for-listitem-for-listcontrol-format.md)" 元素指定定义如何显示属性或脚本值的格式模式。</span><span class="sxs-lookup"><span data-stu-id="36c3d-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="36c3d-168">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-168">This element is optional.</span></span>

- <span data-ttu-id="36c3d-169">[对齐](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定属性或脚本的值的显示方式。</span><span class="sxs-lookup"><span data-stu-id="36c3d-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="36c3d-170">值可以左对齐、右对齐或居中对齐。</span><span class="sxs-lookup"><span data-stu-id="36c3d-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="36c3d-171">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="36c3d-172">定义使用表视图的对象</span><span class="sxs-lookup"><span data-stu-id="36c3d-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="36c3d-173">可以通过两种方法来定义哪些 .NET 对象使用表视图。</span><span class="sxs-lookup"><span data-stu-id="36c3d-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="36c3d-174">您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可由视图的所有定义显示的对象，也可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义由视图的特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="36c3d-175">在大多数情况下，视图只有一个定义，因此对象通常由[ViewSelectedBy](./viewselectedby-element-format.md)元素定义。</span><span class="sxs-lookup"><span data-stu-id="36c3d-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="36c3d-176">下面的示例演示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定义表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="36c3d-177">对于您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素的数量没有限制，它们的顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="36c3d-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="36c3d-178">以下 XML 元素可用于指定表视图所使用的对象：</span><span class="sxs-lookup"><span data-stu-id="36c3d-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="36c3d-179">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="36c3d-180">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的 .net 对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="36c3d-181">完全限定的 .NET 类型名称是必需的。</span><span class="sxs-lookup"><span data-stu-id="36c3d-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="36c3d-182">您必须为视图指定至少一个类型或选择集，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="36c3d-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="36c3d-183">下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="36c3d-184">使用选择集，其中有一组使用多个视图显示的相关对象，例如为同一对象定义列表视图和表视图。</span><span class="sxs-lookup"><span data-stu-id="36c3d-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="36c3d-185">有关如何创建选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="36c3d-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="36c3d-186">以下 XML 元素可用于指定列表视图所使用的对象：</span><span class="sxs-lookup"><span data-stu-id="36c3d-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="36c3d-187">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="36c3d-188">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定可由视图显示的一组对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="36c3d-189">您必须为视图指定至少一个选择集或类型，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="36c3d-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="36c3d-190">下面的示例演示如何使用[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素定义表视图的特定定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="36c3d-191">使用此元素，可以指定对象的 .NET 类型名称、对象的选择集或指定何时使用定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="36c3d-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="36c3d-192">有关如何创建选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="36c3d-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="36c3d-193">创建表视图的多个定义时，不能指定不同的列标题。</span><span class="sxs-lookup"><span data-stu-id="36c3d-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="36c3d-194">您只能指定在表的行中显示的内容，例如显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="36c3d-195">以下 XML 元素可用于指定列表视图的特定定义所使用的对象：</span><span class="sxs-lookup"><span data-stu-id="36c3d-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="36c3d-196">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素定义由定义显示的对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="36c3d-197">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定由定义显示的 .net 对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="36c3d-198">使用此元素时，必须提供完全限定的 .NET 类型名称。</span><span class="sxs-lookup"><span data-stu-id="36c3d-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="36c3d-199">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="36c3d-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="36c3d-200">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定可由此定义显示的一组对象。</span><span class="sxs-lookup"><span data-stu-id="36c3d-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="36c3d-201">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="36c3d-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="36c3d-202">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定必须存在的条件才能使用此定义。</span><span class="sxs-lookup"><span data-stu-id="36c3d-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="36c3d-203">您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。</span><span class="sxs-lookup"><span data-stu-id="36c3d-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="36c3d-204">有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="36c3d-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="36c3d-205">使用格式字符串</span><span class="sxs-lookup"><span data-stu-id="36c3d-205">Using Format Strings</span></span>

<span data-ttu-id="36c3d-206">可以将字符串的格式添加到视图中，以便进一步定义数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="36c3d-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="36c3d-207">下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。</span><span class="sxs-lookup"><span data-stu-id="36c3d-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="36c3d-208">以下 XML 元素可用于指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="36c3d-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="36c3d-209">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义其值显示在行的列中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="36c3d-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="36c3d-210">行的每个列都需要一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="36c3d-211">第一项显示在第一列中，第二项显示在第二列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="36c3d-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="36c3d-212">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示在行中的属性。</span><span class="sxs-lookup"><span data-stu-id="36c3d-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="36c3d-213">您必须指定属性或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="36c3d-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="36c3d-214">"格式[字符串](./label-element-for-listitem-for-listcontrol-format.md)" 元素指定定义如何显示属性或脚本值的格式模式。</span><span class="sxs-lookup"><span data-stu-id="36c3d-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="36c3d-215">在下面的示例中，调用 `ToString` 方法来设置脚本的值的格式。</span><span class="sxs-lookup"><span data-stu-id="36c3d-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="36c3d-216">脚本可以调用对象的任何方法。</span><span class="sxs-lookup"><span data-stu-id="36c3d-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="36c3d-217">因此，如果对象有一个具有格式参数的方法（如 `ToString`），则脚本可以调用该方法来设置脚本的输出值的格式。</span><span class="sxs-lookup"><span data-stu-id="36c3d-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="36c3d-218">以下 XML 元素可用于调用 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="36c3d-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="36c3d-219">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义其值显示在行的列中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="36c3d-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="36c3d-220">行的每个列都需要一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="36c3d-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="36c3d-221">第一项显示在第一列中，第二项显示在第二列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="36c3d-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="36c3d-222">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值在行中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="36c3d-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="36c3d-223">您必须指定脚本或属性，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="36c3d-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="36c3d-224">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36c3d-224">See Also</span></span>

[<span data-ttu-id="36c3d-225">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="36c3d-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

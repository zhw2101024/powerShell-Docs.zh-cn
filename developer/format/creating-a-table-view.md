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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057359"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="ba807-102">创建表视图</span><span class="sxs-lookup"><span data-stu-id="ba807-102">Creating a Table View</span></span>

<span data-ttu-id="ba807-103">表视图中一个或多个列中显示数据。</span><span class="sxs-lookup"><span data-stu-id="ba807-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="ba807-104">表中的每一行表示一个.NET 对象，对象和表的每个列表示的对象或脚本值的属性。</span><span class="sxs-lookup"><span data-stu-id="ba807-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="ba807-105">可以定义显示的对象的所有属性或对象的属性的子集的表视图。</span><span class="sxs-lookup"><span data-stu-id="ba807-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="ba807-106">表视图显示</span><span class="sxs-lookup"><span data-stu-id="ba807-106">A Table View Display</span></span>

<span data-ttu-id="ba807-107">下面的示例演示如何显示 Windows PowerShell [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba807-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="ba807-108">此对象，Windows PowerShell 已定义显示的表视图`Status`属性，`Name`属性 (此属性是别名属性`ServiceName`属性)，和`DisplayName`属性。</span><span class="sxs-lookup"><span data-stu-id="ba807-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="ba807-109">在表中的每一行表示 cmdlet 返回的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="ba807-110">定义表视图</span><span class="sxs-lookup"><span data-stu-id="ba807-110">Defining the Table View</span></span>

<span data-ttu-id="ba807-111">下面的 XML 演示用于显示的表视图架构[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ba807-112">必须指定想要在表视图中显示每个属性。</span><span class="sxs-lookup"><span data-stu-id="ba807-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="ba807-113">以下 XML 元素用于定义列表视图：</span><span class="sxs-lookup"><span data-stu-id="ba807-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="ba807-114">[视图](./view-element-format.md)元素是表视图的父元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="ba807-115">（这是列表中，宽，和自定义控件视图的相同父元素）。</span><span class="sxs-lookup"><span data-stu-id="ba807-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="ba807-116">[名称](./name-element-for-view-format.md)元素指定的视图的名称。</span><span class="sxs-lookup"><span data-stu-id="ba807-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="ba807-117">此元素是必需的所有视图。</span><span class="sxs-lookup"><span data-stu-id="ba807-117">This element is required for all views.</span></span>

- <span data-ttu-id="ba807-118">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="ba807-119">此元素是必需的。</span><span class="sxs-lookup"><span data-stu-id="ba807-119">This element is required.</span></span>

- <span data-ttu-id="ba807-120">[GroupBy](./groupby-element-for-view-format.md)元素 （不在此示例中所示） 定义何时显示新组的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="ba807-121">特定属性或脚本的值发生更改时启动新的组。</span><span class="sxs-lookup"><span data-stu-id="ba807-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ba807-122">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-122">This element is optional.</span></span>

- <span data-ttu-id="ba807-123">[控件](./controls-element-for-view-format.md)元素 （不在此示例中所示） 定义的自定义控件定义的表视图。</span><span class="sxs-lookup"><span data-stu-id="ba807-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="ba807-124">控件提供了一种方法，以便进一步指定如何显示数据。</span><span class="sxs-lookup"><span data-stu-id="ba807-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="ba807-125">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-125">This element is optional.</span></span> <span data-ttu-id="ba807-126">视图可以定义自己的自定义控件或它可以使用可由任意视图中的格式设置文件的公共控件。</span><span class="sxs-lookup"><span data-stu-id="ba807-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="ba807-127">有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="ba807-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="ba807-128">[HideTableHeaders](./hidetableheaders-element-format.md)元素 （不显示在此示例中） 指定的表不会显示任何标签，在表的顶部。</span><span class="sxs-lookup"><span data-stu-id="ba807-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="ba807-129">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-129">This element is optional.</span></span>

- <span data-ttu-id="ba807-130">[TableControl](./tablecontrol-element-format.md)元素，用于定义表的标头和行信息。</span><span class="sxs-lookup"><span data-stu-id="ba807-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="ba807-131">与所有其他视图类似，表视图可以显示对象属性的值或由脚本生成的值。</span><span class="sxs-lookup"><span data-stu-id="ba807-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="ba807-132">定义列标题</span><span class="sxs-lookup"><span data-stu-id="ba807-132">Defining Column Headers</span></span>

1. <span data-ttu-id="ba807-133">[TableHeaders](./tableheaders-element-format.md)元素及其子元素定义的表的顶部显示的内容。</span><span class="sxs-lookup"><span data-stu-id="ba807-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="ba807-134">[TableColumnHeader](./tablecolumnheader-element-format.md)元素定义的表的列的顶部显示的内容。</span><span class="sxs-lookup"><span data-stu-id="ba807-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="ba807-135">你想显示的标头的顺序指定这些元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="ba807-136">可以使用这些元素的数目，但数没有限制[TableColumnHeader](./tablecolumnheader-element-format.md)在表视图中的元素的数目必须相等[TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)您使用的元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="ba807-137">[标签](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定显示的文本。</span><span class="sxs-lookup"><span data-stu-id="ba807-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="ba807-138">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-138">This element is optional.</span></span>

4. <span data-ttu-id="ba807-139">[宽度](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定的列的宽度 （以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="ba807-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="ba807-140">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-140">This element is optional.</span></span>

5. <span data-ttu-id="ba807-141">[对齐](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定标签的显示方式。</span><span class="sxs-lookup"><span data-stu-id="ba807-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="ba807-142">可以向左到右对齐或居中标签。</span><span class="sxs-lookup"><span data-stu-id="ba807-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="ba807-143">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="ba807-144">定义的表行</span><span class="sxs-lookup"><span data-stu-id="ba807-144">Defining the Table Rows</span></span>

<span data-ttu-id="ba807-145">表视图可以提供一个或多个定义，指定显示的数据的表的行中使用的子元素[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="ba807-146">请注意，您可以指定多个定义的行的表，但行的标头将保持不变，无论使用何种行定义。</span><span class="sxs-lookup"><span data-stu-id="ba807-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="ba807-147">通常情况下，表会将只有一个定义。</span><span class="sxs-lookup"><span data-stu-id="ba807-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="ba807-148">在以下示例中，视图提供了显示的多个属性的值的单个定义[System.Diagnostics.Process？Displayproperty =](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="ba807-149">表视图，可以在其行中显示的属性的值或脚本 （在示例中未显示） 的值。</span><span class="sxs-lookup"><span data-stu-id="ba807-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="ba807-150">以下 XML 元素可以用于提供定义的行：</span><span class="sxs-lookup"><span data-stu-id="ba807-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="ba807-151">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素及其子元素定义的表的行中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="ba807-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="ba807-152">[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素提供的行的定义。</span><span class="sxs-lookup"><span data-stu-id="ba807-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="ba807-153">至少一个[TableRowEntry](./listentry-element-for-listcontrol-format.md)是必需的; 但是，没有任何可以添加的元素数目的最大限制。</span><span class="sxs-lookup"><span data-stu-id="ba807-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="ba807-154">在大多数情况下，将具有只有一个定义的视图。</span><span class="sxs-lookup"><span data-stu-id="ba807-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="ba807-155">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素指定所显示的特定定义的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="ba807-156">此元素是可选的仅当定义多个需要[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素，用于显示不同的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="ba807-157">[包装](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)元素指定，在下一行显示超过列宽的文本。</span><span class="sxs-lookup"><span data-stu-id="ba807-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="ba807-158">默认情况下，超过列宽的文本将被截断。</span><span class="sxs-lookup"><span data-stu-id="ba807-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="ba807-159">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)元素定义的属性或其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ba807-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="ba807-160">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义的属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ba807-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ba807-161">一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素是必需的行的每个列。</span><span class="sxs-lookup"><span data-stu-id="ba807-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ba807-162">第一个条目显示在第一列，第二个条目中的第二个列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="ba807-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ba807-163">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定的行中显示其值的属性。</span><span class="sxs-lookup"><span data-stu-id="ba807-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="ba807-164">必须指定一个属性或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="ba807-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ba807-165">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ba807-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="ba807-166">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="ba807-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="ba807-167">[FormatString](./label-element-for-listitem-for-listcontrol-format.md)元素指定的格式模式，它定义如何显示的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="ba807-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="ba807-168">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-168">This element is optional.</span></span>

- <span data-ttu-id="ba807-169">[对齐](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定的属性或脚本的值的显示方式。</span><span class="sxs-lookup"><span data-stu-id="ba807-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="ba807-170">值可以是左到右对齐或居中。</span><span class="sxs-lookup"><span data-stu-id="ba807-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="ba807-171">此元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="ba807-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="ba807-172">定义使用表视图的对象</span><span class="sxs-lookup"><span data-stu-id="ba807-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="ba807-173">有两种方法定义的.NET 对象使用表视图。</span><span class="sxs-lookup"><span data-stu-id="ba807-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="ba807-174">可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可显示的视图，或者您的所有定义的对象可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义将显示哪些对象将视图的特定定义。</span><span class="sxs-lookup"><span data-stu-id="ba807-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="ba807-175">在大多数情况下，视图具有只有一个定义，因此对象通常由定义[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="ba807-176">下面的示例演示如何定义表视图使用显示的对象[ViewSelectedBy](./viewselectedby-element-format.md)并[TypeName](./typename-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ba807-177">数量没有限制[TypeName](./typename-element-for-viewselectedby-format.md)元素可以指定和其顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="ba807-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="ba807-178">以下 XML 元素可以用于指定使用的表视图的对象：</span><span class="sxs-lookup"><span data-stu-id="ba807-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="ba807-179">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ba807-180">[TypeName](./typename-element-for-viewselectedby-format.md)元素指定.NET 对象，该视图显示对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="ba807-181">完全限定的.NET 类型名称是必需的。</span><span class="sxs-lookup"><span data-stu-id="ba807-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="ba807-182">必须指定至少一个类型或所选内容设置对于视图，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="ba807-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ba807-183">下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)并[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ba807-184">使用的选项集，其中有一组相关的相同对象使用多个视图，例如何时定义列表视图和表视图，显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="ba807-185">有关如何创建选项集的详细信息，请参阅[定义的选项集，](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ba807-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="ba807-186">以下 XML 元素可以用于指定使用列表视图的对象：</span><span class="sxs-lookup"><span data-stu-id="ba807-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="ba807-187">[ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ba807-188">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定一组视图可以显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="ba807-189">必须指定至少一个选择集或类型视图，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="ba807-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ba807-190">下面的示例演示如何定义表视图使用的特定定义所显示的对象[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ba807-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="ba807-191">使用此元素，可以指定将对象、 选择一组对象或选择条件，指定当使用定义的.NET 类型名称。</span><span class="sxs-lookup"><span data-stu-id="ba807-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="ba807-192">有关如何创建所选条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ba807-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ba807-193">创建多个定义的表视图时不能指定不同的列标题。</span><span class="sxs-lookup"><span data-stu-id="ba807-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="ba807-194">您可以指定仅中显示的内容的行的表，例如显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="ba807-195">以下 XML 元素可以用于指定使用特定的列表视图中定义的对象：</span><span class="sxs-lookup"><span data-stu-id="ba807-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="ba807-196">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素定义在定义将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="ba807-197">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定显示定义的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="ba807-198">使用此元素，完全限定的.NET 类型名称时，所需。</span><span class="sxs-lookup"><span data-stu-id="ba807-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="ba807-199">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="ba807-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ba807-200">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定一组可显示的此定义的对象。</span><span class="sxs-lookup"><span data-stu-id="ba807-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="ba807-201">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="ba807-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ba807-202">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定要使用此定义中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="ba807-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ba807-203">必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。</span><span class="sxs-lookup"><span data-stu-id="ba807-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="ba807-204">有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ba807-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="ba807-205">使用格式字符串</span><span class="sxs-lookup"><span data-stu-id="ba807-205">Using Format Strings</span></span>

<span data-ttu-id="ba807-206">可以为视图，以进一步定义数据的显示方式添加格式设置字符串。</span><span class="sxs-lookup"><span data-stu-id="ba807-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="ba807-207">下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。</span><span class="sxs-lookup"><span data-stu-id="ba807-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="ba807-208">可以使用以下 XML 元素来指定格式模式：</span><span class="sxs-lookup"><span data-stu-id="ba807-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="ba807-209">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义的属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ba807-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ba807-210">一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素是必需的行的每个列。</span><span class="sxs-lookup"><span data-stu-id="ba807-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ba807-211">第一个条目显示在第一列，第二个条目中的第二个列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="ba807-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ba807-212">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定的行中显示其值的属性。</span><span class="sxs-lookup"><span data-stu-id="ba807-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="ba807-213">必须指定一个属性或脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="ba807-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ba807-214">[FormatString](./label-element-for-listitem-for-listcontrol-format.md)元素指定的格式模式，它定义如何显示的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="ba807-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="ba807-215">在以下示例中，`ToString`调用方法来设置脚本的值的格式。</span><span class="sxs-lookup"><span data-stu-id="ba807-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="ba807-216">脚本可以调用一个对象的任何方法。</span><span class="sxs-lookup"><span data-stu-id="ba807-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="ba807-217">因此，如果对象具有一种方法，如`ToString`，具有格式设置参数，该脚本可以调用该方法，以设置脚本的输出值的格式。</span><span class="sxs-lookup"><span data-stu-id="ba807-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="ba807-218">下面的 XML 元素可用于调用`ToString`方法：</span><span class="sxs-lookup"><span data-stu-id="ba807-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="ba807-219">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义的属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ba807-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ba807-220">一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素是必需的行的每个列。</span><span class="sxs-lookup"><span data-stu-id="ba807-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ba807-221">第一个条目显示在第一列，第二个条目中的第二个列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="ba807-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ba807-222">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ba807-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="ba807-223">必须指定一个脚本或属性，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="ba807-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba807-224">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba807-224">See Also</span></span>

[<span data-ttu-id="ba807-225">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="ba807-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

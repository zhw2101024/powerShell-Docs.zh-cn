---
title: 格式设置文件概述 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863293"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="4d4aa-102">格式设置文件概述</span><span class="sxs-lookup"><span data-stu-id="4d4aa-102">Formatting File Overview</span></span>

<span data-ttu-id="4d4aa-103">由命令 （cmdlet、 函数和脚本） 返回的对象的显示格式使用定义的格式设置文件 （format.ps1xml 文件）。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="4d4aa-104">多个这些文件提供的 PowerShell，若要定义由提供 PowerShell 命令，如返回这些对象的显示格式[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象返回的`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="4d4aa-105">但是，您还可以创建自己的自定义格式设置文件以覆盖默认显示格式，也可以编写自定义格式设置文件来定义自己的命令返回的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d4aa-106">格式设置文件不用于确定返回到管道对象的元素。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="4d4aa-107">当对象返回到管道时，该对象的所有成员都都可用，即使某些未显示。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="4d4aa-108">PowerShell 将使用这些格式设置文件中的数据来确定显示的内容和显示的数据的格式设置方式。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="4d4aa-109">在显示的数据可以包括对象的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="4d4aa-110">如果你想要显示某些值不是可直接从一个对象，如添加两个对象的属性的值并在一段数据以显示总和的属性，则使用脚本。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="4d4aa-111">显示数据的格式设置，可以定义要显示在对象的视图。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="4d4aa-112">可以定义每个对象的单个视图，可以定义多个对象的单一视图也可以定义相同的对象的多个视图。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="4d4aa-113">可以定义的视图数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="4d4aa-114">格式设置文件的常用功能</span><span class="sxs-lookup"><span data-stu-id="4d4aa-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="4d4aa-115">每个格式设置文件可以定义可在文件中定义的所有视图之间共享的以下组件：</span><span class="sxs-lookup"><span data-stu-id="4d4aa-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="4d4aa-116">默认配置设置，如是否显示在表中的行中的数据将显示在下一行数据是否超过了列的宽度。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="4d4aa-117">有关这些设置的详细信息，请参阅[定义常见的配置设置](./defining-common-configuration-features.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="4d4aa-118">任何的组格式设置文件的视图可以显示的对象。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="4d4aa-119">有关这些集的详细信息 (称为*选集*)，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="4d4aa-120">可由格式设置文件的所有视图的公共控件。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="4d4aa-121">控件提供了更精确的控制数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="4d4aa-122">有关控件的详细信息，请参阅[定义自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="4d4aa-123">格式设置的视图</span><span class="sxs-lookup"><span data-stu-id="4d4aa-123">Formatting Views</span></span>

<span data-ttu-id="4d4aa-124">格式设置的视图可以显示在表格格式、 列表格式、 宽格式和自定义格式的对象。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="4d4aa-125">大多数情况下，由一组对视图进行说明的 XML 标记描述每个格式设置的定义。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="4d4aa-126">每个视图包含视图的名称使用视图和视图，如表视图的列和行信息的元素的对象。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="4d4aa-127">表视图列出了对象或一个或多个列中的脚本块值的属性。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="4d4aa-128">每个列表示对象或脚本值的单个的属性。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="4d4aa-129">可以定义显示的对象的对象或属性和脚本值的组合的属性子集的所有属性的表视图。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="4d4aa-130">表的每一行表示一个返回的对象。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="4d4aa-131">创建表视图是非常类似于当你通过管道将对象`Format-Table`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="4d4aa-132">有关此视图的详细信息，请参阅[表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="4d4aa-133">列表视图还列出了对象或单个列中的脚本值的属性。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="4d4aa-134">列表的每行显示的可选标签或属性名称后面跟的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="4d4aa-135">创建列表视图是非常类似于通过管道将对象与`Format-List`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="4d4aa-136">有关此视图的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="4d4aa-137">宽视图列出了对象或一个或多个列中的脚本值的单个属性。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="4d4aa-138">没有标签或此视图的标头。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-138">There is no label or header for this view.</span></span> <span data-ttu-id="4d4aa-139">创建较宽的视图是非常类似于通过管道将对象与`Format-Wide`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="4d4aa-140">有关此视图的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="4d4aa-141">自定义视图显示不符合的表视图、 列表视图或宽视图刚性结构的可自定义视图的对象属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="4d4aa-142">可以定义独立的自定义视图，也可以定义由另一个视图，如表视图或列表视图的自定义视图。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="4d4aa-143">创建自定义视图是非常类似于通过管道将对象与`Format-Custom`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="4d4aa-144">有关此视图的详细信息，请参阅[的自定义视图](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="4d4aa-145">视图的组件</span><span class="sxs-lookup"><span data-stu-id="4d4aa-145">Components of a View</span></span>

<span data-ttu-id="4d4aa-146">以下 XML 示例显示一个视图的基本 XML 组件。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="4d4aa-147">但是，单个 XML 元素不同你想要创建，具体取决于哪种视图是相同的视图的基本组件。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="4d4aa-148">开始时，每个视图具有`Name`元素，它指定用于引用该视图的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="4d4aa-149">`ViewSelectedBy`元素，用于定义视图中，将显示的.NET 对象和一个*控制*元素定义的视图。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="4d4aa-150">在控件元素中，可以定义一个或多个*条目*元素。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="4d4aa-151">如果使用多个定义，则必须指定的.NET 对象使用的每个定义。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="4d4aa-152">通常只有一个条目，只有一个定义，需要为每个控件。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="4d4aa-153">在视图的每个输入元素，可以指定*项*元素定义的.NET 属性或由该视图显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="4d4aa-154">前面的示例中所示，该格式设置文件可以包含多个视图、 视图可以包含多个定义和每个定义可以包含多个项。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="4d4aa-155">表视图的示例</span><span class="sxs-lookup"><span data-stu-id="4d4aa-155">Example of a Table View</span></span>

<span data-ttu-id="4d4aa-156">下面的示例演示用于定义包含两个列的表视图的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="4d4aa-157">[ViewDefinitions](./viewdefinitions-element-format.md)元素是格式设置文件中定义的所有视图的容器元素。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="4d4aa-158">[视图](./view-element-format.md)元素定义特定的表、 列表、 宽，或自定义视图。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="4d4aa-159">在每个[视图](./view-element-format.md)元素，[名称](./name-element-for-view-format.md)元素指定视图的名称[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用的视图，和不同的对象控制元素 (如`TableControl`元素下面的示例中所示) 定义视图的类型。</span><span class="sxs-lookup"><span data-stu-id="4d4aa-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="4d4aa-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d4aa-160">See Also</span></span>

[<span data-ttu-id="4d4aa-161">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="4d4aa-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4d4aa-162">创建表视图</span><span class="sxs-lookup"><span data-stu-id="4d4aa-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4d4aa-163">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="4d4aa-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4d4aa-164">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="4d4aa-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4d4aa-165">编写的 PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="4d4aa-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)

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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363406"
---
# <a name="creating-a-table-view"></a>创建表视图

表视图在一个或多个列中显示数据。 表中的每一行都表示一个 .NET 对象，表中的每一列都表示该对象的一个属性或一个脚本值。 您可以定义显示对象的所有属性或对象的属性子集的表视图。

## <a name="a-table-view-display"></a>表格视图显示

下面的示例演示 Windows PowerShell 如何显示由[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) [Cmdlet 返回](/powershell/module/microsoft.powershell.management/get-service)的 system.serviceprocess 对象。 对于此对象，Windows PowerShell 定义了显示 `Status` 属性、`Name` 属性（此属性是 `ServiceName` 属性的 alias 属性）和 `DisplayName` 属性的表视图。 表中的每一行表示该 cmdlet 返回的对象。

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>定义表视图

下面的 XML 演示用于显示[system.serviceprocess. Servicecontroller 的表视图架构。Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)对象。 您必须指定要在表视图中显示的每个属性。

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

以下 XML 元素用于定义列表视图：

- [View](./view-element-format.md)元素是表视图的父元素。 （这是列表、宽控件和自定义控件视图的相同父元素。）

- [Name](./name-element-for-view-format.md)元素指定视图的名称。 此元素对于所有视图都是必需的。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。 需要此元素。

- [GroupBy](./groupby-element-for-view-format.md)元素（在本示例中未显示）定义显示新的对象组的时间。 每当特定属性或脚本的值发生更改时，就会启动一个新组。 此元素为可选元素。

- [Controls](./controls-element-for-view-format.md)元素（在本示例中未显示）定义表视图定义的自定义控件。 控件使您可以进一步指定数据的显示方式。 此元素为可选元素。 视图可以定义自己的自定义控件，也可以使用可由格式设置文件中的任何视图使用的公共控件。 有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

- [HideTableHeaders](./hidetableheaders-element-format.md)元素（在本示例中不显示）指定表将不会在表的顶部显示任何标签。 此元素为可选元素。

- 定义表的标头和行信息的[TableControl](./tablecontrol-element-format.md)元素。 与所有其他视图类似，表视图可以显示对象属性的值或脚本生成的值。

## <a name="defining-column-headers"></a>定义列标题

1. [TableHeaders](./tableheaders-element-format.md)元素及其子元素定义在表顶部显示的内容。

2. [TableColumnHeader](./tablecolumnheader-element-format.md)元素定义在表的列顶部显示的内容。 按您希望标题显示的顺序指定这些元素。

   您可以使用的这些元素的数量没有限制，但表视图中的[TableColumnHeader](./tablecolumnheader-element-format.md)元素数目必须等于您使用的[TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)元素的数目。

3. [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定显示的文本。 此元素为可选元素。

4. [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定列的宽度（以字符为字符）。 此元素为可选元素。

5. [对齐](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定如何显示标签。 标签可以左对齐、右对齐或居中对齐。 此元素为可选元素。

## <a name="defining-the-table-rows"></a>定义表行

表视图可以提供一个或多个定义，这些定义通过使用[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素的子元素来指定在表的行中显示哪些数据。 请注意，您可以为表中的行指定多个定义，但无论使用哪种行定义，行的标头都保持不变。 通常，表只有一个定义。

在下面的示例中，视图提供了一个定义，用于显示系统的多个属性的值[。Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process)对象。 表视图可以在其行中显示属性的值或脚本的值（不在示例中显示）。

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

以下 XML 元素可用于为行提供定义：

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素及其子元素定义在表的行中显示的内容。

- [TableRowEntry](./listentry-element-for-listcontrol-format.md)元素提供行的定义。 至少需要一个[TableRowEntry](./listentry-element-for-listcontrol-format.md) ;但是，可以添加的元素数没有最大限制。 在大多数情况下，视图将只有一个定义。

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素指定由特定定义显示的对象。 此元素是可选的，仅当定义显示不同对象的多个[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素时才需要此元素。

- [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)元素指定超出列宽的文本显示在下一行。 默认情况下，超过列宽的文本将被截断。

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)元素定义其值显示在行中的属性或脚本。

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义其值显示在行的列中的属性或脚本。 行的每个列都需要一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。 第一项显示在第一列中，第二项显示在第二列，依此类推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示在行中的属性。 您必须指定属性或脚本，但不能同时指定两者。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值在行中显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

- "格式[字符串](./label-element-for-listitem-for-listcontrol-format.md)" 元素指定定义如何显示属性或脚本值的格式模式。 此元素为可选元素。

- [对齐](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定属性或脚本的值的显示方式。 值可以左对齐、右对齐或居中对齐。 此元素为可选元素。

## <a name="defining-the-objects-that-use-the-table-view"></a>定义使用表视图的对象

可以通过两种方法来定义哪些 .NET 对象使用表视图。 您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可由视图的所有定义显示的对象，也可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义由视图的特定定义显示的对象。 在大多数情况下，视图只有一个定义，因此对象通常由[ViewSelectedBy](./viewselectedby-element-format.md)元素定义。

下面的示例演示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定义表视图显示的对象。 对于您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素的数量没有限制，它们的顺序并不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

以下 XML 元素可用于指定表视图所使用的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的 .net 对象。 完全限定的 .NET 类型名称是必需的。 您必须为视图指定至少一个类型或选择集，但没有可指定的最大元素数。

下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。 使用选择集，其中有一组使用多个视图显示的相关对象，例如为同一对象定义列表视图和表视图。 有关如何创建选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

以下 XML 元素可用于指定列表视图所使用的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定可由视图显示的一组对象。 您必须为视图指定至少一个选择集或类型，但没有可指定的最大元素数。

下面的示例演示如何使用[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素定义表视图的特定定义显示的对象。 使用此元素，可以指定对象的 .NET 类型名称、对象的选择集或指定何时使用定义的选择条件。 有关如何创建选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

> [!NOTE]
> 创建表视图的多个定义时，不能指定不同的列标题。 您只能指定在表的行中显示的内容，例如显示的对象。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

以下 XML 元素可用于指定列表视图的特定定义所使用的对象：

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素定义由定义显示的对象。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定由定义显示的 .net 对象。 使用此元素时，必须提供完全限定的 .NET 类型名称。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定可由此定义显示的一组对象。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定必须存在的条件才能使用此定义。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。 有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="using-format-strings"></a>使用格式字符串

可以将字符串的格式添加到视图中，以便进一步定义数据的显示方式。 下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

以下 XML 元素可用于指定格式模式：

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义其值显示在行的列中的属性或脚本。 行的每个列都需要一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。 第一项显示在第一列中，第二项显示在第二列，依此类推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示在行中的属性。 您必须指定属性或脚本，但不能同时指定两者。

- "格式[字符串](./label-element-for-listitem-for-listcontrol-format.md)" 元素指定定义如何显示属性或脚本值的格式模式。

在下面的示例中，调用 `ToString` 方法来设置脚本的值的格式。 脚本可以调用对象的任何方法。 因此，如果对象具有具有格式参数的方法（如 `ToString`），则脚本可以调用该方法来设置脚本的输出值的格式。

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

以下 XML 元素可用于调用 `ToString` 方法：

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义其值显示在行的列中的属性或脚本。 行的每个列都需要一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素。 第一项显示在第一列中，第二项显示在第二列，依此类推。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值在行中显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

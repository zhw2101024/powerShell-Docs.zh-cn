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
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861493"
---
# <a name="creating-a-table-view"></a>创建表视图

表视图中一个或多个列中显示数据。 表中的每一行表示一个.NET 对象，对象和表的每个列表示的对象或脚本值的属性。 可以定义显示的对象的所有属性或对象的属性的子集的表视图。

## <a name="a-table-view-display"></a>表视图显示

下面的示例演示如何显示 Windows PowerShell [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 此对象，Windows PowerShell 已定义显示的表视图`Status`属性，`Name`属性 (此属性是别名属性`ServiceName`属性)，和`DisplayName`属性。 在表中的每一行表示 cmdlet 返回的对象。

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>定义表视图

下面的 XML 演示用于显示的表视图架构[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象。 必须指定想要在表视图中显示每个属性。

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

- [视图](./view-element-format.md)元素是表视图的父元素。 （这是列表中，宽，和自定义控件视图的相同父元素）。

- [名称](./name-element-for-view-format.md)元素指定的视图的名称。 此元素是必需的所有视图。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。 此元素是必需的。

- [GroupBy](./groupby-element-for-view-format.md)元素 （不在此示例中所示） 定义何时显示新组的对象。 特定属性或脚本的值发生更改时启动新的组。 此元素是可选的。

- [控件](./controls-element-for-view-format.md)元素 （不在此示例中所示） 定义的自定义控件定义的表视图。 控件提供了一种方法，以便进一步指定如何显示数据。 此元素是可选的。 视图可以定义自己的自定义控件或它可以使用可由任意视图中的格式设置文件的公共控件。 有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

- [HideTableHeaders](./hidetableheaders-element-format.md)元素 （不显示在此示例中） 指定的表不会显示任何标签，在表的顶部。 此元素是可选的。

- [TableControl](./tablecontrol-element-format.md)元素，用于定义表的标头和行信息。 与所有其他视图类似，表视图可以显示对象属性的值或由脚本生成的值。

## <a name="defining-column-headers"></a>定义列标题

1. [TableHeaders](./tableheaders-element-format.md)元素及其子元素定义的表的顶部显示的内容。

2. [TableColumnHeader](./tablecolumnheader-element-format.md)元素定义的表的列的顶部显示的内容。 你想显示的标头的顺序指定这些元素。

   可以使用这些元素的数目，但数没有限制[TableColumnHeader](./tablecolumnheader-element-format.md)在表视图中的元素的数目必须相等[TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)您使用的元素。

3. [标签](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定显示的文本。 此元素是可选的。

4. [宽度](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定的列的宽度 （以字符为单位）。 此元素是可选的。

5. [对齐](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)元素指定标签的显示方式。 可以向左到右对齐或居中标签。 此元素是可选的。

## <a name="defining-the-table-rows"></a>定义的表行

表视图可以提供一个或多个定义，指定显示的数据的表的行中使用的子元素[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素。 请注意，您可以指定多个定义的行的表，但行的标头将保持不变，无论使用何种行定义。 通常情况下，表会将只有一个定义。

在以下示例中，视图提供了显示的多个属性的值的单个定义[System.Diagnostics.Process？Displayproperty =](/dotnet/api/System.Diagnostics.Process)对象。 表视图，可以在其行中显示的属性的值或脚本 （在示例中未显示） 的值。

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

以下 XML 元素可以用于提供定义的行：

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md)元素及其子元素定义的表的行中显示的内容。

- [TableRowEntry](./listentry-element-for-listcontrol-format.md)元素提供的行的定义。 至少一个[TableRowEntry](./listentry-element-for-listcontrol-format.md)是必需的; 但是，没有任何可以添加的元素数目的最大限制。 在大多数情况下，将具有只有一个定义的视图。

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素指定所显示的特定定义的对象。 此元素是可选的仅当定义多个需要[TableRowEntry](./listentry-element-for-listcontrol-format.md)元素，用于显示不同的对象。

- [包装](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)元素指定，在下一行显示超过列宽的文本。 默认情况下，超过列宽的文本将被截断。

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)元素定义的属性或其值显示的行中的脚本。

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义的属性或其值显示在一行的列中的脚本。 一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素是必需的行的每个列。 第一个条目显示在第一列，第二个条目中的第二个列，依此类推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定的行中显示其值的属性。 必须指定一个属性或脚本，但不能同时指定。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示的行中的脚本。 必须指定一个脚本或属性，但不能同时指定。

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md)元素指定的格式模式，它定义如何显示的属性或脚本的值。 此元素是可选的。

- [对齐](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定的属性或脚本的值的显示方式。 值可以是左到右对齐或居中。 此元素是可选的。

## <a name="defining-the-objects-that-use-the-table-view"></a>定义使用表视图的对象

有两种方法定义的.NET 对象使用表视图。 可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可显示的视图，或者您的所有定义的对象可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义将显示哪些对象将视图的特定定义。 在大多数情况下，视图具有只有一个定义，因此对象通常由定义[ViewSelectedBy](./viewselectedby-element-format.md)元素。

下面的示例演示如何定义表视图使用显示的对象[ViewSelectedBy](./viewselectedby-element-format.md)并[TypeName](./typename-element-for-viewselectedby-format.md)元素。 数量没有限制[TypeName](./typename-element-for-viewselectedby-format.md)元素可以指定和其顺序并不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

以下 XML 元素可以用于指定使用的表视图的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定.NET 对象，该视图显示对象。 完全限定的.NET 类型名称是必需的。 必须指定至少一个类型或所选内容设置对于视图，但可以指定的元素没有最大数目。

下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)并[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。 使用的选项集，其中有一组相关的相同对象使用多个视图，例如何时定义列表视图和表视图，显示的对象。 有关如何创建选项集的详细信息，请参阅[定义的选项集，](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

以下 XML 元素可以用于指定使用列表视图的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定一组视图可以显示的对象。 必须指定至少一个选择集或类型视图，但可以指定的元素没有最大数目。

下面的示例演示如何定义表视图使用的特定定义所显示的对象[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素。 使用此元素，可以指定将对象、 选择一组对象或选择条件，指定当使用定义的.NET 类型名称。 有关如何创建所选条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

> [!NOTE]
> 创建多个定义的表视图时不能指定不同的列标题。 您可以指定仅中显示的内容的行的表，例如显示哪些对象。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

以下 XML 元素可以用于指定使用特定的列表视图中定义的对象：

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)元素定义在定义将显示哪些对象。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定显示定义的.NET 对象。 使用此元素，完全限定的.NET 类型名称时，所需。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定一组可显示的此定义的对象。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定要使用此定义中必须存在的条件。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。 有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="using-format-strings"></a>使用格式字符串

可以为视图，以进一步定义数据的显示方式添加格式设置字符串。 下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

可以使用以下 XML 元素来指定格式模式：

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义的属性或其值显示在一行的列中的脚本。 一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素是必需的行的每个列。 第一个条目显示在第一列，第二个条目中的第二个列，依此类推。

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定的行中显示其值的属性。 必须指定一个属性或脚本，但不能同时指定。

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md)元素指定的格式模式，它定义如何显示的属性或脚本的值。

在以下示例中，`ToString`调用方法来设置脚本的值的格式。 脚本可以调用一个对象的任何方法。 因此，如果对象具有一种方法，如`ToString`，具有格式设置参数，该脚本可以调用该方法，以设置脚本的输出值的格式。

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

下面的 XML 元素可用于调用`ToString`方法：

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素定义的属性或其值显示在一行的列中的脚本。 一个[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)元素是必需的行的每个列。 第一个条目显示在第一列，第二个条目中的第二个列，依此类推。

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)元素指定其值显示的行中的脚本。 必须指定一个脚本或属性，但不能同时指定。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

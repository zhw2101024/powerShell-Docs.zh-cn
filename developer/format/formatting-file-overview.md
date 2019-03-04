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
# <a name="formatting-file-overview"></a>格式设置文件概述

由命令 （cmdlet、 函数和脚本） 返回的对象的显示格式使用定义的格式设置文件 （format.ps1xml 文件）。 多个这些文件提供的 PowerShell，若要定义由提供 PowerShell 命令，如返回这些对象的显示格式[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象返回的`Get-Process`cmdlet。 但是，您还可以创建自己的自定义格式设置文件以覆盖默认显示格式，也可以编写自定义格式设置文件来定义自己的命令返回的对象的显示。

> [!IMPORTANT]
> 格式设置文件不用于确定返回到管道对象的元素。 当对象返回到管道时，该对象的所有成员都都可用，即使某些未显示。

PowerShell 将使用这些格式设置文件中的数据来确定显示的内容和显示的数据的格式设置方式。 在显示的数据可以包括对象的属性或脚本的值。 如果你想要显示某些值不是可直接从一个对象，如添加两个对象的属性的值并在一段数据以显示总和的属性，则使用脚本。 显示数据的格式设置，可以定义要显示在对象的视图。 可以定义每个对象的单个视图，可以定义多个对象的单一视图也可以定义相同的对象的多个视图。 可以定义的视图数目没有限制。

## <a name="common-features-of-formatting-files"></a>格式设置文件的常用功能

每个格式设置文件可以定义可在文件中定义的所有视图之间共享的以下组件：

- 默认配置设置，如是否显示在表中的行中的数据将显示在下一行数据是否超过了列的宽度。 有关这些设置的详细信息，请参阅[定义常见的配置设置](./defining-common-configuration-features.md)。

- 任何的组格式设置文件的视图可以显示的对象。 有关这些集的详细信息 (称为*选集*)，请参阅[定义设置的对象](./defining-selection-sets.md)。

- 可由格式设置文件的所有视图的公共控件。 控件提供了更精确的控制数据的显示方式。 有关控件的详细信息，请参阅[定义自定义控件](./creating-custom-controls.md)。

## <a name="formatting-views"></a>格式设置的视图

格式设置的视图可以显示在表格格式、 列表格式、 宽格式和自定义格式的对象。 大多数情况下，由一组对视图进行说明的 XML 标记描述每个格式设置的定义。 每个视图包含视图的名称使用视图和视图，如表视图的列和行信息的元素的对象。

表视图列出了对象或一个或多个列中的脚本块值的属性。 每个列表示对象或脚本值的单个的属性。 可以定义显示的对象的对象或属性和脚本值的组合的属性子集的所有属性的表视图。 表的每一行表示一个返回的对象。 创建表视图是非常类似于当你通过管道将对象`Format-Table`cmdlet。 有关此视图的详细信息，请参阅[表视图](./creating-a-table-view.md)。

列表视图还列出了对象或单个列中的脚本值的属性。 列表的每行显示的可选标签或属性名称后面跟的属性或脚本的值。 创建列表视图是非常类似于通过管道将对象与`Format-List`cmdlet。 有关此视图的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

宽视图列出了对象或一个或多个列中的脚本值的单个属性。 没有标签或此视图的标头。 创建较宽的视图是非常类似于通过管道将对象与`Format-Wide`cmdlet。 有关此视图的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。

自定义视图显示不符合的表视图、 列表视图或宽视图刚性结构的可自定义视图的对象属性或脚本的值。 可以定义独立的自定义视图，也可以定义由另一个视图，如表视图或列表视图的自定义视图。 创建自定义视图是非常类似于通过管道将对象与`Format-Custom`cmdlet。 有关此视图的详细信息，请参阅[的自定义视图](./creating-custom-controls.md)。

## <a name="components-of-a-view"></a>视图的组件

以下 XML 示例显示一个视图的基本 XML 组件。 但是，单个 XML 元素不同你想要创建，具体取决于哪种视图是相同的视图的基本组件。

开始时，每个视图具有`Name`元素，它指定用于引用该视图的用户友好名称。 `ViewSelectedBy`元素，用于定义视图中，将显示的.NET 对象和一个*控制*元素定义的视图。

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

在控件元素中，可以定义一个或多个*条目*元素。 如果使用多个定义，则必须指定的.NET 对象使用的每个定义。 通常只有一个条目，只有一个定义，需要为每个控件。

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

在视图的每个输入元素，可以指定*项*元素定义的.NET 属性或由该视图显示的脚本。

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

前面的示例中所示，该格式设置文件可以包含多个视图、 视图可以包含多个定义和每个定义可以包含多个项。

## <a name="example-of-a-table-view"></a>表视图的示例

下面的示例演示用于定义包含两个列的表视图的 XML 标记。 [ViewDefinitions](./viewdefinitions-element-format.md)元素是格式设置文件中定义的所有视图的容器元素。 [视图](./view-element-format.md)元素定义特定的表、 列表、 宽，或自定义视图。 在每个[视图](./view-element-format.md)元素，[名称](./name-element-for-view-format.md)元素指定视图的名称[ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用的视图，和不同的对象控制元素 (如`TableControl`元素下面的示例中所示) 定义视图的类型。

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

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[创建表视图](./creating-a-table-view.md)

[创建较宽的视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[编写的 PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)

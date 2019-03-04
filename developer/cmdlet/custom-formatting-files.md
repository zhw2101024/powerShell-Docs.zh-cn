---
title: 自定义格式设置文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860603"
---
# <a name="custom-formatting-files"></a>自定义格式设置文件

使用格式设置文件 （format.ps1xml 文件） 进行定义的 cmdlet、 函数和脚本返回的对象的显示格式。 多个这些文件提供了 Windows PowerShell，若要定义由 Windows PowerShell cmdlet 返回这些对象的默认显示格式。 但是，您还可以创建自己的自定义格式设置文件以覆盖默认显示格式，或若要定义自己的命令返回的对象的显示。

Windows PowerShell 将使用这些格式设置文件中的数据来确定显示的内容和设置数据的格式。 在显示的数据可以包括对象的属性或脚本块的值。  如果你想要显示某些值不是可直接从对象的属性，则使用脚本块。 例如，你可能想要添加两个对象的属性的值并显示为一个单独的数据的总和。 在编写您自己的格式文件时，你将需要定义*视图*你想要显示的对象。 可以定义每个对象的单个视图，可以定义多个对象的单一视图也可以定义相同的对象的多个视图。 可以定义的视图数目没有限制。

> [!IMPORTANT]
> 格式设置文件不用于确定返回到管道对象的元素。 当对象返回到管道时，该对象的所有成员都都可用。

## <a name="format-views"></a>设置视图的格式

格式设置的视图可以显示在表格格式、 以列表格式、 宽格式和自定义格式的对象。 大多数情况下，由一组描述视图的 XML 标记描述每个格式设置的定义。 每个视图包含视图的名称使用视图和视图，如表视图的列和行信息的元素的对象。

提供了以下视图。

表视图列出了对象或一个或多个列中的脚本块值的属性。 每个列表示的对象或脚本块值的属性。 可以定义显示的对象的对象或属性和脚本块值的组合的属性子集的所有属性的表视图。 表的每一行表示一个返回的对象。 有关此视图的详细信息，请参阅[表视图](../format/creating-a-table-view.md)。

列表视图列出了对象或单个列中的脚本块值的属性。 列表的每行显示的可选标签或跟属性或脚本块的值的属性名称。 有关此视图的详细信息，请参阅[列表视图](../format/creating-a-list-view.md)。

宽视图列出了对象或一个或多个列中的脚本块值的单个属性。 没有标签或此视图的标头。 有关此视图的详细信息，请参阅[宽视图](../format/creating-a-wide-view.md)。

自定义视图显示不符合的表视图、 列表视图或宽视图刚性结构的可自定义视图的对象属性或脚本块值。 可以定义独立的自定义视图，也可以定义由另一个视图，如表视图或列表视图的自定义视图。 有关此视图的详细信息，请参阅[的自定义视图](../format/creating-custom-controls.md)。

## <a name="view-xml-elements"></a>查看 XML 元素

下面的示例演示用于定义包含两个列的表视图的 XML 标记。 [ViewDefinitions](../format/viewdefinitions-element-format.md)元素是格式设置文件中定义的所有视图的容器元素。 [视图](../format/view-element-format.md)元素定义特定的表、 列表、 宽，或自定义视图。 在每个视图中，[名称](../format/name-element-for-view-format.md)元素指定的视图名称[ViewSelectedBy](../format/viewselectedby-element-format.md)元素定义使用的视图和不同的控件元素的对象 (如`TableControl`元素） 定义的视图格式。

```xml
ViewDefinitions
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

[表视图](../format/creating-a-table-view.md)

[列表视图](../format/creating-a-list-view.md)

[宽的视图](../format/creating-a-wide-view.md)

[自定义视图](../format/creating-custom-controls.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

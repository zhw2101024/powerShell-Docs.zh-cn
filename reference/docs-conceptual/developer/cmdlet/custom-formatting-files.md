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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369826"
---
# <a name="custom-formatting-files"></a>自定义格式设置文件

Cmdlet、函数和脚本返回的对象的显示格式是使用格式设置文件（types.ps1xml 文件）定义的。 Windows PowerShell 会提供其中几个文件来定义 Windows PowerShell cmdlet 返回的这些对象的默认显示格式。 但是，您还可以创建自己的自定义格式设置文件来覆盖默认显示格式，或定义您自己的命令返回的对象的显示。

Windows PowerShell 使用这些格式设置文件中的数据来确定显示的内容以及如何设置数据的格式。 显示的数据可以包括对象的属性或脚本块的值。  如果希望显示某个不能直接从对象的属性中使用的值，则使用脚本块。 例如，你可能想要添加一个对象的两个属性的值，并将 sum 显示为单独的数据片段。 编写您自己的格式化文件时，需要为要显示的对象定义*视图*。 您可以为每个对象定义一个视图，可以为多个对象定义一个视图，也可以为同一对象定义多个视图。 您可以定义的视图数没有限制。

> [!IMPORTANT]
> 格式化文件不确定返回到管道的对象的元素。 当对象返回到管道时，该对象的所有成员都可用。

## <a name="format-views"></a>格式视图

格式视图可按表格式显示对象、列表格式、宽格式和自定义格式。 大多数情况下，每个格式设置定义由一组描述视图的 XML 标记来描述。 每个视图都包含视图的名称、使用该视图的对象和视图的元素，例如表视图的列和行信息。

以下视图可用。

表视图在一个或多个列中列出对象或脚本块值的属性。 每个列表示对象的一个属性或一个脚本块值。 您可以定义显示对象的所有属性的表视图、对象属性的子集或属性和脚本块值的组合。 表中的每一行都表示一个返回的对象。 有关此视图的详细信息，请参阅[表视图](../format/creating-a-table-view.md)。

列表视图在单个列中列出对象或脚本块值的属性。 列表中的每一行都显示一个可选标签或属性名称，后跟属性或脚本块的值。 有关此视图的详细信息，请参阅[列表视图](../format/creating-a-list-view.md)。

宽视图列出对象的单个属性或一个或多个列中的脚本块值。 此视图没有标签或标题。 有关此视图的详细信息，请参阅[宽视图](../format/creating-a-wide-view.md)。

自定义视图显示对象属性或脚本块值的可自定义视图，这些视图不遵守严格的表视图、列表视图或宽视图结构。 您可以定义一个独立的自定义视图，也可以定义另一个视图使用的自定义视图，如表视图或列表视图。 有关此视图的详细信息，请参阅[自定义视图](../format/creating-custom-controls.md)。

## <a name="view-xml-elements"></a>查看 XML 元素

下面的示例显示用于定义包含两个列的表视图的 XML 标记。 [ViewDefinitions](../format/viewdefinitions-element-format.md)元素是在格式设置文件中定义的所有视图的容器元素。 [View](../format/view-element-format.md)元素定义特定的表、列表、宽视图或自定义视图。 在每个视图中， [name](../format/name-element-for-view-format.md)元素指定视图的名称， [ViewSelectedBy](../format/viewselectedby-element-format.md)元素定义使用视图的对象，不同的控件元素（例如 `TableControl` 元素）定义视图的格式。

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

[宽视图](../format/creating-a-wide-view.md)

[自定义视图](../format/creating-custom-controls.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

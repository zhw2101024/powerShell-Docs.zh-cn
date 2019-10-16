---
title: 配置元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363496"
---
# <a name="configuration-element-format"></a>Configuration Element (Format)

表示格式设置文件的顶级元素。

配置元素

## <a name="syntax"></a>语法

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Configuration` 元素的属性、子元素和父元素。 此元素必须是每个格式化文件的根元素，并且此元素必须包含至少一个子元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于配置的 Controls 元素（格式）](./controls-element-for-configuration-format.md)|可选元素。<br /><br /> 定义可供格式设置文件的所有视图使用的公共控件。|
|[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)|可选元素。<br /><br /> 定义适用于格式设置文件的所有视图的常见设置。|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|可选元素。<br /><br /> 定义可供格式设置文件的所有视图使用的常用 .NET 对象集。|
|[ViewDefinitions 元素（格式）](./viewdefinitions-element-format.md)|可选元素。<br /><br /> 定义用于显示对象的视图。|

### <a name="parent-elements"></a>父元素

无。

## <a name="remarks"></a>备注

格式化文件定义对象的显示方式。 在大多数情况下，此根元素包含一个[ViewDefinitions](./viewdefinitions-element-format.md)元素，该元素定义格式设置文件的表、列表和宽视图。 除了视图定义以外，格式设置文件还可以定义这些视图可以使用的常用选择集、设置和控件。

## <a name="see-also"></a>另请参阅

[用于配置的 Controls 元素（格式）](./controls-element-for-configuration-format.md)

[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)

[SelectionSets 元素（格式）](./selectionsets-element-format.md)

[ViewDefinitions 元素（格式）](./viewdefinitions-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

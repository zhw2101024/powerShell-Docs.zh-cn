---
title: 用于配置的控件（格式）的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364026"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem Element for CustomEntry for Controls for Configuration (Format)

定义控件显示的数据及其显示方式。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for configuration （Format） CustomItem 元素 for CustomEntry for control for control 的控件

## <a name="syntax"></a>语法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomItem` 元素的属性、子元素和父元素。 有关详细信息，请参阅 "备注"。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义控件显示的数据。|
|[用于配置的控件的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 定义数据的显示方式，例如，将数据向左或向右移动。|
|[用于配置的控件的 CustomItem 的换行符元素（格式）](./newline-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 向控件的显示添加一个空白行。|
|[用于配置的控件的 CustomItem 的文本元素（格式）](./text-element-for-customitem-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 向控件的显示添加文本，如括号或方括号。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

指定 `CustomItem` 元素的子元素时，请记住以下事项：

- 必须按以下顺序添加子元素： `ExpressionBinding`、`NewLine`、`Text`和 `Frame`。

- 您可以指定的序列数量没有最大限制。

- 在每个序列中，可使用的 `ExpressionBinding` 元素数没有最大限制。

## <a name="see-also"></a>另请参阅

[用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[用于配置的控件的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[用于配置的控件的 CustomItem 的换行符元素（格式）](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[用于配置的控件的 CustomItem 的文本元素（格式）](./text-element-for-customitem-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

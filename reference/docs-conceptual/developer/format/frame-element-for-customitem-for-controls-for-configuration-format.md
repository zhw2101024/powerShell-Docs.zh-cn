---
title: 用于配置控件的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363656"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame Element for CustomItem for Controls for Configuration (Format)

定义数据的显示方式，例如，将数据向左或向右移动。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for 元素 for for CustomItem for control 的控件

## <a name="syntax"></a>语法

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Frame` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|必需的元素|
|[用于配置的控件的框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定将第一行数据向左移动的字符数。|
|[用于配置的控件的框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定第一行数据向右移动的字符数。|
|[用于配置的控件的框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定数据从左边距向外移动的字符数。|
|[用于配置的控件的框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|可选元素。<br /><br /> 指定数据从右边缘向外移动的字符数。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置控件的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定义控件显示的数据及其显示方式。|

## <a name="remarks"></a>备注

不能在同一个 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)元素。

## <a name="see-also"></a>另请参阅

[用于配置的控件的框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[用于配置的控件的框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[用于配置的控件的框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[用于配置的控件的框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[用于配置控件的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

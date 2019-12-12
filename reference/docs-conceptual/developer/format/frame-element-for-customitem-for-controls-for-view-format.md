---
title: 用于视图（格式）的控件的 CustomItem 的框架元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363646"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame Element for CustomItem for Controls for View (Format)

定义数据的显示方式，例如，将数据向左或向右移动。 定义可由视图使用的控件时，将使用此元素。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for for view （format）元素 for view （format）

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
|[视图控件的框架的 FirstLineHanging 元素（Format）](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定第一行向左移动的字符数。|
|[视图控件的框架的 FirstLineIndent 元素（Format）](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定第一行向右移动的字符数。|
|[视图控件的框架的 LeftIndent 元素（Format）](./leftindent-element-for-frame-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定数据从左边距向外移动的字符数。|
|[视图控件的框架的 RightIndent 元素（Format）](./rightindent-element-for-frame-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定数据从右边缘向外移动的字符数。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)|定义控件显示的数据及其显示方式。|

## <a name="remarks"></a>备注

不能在同一个 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。

## <a name="see-also"></a>另请参阅

[视图控件的框架的 FirstLineHanging 元素（Format）](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[视图控件的框架的 FirstLineIndent 元素（Format）](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[视图控件的框架的 LeftIndent 元素（Format）](./leftindent-element-for-frame-for-controls-for-view-format.md)

[视图控件的框架的 RightIndent 元素（Format）](./rightindent-element-for-frame-for-controls-for-view-format.md)

[用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

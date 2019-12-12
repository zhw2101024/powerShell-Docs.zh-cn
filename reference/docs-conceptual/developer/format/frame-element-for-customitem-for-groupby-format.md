---
title: GroupBy （格式）的 CustomItem 的框架元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362946"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame Element for CustomItem for GroupBy (Format)

定义数据的显示方式，例如，将数据向左或向右移动。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）用于 CustomEntry for groupby 的 for groupby （format） CustomItem 元素的 CustomControl （format）

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
|[GroupBy 的帧的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-groupby-format.md)|可选元素。<br /><br /> 指定将第一行数据向左移动的字符数。|
|[GroupBy 的帧的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-groupby-format.md)|可选元素。<br /><br /> 指定第一行数据向右移动的字符数。|
|[GroupBy 的帧的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-groupby-format.md)|可选元素。<br /><br /> 指定数据从左边距向外移动的字符数。|
|[GroupBy 的帧的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素|可选元素。<br /><br /> 指定数据从右边缘向外移动的字符数。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)|定义控件显示的数据及其显示方式。|

## <a name="remarks"></a>备注

不能在同一个 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。

## <a name="see-also"></a>另请参阅

[GroupBy 的帧的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy 的帧的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy 的帧的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy 的帧的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

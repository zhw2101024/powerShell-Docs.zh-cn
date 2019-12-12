---
title: GroupBy （Format）框架的 FirstLineHanging 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363816"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging Element for Frame for GroupBy (Format)

指定将第一行数据向左移动的字符数。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）用于 CustomEntry for groupby （format） CustomItem 元素的 CustomControl for groupby （format）元素，用于 groupby 的帧的的元素（格式）

## <a name="syntax"></a>语法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `FirstLineHanging` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)|定义数据的显示方式，例如，将数据向左或向右移动。|

## <a name="text-value"></a>文本值

指定要将数据的第一行移动到的字符数。

## <a name="remarks"></a>备注

如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。

## <a name="see-also"></a>另请参阅

[GroupBy 的帧的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

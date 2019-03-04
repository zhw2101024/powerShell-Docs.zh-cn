---
title: GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854293"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName Element for ExpressionBinding for GroupBy (Format)

指定公共控件或视图控件的名称。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl ExpressionBinding 的 GroupBy （格式） 的 GroupBy （格式） CustomControlName 元素 CustomItem GroupBy （格式） ExpressionBinding 元素 CustomEntry GroupBy （格式） CustomItem 元素

## <a name="syntax"></a>语法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`CustomControlName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)|定义由控件显示的数据。|

## <a name="text-value"></a>文本值

指定控件的名称。

## <a name="remarks"></a>备注

可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。 以下元素指定这些控件的名称：

- [配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)

- [控件的视图 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)

[控件的视图 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy （格式） 的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

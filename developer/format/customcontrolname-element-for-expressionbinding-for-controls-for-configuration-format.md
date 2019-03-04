---
title: 配置 （格式） 的控件的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856313"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)

指定公共控件的名称。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl 配置 （格式） 的控件的 Controls 的配置 （格式） CustomControlName CustomItem 配置 ExpressionBinding 元素 CustomEntry CustomItem 元素的控件的格式） CustomEntry 元素ExpressionBinding 的配置 （格式） 的控件的元素

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
|[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定义由控件显示的数据。|

## <a name="text-value"></a>文本值

指定控件的名称。

## <a name="remarks"></a>备注

可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。 以下元素指定这些控件的名称：

- [配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)

- [控件的视图 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)

[控件的视图 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-view-format.md)

[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

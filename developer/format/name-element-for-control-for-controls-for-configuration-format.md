---
title: 命名元素的控件的控件配置 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065183"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Name Element for Control for Controls for Configuration (Format)

指定控件的名称。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （格式） 的控件的控件的名称元素的控件的控件元素的配置元素 （格式） 的 Controls 元素

## <a name="syntax"></a>语法

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`Name`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的控件元素](./control-element-for-controls-for-configuration-format.md)|定义可由格式设置文件和名称，用于引用该控件的所有视图的公共控件。|

## <a name="text-value"></a>文本值

指定用于引用此控件的名称。

## <a name="remarks"></a>备注

此处指定的名称可以在以下元素中，用于引用此控件。

- 在创建表、 列表、 宽或自定义控件视图时，可以通过下面的元素指定的控件：[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

- 在创建另一个常见的控件时，此控件可以指定由以下元素：[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- 当创建控件可以使用的视图时，此控件可以指定由以下元素：[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的控件元素](./control-element-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

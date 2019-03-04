---
title: 配置 （格式） 的控件的控件元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858883"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control Element for Controls for Configuration (Format)

定义可由格式设置文件和名称，用于引用该控件的所有视图的公共控件。

配置 （格式） 的配置 （格式） 的控件的控件元素的配置元素 （格式） 的 Controls 元素

## <a name="syntax"></a>语法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和的父元素`Control`元素。 必须指定每个子元素之一。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[配置 （格式） 的控件的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 定义控件。|
|[配置 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 指定用来引用该控件的名称。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[控件元素的配置 （格式）](./controls-element-for-configuration-format.md)|定义由格式设置文件的所有视图或其他控件可以使用的公共控件。|

## <a name="remarks"></a>备注

可以在以下元素中引用提供给此控件的名称：

- [ExpressionBinding CustomItem （格式） 的元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [View(Format) 的 GroupBy 元素](./groupby-element-for-view-format.md)

## <a name="see-also"></a>另请参阅

[控件元素的配置 （格式）](./controls-element-for-configuration-format.md)

[配置 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding CustomItem （格式） 的元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[View(Format) 的 GroupBy 元素](./groupby-element-for-view-format.md)

[配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

---
title: GroupBy （格式） 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066528"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName Element for GroupBy (Format)

指定用来显示新组的自定义控件的名称。 定义表、 列表、 宽或自定义控件视图时，将使用此元素。

GroupBy （格式） 的视图 （格式） CustomControlName 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述的特性、 子元素和父元素的`CustomControlName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定义 Windows PowerShell 如何显示对象的新的组。|

## <a name="text-value"></a>文本值

指定用来显示新组的自定义控件的名称。

## <a name="remarks"></a>备注

可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。 以下元素指定这些自定义控件的名称：

- [配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)

- [控件的视图 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[配置 （格式） 的控件的控件的名称元素](./name-element-for-control-for-controls-for-configuration-format.md)

[控件的视图 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

---
title: 命名元素的控件的控件视图 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065083"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name Element for Control for Controls for View (Format)

指定控件的名称。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 元素 （格式） 控件的 Controls 元素的控件视图 （格式） 名称元素控件视图 （格式）

## <a name="syntax"></a>语法

```xml
<Name>ControlName</Name>
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
|[视图 （格式） 的控件的控件元素](./control-element-for-controls-for-view-format.md)|定义可由该视图和用于引用该控件的名称的控件。|

## <a name="text-value"></a>文本值

指定用来引用该控件的名称。

## <a name="remarks"></a>备注

此处指定的名称可以在以下元素中，用于引用此控件。

- 在创建表、 列表、 宽或自定义控件视图时，可以通过下面的元素指定的控件：[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

- 当创建另一个控件，可以使用的视图时，此控件可以指定由以下元素：[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[视图 （格式） 的控件的控件元素](./control-element-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

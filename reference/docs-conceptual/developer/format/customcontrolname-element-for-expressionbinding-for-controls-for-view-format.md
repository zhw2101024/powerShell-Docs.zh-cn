---
title: 用于视图（格式）的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369146"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>CustomControlName Element for ExpressionBinding for Controls for View (Format)

指定公共控件或视图控件的名称。 定义可由视图使用的控件时，将使用此元素。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for ExpressionBinding for view （format）View 的 ExpressionBindine 的元素（格式）

## <a name="syntax"></a>语法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomControlName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定义控件显示的数据。|

## <a name="text-value"></a>文本值

指定控件的名称。

## <a name="remarks"></a>备注

您可以创建可供格式设置文件的所有视图使用的公共控件，还可以创建可供特定视图使用的视图控件。 以下元素指定这些控件的名称：

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

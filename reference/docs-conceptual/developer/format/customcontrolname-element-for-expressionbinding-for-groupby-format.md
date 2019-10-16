---
title: GroupBy （Format）的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368906"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName Element for ExpressionBinding for GroupBy (Format)

指定公共控件或视图控件的名称。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for CustomItem for groupby （format） CustomControlName 元素 for groupby （Format）

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
|[GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)|定义控件显示的数据。|

## <a name="text-value"></a>文本值

指定控件的名称。

## <a name="remarks"></a>备注

您可以创建可供格式设置文件的所有视图使用的公共控件，还可以创建可供特定视图使用的视图控件。 以下元素指定这些控件的名称：

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

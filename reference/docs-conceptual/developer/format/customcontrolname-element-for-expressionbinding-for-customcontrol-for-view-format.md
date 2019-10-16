---
title: 用于 CustomControl for View （Format）的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364106"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName Element for ExpressionBinding for CustomControl for View (Format)

指定公共控件或视图控件的名称。 定义自定义控件视图时，将使用此元素。

CustomEntry for view （format） CustomEntries 元素 for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format）用于 CustomItem 的表达式绑定的 CustomItem （Format） CustomControlName 元素的 CustomEntry for View （Format） ExpressionBinding 元素的元素

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
|[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定义控件显示的数据。|

## <a name="text-value"></a>文本值

指定控件的名称。

## <a name="remarks"></a>备注

您可以创建可供格式设置文件的所有视图使用的公共控件，并可以创建可供特定视图使用的视图控件。 以下元素指定这些控件的名称。

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

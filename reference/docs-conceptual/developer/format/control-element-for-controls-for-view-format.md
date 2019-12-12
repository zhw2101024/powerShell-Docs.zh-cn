---
title: 视图控件的控件元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363466"
---
# <a name="control-element-for-controls-for-view--format"></a>Control Element for Controls for View (Format)

定义可供视图使用的控件以及用于引用控件的名称。

Control 元素（Format） ViewDefinitions 元素（格式） View 元素（format） Control Control 元素 for View （format）控件元素

## <a name="syntax"></a>语法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Control` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)|必需的元素。<br /><br /> 指定控件的名称。|
|[用于控件的控件的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)|必需的元素。<br /><br /> 定义此视图使用的控件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Controls 元素（格式）](./controls-element-for-view-format.md)|定义可供特定视图使用的视图控件。|

## <a name="remarks"></a>备注

此控件可由以下元素指定：

- [用于视图的控件的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [GroupBy 的 CustomControlName 元素（Format）](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>另请参阅

[用于控件的控件的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)

[用于视图的控件的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls 元素（格式）](./controls-element-for-view-format.md)

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

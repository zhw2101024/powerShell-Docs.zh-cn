---
title: 控件元素的控件的视图 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066764"
---
# <a name="control-element-for-controls-for-view--format"></a>Control Element for Controls for View (Format)

定义可由该视图和用于引用该控件的名称的控件。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控制元素 （格式） 控件元素的控件的视图 （格式）

## <a name="syntax"></a>语法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`Control`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[控件的视图 （格式） 的名称元素](./name-element-for-control-for-controls-for-view-format.md)|必需的元素。<br /><br /> 指定控件的名称。|
|[控件的视图 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-view-format.md)|必需的元素。<br /><br /> 定义此视图使用的控件。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[控件元素 （格式）](./controls-element-for-view-format.md)|定义可由特定视图的视图控件。|

## <a name="remarks"></a>备注

此控件可以指定由以下元素：

- [ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [GroupBy （格式） 的 CustomControlName 元素](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>另请参阅

[控件的视图 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[控件元素 （格式）](./controls-element-for-view-format.md)

[控件的视图 （格式） 的控件的名称元素](./name-element-for-control-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

---
title: 用于控件的控件的名称元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362706"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Name Element for Control for Controls for Configuration (Format)

指定控件的名称。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format）名称元素控件的配置（格式）控件元素的元素，用于控件的配置（格式）

## <a name="syntax"></a>语法

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Name` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置控件的控件元素（格式）](./control-element-for-controls-for-configuration-format.md)|定义一个公共控件，该控件可供格式设置文件的所有视图和用于引用控件的名称使用。|

## <a name="text-value"></a>文本值

指定用于引用此控件的名称。

## <a name="remarks"></a>备注

此处指定的名称可以用在以下元素中以引用此控件。

- 创建表、列表、宽控件或自定义控件视图时，可通过以下元素指定控件： [view 的 GroupBy 元素（Format）](./groupby-element-for-view-format.md)

- 创建另一个公共控件时，可以通过以下元素指定此控件：用于[配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- 创建可由视图使用的控件时，可以通过以下元素指定此控件：用于视图的控件的[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[用于配置控件的控件元素（格式）](./control-element-for-controls-for-configuration-format.md)

[用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

---
title: 用于控件的控件的名称元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365096"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name Element for Control for Controls for View (Format)

指定控件的名称。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（格式）控件元素（格式）控件元素 for view （format） Name 元素（用于控件）的控件元素

## <a name="syntax"></a>语法

```xml
<Name>ControlName</Name>
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
|[视图控件的控件元素（格式）](./control-element-for-controls-for-view-format.md)|定义可供视图使用的控件以及用于引用控件的名称。|

## <a name="text-value"></a>文本值

指定用于引用控件的名称。

## <a name="remarks"></a>备注

此处指定的名称可以用在以下元素中以引用此控件。

- 创建表、列表、宽控件或自定义控件视图时，可通过以下元素指定控件： [view 的 GroupBy 元素（Format）](./groupby-element-for-view-format.md)

- 创建可由视图使用的另一个控件时，可以通过以下元素指定此控件：用于视图的[控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[视图控件的控件元素（格式）](./control-element-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

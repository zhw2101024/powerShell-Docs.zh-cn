---
title: GroupBy （格式）的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368876"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName Element for GroupBy (Format)

指定用于显示新组的自定义控件的名称。 定义表、列表、宽或自定义控件视图时，将使用此元素。

GroupBy （format）的 View （Format） CustomControlName 元素的 ViewDefinitions 元素（format） View 元素（format） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `CustomControlName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定义 Windows PowerShell 如何显示一组新的对象。|

## <a name="text-value"></a>文本值

指定用于显示新组的自定义控件的名称。

## <a name="remarks"></a>备注

您可以创建可供格式设置文件的所有视图使用的公共控件，还可以创建可供特定视图使用的视图控件。 以下元素指定这些自定义控件的名称：

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

- [用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

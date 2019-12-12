---
title: 用于配置控件的控件元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369006"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control Element for Controls for Configuration (Format)

定义一个公共控件，该控件可供格式设置文件的所有视图和用于引用控件的名称使用。

配置元素的配置元素（格式）控件元素的配置（format）控件元素的元素（格式）

## <a name="syntax"></a>语法

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Control` 元素的属性、子元素和父元素。 必须仅指定每个子元素中的一个。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于控件的控件的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 定义控件。|
|[用于控件配置的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 指定用于引用控件的名称。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Control 的 Controls 元素（格式）](./controls-element-for-configuration-format.md)|定义可由格式设置文件的所有视图或其他控件使用的公共控件。|

## <a name="remarks"></a>备注

可以在以下元素中引用为此控件指定的名称：

- [CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

## <a name="see-also"></a>另请参阅

[Control 的 Controls 元素（格式）](./controls-element-for-configuration-format.md)

[用于控件配置的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[用于控件的控件的名称元素（格式）](./name-element-for-control-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

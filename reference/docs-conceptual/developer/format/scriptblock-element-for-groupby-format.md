---
title: GroupBy （格式）的 ScriptBlock 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364926"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock Element for GroupBy (Format)

指定在新组的值发生更改时启动新组的脚本。

GroupBy 的 View （format） ScriptBlock 元素的配置元素（格式） ViewDefinitions 元素（格式） GroupBy 元素（format）

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定义一组 .NET 对象的显示方式。|

## <a name="text-value"></a>文本值

指定要评估的脚本。

## <a name="remarks"></a>备注

每当此脚本的值发生更改时，PowerShell 就会启动一个新组。

如果指定此元素，则不能指定[PropertyName](propertyname-element-for-groupby-format.md)元素来启动新组。

## <a name="see-also"></a>另请参阅

[GroupBy 的 PropertyName 元素（Format）](propertyname-element-for-groupby-format.md)

[View 的 GroupBy 元素（格式）](groupby-element-for-view-format.md)

[编写 PowerShell 格式化文件](writing-a-powershell-formatting-file.md)

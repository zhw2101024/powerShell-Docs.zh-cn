---
title: CustomControl 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368636"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock Element for SelectionCondition for CustomControl for View (Format)

指定触发条件的脚本。 如果此脚本的计算结果为 `true`，则满足条件，并使用定义。 定义自定义控件视图时，将使用此元素。

Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for EntrySelectedBy for CustomControl for SelectionCondition for CustomControl for view （format） ScriptBlock 元素 for for view （Format）

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
|[用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定义要使用的控件定义必须存在的条件。|

## <a name="text-value"></a>文本值

指定要评估的脚本。

## <a name="remarks"></a>备注

选择条件必须指定至少一个要计算的脚本或属性名称，但不能同时指定两者。 有关如何使用选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

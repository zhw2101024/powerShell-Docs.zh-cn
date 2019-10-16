---
title: ListControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362096"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ScriptBlock Element for ItemSelectionCondition for ListControl (Format)

指定触发条件的脚本。 如果此脚本的计算结果为 `true`，则满足条件，并使用列表项。 定义列表视图时，将使用此元素。

用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素的 ListControl （Format） ListEntry 元素的 Configuration Element （Format） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素对于 ItemSelectionCondition for ListControl 的 ListControl （Format） ScriptBlock 元素的 ListItems 的 ListControl （格式）列表控件（Format） ItemSelectionCondition 元素的元素

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
|[ListControl 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|定义要使用此列表项必须存在的条件。|

## <a name="text-value"></a>文本值

指定要评估的脚本。

## <a name="remarks"></a>备注

如果使用此元素，则在定义选择条件时，不能指定 `PropertyName` 元素。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

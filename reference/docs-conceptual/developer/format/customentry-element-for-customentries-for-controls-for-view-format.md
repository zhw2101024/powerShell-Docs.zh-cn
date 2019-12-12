---
title: 用于视图（格式）的 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364046"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>CustomEntry Element for CustomEntries for Controls for View (Format)

提供控件的定义。 定义可由视图使用的控件时，将使用此元素。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素视图的 CustomControl for View （Format） CustomEntry 元素 for CustomEntries for View （Format）

## <a name="syntax"></a>语法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomEntry` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。|
|[用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)|必需的元素。<br /><br /> 定义控件显示数据的方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[用于视图的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

---
title: 用于 CustomControl for View （Format）的 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364016"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>CustomEntry Element for CustomEntries for CustomControl for View (Format)

提供自定义控件视图的定义。

用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素（format）

## <a name="syntax"></a>语法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomEntry` 元素的属性、子元素和父元素。 您必须指定由定义显示的项。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|可选元素。<br /><br /> 定义使用自定义控件视图的定义或要使用此定义必须存在的条件的 .NET 类型。|
|[用于视图的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定义自定义控件定义的控件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)|提供自定义控件视图的定义。 自定义控件视图必须指定一个或多个定义。|

## <a name="remarks"></a>备注

在大多数情况下，每个自定义控件视图只需要一个定义，但如果您希望使用同一视图显示不同的 .NET 对象，则可以有多个定义。 在这些情况下，可以为每个对象或一组对象提供单独的定义。

## <a name="see-also"></a>另请参阅

[View 的 CustomControl 元素（Format）](./customcontrol-element-for-view-format.md)

[用于视图的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

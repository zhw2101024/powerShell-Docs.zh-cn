---
title: CustomEntry 的 EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368066"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>TypeName Element for EntrySelectedBy for CustomEntry for View (Format)

指定使用自定义控件视图的此定义的 .NET 类型。 对于可以为定义指定的类型数量没有限制。

用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedBy用于 CustomEntry for View （Format）的 EntrySelectedBy 的 CustomEntry for View （Format） TypeName 元素的元素

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定义使用此自定义控件视图定义或要使用此定义必须存在的条件的 .NET 类型。|

## <a name="text-value"></a>文本值

指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

每个自定义控件视图定义都必须定义至少一个类型名称、选择集或选择条件。

有关自定义控件视图组件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

## <a name="see-also"></a>另请参阅

[创建自定义控件](./creating-custom-controls.md)

[用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

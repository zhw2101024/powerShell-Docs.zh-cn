---
title: GroupBy （格式） 的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858803"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a>TypeName Element for SelectionCondition for GroupBy (Format)

指定触发条件的.NET 类型。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl SelectionCondition 为 GroupBy （格式） 的 GroupBy （格式） TypeName 元素 EntrySelectedBy GroupBy （格式） SelectionCondition 元素 CustomEntry GroupBy （格式） EntrySelectedBy 元素

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|定义必须存在要使用的控件定义的条件。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

当指定此元素时，不能指定`SelectionSetName`元素。 有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

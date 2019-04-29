---
title: TypeName 元素 WideEntry （格式） 的 EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083920"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName Element for EntrySelectedBy for WideEntry (Format)

指定定义的.NET 类型。 定义用于显示此对象时。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （WideEntry （格式） TypeName 元素格式）

## <a name="syntax"></a>语法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`TypeName`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)|定义使用此宽的项或要使用此项必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

每个宽的条目都必须指定一个或多个.NET 类型、 一个选择集或要使用的定义中必须存在的选择条件。

有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建较宽的视图](./creating-a-wide-view.md)

[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

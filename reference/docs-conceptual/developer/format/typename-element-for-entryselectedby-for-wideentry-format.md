---
title: WideEntry 的 EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361616"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName Element for EntrySelectedBy for WideEntry (Format)

为定义指定 .NET 类型。 只要显示此对象，就会使用定义。

EntrySelectedBy 的 ViewDefinitions 元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） WideEntry 元素 for WideEntry （Format） TypeName 元素 for （形式

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
|[WideEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-wideentry-format.md)|定义使用此宽项的 .NET 类型或此项要使用的条件。|

## <a name="text-value"></a>文本值

指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

每个宽条目都必须指定一个或多个 .NET 类型、选择集或必须为要使用的定义提供的选择条件。

有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建宽视图](./creating-a-wide-view.md)

[WideEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-wideentry-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

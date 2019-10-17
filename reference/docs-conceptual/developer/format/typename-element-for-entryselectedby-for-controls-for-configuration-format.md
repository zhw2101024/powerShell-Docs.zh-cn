---
title: 用于配置（格式）的控件的 EntrySelectedBy 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30bb1382-8c6b-4371-82e6-baf427fa0781
caps.latest.revision: 6
ms.openlocfilehash: cec8c5d76bded321ec1d6a1cd0409d7c88863c03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368076"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a>TypeName Element for EntrySelectedBy for Controls for Configuration (Format)

指定使用控件的此定义的 .NET 类型。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 的 CustomControl 的元素，用于配置（format）的控件的 EntrySelectedBy 元素 for CustomEntry 的元素，用于配置的控件的的元素（格式）

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
|[用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。|

## <a name="text-value"></a>文本值

指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

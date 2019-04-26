---
title: TableControl （格式） 的 EntrySelectedBy 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083954"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TypeName Element for EntrySelectedBy for TableControl (Format)

指定使用此项的表视图的.NET 类型。 可以为表条目指定的类型的数量没有限制。

元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 （格式） 类型名称的配置元素 EntrySelectedBy有关 TableRowEntry （格式）

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
|[EntrySelectedBy 元素 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定义使用此项或要使用此项必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定.NET 类型的名称。

## <a name="remarks"></a>备注

每个列表项必须具有至少一个类型名称、 选择集或定义的选择条件。

表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。

## <a name="see-also"></a>另请参阅

[创建表视图](./creating-a-table-view.md)

[EntrySelectedBy 元素 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

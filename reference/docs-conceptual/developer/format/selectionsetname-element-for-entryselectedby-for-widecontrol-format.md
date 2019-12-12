---
title: WideControl （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361976"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>SelectionSetName Element for EntrySelectedBy for WideControl (Format)

为定义指定一组 .NET 对象。 当显示其中一个对象时，将使用该定义。

配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionSetName 元素 forEntrySelectedBy for WideEntry （Format）

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-wideentry-format.md)|定义使用此宽项的 .NET 类型或此项要使用的条件。|

## <a name="text-value"></a>文本值

指定选择集的名称。

## <a name="remarks"></a>备注

每个定义必须指定一个类型名称、选择集或选择条件。

当要定义在多个视图中使用的一组对象时，通常使用选择集。 例如，您可能希望为同一组对象创建表视图和列表视图。 有关定义选择集的详细信息，请参阅为[视图定义对象集](./defining-selection-sets.md)。

有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建宽视图](./creating-a-wide-view.md)

[定义选择集](./defining-selection-sets.md)

[WideEntry 的 EntrySelectedBy 元素（格式）](./entryselectedby-element-for-wideentry-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

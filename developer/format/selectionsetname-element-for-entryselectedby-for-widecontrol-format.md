---
title: WideControl （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856793"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>SelectionSetName Element for EntrySelectedBy for WideControl (Format)

指定一组定义的.NET 对象。 定义用于显示这些对象之一时。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式） SelectionSetName 元素EntrySelectedBy 为 WideEntry （格式） 的

## <a name="syntax"></a>语法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)|定义使用此宽的项或要使用此项必须存在的条件的.NET 类型。|

## <a name="text-value"></a>文本值

指定所选内容集的名称。

## <a name="remarks"></a>备注

每个定义必须指定一个类型名称、 选择集或选择条件。

当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。 例如，你可能想要创建的表视图和同一组对象的列表视图。 有关定义的选项集的详细信息，请参阅[定义设置的对象图](./defining-selection-sets.md)。

有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="see-also"></a>另请参阅

[创建较宽的视图](./creating-a-wide-view.md)

[定义的选项集](./defining-selection-sets.md)

[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

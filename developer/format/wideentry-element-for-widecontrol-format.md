---
title: WideControl （格式） 的 WideEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856523"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideEntry Element for WideControl (Format)

提供了宽的视图的定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式）

## <a name="syntax"></a>语法

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`WideEntry`元素。 必须指定单个`WideItem`子元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry （格式） 的 EntrySelectedBy 元素](./entryselectedby-element-for-wideentry-format.md)|可选元素。<br /><br /> 定义使用此宽的项定义或要使用此定义中必须存在的条件的.NET 类型。|
|[WideItem 元素 （格式）](./wideitem-element-for-widecontrol-format.md)|必需的元素。<br /><br /> 定义属性或其值显示的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntries 元素 （格式）](./wideentries-element-for-widecontrol-format.md)|提供了宽的视图的定义。|

## <a name="remarks"></a>备注

较宽的视图是显示单个属性值或为每个对象的脚本值以列表格式。 与其他类型的视图，您可以指定只有一个项元素的每个视图定义。 有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

下面的示例演示`WideEntry`元素定义单个`WideItem`元素。 `WideItem`元素定义其值显示在视图中的属性。

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

有关较宽的视图的完整示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[创建较宽的视图](./creating-a-wide-view.md)

[WideEntry （格式） 的 SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry （格式） 的 SelectionSetName 元素](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry （格式） 的类型名称元素](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries 元素 （格式）](./wideentries-element-for-widecontrol-format.md)

[WideItem 元素 （格式）](./wideitem-element-for-widecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

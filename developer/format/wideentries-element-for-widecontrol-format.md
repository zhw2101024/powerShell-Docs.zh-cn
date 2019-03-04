---
title: WideControl （格式） 的 WideEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853273"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries Element for WideControl (Format)

提供了宽的视图的定义。 宽的视图必须指定一个或多个定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式）

## <a name="syntax"></a>语法

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`WideEntries`元素。 必须指定至少一个子元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素 （格式）](./wideentry-element-for-widecontrol-format.md)|提供了宽的视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl 元素 （格式）](./widecontrol-element-format.md)|定义范围内 （单个值） 的视图的列表格式。|

## <a name="remarks"></a>备注

较宽的视图是显示单个属性值或为每个对象的脚本值以列表格式。 有关较宽的视图的组件的详细信息，请参阅[宽视图组件](./creating-a-wide-view.md)。

## <a name="example"></a>示例

下面的示例演示`WideEntries`元素定义单个`WideEntry`元素。 `WideEntry`元素包含一个`WideItem`定义哪些属性或脚本的值显示在视图中的元素。

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

有关较宽的视图的完整示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[创建较宽的视图](./creating-a-wide-view.md)

[WideControl 元素 （格式）](./widecontrol-element-format.md)

[WideEntry 元素 （格式）](./wideentry-element-for-widecontrol-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

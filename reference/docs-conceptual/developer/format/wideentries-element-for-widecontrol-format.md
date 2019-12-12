---
title: WideControl 的 WideEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361426"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries Element for WideControl (Format)

提供宽视图的定义。 宽视图必须指定一个或多个定义。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（format） WideEntries 元素（Format）

## <a name="syntax"></a>语法

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `WideEntries` 元素的属性、子元素和父元素。 必须至少指定一个子元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)|提供宽视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl 元素（格式）](./widecontrol-element-format.md)|定义视图的宽（单值）列表格式。|

## <a name="remarks"></a>备注

宽视图是显示每个对象的单个属性值或脚本值的列表格式。 有关宽视图组件的详细信息，请参阅[宽视图组件](./creating-a-wide-view.md)。

## <a name="example"></a>示例

下面的示例演示了一个 `WideEntries` 元素，该元素定义单个 `WideEntry` 元素。 `WideEntry` 元素包含一个 `WideItem` 元素，该元素定义在视图中显示的属性或脚本值。

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

有关宽视图的完整示例，请参阅[宽视图（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[创建宽视图](./creating-a-wide-view.md)

[WideControl 元素（格式）](./widecontrol-element-format.md)

[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

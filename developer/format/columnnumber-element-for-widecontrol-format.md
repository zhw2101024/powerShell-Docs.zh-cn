---
title: ColumnNumber WideControl （格式） 的元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066900"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber Element for WideControl (Format)

指定宽视图中显示的列数。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） ColumnNumber 元素 WideControl （格式）

## <a name="syntax"></a>语法

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`ColumnNumber`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[WideControl 元素 （格式）](./widecontrol-element-format.md)|定义范围内 （单个值） 的视图的列表格式。|

## <a name="text-value"></a>文本值

指定一个正整数值。

## <a name="remarks"></a>备注

在定义较宽的视图，你可以添加`AutoSize`元素或`ColumnNumber`元素，但您不能将同时添加。

有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

有关较宽的视图的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[WideControl （格式） 的自动调整大小元素](./autosize-element-for-widecontrol-format.md)

[创建较宽的视图](./creating-a-wide-view.md)

[宽的视图 (Basic)](./wide-view-basic.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

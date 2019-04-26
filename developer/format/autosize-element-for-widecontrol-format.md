---
title: WideControl （格式） 的自动调整大小元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066917"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize Element for WideControl (Format)

指定列的大小和列数会调整基于数据的大小。

元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） 自动调整大小的配置元素 WideControl （格式）

## <a name="syntax"></a>语法

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`AutoSize`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[WideControl 元素 （格式）](./widecontrol-element-format.md)|定义范围内 （单个值） 的视图的列表格式。|

## <a name="remarks"></a>备注

在定义较宽的视图，你可以添加`AutoSize`元素或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素，但您不能将同时添加。

有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

有关较宽的视图的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[ColumnNumber WideControl （格式） 的元素](./columnnumber-element-for-widecontrol-format.md)

[创建较宽的视图](./creating-a-wide-view.md)

[WideControl 元素 （格式）](./widecontrol-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

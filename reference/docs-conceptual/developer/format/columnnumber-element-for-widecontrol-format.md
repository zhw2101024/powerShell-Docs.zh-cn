---
title: WideControl 的 ColumnNumber 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364216"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber Element for WideControl (Format)

指定宽视图中显示的列数。

WideControl 的 Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（format） ColumnNumber 元素（format）

## <a name="syntax"></a>语法

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `ColumnNumber` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl 元素（格式）](./widecontrol-element-format.md)|定义视图的宽（单值）列表格式。|

## <a name="text-value"></a>文本值

指定一个正整数值。

## <a name="remarks"></a>备注

定义宽视图时，可以添加 `AutoSize` 元素或 `ColumnNumber` 元素，但不能同时添加这两个元素。

有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

有关宽视图的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[WideControl 的 Autosize 元素（Format）](./autosize-element-for-widecontrol-format.md)

[创建宽视图](./creating-a-wide-view.md)

[宽视图（基本）](./wide-view-basic.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

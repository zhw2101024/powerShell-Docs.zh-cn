---
title: WideControl 的 AutoSize 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369046"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize Element for WideControl (Format)

指定是否根据数据大小调整列大小和列数。

WideControl （Format）的 Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式） Autosize 元素

## <a name="syntax"></a>语法

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `AutoSize` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl 元素（格式）](./widecontrol-element-format.md)|定义视图的宽（单值）列表格式。|

## <a name="remarks"></a>备注

定义宽视图时，可以添加 `AutoSize` 元素或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素，但不能同时添加这两个元素。

有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

有关宽视图的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[WideControl 的 ColumnNumber 元素（格式）](./columnnumber-element-for-widecontrol-format.md)

[创建宽视图](./creating-a-wide-view.md)

[WideControl 元素（格式）](./widecontrol-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

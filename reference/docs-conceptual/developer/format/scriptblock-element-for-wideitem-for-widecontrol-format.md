---
title: WideControl 的 WideItem 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362026"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock Element for WideItem for WideControl (Format)

指定其值在宽视图中显示的脚本。

用于 WideItem 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式）元素（格式） ScriptBlock 元素（格式）

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `ScriptBlock` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideItem 元素（格式）](./wideitem-element-for-widecontrol-format.md)|定义其值在宽视图中显示的属性或脚本块。|

## <a name="text-value"></a>文本值

指定显示其值的脚本。

## <a name="remarks"></a>备注

有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

此示例演示一个 `WideItem` 元素，该元素定义一个其值在视图中显示的脚本。

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>另请参阅

[WideItem 元素（格式）](./wideitem-element-for-widecontrol-format.md)

[创建宽视图](./creating-a-wide-view.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

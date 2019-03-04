---
title: 脚本块元素 WideControl （格式） 的 WideItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858023"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock Element for WideItem for WideControl (Format)

指定其值宽视图中显示的脚本。

元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） WideItem 元素 （格式） 脚本块的配置元素 WideItem （格式）

## <a name="syntax"></a>语法

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`ScriptBlock`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[WideItem 元素 （格式）](./wideitem-element-for-widecontrol-format.md)|定义宽视图中显示其值的属性或脚本块。|

## <a name="text-value"></a>文本值

指定显示其值的脚本。

## <a name="remarks"></a>备注

有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

此示例显示了`WideItem`元素，用于定义其值显示在视图中的脚本。

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>另请参阅

[WideItem 元素 （格式）](./wideitem-element-for-widecontrol-format.md)

[创建较宽的视图](./creating-a-wide-view.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

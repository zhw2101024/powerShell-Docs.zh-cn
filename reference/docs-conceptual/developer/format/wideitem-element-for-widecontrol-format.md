---
title: WideControl 的 WideItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361396"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideItem Element for WideControl (Format)

定义要显示其值的属性或脚本。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式） WideItem 元素（格式）

## <a name="syntax"></a>语法

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `WideItem` 元素的属性、子元素和父元素。 `FormatString` 元素是可选的。 但是，必须指定 `PropertyName` 或 `ScriptBlock` 元素，但不能同时指定这两个元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl 的 WideItem 的格式字符串元素（格式）](./formatstring-element-for-wideitem-for-widecontrol-format.md)|可选元素。<br /><br /> 指定定义属性或脚本值在视图中显示方式的格式模式。|
|[WideItem 的 PropertyName 元素（Format）](./propertyname-element-for-wideitem-for-widecontrol-format.md)|指定对象的属性，其值显示在宽视图中。|
|[WideItem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|指定其值在宽视图中显示的脚本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)|提供宽视图的定义。|

## <a name="remarks"></a>备注

有关宽视图组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

下面的示例演示了一个 `WideEntry` 元素，该元素定义单个 `WideItem` 元素。 `WideItem` 元素定义其值在视图中显示的属性或脚本。

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

有关宽视图的完整示例，请参阅[宽视图（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[WideControl 的 WideItem 的格式字符串元素（格式）](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[WideItem 的 PropertyName 元素（Format）](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[WideItem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

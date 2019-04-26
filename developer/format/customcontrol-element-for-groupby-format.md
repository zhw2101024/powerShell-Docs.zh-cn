---
title: GroupBy （格式） 的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066747"
---
# <a name="customcontrol-element-for-groupby-format"></a>CustomControl Element for GroupBy (Format)

定义显示新组的自定义控件。

GroupBy （格式） 的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述的特性、 子元素和父元素的`CustomControl`元素。 可以指定任意数量的子元素，并按任何顺序列出它们。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-groupby-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定义 Windows PowerShell 如何显示对象的新的组。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[GroupBy （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-groupby-format.md)

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

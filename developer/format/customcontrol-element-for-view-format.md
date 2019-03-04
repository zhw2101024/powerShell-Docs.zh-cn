---
title: 视图 （格式） 的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861253"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl Element for View (Format)

定义自定义控件的视图格式。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式）

## <a name="syntax"></a>语法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`CustomControl`元素。 必须指定一个子元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[视图 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-view-format.md)|必需的元素。<br /><br /> 提供了自定义控件视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图元素 （格式）](./view-element-format.md)|定义用于显示一个或多个.NET 对象的视图。|

## <a name="remarks"></a>备注

在大多数情况下，只有一个定义需要为每个控件视图，但可以提供多个定义，如果你想要使用相同的视图以显示不同的.NET 对象。 在这些情况下，可以为每个对象或对象集提供一个单独的定义。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 CustomControl CustomEntries 元素](./customentries-element-for-customcontrol-for-view-format.md)

[视图元素 （格式）](./view-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

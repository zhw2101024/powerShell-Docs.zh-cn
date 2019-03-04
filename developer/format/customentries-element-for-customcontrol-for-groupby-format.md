---
title: GroupBy （格式） 的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853673"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries Element for CustomControl for GroupBy (Format)

提供控件的定义。 定义如何显示一组新对象时，将使用此元素。

GroupBy （格式） 的 GroupBy （格式） 的 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`CustomEntries`元素。 可以指定的子元素的数目没有最大限制。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-groupby-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl 元素](./customcontrol-element-for-groupby-format.md)|定义显示新组的自定义控件。|

## <a name="remarks"></a>备注

在大多数情况下，控件具有只有一个定义，指定在单个`CustomEntry`元素。 但是，就可以提供多个定义，如果你想要使用相同的控件来显示不同的组。 在这些情况下，你可以定义`CustomEntry`元素组。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的控件的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-controls-for-view-format.md)

[GroupBy （格式） 的 CustomControl 元素](./customcontrol-element-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

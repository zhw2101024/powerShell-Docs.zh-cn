---
title: 视图 （格式） 的控件的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861803"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries Element for CustomControl for Controls for View (Format)

提供控件的定义。 定义一个视图，可以使用的控件时，将使用此元素。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl 的 Controls 的视图 （格式）

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
|[视图 （格式） 的控件的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-controls-for-view-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[控件的视图 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-view-format.md)|定义视图所使用的控件。|

## <a name="remarks"></a>备注

在大多数情况下，控件具有只有一个定义，指定在单个`CustomEntry`元素。 但是，就可以提供多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。 在这些情况下，你可以定义`CustomEntry`元素为每个对象或对象集。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的控件的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-controls-for-view-format.md)

[控件的视图 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

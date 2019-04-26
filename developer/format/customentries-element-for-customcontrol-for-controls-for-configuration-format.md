---
title: 配置 （格式） 的控件的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066594"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries Element for CustomControl for Controls for Configuration (Format)

提供了公共控件的定义。 定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。

配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素格式）

## <a name="syntax"></a>语法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`CustomEntries`元素。 必须指定一个或多个子元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供了一个常用的控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|定义公共控件。|

## <a name="remarks"></a>备注

在大多数情况下，控件具有只有一个定义，在单个定义`CustomEntry`元素。 但是很可能有多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。 在这些情况下，你可以定义`CustomEntry`元素为每个对象或对象集。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件的 CustomControl 元素](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[配置 （格式） 的控件的 CustomControl CustomEntry 元素](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

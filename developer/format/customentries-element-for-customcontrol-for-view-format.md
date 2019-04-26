---
title: 视图 （格式） 的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066509"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries Element for CustomControl for View (Format)

提供了自定义控件视图的定义。 自定义控件视图必须指定一个或多个定义。

配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式）

## <a name="syntax"></a>语法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`CustomControlEntries`元素。 必须指定一个或多个子元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|必需的元素。<br /><br /> 提供自定义控件视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[视图 （格式） 的 CustomControl 元素](./customcontrol-element-for-view-format.md)|必需的元素。<br /><br /> 定义自定义控件的视图格式。|

## <a name="remarks"></a>备注

在大多数情况下，控件具有只有一个定义，在单个定义`CustomEntry`元素。 但是很可能有多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。 在这些情况下，你可以定义`CustomEntry`元素为每个对象或对象集。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 CustomControl 元素](./customcontrol-element-for-view-format.md)

[视图 （格式） 的 CustomEntries CustomEntry 元素](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

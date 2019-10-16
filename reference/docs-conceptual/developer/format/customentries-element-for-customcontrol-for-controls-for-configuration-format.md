---
title: 用于配置的控件（格式）的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368816"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries Element for CustomControl for Controls for Configuration (Format)

提供公共控件的定义。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（形式

## <a name="syntax"></a>语法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomEntries` 元素的属性、子元素和父元素。 您必须指定一个或多个子元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供公共控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于控件配置的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|定义公共控件。|

## <a name="remarks"></a>备注

在大多数情况下，控件只有一个定义，该定义在单个 @no__t 0 元素中定义。 但是，如果希望使用同一控件显示不同的 .NET 对象，则可以有多个定义。 在这些情况下，可以为每个对象或一组对象定义 `CustomEntry` 元素。

## <a name="see-also"></a>另请参阅

[用于控件配置的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

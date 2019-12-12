---
title: 用于视图（格式）的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368806"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries Element for CustomControl for Controls for View (Format)

提供控件的定义。 定义可由视图使用的控件时，将使用此元素。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素视图控件的 CustomControl （格式）

## <a name="syntax"></a>语法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `CustomEntries` 元素的属性、子元素和父元素。 对于可指定的子元素数没有最大限制。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于控件的控件的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)|定义视图使用的控件。|

## <a name="remarks"></a>备注

在大多数情况下，控件只有一个定义，该定义是在单个 `CustomEntry` 元素中指定的。 但是，如果您希望使用同一控件显示不同的 .NET 对象，则可以提供多个定义。 在这些情况下，可以为每个对象或一组对象定义 `CustomEntry` 元素。

## <a name="see-also"></a>另请参阅

[用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)

[用于控件的控件的 CustomControl 元素（格式）](./customcontrol-element-for-control-for-controls-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

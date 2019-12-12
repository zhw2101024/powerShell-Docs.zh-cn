---
title: 用于视图的 CustomControl 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364076"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries Element for CustomControl for View (Format)

提供自定义控件视图的定义。 自定义控件视图必须指定一个或多个定义。

CustomControl for View 的 Configuration 元素（格式） ViewDefinitions 元素（format） CustomControl 元素（format） CustomEntries 元素（format）

## <a name="syntax"></a>语法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomControlEntries` 元素的属性、子元素和父元素。 您必须指定一个或多个子元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于视图的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|必需的元素。<br /><br /> 提供自定义控件视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 CustomControl 元素（Format）](./customcontrol-element-for-view-format.md)|必需的元素。<br /><br /> 定义视图的自定义控件格式。|

## <a name="remarks"></a>备注

在大多数情况下，控件只有一个定义，该定义在单个 `CustomEntry` 元素中定义。 但是，如果希望使用同一控件显示不同的 .NET 对象，则可以有多个定义。 在这些情况下，可以为每个对象或一组对象定义 `CustomEntry` 元素。

## <a name="see-also"></a>另请参阅

[View 的 CustomControl 元素（Format）](./customcontrol-element-for-view-format.md)

[用于视图的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

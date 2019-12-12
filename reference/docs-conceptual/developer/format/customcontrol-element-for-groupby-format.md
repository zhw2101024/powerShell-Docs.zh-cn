---
title: GroupBy （格式）的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368956"
---
# <a name="customcontrol-element-for-groupby-format"></a>CustomControl Element for GroupBy (Format)

定义显示新组的自定义控件。

GroupBy （format）的 View （format） CustomControl 元素的 ViewDefinitions 元素（format） View 元素（format） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `CustomControl` 元素的属性、子元素和父元素。 可以指定任意数量的子元素，并以任意顺序列出它们。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-groupby-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定义 Windows PowerShell 如何显示一组新的对象。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[GroupBy 的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-groupby-format.md)

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

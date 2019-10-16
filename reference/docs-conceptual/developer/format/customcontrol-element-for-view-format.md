---
title: View 的 CustomControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363356"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl Element for View (Format)

定义视图的自定义控件格式。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（Format）

## <a name="syntax"></a>语法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomControl` 元素的属性、子元素和父元素。 您必须指定一个子元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于视图的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)|必需的元素。<br /><br /> 提供自定义控件视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定义用于显示一个或多个 .NET 对象的视图。|

## <a name="remarks"></a>备注

在大多数情况下，每个控件视图只需要一个定义，但如果您希望使用同一视图显示不同的 .NET 对象，则可以提供多个定义。 在这些情况下，可以为每个对象或一组对象提供单独的定义。

## <a name="see-also"></a>另请参阅

[用于视图的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)

[View 元素（格式）](./view-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

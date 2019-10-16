---
title: GroupBy 的 PropertyName 元素（Format） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362516"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName Element for GroupBy (Format)

指定在新组的值发生更改时启动新组的 .NET 属性。

对于 GroupBy （Format）的 View （Format） PropertyName 元素，Configuration 元素（Format） ViewDefinitions 元素（format） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定义一组 .NET 对象的显示方式。|

## <a name="text-value"></a>文本值

指定 .NET 属性名称。

## <a name="remarks"></a>备注

每当此属性的值发生更改时，Windows PowerShell 就会启动一个新组。

如果指定此元素，则不能指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素来启动新组。

## <a name="example"></a>示例

下面的示例演示如何在属性的值更改时启动新组。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

有关包括此元素的完整格式化文件的示例，请参阅[宽视图（GroupBy）](./wide-view-groupby.md)。

## <a name="see-also"></a>另请参阅

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[GroupBy 的 ScriptBlock 元素（格式）](./scriptblock-element-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

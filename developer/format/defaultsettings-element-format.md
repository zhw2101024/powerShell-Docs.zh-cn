---
title: DefaultSettings 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066339"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings Element (Format)

定义应用于的格式设置文件的所有视图的常见设置。 常用的设置包括显示错误，表定义如何将扩展集合，和的详细信息中的文本换行。

配置元素 （格式） DefaultSettings 元素 （格式）

## <a name="syntax"></a>语法

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了特性、 子元素和父元素的`DefaultSettings`元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[DisplayError 元素 （格式）](./displayerror-element-format.md)|可选元素。<br /><br /> 指定在显示的一段数据的同时发生错误时显示的字符串 #ERR。|
|[EnumerableExpansions 元素 （格式）](./enumerableexpansions-element-format.md)|可选元素。<br /><br /> 定义.NET 对象时它们显示在视图中展开的不同方法。|
|[PropertyCountForTable （格式）](./propertycountfortable-element-format.md)|可选元素。<br /><br /> 指定对象必须具有要在表视图中显示该对象的属性的最小数目。|
|[ShowError 元素 （格式）](./showerror-element-format.md)|可选元素。<br /><br /> 指定在出错时显示一段数据时，显示完整的错误记录。|
|[WrapTables 元素 （格式）](./wraptables-element-format.md)|可选元素。<br /><br /> 指定是否不适合的列的宽度，表中的数据将移到下一行。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[配置元素](./configuration-element-format.md)|表示格式设置文件的顶级元素。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[配置元素](./configuration-element-format.md)

[DisplayError 元素 （格式）](./displayerror-element-format.md)

[EnumerableExpansions 元素 （格式）](./enumerableexpansions-element-format.md)

[PropertyCountForTable （格式）](./propertycountfortable-element-format.md)

[ShowError 元素 （格式）](./showerror-element-format.md)

[WrapTables 元素 （格式）](./wraptables-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

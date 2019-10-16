---
title: DefaultSettings 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363866"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings Element (Format)

定义适用于格式设置文件的所有视图的常见设置。 常见的设置包括显示错误、在表中环绕文本、定义集合的展开方式等。

Configuration 元素（Format） DefaultSettings 元素（Format）

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

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `DefaultSettings` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[DisplayError 元素（格式）](./displayerror-element-format.md)|可选元素。<br /><br /> 指定在显示一段数据的过程中出现错误时，显示字符串 #ERR。|
|[EnumerableExpansions 元素（格式）](./enumerableexpansions-element-format.md)|可选元素。<br /><br /> 定义 .NET 对象显示在视图中时的不同显示方式。|
|[PropertyCountForTable （格式）](./propertycountfortable-element-format.md)|可选元素。<br /><br /> 指定在表视图中显示对象时必须包含的属性的最小数目。|
|[ShowError 元素（格式）](./showerror-element-format.md)|可选元素。<br /><br /> 指定在显示一段数据的过程中出现错误时，显示完整的错误记录。|
|[WrapTables 元素（格式）](./wraptables-element-format.md)|可选元素。<br /><br /> 指定如果表中的数据无法适应列的宽度，则将其移到下一行。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置元素](./configuration-element-format.md)|表示格式设置文件的顶级元素。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[配置元素](./configuration-element-format.md)

[DisplayError 元素（格式）](./displayerror-element-format.md)

[EnumerableExpansions 元素（格式）](./enumerableexpansions-element-format.md)

[PropertyCountForTable （格式）](./propertycountfortable-element-format.md)

[ShowError 元素（格式）](./showerror-element-format.md)

[WrapTables 元素（格式）](./wraptables-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

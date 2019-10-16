---
title: GroupBy （格式）的标签元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365196"
---
# <a name="label-element-for-groupby-format"></a>Label Element for GroupBy (Format)

指定在遇到新组时显示的标签。

GroupBy 的 "视图（格式）" 标签元素的配置元素（格式） ViewDefinitions 元素（格式） GroupBy 元素（格式）

## <a name="syntax"></a>语法

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `Label` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)|定义如何显示新的对象组。|

## <a name="text-value"></a>文本值

指定每当 Windows PowerShell 遇到新的属性或脚本值时所显示的文本。

## <a name="remarks"></a>备注

除了此元素指定的文本，Windows PowerShell 还显示启动组的新值，并在组的前面和后面添加一个空白行。

## <a name="example"></a>示例

下面的示例显示了新组的标签。 显示的标签将如下所示： `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

有关包括此元素的完整格式化文件的示例，请参阅[宽视图（GroupBy）](./wide-view-groupby.md)。

## <a name="see-also"></a>另请参阅

[View 的 GroupBy 元素（格式）](./groupby-element-for-view-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

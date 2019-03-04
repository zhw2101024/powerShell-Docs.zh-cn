---
title: 使用 GroupBy （格式） 的标签元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862393"
---
# <a name="label-element-for-groupby-format"></a>Label Element for GroupBy (Format)

指定遇到新的组时显示的标签。

视图 （格式） 的 GroupBy （格式） 的标签元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素

## <a name="syntax"></a>语法

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`Label`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)|定义新的一组对象的显示方式。|

## <a name="text-value"></a>文本值

指定 Windows PowerShell 遇到新的属性或脚本值时显示的文本。

## <a name="remarks"></a>备注

除了指定此元素的文本，Windows PowerShell 会显示启动组，并添加一个空行之前和之后的组的新值。

## <a name="example"></a>示例

下面的示例显示新组的标签。 显示的标签将类似于此： `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

有关完整的格式设置文件，其中包含此元素的示例，请参阅[宽的视图 (GroupBy)](./wide-view-groupby.md)。

## <a name="see-also"></a>另请参阅

[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

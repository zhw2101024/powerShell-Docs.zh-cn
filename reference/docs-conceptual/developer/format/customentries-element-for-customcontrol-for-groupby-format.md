---
title: GroupBy （Format）的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364086"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries Element for CustomControl for GroupBy (Format)

提供控件的定义。 此元素在定义如何显示新的对象组时使用。

配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 groupby （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）

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
|[GroupBy 的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-groupby-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 元素（Format）](./customcontrol-element-for-groupby-format.md)|定义显示新组的自定义控件。|

## <a name="remarks"></a>备注

在大多数情况下，控件只有一个定义，该定义是在单个 @no__t 0 元素中指定的。 但是，如果要使用相同的控件来显示不同的组，则可以提供多个定义。 在这些情况下，可以为组定义 `CustomEntry` 元素。

## <a name="see-also"></a>另请参阅

[用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-controls-for-view-format.md)

[GroupBy 的 CustomControl 元素（Format）](./customcontrol-element-for-groupby-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

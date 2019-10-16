---
title: DisplayError 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363986"
---
# <a name="displayerror-element-format"></a>DisplayError Element (Format)

指定在显示一段数据时出现错误时显示字符串 #ERR。

配置元素（格式） DefaultSettings 元素（format） DisplayError 元素（格式）

## <a name="syntax"></a>语法

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `DisplayError` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)|定义适用于格式设置文件的所有视图的常见设置。|

## <a name="remarks"></a>备注

默认情况下，在尝试显示一段数据的过程中出现错误时，数据的位置将保留为空。 如果此元素设置为 true，则将显示 #ERR 字符串。

## <a name="see-also"></a>另请参阅

[DefaultSettings 元素（格式）](./defaultsettings-element-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

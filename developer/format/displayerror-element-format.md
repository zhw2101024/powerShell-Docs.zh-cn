---
title: DisplayError 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854913"
---
# <a name="displayerror-element-format"></a>DisplayError Element (Format)

指定当出错时显示一段数据显示 #ERR 的字符串。

配置元素 （格式） DefaultSettings 元素 （格式） DisplayError 元素 (Frmat)

## <a name="syntax"></a>语法

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`DisplayError`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[DefaultSettings 元素 （格式）](./defaultsettings-element-format.md)|定义应用于的格式设置文件的所有视图的常见设置。|

## <a name="remarks"></a>备注

默认情况下，当出错时尝试显示一段数据，数据的位置是保留为空。 如果此元素设置为 true，#ERR 字符串将会显示。

## <a name="see-also"></a>另请参阅

[DefaultSettings 元素 （格式）](./defaultsettings-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

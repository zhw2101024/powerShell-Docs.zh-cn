---
title: 配置 （格式） 的 controls 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861173"
---
# <a name="controls-element-for-configuration-format"></a>Controls Element for Configuration (Format)

定义可由格式设置文件的所有视图的公共控件。

配置 （格式） 的配置元素 （格式） 的 Controls 元素

## <a name="syntax"></a>语法

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`Controls`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[配置 （格式） 的控件的控件元素](./control-element-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 定义可由格式设置文件的所有视图的公共控件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置元素 （格式）](./configuration-element-format.md)|表示格式设置文件的顶级元素。|

## <a name="remarks"></a>备注

可以创建任意数量的公共控件。 对于每个控件，必须指定用来引用控件和控件的组件的名称。

## <a name="see-also"></a>另请参阅

[配置元素 （格式）](./configuration-element-format.md)

[配置 （格式） 的控件的控件元素](./control-element-for-controls-for-configuration-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

---
title: 配置元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856323"
---
# <a name="configuration-element-format"></a>Configuration Element (Format)

表示格式设置文件的顶级元素。

配置元素

## <a name="syntax"></a>语法

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述了特性、 子元素和父元素的`Configuration`元素。 此元素必须为每个格式设置文件的根元素和此元素必须包含至少一个子元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[配置 （格式） 的控件元素](./controls-element-for-configuration-format.md)|可选元素。<br /><br /> 定义可由格式设置文件的所有视图的公共控件。|
|[DefaultSettings 元素 （格式）](./defaultsettings-element-format.md)|可选元素。<br /><br /> 定义应用于的格式设置文件的所有视图的常见设置。|
|[SelectionSets 元素格式](./selectionsets-element-format.md)|可选元素。<br /><br /> 定义可以使用的格式设置文件的所有视图的.NET 对象的公用集。|
|[ViewDefinitions 元素 （格式）](./viewdefinitions-element-format.md)|可选元素。<br /><br /> 定义用于显示对象的视图。|

### <a name="parent-elements"></a>父元素

无。

## <a name="remarks"></a>备注

格式设置文件定义对象的显示方式。 在大多数情况下，此根元素包含[ViewDefinitions](./viewdefinitions-element-format.md)定义表、 列表和格式设置文件的宽视图元素。 除了视图定义中，常见的选项集、 设置和控件，可以使用这些视图可以定义的格式设置文件。

## <a name="see-also"></a>另请参阅

[配置 （格式） 的控件元素](./controls-element-for-configuration-format.md)

[DefaultSettings 元素 （格式）](./defaultsettings-element-format.md)

[SelectionSets 元素 （格式）](./selectionsets-element-format.md)

[ViewDefinitions 元素 （格式）](./viewdefinitions-element-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

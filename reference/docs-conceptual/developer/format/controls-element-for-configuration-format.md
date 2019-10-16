---
title: 用于配置的 Controls 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368996"
---
# <a name="controls-element-for-configuration-format"></a>Controls Element for Configuration (Format)

定义可供格式设置文件的所有视图使用的公共控件。

配置元素（格式）控件配置的元素（格式）

## <a name="syntax"></a>语法

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `Controls` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于配置控件的控件元素（格式）](./control-element-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 定义可供格式设置文件的所有视图使用的公共控件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[配置元素（格式）](./configuration-element-format.md)|表示格式设置文件的顶级元素。|

## <a name="remarks"></a>备注

您可以创建任意数量的公共控件。 对于每个控件，您必须指定用于引用控件和控件组件的名称。

## <a name="see-also"></a>另请参阅

[配置元素（格式）](./configuration-element-format.md)

[用于配置控件的控件元素（格式）](./control-element-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

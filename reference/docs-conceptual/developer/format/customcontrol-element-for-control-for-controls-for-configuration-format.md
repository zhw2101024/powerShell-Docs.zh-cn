---
title: 用于控件的控件（格式）的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368966"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a>CustomControl Element for Control for Controls for Configuration (Format)

定义控件。 此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。

Configuration 元素（Format）控制配置（format）控件元素的元素，用于配置（format） CustomControl 元素的控件以实现配置（格式）

## <a name="syntax"></a>语法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍了 `CustomControl` 元素的属性、子元素和父元素。 此元素必须至少有一个子元素。 对于可指定的子元素数没有最大限制。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[用于配置的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用于配置控件的控件元素（格式）](./control-element-for-controls-for-configuration-format.md)|定义一个公共控件，该控件可供格式设置文件的所有视图和用于引用控件的名称使用。|

## <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[用于配置控件的控件元素（格式）](./control-element-for-controls-for-configuration-format.md)

[用于配置的 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)

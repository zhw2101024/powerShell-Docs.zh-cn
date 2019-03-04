---
title: ValidateSet 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861203"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet 属性声明

ValidateSetAttribute 属性指定一组的可能值的 cmdlet 参数自变量。 Windows PowerShell 函数还可以使用此属性。

当指定此属性时，Windows PowerShell 运行时确定 cmdlet 参数提供的参数是否与中提供的元素集的元素相匹配。 参数自变量与匹配集中的元素时才运行该 cmdlet。 如果不找到任何匹配项，则是由 Windows PowerShell 运行时引发错误。

## <a name="syntax"></a>语法

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>参数

`ValidValues` ([System.String](/dotnet/api/System.String)) 所需。 指定有效的参数元素值。 下面的示例演示如何指定一个元素或多个元素。

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。 默认值`true`指示忽略大小写。 值为`false`使该 cmdlet 区分大小写。

## <a name="remarks"></a>备注

- 此属性可以使用仅一次，每个参数。

- 如果参数值是一个数组，数组的每个元素必须匹配的元素的属性集。

- 通过定义 ValidateSetAttribute 特性[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)类。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

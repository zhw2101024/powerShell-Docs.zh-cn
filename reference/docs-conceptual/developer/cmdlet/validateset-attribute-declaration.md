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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364276"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet 属性声明

ValidateSetAttribute 属性为 cmdlet 参数参数指定一组可能的值。 此属性也可由 Windows PowerShell 函数使用。

如果指定此属性，则 Windows PowerShell 运行时将确定 cmdlet 参数的提供参数是否与提供的元素集中的元素匹配。 仅当参数参数与集中的元素匹配时，才运行 cmdlet。 如果未找到匹配项，则 Windows PowerShell 运行时将引发错误。

## <a name="syntax"></a>语法

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>参数

需要 `ValidValues` （[system.string](/dotnet/api/System.String)）。 指定有效的参数元素值。 下面的示例演示如何指定一个或多个元素。

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

@no__t-[0 （system.string](/dotnet/api/System.Boolean)）可选命名参数。 @No__t 的默认值为-0 指示忽略大小写。 值 `false` 使 cmdlet 区分大小写。

## <a name="remarks"></a>备注

- 此属性仅可用于每个参数一次。

- 如果参数值为数组，则数组的每个元素都必须与属性集的元素匹配。

- ValidateSetAttribute 特性是由[ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)类定义的。

## <a name="see-also"></a>另请参阅

[System.web. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

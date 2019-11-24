---
title: ValidateRange 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369126"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 属性声明

ValidateRange 属性指定 cmdlet 参数参数的最小值和最大值（范围）。 此属性也可由 Windows PowerShell 函数使用。

## <a name="syntax"></a>语法

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>参数

需要 `MinRange`[（system.string）。](/dotnet/api/system.object) 指定允许的最小值。

需要 `MaxRange`[（system.string）。](/dotnet/api/system.object) 指定允许的最大值。

## <a name="remarks"></a>备注

- 当 `MinRange` 参数的值大于 `MaxRange` 参数的值时，Windows PowerShell 运行时将引发构造错误。

- Windows PowerShell 运行时在以下条件下引发验证错误：

    - 当参数的值小于 `MinRange` 限制或大于 `MaxRange` 限制时。

    - 当参数与 `MinRange` 和 `MaxRange` 参数的类型不同时。

- ValidateRange 特性是由[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)类定义的。

## <a name="see-also"></a>另请参阅

[System.web. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857033"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 属性声明

ValidateRange 属性指定的最小值和最大值 （范围） 的 cmdlet 参数自变量。 Windows PowerShell 函数还可以使用此属性。

## <a name="syntax"></a>语法

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>参数

`MinRange` ([System.Object](/dotnet/api/system.object)) 所需。 指定允许的最小值。

`MaxRange` ([System.Object](/dotnet/api/system.object)) 所需。 指定允许的最大值。

## <a name="remarks"></a>备注

- Windows PowerShell 运行时将引发构造错误时的值`MinRange`参数是否大于的值`MaxRange`参数。

- Windows PowerShell 运行时将引发验证错误在以下情况下：

    - 当自变量的值是小于`MinRange`限制或大于`MaxRange`限制。

    - 当参数不是相同的类型`MinRange`和`MaxRange`参数。

- 通过定义 ValidateRange 特性[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)类。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

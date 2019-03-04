---
title: ValidateCount 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859153"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 属性声明

ValidateCount 属性指定参数允许 cmdlet 参数的最小值和最大数目。

## <a name="syntax"></a>语法

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>参数

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 所需。 指定参数的最小的数目。

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) 所需。 指定参数的最大的数目。

## <a name="remarks"></a>备注

- 有关如何声明此属性的详细信息，请参阅[如何声明输入验证规则](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。

- 不调用此属性时，相应的 cmdlet 参数可以具有任意数量的参数。

- Windows PowerShell 运行时将引发错误在以下情况下：

    - `MinLength`并`MaxLength`特性参数的类型不是[System.Int32](/dotnet/api/System.Int32)。

    - 值`MaxLength`特性参数是否小于的值`MinLength`特性参数。

- 通过定义 ValidateCount 特性[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)类。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[如何声明输入的验证规则](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[如何声明输入的验证规则](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

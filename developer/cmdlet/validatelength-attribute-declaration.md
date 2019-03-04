---
title: ValidateLength 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858863"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength 属性声明

ValidateLength 属性指定的最小值和最大字符数为 cmdlet 参数自变量。 Windows PowerShell 函数还可以使用此属性。

## <a name="syntax"></a>语法

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>参数

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。 指定的最小允许的字符数。

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。 指定最大允许的字符。

## <a name="remarks"></a>备注

- 有关如何声明此属性的详细信息，请参阅[如何声明输入验证规则](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。
- 有关如何声明此属性的详细信息，请参阅[如何声明输入验证规则](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。

- 如果不使用此特性，相应参数自变量可以是任意长度。

- Windows PowerShell 运行时将引发错误在以下情况下：

    - 时的值`MaxLength`特性参数是否小于的值`MinLength`特性参数。

    - 当`MaxLength`属性参数设置为 0。

    - 当参数不是字符串。

- 通过定义 ValidateLength 特性[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)类。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

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
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369176"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength 属性声明

ValidateLength 属性指定 cmdlet 参数参数的最小和最大字符数。 此属性也可由 Windows PowerShell 函数使用。

## <a name="syntax"></a>语法

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>参数

需要 `MinLength`[（system.string）。](/dotnet/api/System.Int32) 指定允许的最小字符数。

需要 `MaxLength`[（system.string）。](/dotnet/api/System.Int32) 指定允许的最大字符数。

## <a name="remarks"></a>备注

- 有关如何声明此属性的详细信息，请参阅[如何声明输入验证规则](./how-to-validate-parameter-input.md)。

- 如果未使用此属性，则相应的参数参数可以为任意长度。

- Windows PowerShell 运行时在以下条件下引发错误：

    - 当 `MaxLength` attribute 参数的值小于 `MinLength` attribute 参数的值时。

    - 如果 `MaxLength` 特性参数设置为0，则为。

    - 如果参数不是字符串，则为。

- ValidateLength 特性是由[Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)类定义的。

## <a name="see-also"></a>另请参阅

[System.web. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

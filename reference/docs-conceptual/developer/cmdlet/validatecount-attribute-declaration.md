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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369226"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 属性声明

ValidateCount 属性指定 cmdlet 参数允许的最小和最大参数数量。

## <a name="syntax"></a>语法

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>参数

需要 `MinLength`[System.Int32][] 指定参数的最小数目。

需要 `MaxLength`[System.Int32][] 指定参数的最大数目。

## <a name="remarks"></a>备注

- 有关如何声明此属性的详细信息，请参阅[如何验证参数计数][]。

- 如果未调用此属性，则对应的 cmdlet 参数可以有任意数量的参数。

- Windows PowerShell 运行时在以下条件下引发错误：

    - `MinLength` 和 `MaxLength` 属性参数的类型不是[System.Int32][]。

    - `MaxLength` 属性参数的值小于 `MinLength` attribute 参数的值。

- ValidateCount 特性是由[System.web. ValidateCountAttribute][]类定义的。

## <a name="see-also"></a>另请参阅

[System.web. ValidateCountAttribute][]

[如何验证参数计数][]

[编写 Windows PowerShell Cmdlet][]

[如何验证参数计数]: how-to-validate-an-argument-count.md
[编写 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.web. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute

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
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983892"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 属性声明

ValidateCount 属性指定参数允许 cmdlet 参数的最小值和最大数目。

## <a name="syntax"></a>语法

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>参数

`MinLength` ([System.Int32][]) 所需。 指定参数的最小的数目。

`MaxLength`([System.Int32][]) 所需。 指定参数的最大的数目。

## <a name="remarks"></a>备注

- 有关如何声明此属性的详细信息，请参阅[如何进行验证的参数计数][]。

- 不调用此属性时，相应的 cmdlet 参数可以具有任意数量的参数。

- Windows PowerShell 运行时将引发错误在以下情况下：

    - `MinLength`并`MaxLength`特性参数的类型不是[System.Int32][]。

    - 值`MaxLength`特性参数是否小于的值`MinLength`特性参数。

- 通过定义 ValidateCount 特性[System.Management.Automation.ValidateCountAttribute][]类。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.ValidateCountAttribute][]

[如何进行验证的参数计数][]

[编写 Windows PowerShell Cmdlet][]

[如何进行验证的参数计数]: how-to-validate-an-argument-count.md
[编写 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute

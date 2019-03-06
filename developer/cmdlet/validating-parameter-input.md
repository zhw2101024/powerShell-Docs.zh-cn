---
title: 验证参数输入 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429833"
---
# <a name="validating-parameter-input"></a>验证参数输入

PowerShell 可以验证传递给以下几种方式的 cmdlet 参数的参数。
PowerShell 可以验证长度、 范围和自变量的字符模式。
它可以验证的参数可用 （计数） 的数目。
通过在 cmdlet 类的公共属性的参数属性与声明的验证特性定义这些验证规则。

若要验证参数自变量，PowerShell 运行时使用的验证特性提供的信息确认之前运行该 cmdlet 的参数的值。
如果该参数输入不是有效的用户会收到一条错误消息。
每个验证参数定义由 PowerShell 强制执行的验证规则。

PowerShell 强制执行基于以下属性的验证规则。

### <a name="validatecount"></a>ValidateCount

指定参数可接受的参数最小值和最大的数目。
有关详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。

### <a name="validatelength"></a>ValidateLength

在参数自变量中指定的最小值和最大字符数。
有关详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。

### <a name="validatepattern"></a>ValidatePattern

指定正则表达式，用于验证参数自变量。
有关详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。

### <a name="validaterange"></a>ValidateRange

指定参数自变量的最小值和最大值。
有关详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。

### <a name="validateset"></a>ValidateSet

指定参数自变量的有效值。
有关详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[如何验证参数输入](./how-to-validate-parameter-input.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

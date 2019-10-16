---
title: 正在验证参数输入 |Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363506"
---
# <a name="validating-parameter-input"></a>验证参数输入

PowerShell 可以通过多种方式验证传递到 cmdlet 参数的参数。
PowerShell 可以验证参数的字符的长度、范围和模式。
它可以验证可用参数的数目（计数）。
这些验证规则由使用 cmdlet 类的公共属性上的 Parameter 特性声明的验证特性定义。

若要验证参数参数，PowerShell 运行时使用验证特性提供的信息来确认在运行 cmdlet 之前参数的值。
如果参数输入无效，则用户将收到一条错误消息。
每个验证参数都定义一个由 PowerShell 强制执行的验证规则。

PowerShell 根据以下属性强制执行验证规则。

### <a name="validatecount"></a>ValidateCount

指定参数可以接受的最小和最大参数数目。
有关详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。

### <a name="validatelength"></a>ValidateLength

指定参数参数中的最小和最大字符数。
有关详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。

### <a name="validatepattern"></a>ValidatePattern

指定用于验证参数参数的正则表达式。
有关详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。

### <a name="validaterange"></a>ValidateRange

指定参数参数的最小值和最大值。
有关详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。

### <a name="validateset"></a>ValidateSet

指定参数参数的有效值。
有关详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[如何验证参数输入](./how-to-validate-parameter-input.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

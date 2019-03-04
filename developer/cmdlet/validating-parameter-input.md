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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858843"
---
# <a name="validating-parameter-input"></a>验证参数输入

Windows PowerShell 可以验证传递给以下几种方式的 cmdlet 参数的参数。 Windows PowerShell 可以验证长度、 范围和自变量的字符模式。 它可以验证的参数可用 （计数） 的数目。 通过在 cmdlet 类的公共属性的参数属性与声明的验证特性定义这些验证规则。

若要验证参数自变量，Windows PowerShell 运行时使用的验证特性提供的信息确认之前运行该 cmdlet 的参数的值。 如果该参数输入不是有效的用户会收到一条错误消息。 每个验证参数定义由 Windows PowerShell 强制执行的验证规则。

Windows PowerShell 强制执行基于以下属性的验证规则。

ValidateCount 指定最小值和最大数量的参数可接受的参数。 有关用于声明此属性的语法的详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。

ValidateLength 参数自变量中指定的最小值和最大字符数。 有关用于声明此属性的语法的详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。

ValidatePattern 指定正则表达式，用于验证参数自变量。 有关用于声明此属性的语法的详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。

ValidateRange 指定参数自变量的最小值和最大值。 有关用于声明此属性的语法的详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。

ValidateSet 指定参数自变量的有效值。 有关用于声明此属性的语法的详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[如何验证参数输入](./how-to-validate-parameter-input.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

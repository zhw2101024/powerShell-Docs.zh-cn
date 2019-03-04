---
title: Cmdlet 属性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853913"
---
# <a name="cmdlet-attributes"></a>Cmdlet 属性

Windows PowerShell 定义可用于将常见功能添加到 cmdlet，而无需实现你自己的代码中的该功能的多个属性。 这包括 Cmdlet 属性，用于标识 Microsoft.NET Framework 类作为的 cmdlet，指定该 cmdlet，将公共属性标识为 cmdlet 的参数属性返回的.NET Framework 类型的 OutputType 特性参数和的详细信息。

## <a name="in-this-section"></a>本节内容

[Cmdlet 代码中的属性](./attributes-in-cmdlet-code.md)介绍 cmdlet 代码中使用属性的好处。

[属性类型](./attribute-types.md)介绍可以修饰 cmdlet 类的各种属性。

[别名属性声明](./alias-attribute-declaration.md)介绍如何定义的 cmdlet 参数名称的别名。

[Cmdlet 属性声明](./cmdlet-attribute-declaration.md)介绍如何为 cmdlet 定义.NET Framework 类。

[凭据属性声明](./credential-attribute-declaration.md)介绍了如何添加用于将转换到的字符串输入的支持[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象。

[OutputType 属性声明](./outputtype-attribute-declaration.md)介绍如何指定该 cmdlet 返回的.NET Framework 类型。

[参数特性声明](./parameter-attribute-declaration.md)介绍如何定义一个 cmdlet 的参数。

[ValidateCount 特性声明](./validatecount-attribute-declaration.md)介绍如何定义为参数允许使用多少参数。

[ValidateLength 特性声明](./validatelength-attribute-declaration.md)介绍如何定义参数自变量的长度 （以字符为单位）。

[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)介绍如何定义参数自变量的有效模式。

[ValidateRange 特性声明](./validaterange-attribute-declaration.md)介绍如何定义参数自变量的有效范围。

[ValidateSet 特性声明](./validateset-attribute-declaration.md)介绍如何定义参数自变量的可能值。

## <a name="reference"></a>引用

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

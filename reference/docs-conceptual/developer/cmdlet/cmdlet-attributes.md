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
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369956"
---
# <a name="cmdlet-attributes"></a>Cmdlet 属性

Windows PowerShell 定义多个属性，可用于向 cmdlet 添加常见功能，而无需在自己的代码中实现该功能。 这包括 Cmdlet 属性，该属性用于将 Microsoft .NET 框架类标识为 cmdlet 类、指定 cmdlet 返回的 .NET Framework 类型的 OutputType 属性、用于将公共属性标识为 cmdlet 的参数属性参数等等。

## <a name="in-this-section"></a>本部分内容

[Cmdlet 代码中的属性](./attributes-in-cmdlet-code.md)介绍使用 cmdlet 代码中的属性的好处。

[特性类型](./attribute-types.md)描述可以修饰 cmdlet 类的不同属性。

[Alias 特性声明](./alias-attribute-declaration.md)描述如何为 cmdlet 参数名称定义别名。

[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)描述如何将 .NET Framework 类定义为 cmdlet。

[Credential 特性声明](./credential-attribute-declaration.md)介绍如何添加对将字符串输入转换为[system.web](/dotnet/api/System.Management.Automation.PSCredential)对象的支持。

[OutputType 特性声明](./outputtype-attribute-declaration.md)描述如何指定 cmdlet 返回的 .NET Framework 类型。

[参数属性声明](./parameter-attribute-declaration.md)描述如何定义 cmdlet 的参数。

[ValidateCount 特性声明](./validatecount-attribute-declaration.md)描述如何定义参数允许的参数数量。

[ValidateLength 特性声明](./validatelength-attribute-declaration.md)描述如何定义参数参数的长度（以字符为字符）。

[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)描述如何定义参数参数的有效模式。

[ValidateRange 特性声明](./validaterange-attribute-declaration.md)描述如何定义参数参数的有效范围。

[ValidateSet 特性声明](./validateset-attribute-declaration.md)描述如何定义参数参数的可能值。

## <a name="reference"></a>引用

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

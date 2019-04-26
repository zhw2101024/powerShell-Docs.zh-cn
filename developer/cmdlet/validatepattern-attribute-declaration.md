---
title: ValidatePattern 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067121"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern 属性声明

ValidatePattern 属性指定的正则表达式模式，用于验证的 cmdlet 参数的参数。 Windows PowerShell 函数还可以使用此属性。

在 cmdlet 内调用 ValidatePattern 时，Windows PowerShell 运行时将 cmdlet 参数的参数转换为字符串，然后将该字符串 ValidatePattern 特性提供的模式进行比较。 转换后的字符串表示形式的参数而提供的模式与匹配时才运行该 cmdlet。 如果不匹配，是由 Windows PowerShell 运行时引发错误。

## <a name="syntax"></a>语法

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>参数

`RegexString` ([System.String](/dotnet/api/System.String)) 所需。 指定正则表达式，用于验证参数自变量。

选项 ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 可选的命名参数。 指定的按位组合[System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)标志，用于指定正则表达式选项。

## <a name="remarks"></a>备注

- 此属性可以使用仅一次，每个参数。

- 可以使用`Option`的属性来进一步定义模式参数。 例如，可以使该模式区分大小写。

- 如果此特性应用于一个集合，集合中的每个元素必须匹配的模式。

- 通过定义 ValidatePattern 特性[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)类。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

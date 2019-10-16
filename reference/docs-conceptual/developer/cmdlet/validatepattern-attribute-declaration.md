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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369156"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern 属性声明

ValidatePattern 属性指定用于验证 cmdlet 参数的参数的正则表达式模式。 此属性也可由 Windows PowerShell 函数使用。

在 cmdlet 中调用 ValidatePattern 时，Windows PowerShell 运行时将 cmdlet 参数的参数转换为字符串，然后将该字符串与 ValidatePattern 特性提供的模式进行比较。 仅当参数的转换字符串表示形式和提供的模式匹配时，才运行 cmdlet。 如果二者不匹配，则 Windows PowerShell 运行时将引发错误。

## <a name="syntax"></a>语法

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>参数

需要 `RegexString` （[system.string](/dotnet/api/System.String)）。 指定用于验证参数参数的正则表达式。

选项（[system.text.regularexpressions. system.text.regularexpressions.regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)）可选的命名参数。 指定指定正则表达式选项的[system.text.regularexpressions. system.text.regularexpressions.regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)标志的按位组合。

## <a name="remarks"></a>备注

- 此属性仅可用于每个参数一次。

- 可以使用特性的 @no__t 参数来进一步定义模式。 例如，可以使模式区分大小写。

- 如果将此特性应用于集合，则集合中的每个元素都必须与模式匹配。

- ValidatePattern 特性是由[Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)类定义的。

## <a name="see-also"></a>另请参阅

[System.web. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

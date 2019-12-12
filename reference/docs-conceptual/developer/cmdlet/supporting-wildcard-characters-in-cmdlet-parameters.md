---
title: 支持在 Cmdlet 参数中使用通配符
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365306"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>支持在 Cmdlet 参数中使用通配符

通常，你必须将 cmdlet 设计为针对一组资源而不是针对单个资源运行。 例如，cmdlet 可能需要查找数据存储区中具有相同名称或扩展名的所有文件。 设计将对一组资源运行的 cmdlet 时，必须提供对通配符字符的支持。

> [!NOTE]
> 使用通配符*有时称为 "组合"。*

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>使用通配符的 Windows PowerShell Cmdlet

 许多 Windows PowerShell cmdlet 都支持为其参数值提供通配符。 例如，几乎每个具有 `Name` 或 `Path` 参数的 cmdlet 都支持这些参数的通配符。 （尽管大多数包含 `Path` 参数的 cmdlet 也具有不支持通配符的 `LiteralPath` 参数。）以下命令显示了如何使用通配符来返回当前会话中其名称包含 Get 谓词的所有 cmdlet。

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>支持的通配符

Windows PowerShell 支持以下通配符。

| 通配符 |                             描述                             |  示例   |     匹配      | 不匹配 |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | 匹配零个或多个字符（从指定位置开始） | `a*`       | A、ag、Apple     |                |
| ?        | 匹配指定位置的任何字符                     | `?n`       | ，在中，在       | 为名            |
| [ ]      | 匹配一系列字符                                       | `[a-l]ook` | 书籍，库，查找 | nook，拍摄     |
| [ ]      | 匹配指定字符                                    | `[bn]ook`  | 书籍，nook       | 库，查找     |

设计支持通配符的 cmdlet 时，允许组合通配符字符。 例如，以下命令使用 `Get-ChildItem` cmdlet 来检索 c:\Techdocs 文件夹中所有以字母 "a" 到 "l" 开头的 .txt 文件。

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

前面的命令使用范围通配符 `[a-l]` 来指定文件名应以字符 "a" 到 "l" 开头，并使用 `*` 通配符作为文件名第一个字母与 **.txt**扩展名之间的任何字符的占位符。

下面的示例使用范围通配符模式，该模式不包括字母 "d"，但包含 "a" 到 "f" 的所有其他字母。

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>在通配符模式中处理文本字符

如果指定的通配符模式包含不应解释为通配符的原义字符，请使用反撇号字符（`` ` ``）作为转义符。 当你为 PowerShell API 指定整数字符时，请使用单个反撇号。 在 PowerShell 命令提示符处指定原义字符时，请使用两个反撇号。

例如，下面的模式包含两个必须按原义取的方括号。

使用 PowerShell API 时，请使用：

- "John Smith \`[* ']"

在 PowerShell 命令提示符下使用时：

- "John Smith \`\`[*\`"] "

此模式匹配 "John Smith [行销]" 或 "John Smith [开发]"。 例如：

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet 输出和通配符

当 cmdlet 参数支持通配符时，操作通常会生成一个数组输出。
有时，因为用户可能只使用一个项，所以不能提供支持数组输出的意义。 例如，`Set-Location` cmdlet 不支持数组输出，因为用户仅设置了一个位置。 在这种情况下，该 cmdlet 仍支持通配符，但会强制将分辨率转换为单一位置。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern 类](/dotnet/api/system.management.automation.wildcardpattern)

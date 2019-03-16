---
title: 中的 Cmdlet 参数支持通配符字符 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059603"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>支持在 Cmdlet 参数中使用通配符

通常，您将必须设计用于运行针对一组资源，而不是针对单个资源的 cmdlet。 例如，一个 cmdlet 可能需要在具有相同的名称或扩展的数据存储区中找到的所有文件。 在设计的 cmdlet，将针对资源组的运行时，你必须提供支持的通配符字符。

> [!NOTE]
> 使用通配符字符有时称为*通配*。

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>使用通配符的 Windows PowerShell Cmdlet

 许多 Windows PowerShell cmdlet 的参数值支持通配符字符。 例如，几乎每个 cmdlet，具有`Name`或`Path`参数支持通配符字符为这些参数。 (尽管大多数 cmdlet 都`Path`参数还具有`LiteralPath`不支持通配符字符的参数。)以下命令演示如何使用通配符字符以返回名称中包含 Get 谓词在当前会话中的所有 cmdlet。

 **PS > get 命令 get-\***

## <a name="supported-wildcard-characters"></a>受支持的通配符字符

Windows PowerShell 支持下列通配符。

|通配符字符|说明|示例|匹配|不匹配|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|匹配零个或多个字符，从指定位置开始|a*|A，ag Apple||
|?|位于指定位置的匹配任何字符|？ n|中，在|运行|
|[ ]|匹配字符的范围|[a-l]ook|书籍、 cook 外观|花费了|
|[ ]|匹配指定的字符|[bc]ook|书籍、 cook|查找|

在设计时支持通配符的 cmdlet，允许的通配符字符的组合。 例如，下面的命令使用`Get-ChildItem`cmdlet 来检索所有.txt 文件，位于 c:\Techdocs 文件夹然后开头的字母"a"到"l。"

**get-childitem c:\techdocs\\[a-l]\*.txt**

前一个命令使用范围通配符 **[a-l]** 以指定的文件名称应开始的字符"a"到"l。" 该命令将使用 * 通配符作为.txt 扩展名的文件的名称的第一个字母之间的任何字符的占位符。

下面的示例使用范围通配符模式排除字母"d"，但包含从"a"到"f。"的所有其他字母

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>处理文本字符的通配符模式

如果所指定的通配符模式包含原义字符，使用反撇号字符 （'） 作为转义符。 当以编程方式指定的原义字符时，请使用单个反引号。 当指定文本字符的命令提示符处时，使用两个反撇号。 例如，以下模式包含必须按字面的两个方括号。

"John Smith \`[*']"（指定以编程方式）

"John Smith \` \`[*\`]"（在命令提示符下指定）

此模式匹配"John Smith [营销]"或"John Smith [开发]"。

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet 的输出和通配符

如果 cmdlet 参数支持通配符，cmdlet 操作通常生成数组输出。 有时，它成为支持输出，因为用户可能会一次使用单个项的数组没有意义。 例如， `Set-Location` cmdlet 支持输出，因为用户设置的单个位置的数组。 在此情况下，该 cmdlet 仍然支持通配符，但它会强制解析为单个位置。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern 类](/dotnet/api/system.management.automation.wildcardpattern)

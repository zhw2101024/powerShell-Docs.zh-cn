---
title:  使用熟悉的命令名称
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  021e2424-c64e-4fa5-aa98-aa6405758d5d
---

# 使用熟悉的命令名称
使用称为*别名*的机制，Windows PowerShell 允许用户通过备用名称引用命令。 别名允许具有其他 Shell 经验的用户重复使用其已知的常见命令名称在 Windows PowerShell 中执行类似操作。 虽然我们不会详细讨论 Windows PowerShell 别名，但当你开始使用 Windows PowerShell 时，你仍可以使用它们。

别名将你键入的命令名称与另一个命令相关联。 例如，Windows PowerShell 具有名为 **Clear-Host** 的内部函数，该函数清空输出窗口。 如果你在命令提示符处输入 **cls** 或 **clear** 命令，Windows PowerShell 会将其解释为 **Clear-Host** 函数的别名，并运行 **Clear-Host** 函数。

此功能可帮助用户了解 Windows PowerShell。 首先，大多数 Cmd.exe 和 UNIX 用户拥有大量已知的常用命令，并且尽管与 Windows PowerShell 相当的程序可能不会产生完全相同的结果，但它们在形式上的接近程度已足以让用户可使用它们来进行工作，而无需先记住 Windows PowerShell 名称。 其次，如果用户已熟悉一种 Shell，而在学习新的 Shell 时却面临挫折，其主要原因是“手指记忆”所导致的错误。 如果你已使用 Cmd.exe 多年，当你的屏幕满是输出并且想要清理它时，你会条件反射地键入 **cls** 命令然后按下 ENTER 键。 如果在 Windows PowerShel 中没有用于 **Clear-Host** 函数的别名，你只会收到一个错误消息“**‘cls’ 不视为 cmdlet、函数、可操作程序或脚本文件。**” 然后便不知道该如何清除输出了。

下面是可在 Windows PowerShell 中使用的常见 Cmd.exe 和 UNIX 命令的简短列表：

|||||
|-|-|-|-|
|cat|dir|装载|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|类型|
|del|lp|r|write|
|diff|ls|ren||

如果你发现自己正条件发射性地使用其中一种命令并且想要了解本机 Windows PowerShell 命令的真实名称，可以使用 **Get-Alias** 命令：

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

为了让示例更具可读性，Windows PowerShell 用户指南通常避免使用别名。 但是，如果你要处理来自其他源的任意 Windows PowerShell 代码段，或想要定义你自己的别名，这么尽早了解有关别名的知识仍然十分有用。 本部分的其余部分将讨论标准别名以及如何定义你自己的别名。

### 解释标准别名
与上述别名不同，上述别名旨在实现与其他接口的名称兼容性，而 Windows PowerShell 内置的别名一般旨在提供便利性。 这些简短的名称可快速键入，但如果你不知道其所指的内容，你便无法读取。

Windows PowerShell 尝试通过提供一组基于常见谓词和名词的简写名称的标准别名，实现明晰度和简洁度之间的折中。 这样，如果你知道简写名称，便可使用一组常见 cmdlet 的可读核心别名。 例如，在标准别名中，谓词 **Get** 缩写为 **g**，谓词 **Set** 缩写为 **s**，名词 **Item** 缩写为 **i**，名词 **Location** 缩写为 **l**，名称 Command 缩写为 **cm**。

下面是一个解释其工作原理的简短示例。 Get-Item 的标准别名来自 Get 的 **g** 和 Item 的 **i** 的组合：**gi**。 Set-Item 的标准别名来自 Set 的 **s** 和 Item 的 **i** 的组合：**si**。 Get-Location 的标准别名来自 Get 的 **g** 和 Location 的 **l** 的组合：**gl**。 Set-Location 的标准别名来自 Set 的 **s** 和 Location 的 **l** 的组合：**sl**。 Get-Command 的标准别名来自 Get 的 **g** 和 Command 的 **cm** 的组合：**gcm**。 不存在 Set-Command cmdlet，但如果存在，我们可以猜出它的标准别名来自 Set 的 **s** 和 Command 的 **cm**：**scm**。 此外，熟悉 Windows PowerShell 别名的人如果遇到 **scm**，他们将能够猜到此别名指的是 Set-Command。

### 创建新别名
你可以使用 Set-Alias cmdlet 创建自己的别名。 例如，以下语句创建“解释标准别名”中所讨论的标准 cmdlet 别名：

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

在内部，Windows PowerShell 会在启动过程中使用这样的别名，但这些别名不可更改。 如果尝试实际执行其中一个命令，你将获得一个错误，该错误会说明别名无法进行修改。 例如：

<pre>PS> Set-Alias -Name gi -Value Get-Item Set-Alias：别名不可编写，因为别名 gi 为只读或常量，且无法写入。
At line:1 char:10 + Set-Alias  <<<< -Name gi -Value Get-Item</pre>



<!--HONumber=May16_HO2-->



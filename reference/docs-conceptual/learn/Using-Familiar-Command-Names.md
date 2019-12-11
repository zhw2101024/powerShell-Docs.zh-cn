---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用熟悉的命令名称
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030890"
---
# <a name="using-familiar-command-names"></a>使用熟悉的命令名称

PowerShell 支持别名以通过备用名称引用命令。 别名允许具有其他 Shell 经验的用户使用其已知的常见命令名称在 PowerShell 中执行类似操作。

别名将新名称与其他命令关联。 例如，PowerShell 具有名为 `Clear-Host` 的内部函数，该函数清空输出窗口。 可以在命令提示符下键入 `cls` 或 `clear` 别名。 PowerShell 解释这些别名并运行 `Clear-Host` 函数。

此功能可帮助用户了解 PowerShell。 首先，大多数 cmd.exe  和 Unix 用户都要使用大量命令，用户通过名称已经了解这些命令。 PowerShell 等效项可能不会产生相同的结果。 但是，结果非常接近，用户可以在不知道 PowerShell 命令名称的情况下完成工作。 学习新的命令 shell 时，“手指记忆”是另一个令人沮丧的主要原因。 如果你已使用 cmd.exe  多年，则可能会条件反射地键入 `cls` 命令来清除屏幕。 如果没有 `Clear-Host` 的别名，则会收到一条错误消息，并且不知道如何操作才能清除输出。

以下列表显示可在 PowerShell 中使用的常见 cmd.exe  和 UNIX 命令：

|||||
|-|-|-|-|
|cat|dir|mount|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|type|
|del|lp|r|write|
|diff|ls|ren||

`Get-Alias` cmdlet 显示与别名关联的本机 PowerShell 命令的真实名称。

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>解释标准别名

我们之前描述的别名时为了实现与其他命令 shell 的名称兼容性而设计的。
PowerShell 中内置的大多数别名都是为了实现简洁性而设计的。 较短的名称更容易键入，但如果你不知道它们所指的是什么，则难以理解。

PowerShell 别名尝试兼顾清晰度和简洁性。 PowerShell 为常见名词和谓词使用一组标准的别名。

示例缩写：

| 名词或谓词 | 缩写 |
|--------------|--------------|
| Get          | g            |
| Set          | s            |
| Item         | i            |
| Location     | l            |
| Command      | cm           |
| Alias        | al           |

了解简写名称后，这些别名是可以理解的。

| Cmdlet 名称    | Alias |
|----------------|-------|
| `Get-Item`     | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

熟悉 PowerShell 别名后，就很容易猜到 sal  别名指的是 `Set-Alias`。

## <a name="creating-new-aliases"></a>创建新别名

可以使用 `Set-Alias` cmdlet 创建自己的别名。 例如，以下语句创建之前讨论的标准 cmdlet 别名：

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

在内部，PowerShell 会在启动过程中使用类似的命令，但这些别名不可更改。
如果尝试执行其中一个命令，你将收到一个错误，该错误说明别名无法进行修改。 例如：

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```

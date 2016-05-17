---
title:  获取有关命令的信息
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
---

# 获取有关命令的信息
Windows PowerShell **Get-Command** cmdlet 获取在当前会话中可用的所有命令。 当在 Windows PowerShell 提示符下键入 **Get-Command** 时，将看到类似于以下内容的输出：

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

该输出与 Cmd.exe 的帮助输出非常相似：内部命令的表格式摘要。 在如上所示的 **Get-Command** 命令输出摘录中，显示的每个命令都具有 Cmdlet 的 CommandType。 Cmdlet 是 Windows PowerShell 的内部命令类型 - 此类型大致对应于 Cmd.exe 的 **dir** 和 **cd** 命令，以及 UNIX shell 中的 BASH 等内置命令。

在 **Get-Command** 命令的输出中，所有定义均以省略号 (...) 结尾，表示 PowerShell 无法在可用空间内显示所有内容。 当 Windows PowerShell 显示输出时，它将输出格式设置为文本，然后对其进行排列以使数据恰好适应窗口。 稍后我们将在有关格式设置的部分中对此进行讨论。

**Get-Command** cmdlet 具有可获取每个 cmdlet 语法的 **Syntax** 参数。 若要获取 Get-Help cmdlet 的语法，请使用以下命令：

**Get-Command Get-Help -Syntax**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### 显示可用的命令类型
**Get-Command** 命令不会列出 Windows PowerShell 中的每个可用命令。 **Get-Command** 命令仅列出当前会话中的 cmdlet。 实际上，Windows PowerShell 支持几种其他类型的命令。 别名、函数和脚本也是 Windows PowerShell 命令，尽管在 Windows PowerShell 用户指南中并未对它们进行详细讨论。 属于可执行文件，或具有已注册的文件类型处理程序的外部文件也被归类为命令。

若要获取会话中的所有命令，请键入：

```
Get-Command *
```

由于此列表包含搜索路径中的外部文件，因此它可能包含数千个项。 查看一组缩减的命令更加有用。

若要获取其他类型的本机命令，请使用 **Get-Command** cmdlet 的 **CommandType** 参数。

> [!NOTE]
> 星号 (*) 用于 Windows PowerShell 命令参数中的通配符匹配。 * 表示“匹配一个或多个任意字符”。 你可以键入 **Get-Command a&#42;** 查找所有以字母“a”开头的命令。 与 Cmd.exe 中的通配符匹配不同，Windows PowerShell 的通配符还将匹配句点。

若要获取命令别名（即命令的已分配昵称），请键入：

```
Get-Command -CommandType Alias
```

若要获取当前会话中的函数，请键入：

```
Get-Command -CommandType Function
```

若要显示 Windows PowerShell 搜索路径中的脚本，请键入：

```
Get-Command -CommandType Script
```



<!--HONumber=May16_HO2-->



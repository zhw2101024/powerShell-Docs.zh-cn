---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 获取有关命令的信息
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401034"
---
# <a name="getting-information-about-commands"></a>获取有关命令的信息

PowerShell `Get-Command` 显示在当前会话中可用的命令。
运行 `Get-Command` cmdlet 时，会看到类似于以下输出的内容：

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

该输出与 cmd.exe 的帮助输出非常相似：内部命令的表格式摘要。 在如上所示的 `Get-Command` 命令输出摘录中，显示的每个命令都具有 Cmdlet 的 CommandType。 cmdlet 是 PowerShell 的内部命令类型。 此类型大致对应于 cmd.exe 中的 `dir` 和 `cd` 等命令，或者像 bash 这样的 Unix shell 的内置命令。

`Get-Command` cmdlet 具有可返回每个 cmdlet 语法的 Syntax 参数。 下面的示例演示如何获取 `Get-Help` cmdlet 的语法：

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>显示可用的命令类型

`Get-Command` 命令仅列出当前会话中的 cmdlet。 实际上，PowerShell 支持几种其他类型的命令：

- 别名
- 功能
- 脚本

外部可执行文件，或具有已注册的文件类型处理程序的文件也被归类为命令。

若要获取会话中的所有命令，请键入：

```powershell
Get-Command *
```

此列表包含搜索路径中的外部命令，因此它可能包含数千个项。
查看一组缩减的命令更加有用。

> [!NOTE]
> 星号 (\*) 用于 PowerShell 命令参数中的通配符匹配。 \* 表示“匹配一个或多个任意字符”。 可以键入 `Get-Command a*` 查找所有以字母“a”开头的命令。 与 cmd.exe 中的通配符匹配不同，PowerShell 的通配符还会匹配句点。

使用 `Get-Command` 的 CommandType 参数可以获取其他类型的本机命令。
cmdlet 时返回的仲裁资源的信息。

若要获取命令别名（即命令的已分配昵称），请键入：

```powershell
Get-Command -CommandType Alias
```

若要获取当前会话中的函数，请键入：

```powershell
Get-Command -CommandType Function
```

若要显示 PowerShell 搜索路径中的脚本，请键入：

```powershell
Get-Command -CommandType Script
```
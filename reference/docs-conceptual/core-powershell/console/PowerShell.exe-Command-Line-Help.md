---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: PowerShell.exe 命令行帮助
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133068"
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe 命令行帮助

可以使用 PowerShell.exe 从另一工具（如 Cmd.exe）的命令行启动 PowerShell 会话，或在 PowerShell 命令行中使用它来启动新会话。 使用参数自定义会话。

## <a name="syntax"></a>语法

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>参数

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

接受命令的 base-64 编码字符串版本。 使用此参数将命令提交到需要复杂的引号或大括号的 PowerShell。

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

为当前会话设置默认执行策略，并将其保存在 $env:PSExecutionPolicyPreference 环境变量中。 此参数不会更改在注册表中设置的 PowerShell 执行策略。 若要了解 PowerShell 执行策略（包括有效值列表），请参阅 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

在本地作用域中运行指定的脚本（“dot-sourced”），以便脚本创建的函数和变量在当前会话中可用。 输入脚本文件路径和任何参数。 “文件”必须是命令中的最后一个参数。 在 -File 参数之后键入的所有值都被视为脚本文件路径和传递到该脚本的参数。

传递给脚本的参数作为文字字符串（在当前 shell 的解释后）传递。 例如，如果处于 cmd.exe，并要传递环境变量值，则使用 cmd.exe 语法：`powershell -File .\test.ps1 -Sample %windir%`。在此示例中，脚本将收到文本字符串 `$env:windir`，而非该环境变量的值：`powershell -File .\test.ps1 -Sample $env:windir`

### <a name="-inputformat-text--xml"></a>\-InputFormat {文本 |XML}

描述发送到 PowerShell 的数据格式。 有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。

### <a name="-mta"></a>-Mta

使用多线程单元启动 PowerShell。 此参数是在 PowerShell 3.0 中引入的。 在 PowerShell 3.0 中，单线程单元 (STA) 是默认设置。 在 PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。

### <a name="-noexit"></a>-NoExit

运行启动命令后不退出。

### <a name="-nologo"></a>-NoLogo

启动时隐藏版权横幅。

### <a name="-noninteractive"></a>-NonInteractive

不向用户显示交互式提示。

### <a name="-noprofile"></a>-NoProfile

不加载 PowerShell 配置文件。

### <a name="-outputformat-text--xml"></a>-OutputFormat {文本 | XML}

确定 PowerShell 输出内容的格式。 有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

加载指定的 PowerShell 控制台文件。 输入控制台文件的路径和名称。 若要创建控制台文件，请在 PowerShell 中运行 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet。

### <a name="-sta"></a>-Sta

使用单线程单元启动 PowerShell。 在 PowerShell 3.0 中，单线程单元 (STA) 是默认设置。 在 PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

启动 PowerShell 的指定版本。 必须在系统上安装指定的版本。 如果计算机上已安装 PowerShell 3.0，则有效值为“2.0”和“3.0”。 默认值为“3.0”。

如果未安装 PowerShell 3.0，则唯一的有效值为“2.0”。 将忽略其他值。

有关详细信息，请参阅[安装 Windows PowerShell](../../setup/installing-windows-powershell.md)。

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

为会话设置窗口样式。 有效值包括 Normal、Minimized、Maximized 和 Hidden。

### <a name="-command"></a>-Command

执行指定的命令（和所有参数），就像是在 PowerShell 命令提示符下键入的命令一样。 在执行后，除非指定 `-NoExit` 参数，否则 PowerShell 会退出。
`-Command` 后面的任何文本都会作为单个命令行发送到 PowerShell。 这与 `-File` 处理发送到脚本的参数的方式不同。

Command 的值可以为“-”、字符串。 或脚本块。 如果 Command 的值为“-”，则将从标准输入读取命令文本。

脚本块必须括在大括号 ({}) 中。 只有在 PowerShell 中运行 PowerShell.exe 时才能指定脚本块。 脚本的结果作为反序列化 XML 对象（而非活动对象）返回到父外壳程序。

如果 Command 的值为字符串，则 Command 必须是该命令的最后一个参数，因为其后键入的所有字符都会被解释为它的参数。

若要编写运行 PowerShell 命令的字符串，请使用以下格式：

```powershell
"& {<command>}"
```

引号指示一个字符串，调用运算符 (&) 用于执行命令。

### <a name="-help---"></a>-Help、-?、/?

显示 powershell.exe 的语法。 如果要在 PowerShell 中键入 PowerShell.exe 命令，请以连字符 (-) 作为命令参数的前缀，不要使用正斜杠 (/)。 你可以在 Cmd.exe 中使用连字符或正斜杠。

> [!NOTE]
> 疑难解答注释：在 PowerShell 2.0 中，在 Windows PowerShell 控制台中启动某些程序将失败，LastExitCode 为 0xc0000142。

## <a name="examples"></a>示例

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

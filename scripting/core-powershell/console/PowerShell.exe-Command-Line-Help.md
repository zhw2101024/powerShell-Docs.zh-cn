---
title: PowerShell.exe 命令行帮助
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
---
# PowerShell.exe 命令行帮助
启动 Windows PowerShell 会话。 可以使用 PowerShell.exe 从另一工具（如 Cmd.exe）的命令行启动 Windows PowerShell 会话，或在 Windows PowerShell 命令行中使用它来启动新会话。 使用参数自定义会话。

## 语法

```
PowerShell[.exe]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
       [-File <FilePath> [<Args>]]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

## 参数

### -EncodedCommand <Base64EncodedCommand>
接受命令的 base-64 编码字符串版本。 使用此参数将命令提交到需要复杂的引号或大括号的 Windows PowerShell。

### -ExecutionPolicy <ExecutionPolicy>
为当前会话设置默认执行策略，并将其保存在 $env:PSExecutionPolicyPreference 环境变量中。 此参数不会更改在注册表中设置的 Windows PowerShell 执行策略。 有关 Windows PowerShell 执行策略的信息（包括有效值列表），请参阅 _Execution_Policies (http://go.microsoft.com/fwlink/?LinkID\=135170)。

### -File <FilePath> [<Parameters>]
在本地作用域中运行指定的脚本（“dot-sourced”），以便脚本创建的函数和变量在当前会话中可用。 输入脚本文件路径和任何参数。 **File** 必须是命令中的最后一个参数，因为在 **File** 参数名称后键入的所有字符都会被解释为后跟脚本参数及其值的脚本文件路径。

**File** 参数的值中可以包括脚本参数和参数值。 例如： `-File .\Get-Script.ps1 -Domain Central`

通常，将包括或忽略脚本的开关参数。 例如，下面的命令使用 Get-Script.ps1 脚本文件的 **All** 参数： `-File .\Get-Script.ps1 -All`

在极少数情况下，你可能需要为开关参数提供一个布尔值。 若要在 **File** 参数的值中为开关参数提供布尔值，请将参数名称和参数值括在大括号中，如下所示： `-File .\Get-Script.ps1 {-All:$False}`

### -InputFormat {文本 |XML}
描述发送到 Windows PowerShell 的数据格式。 有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。

### -Mta
使用多线程单元启动 Windows PowerShell。 此参数是在 Windows PowerShell 3.0 中引入的。 在 Windows PowerShell 3.0 中，单线程单元 (STA) 是默认设置。 在 Windows PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。

### -NoExit
运行启动命令后不退出。

### -NoLogo
启动时隐藏版权横幅。

### -NonInteractive
不向用户显示交互式提示。

### -NoProfile
不加载 Windows PowerShell 配置文件。

### -OutputFormat {文本 | XML}
确定 Windows PowerShell 输出内容的格式。 有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。

### -PSConsoleFile <FilePath>
加载指定的 Windows PowerShell 控制台文件。 输入控制台文件的路径和名称。 若要创建控制台文件，请使用 Windows PowerShell 中的 [Export-console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet。

### -Sta
使用单线程单元启动 Windows PowerShell。 在 Windows PowerShell 3.0 中，单线程单元 (STA) 是默认设置。 在 Windows PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。

### -Version <Windows PowerShell Version>
启动 Windows PowerShell 的指定版本。 必须在系统上安装指定的版本。 如果计算机上已安装 Windows PowerShell 3.0，则有效值为“2.0”和“3.0”。 默认值为“3.0”。

如果未安装 Windows PowerShell 3.0，则唯一的有效值为“2.0”。 将忽略其他值。

有关详细信息，请参阅 [Windows PowerShell 入门 [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd) 中的“安装 Windows PowerShell”.

### -WindowStyle <Window style>
为会话设置窗口样式。 有效值包括 Normal、Minimized、Maximized 和 Hidden。

### -Command
执行指定的命令和所有参数，就像从 Windows PowerShell 命令提示符下键入的命令一样，如果未指定 NoExit，则随后退出。

Command 的值可以为“-”、字符串。 或脚本块。 如果 Command 的值为“-”，则将从标准输入读取命令文本。

脚本块必须括在大括号 ({}) 中。 只有在 Windows PowerShell 中运行 PowerShell.exe 时才能指定脚本块。 脚本的结果作为反序列化 XML 对象（而非活动对象）返回到父外壳程序。

如果 Command 的值为字符串，则 **Command** 必须是该命令的最后一个参数，因为其后键入的所有字符都会被解释为它的参数。

若要编写运行 Windows PowerShell 命令的字符串，请使用以下格式：

```
"& {<command>}"
```

其中，引号指示一个字符串，调用运算符 (&) 用于执行命令。

### -Help, -?, /?
显示此消息。 如果要在 Windows PowerShell 中键入 PowerShell.exe 命令，请以连字符 (-) 作为命令参数的前缀，不要使用正斜杠 (/)。 你可以在 Cmd.exe 中使用连字符或正斜杠。

> [!NOTE]
> 疑难解答注释：在 Windows PowerShell 2.0 中，在 Windows PowerShell 控制台中启动某些程序将失败，LastExitCode 为 0xc0000142。

## 示例

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```



<!--HONumber=May16_HO2-->



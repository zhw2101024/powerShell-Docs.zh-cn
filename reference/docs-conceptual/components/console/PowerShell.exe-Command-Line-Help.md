---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: PowerShell.exe 命令行帮助
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400435"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="215af-103">PowerShell.exe 命令行帮助</span><span class="sxs-lookup"><span data-stu-id="215af-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="215af-104">可以使用 PowerShell.exe 从另一工具（如 Cmd.exe）的命令行启动 PowerShell 会话，或在 PowerShell 命令行中使用它来启动新会话。</span><span class="sxs-lookup"><span data-stu-id="215af-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="215af-105">使用参数自定义会话。</span><span class="sxs-lookup"><span data-stu-id="215af-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="215af-106">语法</span><span class="sxs-lookup"><span data-stu-id="215af-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="215af-107">参数</span><span class="sxs-lookup"><span data-stu-id="215af-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="215af-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="215af-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="215af-109">接受命令的 base-64 编码字符串版本。</span><span class="sxs-lookup"><span data-stu-id="215af-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="215af-110">使用此参数将命令提交到需要复杂的引号或大括号的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="215af-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="215af-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="215af-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="215af-112">为当前会话设置默认执行策略，并将其保存在 $env:PSExecutionPolicyPreference 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="215af-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="215af-113">此参数不会更改在注册表中设置的 PowerShell 执行策略。</span><span class="sxs-lookup"><span data-stu-id="215af-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="215af-114">若要了解 PowerShell 执行策略（包括有效值列表），请参阅 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="215af-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="215af-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="215af-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="215af-116">在本地作用域中运行指定的脚本（“dot-sourced”），以便脚本创建的函数和变量在当前会话中可用。</span><span class="sxs-lookup"><span data-stu-id="215af-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="215af-117">输入脚本文件路径和任何参数。</span><span class="sxs-lookup"><span data-stu-id="215af-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="215af-118">“文件”必须是命令中的最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="215af-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="215af-119">在 -File 参数之后键入的所有值都被视为脚本文件路径和传递到该脚本的参数。</span><span class="sxs-lookup"><span data-stu-id="215af-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="215af-120">传递给脚本的参数作为文字字符串（在当前 shell 的解释后）传递。</span><span class="sxs-lookup"><span data-stu-id="215af-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="215af-121">例如，如果处于 cmd.exe，并且想要将环境变量值传递，将使用 cmd.exe 语法： `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="215af-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="215af-122">与此相反，运行`powershell.exe -File .\test.ps1 -TestParam $env:windir`中接收的文本字符串在脚本中的 cmd.exe 结果`$env:windir`因为它具有到当前的 cmd.exe shell 没有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="215af-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="215af-123">`$env:windir`环境变量引用样式_可以_内部使用`-Command`参数，因为它那里将解释为 PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="215af-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="215af-124">\-InputFormat {文本 |XML}</span><span class="sxs-lookup"><span data-stu-id="215af-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="215af-125">描述发送到 PowerShell 的数据格式。</span><span class="sxs-lookup"><span data-stu-id="215af-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="215af-126">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="215af-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="215af-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="215af-127">-Mta</span></span>

<span data-ttu-id="215af-128">使用多线程单元启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="215af-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="215af-129">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="215af-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="215af-130">在 PowerShell 3.0 中，单线程单元 (STA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="215af-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="215af-131">在 PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="215af-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="215af-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="215af-132">-NoExit</span></span>

<span data-ttu-id="215af-133">运行启动命令后不退出。</span><span class="sxs-lookup"><span data-stu-id="215af-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="215af-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="215af-134">-NoLogo</span></span>

<span data-ttu-id="215af-135">启动时隐藏版权横幅。</span><span class="sxs-lookup"><span data-stu-id="215af-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="215af-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="215af-136">-NonInteractive</span></span>

<span data-ttu-id="215af-137">不向用户显示交互式提示。</span><span class="sxs-lookup"><span data-stu-id="215af-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="215af-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="215af-138">-NoProfile</span></span>

<span data-ttu-id="215af-139">不加载 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="215af-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="215af-140">-OutputFormat {文本 | XML}</span><span class="sxs-lookup"><span data-stu-id="215af-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="215af-141">确定 PowerShell 输出内容的格式。</span><span class="sxs-lookup"><span data-stu-id="215af-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="215af-142">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="215af-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="215af-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="215af-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="215af-144">加载指定的 PowerShell 控制台文件。</span><span class="sxs-lookup"><span data-stu-id="215af-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="215af-145">输入控制台文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="215af-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="215af-146">若要创建控制台文件，请在 PowerShell 中运行 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="215af-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="215af-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="215af-147">-Sta</span></span>

<span data-ttu-id="215af-148">使用单线程单元启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="215af-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="215af-149">在 PowerShell 3.0 中，单线程单元 (STA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="215af-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="215af-150">在 PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="215af-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="215af-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="215af-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="215af-152">启动 PowerShell 的指定版本。</span><span class="sxs-lookup"><span data-stu-id="215af-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="215af-153">必须在系统上安装指定的版本。</span><span class="sxs-lookup"><span data-stu-id="215af-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="215af-154">如果计算机上已安装 PowerShell 3.0，则有效值为“2.0”和“3.0”。</span><span class="sxs-lookup"><span data-stu-id="215af-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="215af-155">默认值为“3.0”。</span><span class="sxs-lookup"><span data-stu-id="215af-155">The default value is "3.0".</span></span>

<span data-ttu-id="215af-156">如果未安装 PowerShell 3.0，则唯一的有效值为“2.0”。</span><span class="sxs-lookup"><span data-stu-id="215af-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="215af-157">将忽略其他值。</span><span class="sxs-lookup"><span data-stu-id="215af-157">Other values are ignored.</span></span>

<span data-ttu-id="215af-158">有关详细信息，请参阅[安装 Windows PowerShell](../../setup/installing-windows-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="215af-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="215af-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="215af-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="215af-160">为会话设置窗口样式。</span><span class="sxs-lookup"><span data-stu-id="215af-160">Sets the window style for the session.</span></span> <span data-ttu-id="215af-161">有效值包括 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="215af-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="215af-162">-Command</span><span class="sxs-lookup"><span data-stu-id="215af-162">-Command</span></span>

<span data-ttu-id="215af-163">执行指定的命令（和所有参数），就像是在 PowerShell 命令提示符下键入的命令一样。</span><span class="sxs-lookup"><span data-stu-id="215af-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="215af-164">在执行之后，PowerShell 退出除非**NoExit**指定参数。</span><span class="sxs-lookup"><span data-stu-id="215af-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="215af-165">`-Command` 后面的任何文本都会作为单个命令行发送到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="215af-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="215af-166">这与 `-File` 处理发送到脚本的参数的方式不同。</span><span class="sxs-lookup"><span data-stu-id="215af-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="215af-167">值`-Command`可以是"-"，一个字符串或脚本块。</span><span class="sxs-lookup"><span data-stu-id="215af-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="215af-168">该命令的结果作为反序列化 XML 对象，而非活动对象返回到父外壳程序。</span><span class="sxs-lookup"><span data-stu-id="215af-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="215af-169">如果的值`-Command`是"-"，从标准输入读取命令文本。</span><span class="sxs-lookup"><span data-stu-id="215af-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="215af-170">时的值`-Command`是一个字符串，**命令**_必须_是最后一个参数指定，因为该命令将被解释为命令参数后键入的所有字符。</span><span class="sxs-lookup"><span data-stu-id="215af-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="215af-171">**命令**参数仅接受执行的脚本块时它可以识别的值传递给`-Command`作为脚本块类型。</span><span class="sxs-lookup"><span data-stu-id="215af-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="215af-172">这是_仅_可能从另一个 PowerShell 主机中运行 PowerShell.exe 时。</span><span class="sxs-lookup"><span data-stu-id="215af-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="215af-173">类型可能包含中的现有变量、 返回由表达式，或已分析的 PowerShell 脚本块括在大括号中的文本的脚本块的形式托管`{}`之前传递给 PowerShell.exe。</span><span class="sxs-lookup"><span data-stu-id="215af-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="215af-174">在 cmd.exe，没有就没有脚本块 （或脚本块类型） 中，因此传递给的值**命令**将_始终_是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="215af-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="215af-175">您可以编写一个脚本块内的字符串，但而不是正在执行它的行为完全像你在典型的 PowerShell 提示符下键入它，请打印脚本的内容阻止回给你。</span><span class="sxs-lookup"><span data-stu-id="215af-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="215af-176">字符串传递给`-Command`仍将继续执行作为 PowerShell，因此脚本块的大括号通常不需要首先从 cmd.exe 运行时。</span><span class="sxs-lookup"><span data-stu-id="215af-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="215af-177">若要执行内联脚本块内一个字符串，定义[调用运算符](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-)`&`可用：</span><span class="sxs-lookup"><span data-stu-id="215af-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="215af-178">-Help、-?、/?</span><span class="sxs-lookup"><span data-stu-id="215af-178">-Help, -?, /?</span></span>

<span data-ttu-id="215af-179">显示 powershell.exe 的语法。</span><span class="sxs-lookup"><span data-stu-id="215af-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="215af-180">如果要在 PowerShell 中键入 PowerShell.exe 命令，请以连字符 (-) 作为命令参数的前缀，不要使用正斜杠 (/)。</span><span class="sxs-lookup"><span data-stu-id="215af-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="215af-181">你可以在 Cmd.exe 中使用连字符或正斜杠。</span><span class="sxs-lookup"><span data-stu-id="215af-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="215af-182">故障排除注释：在 PowerShell 2.0 中中, 启动某些程序在 Windows PowerShell 控制台失败，lastexitcode 为 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="215af-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="215af-183">示例</span><span class="sxs-lookup"><span data-stu-id="215af-183">EXAMPLES</span></span>

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

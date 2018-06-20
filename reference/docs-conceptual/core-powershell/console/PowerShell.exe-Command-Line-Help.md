---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShell.exe 命令行帮助
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952573"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="9650d-103">PowerShell.exe 命令行帮助</span><span class="sxs-lookup"><span data-stu-id="9650d-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="9650d-104">可以使用 PowerShell.exe 从另一工具（如 Cmd.exe）的命令行启动 PowerShell 会话，或在 PowerShell 命令行中使用它来启动新会话。</span><span class="sxs-lookup"><span data-stu-id="9650d-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="9650d-105">使用参数自定义会话。</span><span class="sxs-lookup"><span data-stu-id="9650d-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="9650d-106">语法</span><span class="sxs-lookup"><span data-stu-id="9650d-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="9650d-107">参数</span><span class="sxs-lookup"><span data-stu-id="9650d-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="9650d-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="9650d-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="9650d-109">接受命令的 base-64 编码字符串版本。</span><span class="sxs-lookup"><span data-stu-id="9650d-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="9650d-110">使用此参数将命令提交到需要复杂的引号或大括号的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9650d-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="9650d-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="9650d-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="9650d-112">为当前会话设置默认执行策略，并将其保存在 $env:PSExecutionPolicyPreference 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="9650d-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="9650d-113">此参数不会更改在注册表中设置的 PowerShell 执行策略。</span><span class="sxs-lookup"><span data-stu-id="9650d-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="9650d-114">若要了解 PowerShell 执行策略（包括有效值列表），请参阅 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="9650d-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="9650d-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="9650d-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="9650d-116">在本地作用域中运行指定的脚本（“dot-sourced”），以便脚本创建的函数和变量在当前会话中可用。</span><span class="sxs-lookup"><span data-stu-id="9650d-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="9650d-117">输入脚本文件路径和任何参数。</span><span class="sxs-lookup"><span data-stu-id="9650d-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="9650d-118">**File** 必须是命令中的最后一个参数，因为在 **File** 参数名称后键入的所有字符都会被解释为后跟脚本参数及其值的脚本文件路径。</span><span class="sxs-lookup"><span data-stu-id="9650d-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="9650d-119">**File** 参数的值中可以包括脚本参数和参数值。</span><span class="sxs-lookup"><span data-stu-id="9650d-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="9650d-120">例如：`-File .\Get-Script.ps1 -Domain Central`。请注意，传递给脚本的参数作为文字字符串（在当前 shell 的解释后）传递。</span><span class="sxs-lookup"><span data-stu-id="9650d-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="9650d-121">例如，如果处于 cmd.exe，并要传递环境变量值，则使用 cmd.exe 语法：`powershell -File .\test.ps1 -Sample %windir%`。如果计划使用 PowerShell 语法，则在此示例中，脚本将收到文本“$env: windir”，而非该环境变量的值：`powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="9650d-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="9650d-122">通常，将包括或忽略脚本的开关参数。</span><span class="sxs-lookup"><span data-stu-id="9650d-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="9650d-123">例如，下面的命令使用 Get-Script.ps1 脚本文件的 **All** 参数：`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="9650d-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="9650d-124">\-InputFormat {文本 |XML}</span><span class="sxs-lookup"><span data-stu-id="9650d-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="9650d-125">描述发送到 PowerShell 的数据格式。</span><span class="sxs-lookup"><span data-stu-id="9650d-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="9650d-126">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="9650d-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="9650d-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="9650d-127">-Mta</span></span>

<span data-ttu-id="9650d-128">使用多线程单元启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9650d-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="9650d-129">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="9650d-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="9650d-130">在 PowerShell 3.0 中，单线程单元 (STA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="9650d-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9650d-131">在 PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="9650d-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="9650d-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="9650d-132">-NoExit</span></span>

<span data-ttu-id="9650d-133">运行启动命令后不退出。</span><span class="sxs-lookup"><span data-stu-id="9650d-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="9650d-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="9650d-134">-NoLogo</span></span>

<span data-ttu-id="9650d-135">启动时隐藏版权横幅。</span><span class="sxs-lookup"><span data-stu-id="9650d-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="9650d-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="9650d-136">-NonInteractive</span></span>

<span data-ttu-id="9650d-137">不向用户显示交互式提示。</span><span class="sxs-lookup"><span data-stu-id="9650d-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="9650d-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="9650d-138">-NoProfile</span></span>

<span data-ttu-id="9650d-139">不加载 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="9650d-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="9650d-140">-OutputFormat {文本 | XML}</span><span class="sxs-lookup"><span data-stu-id="9650d-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="9650d-141">确定 PowerShell 输出内容的格式。</span><span class="sxs-lookup"><span data-stu-id="9650d-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="9650d-142">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="9650d-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="9650d-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="9650d-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="9650d-144">加载指定的 PowerShell 控制台文件。</span><span class="sxs-lookup"><span data-stu-id="9650d-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="9650d-145">输入控制台文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="9650d-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="9650d-146">若要创建控制台文件，请在 PowerShell 中运行 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9650d-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="9650d-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="9650d-147">-Sta</span></span>

<span data-ttu-id="9650d-148">使用单线程单元启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9650d-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="9650d-149">在 PowerShell 3.0 中，单线程单元 (STA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="9650d-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9650d-150">在 PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="9650d-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="9650d-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="9650d-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="9650d-152">启动 PowerShell 的指定版本。</span><span class="sxs-lookup"><span data-stu-id="9650d-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="9650d-153">必须在系统上安装指定的版本。</span><span class="sxs-lookup"><span data-stu-id="9650d-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="9650d-154">如果计算机上已安装 PowerShell 3.0，则有效值为“2.0”和“3.0”。</span><span class="sxs-lookup"><span data-stu-id="9650d-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="9650d-155">默认值为“3.0”。</span><span class="sxs-lookup"><span data-stu-id="9650d-155">The default value is "3.0".</span></span>

<span data-ttu-id="9650d-156">如果未安装 PowerShell 3.0，则唯一的有效值为“2.0”。</span><span class="sxs-lookup"><span data-stu-id="9650d-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="9650d-157">将忽略其他值。</span><span class="sxs-lookup"><span data-stu-id="9650d-157">Other values are ignored.</span></span>

<span data-ttu-id="9650d-158">有关详细信息，请参阅“[安装 Windows PowerShell](../../setup/installing-windows-powershell.md)”。</span><span class="sxs-lookup"><span data-stu-id="9650d-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="9650d-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="9650d-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="9650d-160">为会话设置窗口样式。</span><span class="sxs-lookup"><span data-stu-id="9650d-160">Sets the window style for the session.</span></span> <span data-ttu-id="9650d-161">有效值包括 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="9650d-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="9650d-162">-Command</span><span class="sxs-lookup"><span data-stu-id="9650d-162">-Command</span></span>

<span data-ttu-id="9650d-163">执行指定的命令（和所有参数），就像从 PowerShell 命令提示符下键入的命令一样，如果未指定 NoExit，则随后退出。</span><span class="sxs-lookup"><span data-stu-id="9650d-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="9650d-164">实际上，`-Command` 后的任何文本都会作为单个命令行发送到 PowerShell，这与 `-File` 对发送到脚本的参数的处理方式不同。</span><span class="sxs-lookup"><span data-stu-id="9650d-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="9650d-165">Command 的值可以为“-”、字符串。</span><span class="sxs-lookup"><span data-stu-id="9650d-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="9650d-166">或脚本块。</span><span class="sxs-lookup"><span data-stu-id="9650d-166">or a script block.</span></span> <span data-ttu-id="9650d-167">如果 Command 的值为“-”，则将从标准输入读取命令文本。</span><span class="sxs-lookup"><span data-stu-id="9650d-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="9650d-168">脚本块必须括在大括号 ({}) 中。</span><span class="sxs-lookup"><span data-stu-id="9650d-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="9650d-169">只有在 PowerShell 中运行 PowerShell.exe 时才能指定脚本块。</span><span class="sxs-lookup"><span data-stu-id="9650d-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="9650d-170">脚本的结果作为反序列化 XML 对象（而非活动对象）返回到父外壳程序。</span><span class="sxs-lookup"><span data-stu-id="9650d-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="9650d-171">如果 Command 的值为字符串，则 Command 必须是该命令的最后一个参数，因为其后键入的所有字符都会被解释为它的参数。</span><span class="sxs-lookup"><span data-stu-id="9650d-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="9650d-172">若要编写运行 PowerShell 命令的字符串，请使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="9650d-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="9650d-173">其中，引号指示一个字符串，调用运算符 (&) 用于执行命令。</span><span class="sxs-lookup"><span data-stu-id="9650d-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="9650d-174">-Help、-?、/?</span><span class="sxs-lookup"><span data-stu-id="9650d-174">-Help, -?, /?</span></span>

<span data-ttu-id="9650d-175">显示此消息。</span><span class="sxs-lookup"><span data-stu-id="9650d-175">Shows this message.</span></span> <span data-ttu-id="9650d-176">如果要在 PowerShell 中键入 PowerShell.exe 命令，请以连字符 (-) 作为命令参数的前缀，不要使用正斜杠 (/)。</span><span class="sxs-lookup"><span data-stu-id="9650d-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="9650d-177">你可以在 Cmd.exe 中使用连字符或正斜杠。</span><span class="sxs-lookup"><span data-stu-id="9650d-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="9650d-178">疑难解答注释：在 PowerShell 2.0 中，在 Windows PowerShell 控制台中启动某些程序将失败，LastExitCode 为 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="9650d-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="9650d-179">示例</span><span class="sxs-lookup"><span data-stu-id="9650d-179">EXAMPLES</span></span>

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
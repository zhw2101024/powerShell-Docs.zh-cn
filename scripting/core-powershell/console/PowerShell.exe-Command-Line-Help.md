---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShell.exe 命令行帮助"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 9c56f09ac186b0c3a64cce6700740ca1ba6abd06
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="cf1c2-103">PowerShell.exe 命令行帮助</span><span class="sxs-lookup"><span data-stu-id="cf1c2-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="cf1c2-104">启动 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="cf1c2-105">可以使用 PowerShell.exe 从另一工具（如 Cmd.exe）的命令行启动 Windows PowerShell 会话，或在 Windows PowerShell 命令行中使用它来启动新会话。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="cf1c2-106">使用参数自定义会话。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf1c2-107">语法</span><span class="sxs-lookup"><span data-stu-id="cf1c2-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="cf1c2-108">参数</span><span class="sxs-lookup"><span data-stu-id="cf1c2-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="cf1c2-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="cf1c2-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="cf1c2-110">接受命令的 base-64 编码字符串版本。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="cf1c2-111">使用此参数将命令提交到需要复杂的引号或大括号的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="cf1c2-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="cf1c2-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="cf1c2-113">为当前会话设置默认执行策略，并将其保存在 $env:PSExecutionPolicyPreference 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="cf1c2-114">此参数不会更改在注册表中设置的 Windows PowerShell 执行策略。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="cf1c2-115">有关 Windows PowerShell 执行策略的信息（包括有效值列表），请参阅 about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170)。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="cf1c2-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="cf1c2-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="cf1c2-117">在本地作用域中运行指定的脚本（“dot-sourced”），以便脚本创建的函数和变量在当前会话中可用。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="cf1c2-118">输入脚本文件路径和任何参数。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="cf1c2-119">**File** 必须是命令中的最后一个参数，因为在 **File** 参数名称后键入的所有字符都会被解释为后跟脚本参数及其值的脚本文件路径。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="cf1c2-120">**File** 参数的值中可以包括脚本参数和参数值。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="cf1c2-121">例如：`-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="cf1c2-121">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="cf1c2-122">通常，将包括或忽略脚本的开关参数。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="cf1c2-123">例如，下面的命令使用 Get-Script.ps1 脚本文件的 **All** 参数：`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="cf1c2-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="cf1c2-124">在极少数情况下，你可能需要为开关参数提供一个布尔值。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-124">In rare cases, you might need to provide a Boolean value for a switch parameter.</span></span> <span data-ttu-id="cf1c2-125">若要在 **File** 参数的值中为开关参数提供布尔值，请将参数名称和参数值括在大括号中，如下所示：`-File .\Get-Script.ps1 {-All:$False}`</span><span class="sxs-lookup"><span data-stu-id="cf1c2-125">To provide a Boolean value for a switch parameter in the value of the **File** parameter, enclose the parameter name and value in curly braces, such as the following: `-File .\Get-Script.ps1 {-All:$False}`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="cf1c2-126">-InputFormat {文本 |XML}</span><span class="sxs-lookup"><span data-stu-id="cf1c2-126">-InputFormat {Text | XML}</span></span>
<span data-ttu-id="cf1c2-127">描述发送到 Windows PowerShell 的数据格式。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-127">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="cf1c2-128">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-128">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="cf1c2-129">-Mta</span><span class="sxs-lookup"><span data-stu-id="cf1c2-129">-Mta</span></span>
<span data-ttu-id="cf1c2-130">使用多线程单元启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-130">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="cf1c2-131">此参数是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-131">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="cf1c2-132">在 Windows PowerShell 3.0 中，单线程单元 (STA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-132">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="cf1c2-133">在 Windows PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-133">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="cf1c2-134">-NoExit</span><span class="sxs-lookup"><span data-stu-id="cf1c2-134">-NoExit</span></span>
<span data-ttu-id="cf1c2-135">运行启动命令后不退出。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-135">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="cf1c2-136">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="cf1c2-136">-NoLogo</span></span>
<span data-ttu-id="cf1c2-137">启动时隐藏版权横幅。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-137">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="cf1c2-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="cf1c2-138">-NonInteractive</span></span>
<span data-ttu-id="cf1c2-139">不向用户显示交互式提示。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-139">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="cf1c2-140">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="cf1c2-140">-NoProfile</span></span>
<span data-ttu-id="cf1c2-141">不加载 Windows PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-141">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="cf1c2-142">-OutputFormat {文本 | XML}</span><span class="sxs-lookup"><span data-stu-id="cf1c2-142">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="cf1c2-143">确定 Windows PowerShell 输出内容的格式。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-143">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="cf1c2-144">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-144">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="cf1c2-145">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="cf1c2-145">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="cf1c2-146">加载指定的 Windows PowerShell 控制台文件。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-146">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="cf1c2-147">输入控制台文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-147">Enter the path and name of the console file.</span></span> <span data-ttu-id="cf1c2-148">若要创建控制台文件，请使用 Windows PowerShell 中的 [Export-console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-148">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="cf1c2-149">-Sta</span><span class="sxs-lookup"><span data-stu-id="cf1c2-149">-Sta</span></span>
<span data-ttu-id="cf1c2-150">使用单线程单元启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-150">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="cf1c2-151">在 Windows PowerShell 3.0 中，单线程单元 (STA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-151">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="cf1c2-152">在 Windows PowerShell 2.0 中，多线程单元 (MTA) 是默认设置。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-152">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="cf1c2-153">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="cf1c2-153">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="cf1c2-154">启动 Windows PowerShell 的指定版本。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-154">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="cf1c2-155">必须在系统上安装指定的版本。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-155">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="cf1c2-156">如果计算机上已安装 Windows PowerShell 3.0，则有效值为“2.0”和“3.0”。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-156">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="cf1c2-157">默认值为“3.0”。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-157">The default value is "3.0".</span></span>

<span data-ttu-id="cf1c2-158">如果未安装 Windows PowerShell 3.0，则唯一的有效值为“2.0”。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-158">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="cf1c2-159">将忽略其他值。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-159">Other values are ignored.</span></span>

<span data-ttu-id="cf1c2-160">有关详细信息，请参阅 [Windows PowerShell 入门 [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd)中的“安装 Windows PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-160">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="cf1c2-161">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="cf1c2-161">-WindowStyle <Window style></span></span>
<span data-ttu-id="cf1c2-162">为会话设置窗口样式。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-162">Sets the window style for the session.</span></span> <span data-ttu-id="cf1c2-163">有效值包括 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-163">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="cf1c2-164">-Command</span><span class="sxs-lookup"><span data-stu-id="cf1c2-164">-Command</span></span>
<span data-ttu-id="cf1c2-165">执行指定的命令和所有参数，就像从 Windows PowerShell 命令提示符下键入的命令一样，如果未指定 NoExit，则随后退出。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-165">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>

<span data-ttu-id="cf1c2-166">Command 的值可以为“-”、字符串。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="cf1c2-167">或脚本块。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-167">or a script block.</span></span> <span data-ttu-id="cf1c2-168">如果 Command 的值为“-”，则将从标准输入读取命令文本。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="cf1c2-169">脚本块必须括在大括号 ({}) 中。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="cf1c2-170">只有在 Windows PowerShell 中运行 PowerShell.exe 时才能指定脚本块。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="cf1c2-171">脚本的结果作为反序列化 XML 对象（而非活动对象）返回到父外壳程序。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="cf1c2-172">如果 Command 的值为字符串，则 **Command** 必须是该命令的最后一个参数，因为其后键入的所有字符都会被解释为它的参数。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-172">If the value of Command is a string, **Command** must be the last parameter in the command , because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="cf1c2-173">若要编写运行 Windows PowerShell 命令的字符串，请使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="cf1c2-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="cf1c2-174">其中，引号指示一个字符串，调用运算符 (&) 用于执行命令。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="cf1c2-175">-Help、-?、/?</span><span class="sxs-lookup"><span data-stu-id="cf1c2-175">-Help, -?, /?</span></span>
<span data-ttu-id="cf1c2-176">显示此消息。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-176">Shows this message.</span></span> <span data-ttu-id="cf1c2-177">如果要在 Windows PowerShell 中键入 PowerShell.exe 命令，请以连字符 (-) 作为命令参数的前缀，不要使用正斜杠 (/)。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="cf1c2-178">你可以在 Cmd.exe 中使用连字符或正斜杠。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="cf1c2-179">疑难解答注释：在 Windows PowerShell 2.0 中，在 Windows PowerShell 控制台中启动某些程序将失败，LastExitCode 为 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="cf1c2-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="cf1c2-180">示例</span><span class="sxs-lookup"><span data-stu-id="cf1c2-180">EXAMPLES</span></span>

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command "Get-EventLog -LogName security"

# in an existing PowerShell session that understands the curly braces mean a script block
PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```


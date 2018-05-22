---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: JEA 角色功能
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="0a886-103">JEA 角色功能</span><span class="sxs-lookup"><span data-stu-id="0a886-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="0a886-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0a886-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0a886-105">创建 JEA 终结点时，需要定义一个或多个“角色功能”，该功能描述了用户可在 JEA 会话中执行*哪些*操作。</span><span class="sxs-lookup"><span data-stu-id="0a886-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="0a886-106">角色功能是一个带 .psrc 扩展名的 PowerShell 数据文件，列出了应向连接用户提供的所有 cmdlet、函数、提供程序和外部程序。</span><span class="sxs-lookup"><span data-stu-id="0a886-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="0a886-107">本主题介绍如何为 JEA 用户创建 PowerShell 角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="0a886-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="0a886-108">确定要允许的命令</span><span class="sxs-lookup"><span data-stu-id="0a886-108">Determine which commands to allow</span></span>

<span data-ttu-id="0a886-109">创建角色功能文件时，首先要考虑分配有角色的用户将需要访问哪些内容。</span><span class="sxs-lookup"><span data-stu-id="0a886-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="0a886-110">此需求收集过程可能需要一段时间，但非常必要。</span><span class="sxs-lookup"><span data-stu-id="0a886-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="0a886-111">如果用户具有访问权限的 cmdlet 和函数太少，则会阻碍他们完成工作。</span><span class="sxs-lookup"><span data-stu-id="0a886-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="0a886-112">如果用户可访问的 cmdlet 和函数太多，可能导致其利用隐式管理员权限完成你期望之外的任务，从而降低你的安全性。</span><span class="sxs-lookup"><span data-stu-id="0a886-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="0a886-113">此过程的执行方式取决于你的组织和目标，但以下提示有助于确保你符合要求。</span><span class="sxs-lookup"><span data-stu-id="0a886-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="0a886-114">**标识**用户用于完成工作的命令。</span><span class="sxs-lookup"><span data-stu-id="0a886-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="0a886-115">这可能需要调查 IT 员工、检查自动化脚本，或者分析 PowerShell 会话脚本/日志。</span><span class="sxs-lookup"><span data-stu-id="0a886-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="0a886-116">将命令行工具**改为**使用 PowerShell 等效工具（若可能），实现最佳的审核和 JEA 自定义体验。</span><span class="sxs-lookup"><span data-stu-id="0a886-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="0a886-117">不可将外部程序限制为与本机 PowerShell cmdlet 和 JEA 中的函数一样精细。</span><span class="sxs-lookup"><span data-stu-id="0a886-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="0a886-118">必要时，将 cmdlet 的作用域**限制**为仅允许特定参数或参数值。</span><span class="sxs-lookup"><span data-stu-id="0a886-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="0a886-119">如果用户应只能管理部分系统，此操作尤其重要。</span><span class="sxs-lookup"><span data-stu-id="0a886-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="0a886-120">**创建**自定义函数，替换复杂的命令或者很难在 JEA 中进行约束的命令。</span><span class="sxs-lookup"><span data-stu-id="0a886-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="0a886-121">封装了复杂命令或应用其他验证逻辑的简单函数可提供额外的掌控力，简化管理员和最终用户的操作。</span><span class="sxs-lookup"><span data-stu-id="0a886-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="0a886-122">通过用户和/或自动化服务**测试**允许命令的作用域列表，并根据需要进行调整。</span><span class="sxs-lookup"><span data-stu-id="0a886-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="0a886-123">请牢记，通常使用管理员权限（或提升后的权限）运行 JEA 会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="0a886-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="0a886-124">有必要仔细选择可用的命令，确保 JEA 终结点不允许连接用户提升其权限。</span><span class="sxs-lookup"><span data-stu-id="0a886-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="0a886-125">下面的一些示例介绍了在不受约束的状态下允许使用时可能被恶意使用的命令。</span><span class="sxs-lookup"><span data-stu-id="0a886-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="0a886-126">请注意，此列表并非全面详尽，应在开始时谨慎使用。</span><span class="sxs-lookup"><span data-stu-id="0a886-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="0a886-127">可能存在危险的命令示例</span><span class="sxs-lookup"><span data-stu-id="0a886-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="0a886-128">风险</span><span class="sxs-lookup"><span data-stu-id="0a886-128">Risk</span></span> | <span data-ttu-id="0a886-129">示例</span><span class="sxs-lookup"><span data-stu-id="0a886-129">Example</span></span> | <span data-ttu-id="0a886-130">相关命令</span><span class="sxs-lookup"><span data-stu-id="0a886-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="0a886-131">向连接用户授予管理员特权以绕过 JEA</span><span class="sxs-lookup"><span data-stu-id="0a886-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="0a886-132">`Add-ADGroupMember`、`Add-LocalGroupMember`、`net.exe`、`dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="0a886-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="0a886-133">运行任意代码（如恶意软件、攻击或自定义脚本）以绕过保护</span><span class="sxs-lookup"><span data-stu-id="0a886-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="0a886-134">`Start-Process`、`New-Service`、`Invoke-Item`、`Invoke-WmiMethod`、`Invoke-CimMethod`、`Invoke-Expression`、`Invoke-Command`、`New-ScheduledTask`、`Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="0a886-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="0a886-135">创建角色功能文件</span><span class="sxs-lookup"><span data-stu-id="0a886-135">Create a role capability file</span></span>

<span data-ttu-id="0a886-136">可使用 [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet 创建新的 PowerShell 角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="0a886-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="0a886-137">可在文本编辑器中打开生成的角色功能文件，并进行修改以允许角色所需的命令。</span><span class="sxs-lookup"><span data-stu-id="0a886-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="0a886-138">PowerShell 帮助文档包括文件配置方式的多个示例。</span><span class="sxs-lookup"><span data-stu-id="0a886-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="0a886-139">允许 PowerShell cmdlet 和函数</span><span class="sxs-lookup"><span data-stu-id="0a886-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="0a886-140">若要授权用户运行 PowerShell cmdlet 或函数，请将 cmdlet 或函数名称添加到 VisbibleCmdlets 或 VisibleFunctions 字段。</span><span class="sxs-lookup"><span data-stu-id="0a886-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="0a886-141">如果不确定命令是 cmdlet 还是函数，可运行 `Get-Command <name>` 并查看输出中的“CommandType”属性。</span><span class="sxs-lookup"><span data-stu-id="0a886-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="0a886-142">有时，特定 cmdlet 或函数的作用域对用户需求而言过于宽泛。</span><span class="sxs-lookup"><span data-stu-id="0a886-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="0a886-143">例如，DNS 管理员可能只需进行访问来重启 DNS 服务。</span><span class="sxs-lookup"><span data-stu-id="0a886-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="0a886-144">在租户拥有自助式管理工具的访问权限的多租户环境中，应将租户限制为使用其自己的资源进行管理。</span><span class="sxs-lookup"><span data-stu-id="0a886-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="0a886-145">对于这些情况，可限制 cmdlet 或函数中公开的参数。</span><span class="sxs-lookup"><span data-stu-id="0a886-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="0a886-146">在其他高级应用场景中，可能还需要限制用户能向这些参数提供的值。</span><span class="sxs-lookup"><span data-stu-id="0a886-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="0a886-147">通过角色功能，可定义一组允许值，或者定义一种进行提升以确定是否允许给定输入的正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="0a886-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="0a886-148">即使限制可用参数，仍始终允许使用[常用 PowerShell 参数](https://technet.microsoft.com/library/hh847884.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0a886-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="0a886-149">不可在参数字段中明确列出这些参数。</span><span class="sxs-lookup"><span data-stu-id="0a886-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="0a886-150">下表介绍自定义可见 cmdlet 或函数的各种方式。</span><span class="sxs-lookup"><span data-stu-id="0a886-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="0a886-151">可在 VisibleCmdlets 字段中组合和配对以下任何内容。</span><span class="sxs-lookup"><span data-stu-id="0a886-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="0a886-152">示例</span><span class="sxs-lookup"><span data-stu-id="0a886-152">Example</span></span>                                                                                      | <span data-ttu-id="0a886-153">用例</span><span class="sxs-lookup"><span data-stu-id="0a886-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="0a886-154">`'My-Func'` 或 `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="0a886-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="0a886-155">允许用户运行 `My-Func` 且不限制参数。</span><span class="sxs-lookup"><span data-stu-id="0a886-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="0a886-156">允许用户通过模块 `MyModule` 运行 `My-Func` 且不限制参数。</span><span class="sxs-lookup"><span data-stu-id="0a886-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="0a886-157">允许用户使用谓词 `My` 运行任意 cmdlet 或函数。</span><span class="sxs-lookup"><span data-stu-id="0a886-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="0a886-158">允许用户使用名词 `Func` 运行任意 cmdlet 或函数。</span><span class="sxs-lookup"><span data-stu-id="0a886-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="0a886-159">允许用户使用 `Param1` 和/或 `Param2` 参数运行 `My-Func`。</span><span class="sxs-lookup"><span data-stu-id="0a886-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="0a886-160">可向参数提供任何值。</span><span class="sxs-lookup"><span data-stu-id="0a886-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="0a886-161">允许用户使用 `Param1` 参数运行 `My-Func`。</span><span class="sxs-lookup"><span data-stu-id="0a886-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="0a886-162">仅可向该参数提供“Value1”和“Value2”。</span><span class="sxs-lookup"><span data-stu-id="0a886-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="0a886-163">允许用户使用 `Param1` 参数运行 `My-Func`。</span><span class="sxs-lookup"><span data-stu-id="0a886-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="0a886-164">可向参数提供以“contoso”开头的任意值。</span><span class="sxs-lookup"><span data-stu-id="0a886-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="0a886-165">最佳的安全做法是，建议在定义可见 cmdlet 或函数时不要使用通配符。</span><span class="sxs-lookup"><span data-stu-id="0a886-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="0a886-166">相反，应明确列出每个受信任的命令，确保共享同一命名方案的其他命令均未在无意中获得授权。</span><span class="sxs-lookup"><span data-stu-id="0a886-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="0a886-167">无法向同一个 cmdlet 或函数同时应用 ValidatePattern 和 ValidateSet。</span><span class="sxs-lookup"><span data-stu-id="0a886-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="0a886-168">若如此操作，ValidatePattern 将覆盖 ValidateSet。</span><span class="sxs-lookup"><span data-stu-id="0a886-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="0a886-169">有关 ValidatePattern 的详细信息，请参阅[*你好，脚本专家*博文](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 正则表达式](https://technet.microsoft.com/library/hh847880.aspx)参考内容。</span><span class="sxs-lookup"><span data-stu-id="0a886-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="0a886-170">允许使用外部命令和 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="0a886-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="0a886-171">若要允许用户在 JEA 会话中运行可执行文件和 PowerShell 脚本 (.ps1)，必须在 VisibleExternalCommands 字段中添加每个程序的完整路径。</span><span class="sxs-lookup"><span data-stu-id="0a886-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="0a886-172">如果可能，建议使用你授权的任意外部可执行文件的 PowerShell cmdlet/函数等效项，因为你可控制哪些参数允许使用 PowerShell cmdlet/函数。</span><span class="sxs-lookup"><span data-stu-id="0a886-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="0a886-173">很多可执行文件均允许读取当前状态，并允许随后只需提供其他参数即可进行更改。</span><span class="sxs-lookup"><span data-stu-id="0a886-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="0a886-174">例如，考虑文件服务器管理员的角色，该管理员想要查看本地计算机托管的网络共享。</span><span class="sxs-lookup"><span data-stu-id="0a886-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="0a886-175">一种检查方法是使用 `net share`。</span><span class="sxs-lookup"><span data-stu-id="0a886-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="0a886-176">但是，允许 net.exe 会带来很大风险，因为管理员可轻松使用该命令获取 `net group Administrators unprivilegedjeauser /add` 的管理员权限。</span><span class="sxs-lookup"><span data-stu-id="0a886-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="0a886-177">更好的方法是允许使用 [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx)，该命令可实现相同的结果，但作用域更受限制。</span><span class="sxs-lookup"><span data-stu-id="0a886-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="0a886-178">在 JEA 会话中向用户提供外部命令时，请始终指定可执行文件的完整路径，确保不会转而执行系统其他位置中名称相似（且可能恶意）的程序。</span><span class="sxs-lookup"><span data-stu-id="0a886-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="0a886-179">允许访问 PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="0a886-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="0a886-180">默认情况下，PowerShell 提供程序均不适用于 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="0a886-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="0a886-181">这主要是为了降低向连接用户泄漏敏感信息和配置设置的风险。</span><span class="sxs-lookup"><span data-stu-id="0a886-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="0a886-182">必要时，可使用 `VisibleProviders` 命令允许访问 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="0a886-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="0a886-183">有关提供程序的完整列表，请运行 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="0a886-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="0a886-184">对于需要访问文件系统、注册表、证书存储或其他敏感提供程序的简单任务，还可考虑编写将代表用户使用提供程序的自定义函数。</span><span class="sxs-lookup"><span data-stu-id="0a886-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="0a886-185">JEA 会话中可用的函数、cmdlet 和外部程序不遵从 JEA 的相同约束；默认情况下，它们可访问任意提供程序。</span><span class="sxs-lookup"><span data-stu-id="0a886-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="0a886-186">如果需要将文件复制到 JEA 终结点/从中复制文件，还可考虑使用[用户驱动器](session-configurations.md#user-drive)。</span><span class="sxs-lookup"><span data-stu-id="0a886-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="0a886-187">创建自定义函数</span><span class="sxs-lookup"><span data-stu-id="0a886-187">Creating custom functions</span></span>

<span data-ttu-id="0a886-188">可在角色功能文件中创作自定义函数，简化最终用户的复杂任务。</span><span class="sxs-lookup"><span data-stu-id="0a886-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="0a886-189">如果需要 cmdlet 参数值的高级验证逻辑时，自定义函数也很有用。</span><span class="sxs-lookup"><span data-stu-id="0a886-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="0a886-190">可在 **FunctionDefinitions** 字段中编写简单函数：</span><span class="sxs-lookup"><span data-stu-id="0a886-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="0a886-191">不要忘记向 **VisibleFunctions** 字段添加自定义函数的名称，使其可由 JEA 用户运行。</span><span class="sxs-lookup"><span data-stu-id="0a886-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="0a886-192">自定义函数的主体（脚本块）在系统的默认语言模式下运行，不受 JEA 的语言约束。</span><span class="sxs-lookup"><span data-stu-id="0a886-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="0a886-193">这意味着函数可访问文件系统和注册表，并可运行角色功能文件中隐藏的命令。</span><span class="sxs-lookup"><span data-stu-id="0a886-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="0a886-194">使用参数时，请注意避免允许运行任意代码，并避免直接将用户输入传输到 `Invoke-Expression` 等 cmdlet 中。</span><span class="sxs-lookup"><span data-stu-id="0a886-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="0a886-195">在上例中，可注意到使用的是完全限定的模块名称 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而非速记 `Select-Object`。</span><span class="sxs-lookup"><span data-stu-id="0a886-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="0a886-196">角色功能文件中定义的函数仍受限于 JEA 会话的作用域，这包括 JEA 创建用于约束现有命令的代理函数。</span><span class="sxs-lookup"><span data-stu-id="0a886-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="0a886-197">Select-Object 是所有 JEA 会话中受约束的默认 cmdlet，不允许选择对象的任意属性。</span><span class="sxs-lookup"><span data-stu-id="0a886-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="0a886-198">若要在函数中使用不受约束的 Select-Object，必须通过指定 FQMN 显式请求完整的实现。</span><span class="sxs-lookup"><span data-stu-id="0a886-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="0a886-199">JEA 会话中受约束的所有 cmdlet 在通过函数调用时的行为均相同，且符合 PowerShell 的[命令优先顺序](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence)。</span><span class="sxs-lookup"><span data-stu-id="0a886-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="0a886-200">如果正在编写大量自定义函数，将其放在 [PowerShell 脚本模块](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx)中可能会更容易。</span><span class="sxs-lookup"><span data-stu-id="0a886-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="0a886-201">然后，与使用内置和第三方模块时一样，可使用 VisibleFunctions 字段使这些函数在 JEA 会话中可见。</span><span class="sxs-lookup"><span data-stu-id="0a886-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="0a886-202">在模块中放置角色功能</span><span class="sxs-lookup"><span data-stu-id="0a886-202">Place role capabilities in a module</span></span>

<span data-ttu-id="0a886-203">为使 PowerShell 能找到角色功能文件，必须将其存储在 PowerShell 模块的“RoleCapabilities”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0a886-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="0a886-204">该模块可存储在 `$env:PSModulePath` 环境变量所内附的任何文件夹中，但不得放置在 System32（针对内置模块保留）或者不受信用户可在其中修改文件的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0a886-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="0a886-205">下例说明了如何在“Program Files”路径中创建名为 *ContosoJEA* 的基本 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="0a886-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="0a886-206">若要深入了解 PowerShell 模块、模块清单和 PSModulePath 环境变量，请参阅[了解 PowerShell 模块](https://msdn.microsoft.com/en-us/library/dd878324.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0a886-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="0a886-207">更新角色功能</span><span class="sxs-lookup"><span data-stu-id="0a886-207">Updating role capabilities</span></span>


<span data-ttu-id="0a886-208">只需保存对角色功能文件的更改，即可随时更新该文件。</span><span class="sxs-lookup"><span data-stu-id="0a886-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="0a886-209">角色功能更新后启动的任意新 JEA 会话均可反映出修订后的功能。</span><span class="sxs-lookup"><span data-stu-id="0a886-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="0a886-210">这就是有必要控制角色功能文件夹的访问权限的原因。</span><span class="sxs-lookup"><span data-stu-id="0a886-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="0a886-211">应该只有高度受信任的管理员才可更改角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="0a886-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="0a886-212">如果不受信任的用户可更改角色功能文件，则其可轻松为自己授予 cmdlet 访问权限，便于提升自身权限。</span><span class="sxs-lookup"><span data-stu-id="0a886-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="0a886-213">对于想要锁定角色功能访问权限的管理员，请确保本地系统具有角色功能文件的访问权限且包含相关模块。</span><span class="sxs-lookup"><span data-stu-id="0a886-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="0a886-214">如何合并角色功能</span><span class="sxs-lookup"><span data-stu-id="0a886-214">How role capabilities are merged</span></span>

<span data-ttu-id="0a886-215">用户在输入 JEA 会话时，可获取多个角色功能的访问权限，具体取决于[会话配置文件](session-configurations.md)中的角色映射。</span><span class="sxs-lookup"><span data-stu-id="0a886-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="0a886-216">发生此情况时，JEA 将尝试为用户提供所有角色允许的*最宽松*的命令集。</span><span class="sxs-lookup"><span data-stu-id="0a886-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="0a886-217">**VisibleCmdlets 和 VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="0a886-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="0a886-218">最复杂的合并逻辑会影响 cmdlet 和函数，会在 JEA 中限制其参数和参数值。</span><span class="sxs-lookup"><span data-stu-id="0a886-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="0a886-219">规则如下：</span><span class="sxs-lookup"><span data-stu-id="0a886-219">The rules are as follows:</span></span>

1. <span data-ttu-id="0a886-220">如果 cmdlet 仅在一个角色中可见，其将会对具有任意适用参数约束的用户可见。</span><span class="sxs-lookup"><span data-stu-id="0a886-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="0a886-221">如果 cmdlet 在多个角色中可见，并且每个角色在该 cmdlet 上具有相同的约束，则该 cmdlet 将对具有这些约束的用户可见。</span><span class="sxs-lookup"><span data-stu-id="0a886-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="0a886-222">如果 cmdlet 在多个角色中可见，并且每个角色允许使用一组不同的参数，则该 cmdlet 及其在每个角色中定义的所有参数都将对用户可见。</span><span class="sxs-lookup"><span data-stu-id="0a886-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="0a886-223">如果角色没有参数约束，则允许使用所有参数。</span><span class="sxs-lookup"><span data-stu-id="0a886-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="0a886-224">如果一个角色定义 cmdlet 参数的验证集或验证模式，另一角色允许使用该参数但不约束参数值，则将忽略验证集或验证模式。</span><span class="sxs-lookup"><span data-stu-id="0a886-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="0a886-225">如果在多个角色中定义了同一个 cmdlet 参数的验证集，则所有验证集中的所有值均可用。</span><span class="sxs-lookup"><span data-stu-id="0a886-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="0a886-226">如果在多个角色中定义了同一个 cmdlet 参数的验证模式，则与任何模式匹配的任何值均可用。</span><span class="sxs-lookup"><span data-stu-id="0a886-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="0a886-227">如果在一个或多个角色中定义验证集，在另一角色中定义相同 cmdlet 参数的验证模式，则将忽略应用于剩余验证模式的验证集和规则 (6)。</span><span class="sxs-lookup"><span data-stu-id="0a886-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="0a886-228">以下是如何根据这些规则合并角色的示例：</span><span class="sxs-lookup"><span data-stu-id="0a886-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="0a886-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="0a886-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="0a886-230">角色功能文件中的所有其他字段均简单添加到一组集中且可允许使用的外部命令、别名、提供程序和启动脚本中。</span><span class="sxs-lookup"><span data-stu-id="0a886-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="0a886-231">角色功能中可见的任何命令、别名、提供程序或脚本均可供 JEA 用户使用。</span><span class="sxs-lookup"><span data-stu-id="0a886-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="0a886-232">请务必确保在包含某角色功能的提供程序和另一角色功能的 cmdlet/函数/命令的组合集中，连接用户不可在无意中访问系统资源。</span><span class="sxs-lookup"><span data-stu-id="0a886-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="0a886-233">例如，如果一个角色允许使用 `Remove-Item` cmdlet，而另一角色允许 `FileSystem` 提供程序，则 JEA 用户可能会删除计算机上的任意文件。</span><span class="sxs-lookup"><span data-stu-id="0a886-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="0a886-234">有关确定用户有效权限的其他信息，可参阅[审核 JEA 主题](audit-and-report.md)。</span><span class="sxs-lookup"><span data-stu-id="0a886-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0a886-235">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0a886-235">Next steps</span></span>

- [<span data-ttu-id="0a886-236">创建会话配置文件</span><span class="sxs-lookup"><span data-stu-id="0a886-236">Create a session configuration file</span></span>](session-configurations.md)
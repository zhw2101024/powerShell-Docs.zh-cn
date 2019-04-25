---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: 了解 PowerShell 命令名称
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 8d50ca03f98ed4ca8f9c09c83ae57afbf0d7888d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086419"
---
# <a name="learning-powershell-command-names"></a><span data-ttu-id="10e2b-103">了解 PowerShell 命令名称</span><span class="sxs-lookup"><span data-stu-id="10e2b-103">Learning PowerShell command names</span></span>

<span data-ttu-id="10e2b-104">学习命令和参数的名称需要在了解大多数命令行接口方面投入大量的时间。</span><span class="sxs-lookup"><span data-stu-id="10e2b-104">Learning names of commands and parameters requires a significant time investment with most command-line interfaces.</span></span> <span data-ttu-id="10e2b-105">问题是模式很少。</span><span class="sxs-lookup"><span data-stu-id="10e2b-105">The issue is that there are few patterns.</span></span> <span data-ttu-id="10e2b-106">记忆是了解需要定期使用的命令和参数的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="10e2b-106">Memorization is the only way to learn the commands and parameters that you need to use on a regular basis.</span></span>

<span data-ttu-id="10e2b-107">使用新命令或参数时，不能总是使用已经知道的内容。</span><span class="sxs-lookup"><span data-stu-id="10e2b-107">When you work with a new command or parameter, you can't always use what you already know.</span></span> <span data-ttu-id="10e2b-108">必须找到并了解一个新名称。</span><span class="sxs-lookup"><span data-stu-id="10e2b-108">You have to find and learn a new name.</span></span> <span data-ttu-id="10e2b-109">按照惯例，命令行界面从一小组工具开始，并随着增量添加而增长。</span><span class="sxs-lookup"><span data-stu-id="10e2b-109">Traditionally, command-line interfaces start with a small set of tools and grow with incremental additions.</span></span> <span data-ttu-id="10e2b-110">这就很容易理解命令行界面为什么没有标准结构。</span><span class="sxs-lookup"><span data-stu-id="10e2b-110">It's easy to see why there's no standard structure.</span></span>
<span data-ttu-id="10e2b-111">这似乎是命令名称的逻辑，因为每个命令都是一个单独的工具。</span><span class="sxs-lookup"><span data-stu-id="10e2b-111">This seems logical for command names since each command is a separate tool.</span></span> <span data-ttu-id="10e2b-112">PowerShell 有一种更好的方法来处理命令名称。</span><span class="sxs-lookup"><span data-stu-id="10e2b-112">PowerShell has a better way to handle command names.</span></span>

## <a name="learning-command-names-in-traditional-shells"></a><span data-ttu-id="10e2b-113">学习传统 shell 中的命令名称</span><span class="sxs-lookup"><span data-stu-id="10e2b-113">Learning command names in traditional shells</span></span>

<span data-ttu-id="10e2b-114">大多数命令用于管理操作系统或应用程序中的元素，如服务或进程。</span><span class="sxs-lookup"><span data-stu-id="10e2b-114">Most commands are built to manage elements of the operating system or applications, such as services or processes.</span></span> <span data-ttu-id="10e2b-115">命令具有多个名称，这些名称可能或可能不会纳入一个系列。</span><span class="sxs-lookup"><span data-stu-id="10e2b-115">The commands have names that may or may not fit into a family.</span></span> <span data-ttu-id="10e2b-116">例如，在 Windows 系统中，你可以使用 `net start` 和 `net stop` 命令来启动和停止服务。</span><span class="sxs-lookup"><span data-stu-id="10e2b-116">For example, on Windows systems, you can use the `net start` and `net stop` commands to start and stop a service.</span></span> <span data-ttu-id="10e2b-117">Sc.exe 是另一个适用于 Windows 的服务控制工具。</span><span class="sxs-lookup"><span data-stu-id="10e2b-117">**Sc.exe** is another service control tool for Windows.</span></span> <span data-ttu-id="10e2b-118">该名称不会纳入 net.exe 服务命令的命名模式。</span><span class="sxs-lookup"><span data-stu-id="10e2b-118">That name does not fit into the naming pattern for the **net.exe** service commands.</span></span> <span data-ttu-id="10e2b-119">对于流程管理，Windows 使用 tasklist.exe 命令列出进程，使用 taskkill.exe 命令终止进程。</span><span class="sxs-lookup"><span data-stu-id="10e2b-119">For process management, Windows has the **tasklist.exe** command to list processes and the **taskkill.exe** command to kill processes.</span></span>

<span data-ttu-id="10e2b-120">另外，这些命令的参数规范不规则。</span><span class="sxs-lookup"><span data-stu-id="10e2b-120">Also, these commands have irregular parameter specifications.</span></span> <span data-ttu-id="10e2b-121">不能使用 `net start` 命令来启动远程计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="10e2b-121">You can't use the `net start` command to start a service on a remote computer.</span></span> <span data-ttu-id="10e2b-122">sc.exe  命令可以启动远程计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="10e2b-122">The **sc.exe** command can start a service on a remote computer.</span></span> <span data-ttu-id="10e2b-123">但是，若要指定远程计算机，则必须在其名称前添加双反斜杠作为前缀。</span><span class="sxs-lookup"><span data-stu-id="10e2b-123">But to specify the remote computer, you must prefix its name with a double backslash.</span></span> <span data-ttu-id="10e2b-124">若要在名为 DC01 的远程计算机上启动后台处理程序服务，请键入 `sc.exe \\DC01 start spooler`。</span><span class="sxs-lookup"><span data-stu-id="10e2b-124">To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.</span></span>
<span data-ttu-id="10e2b-125">若要列出在 DC01 上运行的任务，请使用 /S 参数和不带反斜杠的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="10e2b-125">To list tasks running on DC01, you use the **/S** parameter and the computer name without backslashes.</span></span> <span data-ttu-id="10e2b-126">例如，`tasklist /S DC01`。</span><span class="sxs-lookup"><span data-stu-id="10e2b-126">For example, `tasklist /S DC01`.</span></span>

> [!NOTE]
> <span data-ttu-id="10e2b-127">在 PowerShell v6 之前，`sc` 是 `Set-Content` cmdlet 的别名。</span><span class="sxs-lookup"><span data-stu-id="10e2b-127">Prior to PowerShell v6, `sc` was an alias for the `Set-Content` cmdlet.</span></span> <span data-ttu-id="10e2b-128">因此，若要在 v6 之前的 PowerShell 版本中运行 sc.exe 命令，必须使用包含文件扩展名 exe的完整文件名 sc.exe。</span><span class="sxs-lookup"><span data-stu-id="10e2b-128">Therefore, to run the **sc.exe** command in a version of PowerShell prior to v6, you must include the full filename **sc.exe** including the file extension **exe**.</span></span>

<span data-ttu-id="10e2b-129">服务和进程是计算机上具有明确定义的生命周期的可管理元素的示例。</span><span class="sxs-lookup"><span data-stu-id="10e2b-129">Services and processes are examples of manageable elements on a computer that have well-defined life cycles.</span></span> <span data-ttu-id="10e2b-130">你可能想要启动或停止服务或进程，或获取所有当前正在运行的服务或进程的列表。</span><span class="sxs-lookup"><span data-stu-id="10e2b-130">You may start or stop services and processes, or get a list of all currently running services or processes.</span></span> <span data-ttu-id="10e2b-131">虽然它们之间存在重要的技术差异，但在服务和进程上执行的操作在概念上是相同的。</span><span class="sxs-lookup"><span data-stu-id="10e2b-131">Although there are important technical distinctions between them, the actions you perform on services and processes are conceptually the same.</span></span> <span data-ttu-id="10e2b-132">此外，通过指定参数自定义操作所做的选择从概念上讲也是相似的。</span><span class="sxs-lookup"><span data-stu-id="10e2b-132">Furthermore, the choices we make to customize an action by specifying parameters may be conceptually similar as well.</span></span>

<span data-ttu-id="10e2b-133">PowerShell 利用这些相似之处减少了解和使用 cmdlet 时需要知道的不同名称的数量。</span><span class="sxs-lookup"><span data-stu-id="10e2b-133">PowerShell exploits these similarities to reduce the number of distinct names you need to know to understand and use cmdlets.</span></span>

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a><span data-ttu-id="10e2b-134">Cmdlet 使用谓词-名词的名称来减少命令记忆</span><span class="sxs-lookup"><span data-stu-id="10e2b-134">Cmdlets use verb-noun names to reduce command memorization</span></span>

<span data-ttu-id="10e2b-135">PowerShell 使用“谓词 - 名词”命名系统。</span><span class="sxs-lookup"><span data-stu-id="10e2b-135">PowerShell uses a "verb-noun" naming system.</span></span> <span data-ttu-id="10e2b-136">每个 cmdlet 名称都由一个标准谓词、连字符和特定名词组成。</span><span class="sxs-lookup"><span data-stu-id="10e2b-136">Each cmdlet name consists of a standard verb hyphenated with a specific noun.</span></span> <span data-ttu-id="10e2b-137">PowerShell 谓词并不始终是英文谓词，但在 PowerShell 中表达特定的操作。</span><span class="sxs-lookup"><span data-stu-id="10e2b-137">PowerShell verbs are not always English verbs, but they express specific actions in PowerShell.</span></span> <span data-ttu-id="10e2b-138">名词非常类似于任何语言中的名词。</span><span class="sxs-lookup"><span data-stu-id="10e2b-138">Nouns are very much like nouns in any language.</span></span> <span data-ttu-id="10e2b-139">它们描述在系统管理中十分重要的特定类型的对象。</span><span class="sxs-lookup"><span data-stu-id="10e2b-139">They describe specific types of objects that are important in system administration.</span></span> <span data-ttu-id="10e2b-140">通过查看一些示例，可以很容易地演示这些包含两个部分的名称如何减少学习的负担。</span><span class="sxs-lookup"><span data-stu-id="10e2b-140">It's easy to demonstrate how these two-part names reduce learning effort by looking at a few examples.</span></span>

<span data-ttu-id="10e2b-141">PowerShell 有一套推荐的标准谓词。</span><span class="sxs-lookup"><span data-stu-id="10e2b-141">PowerShell has a recommended set of standard verbs.</span></span> <span data-ttu-id="10e2b-142">名词所受限制较少，但它们应始终描述谓词作用的对象。</span><span class="sxs-lookup"><span data-stu-id="10e2b-142">Nouns are less restricted, but always describe what the verb acts upon.</span></span> <span data-ttu-id="10e2b-143">PowerShell 具有 `Get-Process`、`Stop-Process`、`Get-Service` 和 `Stop-Service` 等命令。</span><span class="sxs-lookup"><span data-stu-id="10e2b-143">PowerShell has commands such as `Get-Process`, `Stop-Process`, `Get-Service`, and `Stop-Service`.</span></span>

<span data-ttu-id="10e2b-144">对于包含两个名词和两个谓词的此示例，一致性并未简化太多学习。</span><span class="sxs-lookup"><span data-stu-id="10e2b-144">For this example of two nouns and verbs, consistency does not simplify learning that much.</span></span> <span data-ttu-id="10e2b-145">将该列表扩展为一组标准化的 10 个谓词和 10 个名词。</span><span class="sxs-lookup"><span data-stu-id="10e2b-145">Extend that list to a standardized set of 10 verbs and 10 nouns.</span></span> <span data-ttu-id="10e2b-146">现在你只需要了解 20 个词。</span><span class="sxs-lookup"><span data-stu-id="10e2b-146">Now you only have 20 words to understand.</span></span>
<span data-ttu-id="10e2b-147">但是这些词可以组合形成 100 个不同的命令名称。</span><span class="sxs-lookup"><span data-stu-id="10e2b-147">But those words can be combined to form 100 distinct command names.</span></span>

<span data-ttu-id="10e2b-148">通过阅读其名称，可以很容易地了解 PowerShell 命令的作用。</span><span class="sxs-lookup"><span data-stu-id="10e2b-148">It's easy to understand what a PowerShell command does by reading its name.</span></span> <span data-ttu-id="10e2b-149">关闭计算机的命令是 `Stop-Computer`。</span><span class="sxs-lookup"><span data-stu-id="10e2b-149">The command to shut down a computer is `Stop-Computer`.</span></span> <span data-ttu-id="10e2b-150">列出网络上所有计算机的命令是 `Get-Computer`。</span><span class="sxs-lookup"><span data-stu-id="10e2b-150">The command to list all computers on a network is `Get-Computer`.</span></span> <span data-ttu-id="10e2b-151">获取系统日期的命令是 `Get-Date`。</span><span class="sxs-lookup"><span data-stu-id="10e2b-151">The command to get the system date is `Get-Date`.</span></span>

<span data-ttu-id="10e2b-152">可以使用 `Get-Command` 的 Verb 参数列出包含特定谓词的所有命令。</span><span class="sxs-lookup"><span data-stu-id="10e2b-152">You can list all commands that include a particular verb with the **Verb** parameter for `Get-Command`.</span></span> <span data-ttu-id="10e2b-153">例如，若要查看使用谓词 `Get` 的所有 cmdlet，键入：</span><span class="sxs-lookup"><span data-stu-id="10e2b-153">For example, to see all cmdlets that use the verb `Get`, type:</span></span>

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

<span data-ttu-id="10e2b-154">使用 Noun 参数查看将对同一类型的对象产生影响的命令系列。</span><span class="sxs-lookup"><span data-stu-id="10e2b-154">Use the **Noun** parameter to see a family of commands that affect the same type of object.</span></span> <span data-ttu-id="10e2b-155">例如，运行以下命令可以查看用于管理服务的命令：</span><span class="sxs-lookup"><span data-stu-id="10e2b-155">For example, run following command to see the commands  available for managing services:</span></span>

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a><span data-ttu-id="10e2b-156">Cmdlet 使用标准参数</span><span class="sxs-lookup"><span data-stu-id="10e2b-156">Cmdlets use standard parameters</span></span>

<span data-ttu-id="10e2b-157">如前文所述，在传统命令行接口中使用的命令并不总是具有一致的参数名称。</span><span class="sxs-lookup"><span data-stu-id="10e2b-157">As noted earlier, commands used in traditional command-line interfaces don't always have consistent parameter names.</span></span> <span data-ttu-id="10e2b-158">参数通常是易于键入但对新用户来说不能轻松理解的单个字符或缩写词。</span><span class="sxs-lookup"><span data-stu-id="10e2b-158">Parameters are often single-character or abbreviated words that are easy to type but aren't easily understood by new users.</span></span>

<span data-ttu-id="10e2b-159">不同于大多数其他传统的命令行接口，PowerShell 直接处理参数，并使用参数的这种直接访问权限以及开发人员指南标准化参数名称。</span><span class="sxs-lookup"><span data-stu-id="10e2b-159">Unlike most other traditional command-line interfaces, PowerShell processes parameters directly, and it uses this direct access to the parameters along with developer guidance to standardize parameter names.</span></span> <span data-ttu-id="10e2b-160">本指南建议但不会保证每个 cmdlet 都符合标准。</span><span class="sxs-lookup"><span data-stu-id="10e2b-160">This guidance encourages but does not guarantee that every cmdlet conforms to the standard.</span></span>

<span data-ttu-id="10e2b-161">PowerShell 还标准化参数分隔符。</span><span class="sxs-lookup"><span data-stu-id="10e2b-161">PowerShell also standardizes the parameter separator.</span></span> <span data-ttu-id="10e2b-162">使用 PowerShell 命令，参数名称前面始终带有“-”。</span><span class="sxs-lookup"><span data-stu-id="10e2b-162">Parameter names always have a '-' prepended to them with a PowerShell command.</span></span> <span data-ttu-id="10e2b-163">请考虑以下示例：</span><span class="sxs-lookup"><span data-stu-id="10e2b-163">Consider the following example:</span></span>

```powershell
Get-Command -Name Clear-Host
```

<span data-ttu-id="10e2b-164">参数的名称为 Name，但在命令行上用作参数时，将其键入为 `-Name`。</span><span class="sxs-lookup"><span data-stu-id="10e2b-164">The parameter's name is **Name**, but it is typed as `-Name` when used on the command line as a parameter.</span></span>

<span data-ttu-id="10e2b-165">以下是标准参数名称和用法的一些一般特征。</span><span class="sxs-lookup"><span data-stu-id="10e2b-165">Here are some of the general characteristics of the standard parameter names and usages.</span></span>

### <a name="the-help-parameter-"></a><span data-ttu-id="10e2b-166">帮助参数 (?)</span><span class="sxs-lookup"><span data-stu-id="10e2b-166">The Help parameter (?)</span></span>

<span data-ttu-id="10e2b-167">在任何 cmdlet 上指定 `-?` 参数时，PowerShell 将显示该 cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="10e2b-167">When you specify the `-?` parameter on any cmdlet, PowerShell displays help for the cmdlet.</span></span>
<span data-ttu-id="10e2b-168">未执行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="10e2b-168">The cmdlet is not executed.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="10e2b-169">通用参数</span><span class="sxs-lookup"><span data-stu-id="10e2b-169">Common parameters</span></span>

<span data-ttu-id="10e2b-170">PowerShell 有几个通用参数。</span><span class="sxs-lookup"><span data-stu-id="10e2b-170">PowerShell has several *common parameters*.</span></span> <span data-ttu-id="10e2b-171">这些参数由 PowerShell 引擎控制。</span><span class="sxs-lookup"><span data-stu-id="10e2b-171">These parameters are controlled by the PowerShell engine.</span></span> <span data-ttu-id="10e2b-172">通用参数的行为方式始终相同。</span><span class="sxs-lookup"><span data-stu-id="10e2b-172">Common parameters always behave the same way.</span></span> <span data-ttu-id="10e2b-173">通用参数有 **WhatIf**、**Confirm**、**Verbose**、**Debug**、**Warn**、**ErrorAction**、**ErrorVariable**、**OutVariable** 和 **OutBuffer**</span><span class="sxs-lookup"><span data-stu-id="10e2b-173">The common parameters are **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable**, and **OutBuffer**.</span></span>

### <a name="recommended-parameter-names"></a><span data-ttu-id="10e2b-174">建议的参数名称</span><span class="sxs-lookup"><span data-stu-id="10e2b-174">Recommended parameter names</span></span>

<span data-ttu-id="10e2b-175">对于类似的参数，PowerShell 核心 cmdlet 使用标准名称。</span><span class="sxs-lookup"><span data-stu-id="10e2b-175">The PowerShell core cmdlets use standard names for similar parameters.</span></span> <span data-ttu-id="10e2b-176">尽管不强制使用这些标准名称，但是具有明确的指南来鼓励进行标准化。</span><span class="sxs-lookup"><span data-stu-id="10e2b-176">The use of these standard names is not enforced, but there is explicit guidance to encourage standardization.</span></span>

<span data-ttu-id="10e2b-177">例如，指示计算机的参数的建议名称是 ComputerName，而不是 Server、Host、System、Node 或其他常见的备选单词。</span><span class="sxs-lookup"><span data-stu-id="10e2b-177">For example, the recommended name for a parameter that refers to a computer is **ComputerName**, rather than Server, Host, System, Node, or some other common alternative.</span></span> <span data-ttu-id="10e2b-178">其他重要的建议参数名称是 Force、Exclude、Include、PassThru、Path 和 CaseSensitive。</span><span class="sxs-lookup"><span data-stu-id="10e2b-178">Other important recommended parameter names are **Force**, **Exclude**, **Include**, **PassThru**, **Path**, and **CaseSensitive**.</span></span>

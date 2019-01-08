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
# <a name="getting-information-about-commands"></a><span data-ttu-id="6b6db-103">获取有关命令的信息</span><span class="sxs-lookup"><span data-stu-id="6b6db-103">Getting information about commands</span></span>

<span data-ttu-id="6b6db-104">PowerShell `Get-Command` 显示在当前会话中可用的命令。</span><span class="sxs-lookup"><span data-stu-id="6b6db-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="6b6db-105">运行 `Get-Command` cmdlet 时，会看到类似于以下输出的内容：</span><span class="sxs-lookup"><span data-stu-id="6b6db-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

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

<span data-ttu-id="6b6db-106">该输出与 cmd.exe 的帮助输出非常相似：内部命令的表格式摘要。</span><span class="sxs-lookup"><span data-stu-id="6b6db-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="6b6db-107">在如上所示的 `Get-Command` 命令输出摘录中，显示的每个命令都具有 Cmdlet 的 CommandType。</span><span class="sxs-lookup"><span data-stu-id="6b6db-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="6b6db-108">cmdlet 是 PowerShell 的内部命令类型。</span><span class="sxs-lookup"><span data-stu-id="6b6db-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="6b6db-109">此类型大致对应于 cmd.exe 中的 `dir` 和 `cd` 等命令，或者像 bash 这样的 Unix shell 的内置命令。</span><span class="sxs-lookup"><span data-stu-id="6b6db-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="6b6db-110">`Get-Command` cmdlet 具有可返回每个 cmdlet 语法的 Syntax 参数。</span><span class="sxs-lookup"><span data-stu-id="6b6db-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="6b6db-111">下面的示例演示如何获取 `Get-Help` cmdlet 的语法：</span><span class="sxs-lookup"><span data-stu-id="6b6db-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

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

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="6b6db-112">显示可用的命令类型</span><span class="sxs-lookup"><span data-stu-id="6b6db-112">Displaying available command by type</span></span>

<span data-ttu-id="6b6db-113">`Get-Command` 命令仅列出当前会话中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6b6db-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="6b6db-114">实际上，PowerShell 支持几种其他类型的命令：</span><span class="sxs-lookup"><span data-stu-id="6b6db-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="6b6db-115">别名</span><span class="sxs-lookup"><span data-stu-id="6b6db-115">Aliases</span></span>
- <span data-ttu-id="6b6db-116">功能</span><span class="sxs-lookup"><span data-stu-id="6b6db-116">Functions</span></span>
- <span data-ttu-id="6b6db-117">脚本</span><span class="sxs-lookup"><span data-stu-id="6b6db-117">Scripts</span></span>

<span data-ttu-id="6b6db-118">外部可执行文件，或具有已注册的文件类型处理程序的文件也被归类为命令。</span><span class="sxs-lookup"><span data-stu-id="6b6db-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="6b6db-119">若要获取会话中的所有命令，请键入：</span><span class="sxs-lookup"><span data-stu-id="6b6db-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="6b6db-120">此列表包含搜索路径中的外部命令，因此它可能包含数千个项。</span><span class="sxs-lookup"><span data-stu-id="6b6db-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="6b6db-121">查看一组缩减的命令更加有用。</span><span class="sxs-lookup"><span data-stu-id="6b6db-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="6b6db-122">星号 (\*) 用于 PowerShell 命令参数中的通配符匹配。</span><span class="sxs-lookup"><span data-stu-id="6b6db-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="6b6db-123">\* 表示“匹配一个或多个任意字符”。</span><span class="sxs-lookup"><span data-stu-id="6b6db-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="6b6db-124">可以键入 `Get-Command a*` 查找所有以字母“a”开头的命令。</span><span class="sxs-lookup"><span data-stu-id="6b6db-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="6b6db-125">与 cmd.exe 中的通配符匹配不同，PowerShell 的通配符还会匹配句点。</span><span class="sxs-lookup"><span data-stu-id="6b6db-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="6b6db-126">使用 `Get-Command` 的 CommandType 参数可以获取其他类型的本机命令。</span><span class="sxs-lookup"><span data-stu-id="6b6db-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="6b6db-127">cmdlet 时返回的仲裁资源的信息。</span><span class="sxs-lookup"><span data-stu-id="6b6db-127">cmdlet.</span></span>

<span data-ttu-id="6b6db-128">若要获取命令别名（即命令的已分配昵称），请键入：</span><span class="sxs-lookup"><span data-stu-id="6b6db-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="6b6db-129">若要获取当前会话中的函数，请键入：</span><span class="sxs-lookup"><span data-stu-id="6b6db-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="6b6db-130">若要显示 PowerShell 搜索路径中的脚本，请键入：</span><span class="sxs-lookup"><span data-stu-id="6b6db-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
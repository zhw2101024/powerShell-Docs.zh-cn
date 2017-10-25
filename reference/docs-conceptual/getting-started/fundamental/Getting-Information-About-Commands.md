---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "获取有关命令的信息"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="c207f-103">获取有关命令的信息</span><span class="sxs-lookup"><span data-stu-id="c207f-103">Getting Information About Commands</span></span>
<span data-ttu-id="c207f-104">Windows PowerShell **Get-Command** cmdlet 获取在当前会话中可用的所有命令。</span><span class="sxs-lookup"><span data-stu-id="c207f-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="c207f-105">当在 Windows PowerShell 提示符下键入 **Get-Command** 时，将看到类似于以下内容的输出：</span><span class="sxs-lookup"><span data-stu-id="c207f-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="c207f-106">该输出与 Cmd.exe 的帮助输出非常相似：内部命令的表格式摘要。</span><span class="sxs-lookup"><span data-stu-id="c207f-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="c207f-107">在如上所示的 **Get-Command** 命令输出摘录中，显示的每个命令都具有 Cmdlet 的 CommandType。</span><span class="sxs-lookup"><span data-stu-id="c207f-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="c207f-108">cmdlet 是 Windows PowerShell 的内部命令类型，此类型大致对应于 Cmd.exe 的 **dir** 和 **cd** 命令，以及 UNIX shell 中的 BASH 等内置命令。</span><span class="sxs-lookup"><span data-stu-id="c207f-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="c207f-109">在 **Get-Command** 命令的输出中，所有定义均以省略号 (...) 结尾，表示 PowerShell 无法在可用空间内显示所有内容。</span><span class="sxs-lookup"><span data-stu-id="c207f-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="c207f-110">当 Windows PowerShell 显示输出时，它将输出格式设置为文本，然后对其进行排列以使数据恰好适应窗口。</span><span class="sxs-lookup"><span data-stu-id="c207f-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="c207f-111">稍后我们将在有关格式设置的部分中对此进行讨论。</span><span class="sxs-lookup"><span data-stu-id="c207f-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="c207f-112">**Get-Command** cmdlet 具有可获取每个 cmdlet 语法的 **Syntax** 参数。</span><span class="sxs-lookup"><span data-stu-id="c207f-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="c207f-113">若要获取 Get-Help cmdlet 的语法，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="c207f-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="c207f-114">**Get-Command Get-Help -语法**</span><span class="sxs-lookup"><span data-stu-id="c207f-114">**Get-Command Get-Help -Syntax**</span></span>

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

### <a name="displaying-available-command-types"></a><span data-ttu-id="c207f-115">显示可用的命令类型</span><span class="sxs-lookup"><span data-stu-id="c207f-115">Displaying Available Command Types</span></span>
<span data-ttu-id="c207f-116">**Get-Command** 命令不会列出 Windows PowerShell 中的每个可用命令。</span><span class="sxs-lookup"><span data-stu-id="c207f-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="c207f-117">**Get-Command** 命令仅列出当前会话中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c207f-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="c207f-118">实际上，Windows PowerShell 支持几种其他类型的命令。</span><span class="sxs-lookup"><span data-stu-id="c207f-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="c207f-119">别名、函数和脚本也是 Windows PowerShell 命令，尽管在 Windows PowerShell 用户指南中并未对它们进行详细讨论。</span><span class="sxs-lookup"><span data-stu-id="c207f-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="c207f-120">属于可执行文件，或具有已注册的文件类型处理程序的外部文件也被归类为命令。</span><span class="sxs-lookup"><span data-stu-id="c207f-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="c207f-121">若要获取会话中的所有命令，请键入：</span><span class="sxs-lookup"><span data-stu-id="c207f-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="c207f-122">由于此列表包含搜索路径中的外部文件，因此它可能包含数千个项。</span><span class="sxs-lookup"><span data-stu-id="c207f-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="c207f-123">查看一组缩减的命令更加有用。</span><span class="sxs-lookup"><span data-stu-id="c207f-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="c207f-124">若要获取其他类型的本机命令，请使用 **Get-Command cmdlet** 的 **CommandType** 参数。</span><span class="sxs-lookup"><span data-stu-id="c207f-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c207f-125">星号 (\*) 用于 Windows PowerShell 命令参数中的通配符匹配。</span><span class="sxs-lookup"><span data-stu-id="c207f-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="c207f-126">\* 表示“匹配一个或多个任意字符”。</span><span class="sxs-lookup"><span data-stu-id="c207f-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="c207f-127">你可以键入 **Get-Command a\&#42;**查找所有以字母“a”开头的命令。</span><span class="sxs-lookup"><span data-stu-id="c207f-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="c207f-128">与 Cmd.exe 中的通配符匹配不同，Windows PowerShell 的通配符还将匹配句点。</span><span class="sxs-lookup"><span data-stu-id="c207f-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="c207f-129">若要获取命令别名（即命令的已分配昵称），请键入：</span><span class="sxs-lookup"><span data-stu-id="c207f-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="c207f-130">若要获取当前会话中的函数，请键入：</span><span class="sxs-lookup"><span data-stu-id="c207f-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="c207f-131">若要显示 Windows PowerShell 搜索路径中的脚本，请键入：</span><span class="sxs-lookup"><span data-stu-id="c207f-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```


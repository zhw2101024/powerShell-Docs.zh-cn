---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell 脚本
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058482"
---
# <a name="powershell"></a><span data-ttu-id="77973-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="77973-103">PowerShell</span></span>

<span data-ttu-id="77973-104">PowerShell 是构建于 .NET 上基于任务的命令行 shell 和脚本语言。</span><span class="sxs-lookup"><span data-stu-id="77973-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="77973-105">PowerShell 可帮助系统管理员和高级用户快速自动执行用于管理操作系统（Linux、macOS 和 Windows）和流程的任务。</span><span class="sxs-lookup"><span data-stu-id="77973-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="77973-106">使用 PowerShell 命令可以从命令行管理计算机。</span><span class="sxs-lookup"><span data-stu-id="77973-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="77973-107">PowerShell 提供程序可让你访问数据存储（如注册表和证书存储），与你访问文件系统一样方便。</span><span class="sxs-lookup"><span data-stu-id="77973-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="77973-108">PowerShell 具有丰富的表达式分析器和完全开发的脚本语言。</span><span class="sxs-lookup"><span data-stu-id="77973-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="77973-109">PowerShell 是开放源代码</span><span class="sxs-lookup"><span data-stu-id="77973-109">PowerShell is open-source</span></span>

<span data-ttu-id="77973-110">PowerShell 基本源代码目前在 GitHub 中提供，且对社区贡献开放。</span><span class="sxs-lookup"><span data-stu-id="77973-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="77973-111">请参阅 [GitHub 上的 PowerShell 源](https://github.com/powershell/powershell)。</span><span class="sxs-lookup"><span data-stu-id="77973-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="77973-112">可以从[获取 PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 中的所需位数入手。</span><span class="sxs-lookup"><span data-stu-id="77973-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="77973-113">或者可以快速查看[入门](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)。</span><span class="sxs-lookup"><span data-stu-id="77973-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="77973-114">PowerShell 设计目标</span><span class="sxs-lookup"><span data-stu-id="77973-114">PowerShell design goals</span></span>

<span data-ttu-id="77973-115">PowerShell 旨在消除长期存在的问题和添加新功能，从而改进命令行和脚本环境。</span><span class="sxs-lookup"><span data-stu-id="77973-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="77973-116">可发现性</span><span class="sxs-lookup"><span data-stu-id="77973-116">Discoverability</span></span>

<span data-ttu-id="77973-117">PowerShell 简化了它的功能发现过程。</span><span class="sxs-lookup"><span data-stu-id="77973-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="77973-118">例如，若要查找用于查看和更改 Windows 服务的 cmdlet 列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="77973-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="77973-119">发现完成任务的 cmdlet 后，可以运行 `Get-Help` cmdlet 来详细了解此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77973-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="77973-120">例如，若要显示 `Get-Service` cmdlet 的帮助信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="77973-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="77973-121">大多数 cmdlet 会返回对象，这些对象可获得操作，然后再呈现为显示文本。</span><span class="sxs-lookup"><span data-stu-id="77973-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="77973-122">若要全面了解 cmdlet 的输出，请将输出通过管道传递给 `Get-Member` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77973-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="77973-123">例如，下面的命令显示 `Get-Service` cmdlet 的输出对象成员的相关信息。</span><span class="sxs-lookup"><span data-stu-id="77973-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="77973-124">一致性</span><span class="sxs-lookup"><span data-stu-id="77973-124">Consistency</span></span>

<span data-ttu-id="77973-125">管理系统是一项复杂的任务。</span><span class="sxs-lookup"><span data-stu-id="77973-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="77973-126">具有一致的接口的工具有助于控制固有的复杂性。</span><span class="sxs-lookup"><span data-stu-id="77973-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="77973-127">遗憾的是，命令行工具和可编写脚本的组件对象模型 (COM) 对象的一致性均未知。</span><span class="sxs-lookup"><span data-stu-id="77973-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="77973-128">PowerShell 一致性是它的主要资产之一。</span><span class="sxs-lookup"><span data-stu-id="77973-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="77973-129">例如，如果了解如何使用 `Sort-Object` cmdlet，可以利用这一知识对任何 cmdlet 的输出进行排序。</span><span class="sxs-lookup"><span data-stu-id="77973-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="77973-130">不需要了解每个 cmdlet 的不同排序例程。</span><span class="sxs-lookup"><span data-stu-id="77973-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="77973-131">此外，cmdlet 开发人员无需为其 cmdlet 设计排序功能。</span><span class="sxs-lookup"><span data-stu-id="77973-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="77973-132">PowerShell 提供了一个框架，其中包含强制执行一致性的基本功能。</span><span class="sxs-lookup"><span data-stu-id="77973-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="77973-133">该框架消除了留给开发人员的一些选择。</span><span class="sxs-lookup"><span data-stu-id="77973-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="77973-134">但是，它也因而使得 cmdlet 的开发更加简单。</span><span class="sxs-lookup"><span data-stu-id="77973-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="77973-135">交互式脚本编写环境</span><span class="sxs-lookup"><span data-stu-id="77973-135">Interactive and scripting environments</span></span>

<span data-ttu-id="77973-136">Windows 命令提示符提供了一个可访问命令行工具和基本脚本的交互式 shell。</span><span class="sxs-lookup"><span data-stu-id="77973-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="77973-137">Windows 脚本宿主 (WSH) 具有可编写脚本的命令行工具和 COM 自动化对象，但不提供交互式 shell。</span><span class="sxs-lookup"><span data-stu-id="77973-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="77973-138">PowerShell 结合了交互式 shell 和脚本编写环境。</span><span class="sxs-lookup"><span data-stu-id="77973-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="77973-139">PowerShell 可以访问命令行工具、COM 对象和 .NET 类库。</span><span class="sxs-lookup"><span data-stu-id="77973-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="77973-140">此功能组合可扩展交互用户、脚本编写者和系统管理员的功能。</span><span class="sxs-lookup"><span data-stu-id="77973-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="77973-141">面向对象</span><span class="sxs-lookup"><span data-stu-id="77973-141">Object orientation</span></span>

<span data-ttu-id="77973-142">PowerShell 基于对象而非文本。</span><span class="sxs-lookup"><span data-stu-id="77973-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="77973-143">命令的输出是一个对象。</span><span class="sxs-lookup"><span data-stu-id="77973-143">The output of a command is an object.</span></span> <span data-ttu-id="77973-144">可以将输出对象通过管道发送给另一个命令以作为其输入。</span><span class="sxs-lookup"><span data-stu-id="77973-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="77973-145">此管道为具有使用其他 shell 经验的人员提供熟悉的界面。</span><span class="sxs-lookup"><span data-stu-id="77973-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="77973-146">通过发送对象而不是文本，PowerShell 扩展了这一概念。</span><span class="sxs-lookup"><span data-stu-id="77973-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="77973-147">轻松转换到脚本</span><span class="sxs-lookup"><span data-stu-id="77973-147">Easy transition to scripting</span></span>

<span data-ttu-id="77973-148">借助 PowerShell 的命令可发现性，可以从以交互方式键入命令轻松转换为创建和运行脚本。</span><span class="sxs-lookup"><span data-stu-id="77973-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="77973-149">使用 PowerShell 脚本和历史记录，可以轻松地将命令复制到文件以用作脚本。</span><span class="sxs-lookup"><span data-stu-id="77973-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>

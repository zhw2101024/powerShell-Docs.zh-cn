---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShell 脚本
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094045"
---
# <a name="powershell"></a><span data-ttu-id="97329-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="97329-103">PowerShell</span></span>

<span data-ttu-id="97329-104">PowerShell 在 .NET Framework 基础之上构建，是一种基于任务的命令行 Shell 脚本语言；专门面向系统管理员和高级用户，可快速自动化多个操作系统（Linux、macOS、Unix 和 Windows）和这些操作系统上运行的应用程序相关进程的管理。</span><span class="sxs-lookup"><span data-stu-id="97329-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="97329-105">PowerShell 是开放源代码</span><span class="sxs-lookup"><span data-stu-id="97329-105">PowerShell is open source</span></span>

<span data-ttu-id="97329-106">PowerShell 基本源代码目前在 GitHub 中提供，且对社区贡献开放。</span><span class="sxs-lookup"><span data-stu-id="97329-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="97329-107">请参阅 [GitHub 上的 PowerShell 源](https://github.com/powershell/powershell)。</span><span class="sxs-lookup"><span data-stu-id="97329-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="97329-108">可以从[获取 PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 中的所需位数入手。</span><span class="sxs-lookup"><span data-stu-id="97329-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="97329-109">或者快速查看[入门](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="97329-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="97329-110">PowerShell 设计目标</span><span class="sxs-lookup"><span data-stu-id="97329-110">PowerShell design goals</span></span>
<span data-ttu-id="97329-111">PowerShell 旨在消除长期存在的问题和添加新功能，从而改进命令行和脚本环境。</span><span class="sxs-lookup"><span data-stu-id="97329-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="97329-112">可发现性</span><span class="sxs-lookup"><span data-stu-id="97329-112">Discoverability</span></span>
<span data-ttu-id="97329-113">PowerShell 简化了它的功能发现过程。</span><span class="sxs-lookup"><span data-stu-id="97329-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="97329-114">例如，若要查找用于查看和更改 Windows 服务的 cmdlet 列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="97329-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="97329-115">发现完成任务的 cmdlet 后，可以运行 `Get-Help` cmdlet 来详细了解此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="97329-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="97329-116">例如，若要显示 `Get-Service` cmdlet 的帮助信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="97329-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="97329-117">大多数 cmdlet 会发出对象，这些对象可获得操作，然后再呈现为显示文本。</span><span class="sxs-lookup"><span data-stu-id="97329-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="97329-118">若要全面了解此 cmdlet 的输出，请将它的输出通过管道传递给 `Get-Member` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="97329-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="97329-119">例如，下面的命令显示 `Get-Service` cmdlet 的输出对象成员的相关信息。</span><span class="sxs-lookup"><span data-stu-id="97329-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="97329-120">一致性</span><span class="sxs-lookup"><span data-stu-id="97329-120">Consistency</span></span>
<span data-ttu-id="97329-121">管理系统是一项复杂的任务，具有一致的接口的工具有助于控制固有的复杂性。</span><span class="sxs-lookup"><span data-stu-id="97329-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="97329-122">遗憾的是，命令行工具和可脚本化 COM 对象的一致性均未知。</span><span class="sxs-lookup"><span data-stu-id="97329-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="97329-123">PowerShell 一致性是它的主要资产之一。</span><span class="sxs-lookup"><span data-stu-id="97329-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="97329-124">例如，如果了解如何使用 `Sort-Object` cmdlet，可以利用这一知识对任何 cmdlet 的输出进行排序。</span><span class="sxs-lookup"><span data-stu-id="97329-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="97329-125">不需要了解每个 cmdlet 的不同排序例程。</span><span class="sxs-lookup"><span data-stu-id="97329-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="97329-126">此外，cmdlet 开发人员无需为其 cmdlet 设计排序功能。</span><span class="sxs-lookup"><span data-stu-id="97329-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="97329-127">PowerShell 包含提供基本功能的框架，并强制在接口的多个方面保持一致。</span><span class="sxs-lookup"><span data-stu-id="97329-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="97329-128">该框架消除了通常留给开发人员的某些选择，但它也因而使得开发可靠的和易于使用的 cmdlet 变得简单得多。</span><span class="sxs-lookup"><span data-stu-id="97329-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="97329-129">交互式脚本编写环境</span><span class="sxs-lookup"><span data-stu-id="97329-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="97329-130">PowerShell 是组合的交互式脚本编写环境，便于用户访问命令行工具和 COM 对象，并使用 .NET Framework 类库 (FCL) 的强大功能。</span><span class="sxs-lookup"><span data-stu-id="97329-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="97329-131">此环境改进了 Windows 命令提示，它将提供具有多个命令行工具的交互式环境。</span><span class="sxs-lookup"><span data-stu-id="97329-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="97329-132">它还改进了 Windows 脚本宿主 (WSH) 脚本，让你可以使用多个命令行工具和 COM 自动化对象，但不提供交互式环境。</span><span class="sxs-lookup"><span data-stu-id="97329-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="97329-133">通过结合使用以上所有功能，PowerShell 可以扩展交互用户和脚本编写者的能力，并提高系统可管理性。</span><span class="sxs-lookup"><span data-stu-id="97329-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="97329-134">面向对象</span><span class="sxs-lookup"><span data-stu-id="97329-134">Object Orientation</span></span>
<span data-ttu-id="97329-135">尽管可以在文本框中键入命令与 PowerShell 交互，PowerShell 仍以对象（而不是文本）为基础。</span><span class="sxs-lookup"><span data-stu-id="97329-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="97329-136">命令的输出是一个对象。</span><span class="sxs-lookup"><span data-stu-id="97329-136">The output of a command is an object.</span></span>
<span data-ttu-id="97329-137">可以将输出对象发送给另一个命令以作为其输入。</span><span class="sxs-lookup"><span data-stu-id="97329-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="97329-138">因此，PowerShell 为使用过其他命令行管理程序的用户提供熟悉界面，同时引入新的强大命令行范例。</span><span class="sxs-lookup"><span data-stu-id="97329-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="97329-139">它让你能够发送对象而不是文本，从而扩展了在命令之间发送数据的概念。</span><span class="sxs-lookup"><span data-stu-id="97329-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="97329-140">轻松转换到脚本</span><span class="sxs-lookup"><span data-stu-id="97329-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="97329-141">借助 PowerShell，可以从以交互方式键入命令轻松转换为创建和运行脚本。</span><span class="sxs-lookup"><span data-stu-id="97329-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="97329-142">可以在 PowerShell 命令提示符处键入命令，从而发现执行某项任务的命令。</span><span class="sxs-lookup"><span data-stu-id="97329-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="97329-143">然后，你可以在将这些命令保存到副本或历史记录中，然后将其复制到文件以用作脚本。</span><span class="sxs-lookup"><span data-stu-id="97329-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>

---
title: 使用 Visual Studio Code 进行远程编辑和调试
description: 使用 Visual Studio Code 进行远程编辑和调试
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655573"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="cbc35-103">使用 Visual Studio Code 进行远程编辑和调试</span><span class="sxs-lookup"><span data-stu-id="cbc35-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="cbc35-104">对于您已熟悉 ISE，您可能记得，可以运行`psedit file.ps1`从打开的文件-本地或远程的集成控制台右键在 ISE 中。</span><span class="sxs-lookup"><span data-stu-id="cbc35-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="cbc35-105">事实证明，此功能也是适用于 VSCode 的 PowerShell 扩展中可用。</span><span class="sxs-lookup"><span data-stu-id="cbc35-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="cbc35-106">本指南将演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="cbc35-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cbc35-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="cbc35-107">Prerequisites</span></span>

<span data-ttu-id="cbc35-108">本指南假定你拥有：</span><span class="sxs-lookup"><span data-stu-id="cbc35-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="cbc35-109">远程资源 (例如： 虚拟机，容器) 有权访问</span><span class="sxs-lookup"><span data-stu-id="cbc35-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="cbc35-110">它和主机计算机上运行的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cbc35-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="cbc35-111">VSCode 和适用于 VSCode 的 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="cbc35-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="cbc35-112">此功能适用于 Windows PowerShell 和 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="cbc35-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="cbc35-113">连接到远程计算机通过 WinRM、 PowerShell Direct 或 SSH 时，此功能也适用。</span><span class="sxs-lookup"><span data-stu-id="cbc35-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="cbc35-114">如果你想要使用 SSH，但使用的 Windows，请查看[Win32 版本的 SSH](https://github.com/PowerShell/Win32-OpenSSH)！</span><span class="sxs-lookup"><span data-stu-id="cbc35-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="cbc35-115">开始</span><span class="sxs-lookup"><span data-stu-id="cbc35-115">Let's go</span></span>

<span data-ttu-id="cbc35-116">在本部分中，我将逐步远程编辑和调试从我正在 MacBook Pro，到 Ubuntu VM 在 Azure 中运行。</span><span class="sxs-lookup"><span data-stu-id="cbc35-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="cbc35-117">我可能没有使用 Windows，但**的过程是相同**。</span><span class="sxs-lookup"><span data-stu-id="cbc35-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="cbc35-118">使用打开 EditorFile 进行编辑的本地文件</span><span class="sxs-lookup"><span data-stu-id="cbc35-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="cbc35-119">使用 PowerShell 扩展启动 VSCode 并打开 PowerShell 控制台中集成，我们可以键入`Open-EditorFile foo.ps1`或`psedit foo.ps1`以在编辑器中打开本地 foo.ps1 文件权限。</span><span class="sxs-lookup"><span data-stu-id="cbc35-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![打开 EditorFile foo.ps1 可在本地工作](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="cbc35-121">foo.ps1 必须已存在。</span><span class="sxs-lookup"><span data-stu-id="cbc35-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="cbc35-122">在这里，我们可以：</span><span class="sxs-lookup"><span data-stu-id="cbc35-122">From there, we can:</span></span>

<span data-ttu-id="cbc35-123">将断点添加到滚动条槽![添加断点，以线](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="cbc35-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="cbc35-124">并按 F5 调试 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="cbc35-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="cbc35-125">![调试 PowerShell 本地脚本](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="cbc35-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="cbc35-126">调试时，可以使用调试控制台进行交互，请查看左侧和调试工具的所有其他标准中的作用域中的变量。</span><span class="sxs-lookup"><span data-stu-id="cbc35-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="cbc35-127">使用打开 EditorFile 进行编辑的远程文件</span><span class="sxs-lookup"><span data-stu-id="cbc35-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="cbc35-128">现在让我们将放入远程文件编辑和调试。</span><span class="sxs-lookup"><span data-stu-id="cbc35-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="cbc35-129">步骤都几乎相同，只是一件事我们需要先做-我们的 PowerShell 会话输入到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="cbc35-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="cbc35-130">没有为 cmdlet 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="cbc35-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="cbc35-131">它称为`Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="cbc35-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="cbc35-132">该 cmdlet 的已关闭说明是：</span><span class="sxs-lookup"><span data-stu-id="cbc35-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="cbc35-133">`Enter-PSSession -ComputerName foo` 启动 WinRM 通过会话</span><span class="sxs-lookup"><span data-stu-id="cbc35-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="cbc35-134">`Enter-PSSession -ContainerId foo` 和`Enter-PSSession -VmId foo`开始通过 PowerShell Direct 会话</span><span class="sxs-lookup"><span data-stu-id="cbc35-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="cbc35-135">`Enter-PSSession -HostName foo` 启动通过 SSH 会话</span><span class="sxs-lookup"><span data-stu-id="cbc35-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="cbc35-136">有关详细信息`Enter-PSSession`，签出文档[此处](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="cbc35-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="cbc35-137">我将使用 SSH 远程处理由于我从 macOS 将在 Azure 中的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="cbc35-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="cbc35-138">首先，在集成的控制台中，让我们运行我们 Enter-pssession。</span><span class="sxs-lookup"><span data-stu-id="cbc35-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="cbc35-139">您将知道由于是在会话中`[something]`会显示在提示符下的左侧。</span><span class="sxs-lookup"><span data-stu-id="cbc35-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Enter-pssession 调用](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="cbc35-141">在这里，我们可以像我们所编辑的本地脚本执行的确切步骤。</span><span class="sxs-lookup"><span data-stu-id="cbc35-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="cbc35-142">运行`Open-EditorFile test.ps1`或`psedit test.ps1`若要打开远程`test.ps1`文件![打开 EditorFile test.ps1 文件](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="cbc35-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="cbc35-143">编辑文件/设置断点</span><span class="sxs-lookup"><span data-stu-id="cbc35-143">Edit the file/set breakpoints</span></span> ![编辑并设置断点](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="cbc35-145">启动调试 (F5) 该远程文件</span><span class="sxs-lookup"><span data-stu-id="cbc35-145">Start debugging (F5) the remote file</span></span>

![调试远程文件](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="cbc35-147">这就是一切就这么简单 ！</span><span class="sxs-lookup"><span data-stu-id="cbc35-147">That's all there's to it!</span></span> <span data-ttu-id="cbc35-148">我们希望本指南帮助清除了有关远程调试和编辑 PowerShell 在 VSCode 中的任何问题。</span><span class="sxs-lookup"><span data-stu-id="cbc35-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="cbc35-149">如果有任何疑问，欢迎您随时打开问题[GitHub 存储库上](http://github.com/powershell/vscode-powershell)。</span><span class="sxs-lookup"><span data-stu-id="cbc35-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>

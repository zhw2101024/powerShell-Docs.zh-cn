---
title: 使用 Visual Studio Code 进行远程编辑和调试
description: 使用 Visual Studio Code 进行远程编辑和调试
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086658"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="fc528-103">使用 Visual Studio Code 进行远程编辑和调试</span><span class="sxs-lookup"><span data-stu-id="fc528-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="fc528-104">对于熟悉 ISE 的人来说，你可能还记得可以从集成控制台运行 `psedit file.ps1` 以在 ISE 中打开本地或远程文件。</span><span class="sxs-lookup"><span data-stu-id="fc528-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="fc528-105">事实证明，该功能在适用于 VSCode 的 PowerShell 扩展中也可用。</span><span class="sxs-lookup"><span data-stu-id="fc528-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="fc528-106">本指南将演示如何操作。</span><span class="sxs-lookup"><span data-stu-id="fc528-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc528-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="fc528-107">Prerequisites</span></span>

<span data-ttu-id="fc528-108">本指南假定你拥有：</span><span class="sxs-lookup"><span data-stu-id="fc528-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="fc528-109">可访问的远程资源（例如：虚拟机、容器）</span><span class="sxs-lookup"><span data-stu-id="fc528-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="fc528-110">在其中运行的 PowerShell 和主机计算机</span><span class="sxs-lookup"><span data-stu-id="fc528-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="fc528-111">VSCode 和适用于 VSCode 的 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="fc528-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="fc528-112">此功能适用于 Windows PowerShell 和 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="fc528-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="fc528-113">当通过 WinRM、PowerShell Direct 或 SSH 连接到远程计算机时，此功能也适用。</span><span class="sxs-lookup"><span data-stu-id="fc528-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="fc528-114">如果要使用 SSH，但使用的是 Windows，请查看 [Win32 版本的 SSH](https://github.com/PowerShell/Win32-OpenSSH)！</span><span class="sxs-lookup"><span data-stu-id="fc528-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="fc528-115">开始</span><span class="sxs-lookup"><span data-stu-id="fc528-115">Let's go</span></span>

<span data-ttu-id="fc528-116">在本节中，我将介绍从 MacBook Pro 到在 Azure 中运行的 Ubuntu VM 的远程编辑和调试。</span><span class="sxs-lookup"><span data-stu-id="fc528-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="fc528-117">我可能不使用 Windows，但过程是相同的。</span><span class="sxs-lookup"><span data-stu-id="fc528-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="fc528-118">使用 Open-EditorFile 编辑的本地文件</span><span class="sxs-lookup"><span data-stu-id="fc528-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="fc528-119">启动适用于 VSCode 的 PowerShell 扩展并打开 PowerShell 集成控制台之后，可以在编辑器中键入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1` 来打开本地 foo.ps1 文件。</span><span class="sxs-lookup"><span data-stu-id="fc528-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 可在本地工作](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="fc528-121">foo.ps1 必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="fc528-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="fc528-122">由此，我们可以：</span><span class="sxs-lookup"><span data-stu-id="fc528-122">From there, we can:</span></span>

<span data-ttu-id="fc528-123">向装订线添加断点![向装订线添加断点](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="fc528-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="fc528-124">并按 F5 调试 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="fc528-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="fc528-125">![调试 PowerShell 本地脚本](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="fc528-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="fc528-126">调试期间，可以与调试控制台进行交互，查看左边范围中的变量，以及所有其他标准调试工具。</span><span class="sxs-lookup"><span data-stu-id="fc528-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="fc528-127">使用 Open-EditorFile 编辑的远程文件</span><span class="sxs-lookup"><span data-stu-id="fc528-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="fc528-128">现在让我们进入远程文件编辑和调试。</span><span class="sxs-lookup"><span data-stu-id="fc528-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="fc528-129">步骤几乎相同，只需要先完成一个操作 - 将 PowerShell 会话输入到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="fc528-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="fc528-130">有一个 cmdlet 可以做到这一点。</span><span class="sxs-lookup"><span data-stu-id="fc528-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="fc528-131">它被称为 `Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="fc528-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="fc528-132">该 cmdlet 的简化说明是：</span><span class="sxs-lookup"><span data-stu-id="fc528-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="fc528-133">`Enter-PSSession -ComputerName foo` 通过 WinRM 启动会话</span><span class="sxs-lookup"><span data-stu-id="fc528-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="fc528-134">`Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 通过 PowerShell Direct 启动会话</span><span class="sxs-lookup"><span data-stu-id="fc528-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="fc528-135">`Enter-PSSession -HostName foo` 通过 SSH 启动会话</span><span class="sxs-lookup"><span data-stu-id="fc528-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="fc528-136">有关 `Enter-PSSession` 的详细信息，请查看[此处](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6)的文档。</span><span class="sxs-lookup"><span data-stu-id="fc528-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="fc528-137">我将使用 SSH 进行远程处理，因为我要从 macOS 转到 Azure 中的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="fc528-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="fc528-138">首先，在集成控制台中运行 Enter - PSSsession。</span><span class="sxs-lookup"><span data-stu-id="fc528-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="fc528-139">你会知道自己正在参与会话，因为 `[something]` 会显示在提示符左侧。</span><span class="sxs-lookup"><span data-stu-id="fc528-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![对 Enter-PSSession 的调用](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="fc528-141">在这里，我们可以执行与编辑本地脚本完全相同的步骤。</span><span class="sxs-lookup"><span data-stu-id="fc528-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="fc528-142">运行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 打开远程 `test.ps1` 文件 ![Open-EditorFile test.ps1 文件](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="fc528-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="fc528-143">编辑文件/设置断点</span><span class="sxs-lookup"><span data-stu-id="fc528-143">Edit the file/set breakpoints</span></span> ![编辑并设置断点](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="fc528-145">开始调试 (F5) 远程文件</span><span class="sxs-lookup"><span data-stu-id="fc528-145">Start debugging (F5) the remote file</span></span>

![调试远程文件](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="fc528-147">一切就是这么简单！</span><span class="sxs-lookup"><span data-stu-id="fc528-147">That's all there's to it!</span></span> <span data-ttu-id="fc528-148">我们希望本指南有助于解答有关在 VSCode 中远程调试和编辑 PowerShell 的任何问题。</span><span class="sxs-lookup"><span data-stu-id="fc528-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="fc528-149">如有任何疑问，欢迎随时[在 GitHub 存储库上](http://github.com/powershell/vscode-powershell)提问。</span><span class="sxs-lookup"><span data-stu-id="fc528-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>

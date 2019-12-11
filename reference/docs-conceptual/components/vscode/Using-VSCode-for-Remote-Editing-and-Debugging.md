---
title: 使用 Visual Studio Code 进行远程编辑和调试
description: 使用 Visual Studio Code 进行远程编辑和调试
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67264002"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="14f68-103">使用 Visual Studio Code 进行远程编辑和调试</span><span class="sxs-lookup"><span data-stu-id="14f68-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="14f68-104">对于熟悉 ISE 的你来说，你可能还记得可以从集成控制台运行 `psedit file.ps1` 以在 ISE 中打开本地或远程文件。</span><span class="sxs-lookup"><span data-stu-id="14f68-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="14f68-105">该功能在适用于 VSCode 的 PowerShell 扩展中也可用。</span><span class="sxs-lookup"><span data-stu-id="14f68-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="14f68-106">本指南将演示如何操作。</span><span class="sxs-lookup"><span data-stu-id="14f68-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14f68-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="14f68-107">Prerequisites</span></span>

<span data-ttu-id="14f68-108">本指南假定你拥有：</span><span class="sxs-lookup"><span data-stu-id="14f68-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="14f68-109">可访问的远程资源（例如：虚拟机、容器）</span><span class="sxs-lookup"><span data-stu-id="14f68-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="14f68-110">在其中运行的 PowerShell 和主机计算机</span><span class="sxs-lookup"><span data-stu-id="14f68-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="14f68-111">VSCode 和适用于 VSCode 的 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="14f68-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="14f68-112">此功能适用于 Windows PowerShell 和 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="14f68-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="14f68-113">当通过 WinRM、PowerShell Direct 或 SSH 连接到远程计算机时，此功能也适用。</span><span class="sxs-lookup"><span data-stu-id="14f68-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="14f68-114">如果要使用 SSH，但使用的是 Windows，请查看 [Win32 版本的 SSH](https://github.com/PowerShell/Win32-OpenSSH)！</span><span class="sxs-lookup"><span data-stu-id="14f68-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14f68-115">`Open-EditorFile` 和 `psedit` 命令仅适用于 PowerShell 集成控制台  （由适用于 VSCode 的 PowerShell 扩展创建）。</span><span class="sxs-lookup"><span data-stu-id="14f68-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="14f68-116">用法示例</span><span class="sxs-lookup"><span data-stu-id="14f68-116">Usage examples</span></span>

<span data-ttu-id="14f68-117">这些示例介绍从 MacBook Pro 到在 Azure 中运行的 Ubuntu VM 的远程编辑和调试。</span><span class="sxs-lookup"><span data-stu-id="14f68-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="14f68-118">Windows 上的过程相同。</span><span class="sxs-lookup"><span data-stu-id="14f68-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="14f68-119">使用 Open-EditorFile 编辑的本地文件</span><span class="sxs-lookup"><span data-stu-id="14f68-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="14f68-120">启动适用于 VSCode 的 PowerShell 扩展并打开 PowerShell 集成控制台之后，可以在编辑器中键入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1` 来打开本地 foo.ps1 文件。</span><span class="sxs-lookup"><span data-stu-id="14f68-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 可在本地工作](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="14f68-122">文件 `foo.ps1` 必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="14f68-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="14f68-123">由此，我们可以：</span><span class="sxs-lookup"><span data-stu-id="14f68-123">From there, we can:</span></span>

- <span data-ttu-id="14f68-124">将断点添加到装订线</span><span class="sxs-lookup"><span data-stu-id="14f68-124">Add breakpoints to the gutter</span></span>

  ![将断点添加到装订线](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="14f68-126">按 F5 调试 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="14f68-126">Hit F5 to debug the PowerShell script.</span></span>

  ![调试 PowerShell 本地脚本](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="14f68-128">调试期间，可以与调试控制台进行交互，查看左边范围中的变量，以及所有其他标准调试工具。</span><span class="sxs-lookup"><span data-stu-id="14f68-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="14f68-129">使用 Open-EditorFile 编辑的远程文件</span><span class="sxs-lookup"><span data-stu-id="14f68-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="14f68-130">现在让我们进入远程文件编辑和调试。</span><span class="sxs-lookup"><span data-stu-id="14f68-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="14f68-131">步骤几乎相同，只需要先完成一个操作 - 将 PowerShell 会话输入到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="14f68-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="14f68-132">有一个 cmdlet 可以做到这一点。</span><span class="sxs-lookup"><span data-stu-id="14f68-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="14f68-133">它被称为 `Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="14f68-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="14f68-134">该 cmdlet 的简化说明是：</span><span class="sxs-lookup"><span data-stu-id="14f68-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="14f68-135">`Enter-PSSession -ComputerName foo` 通过 WinRM 启动会话</span><span class="sxs-lookup"><span data-stu-id="14f68-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="14f68-136">`Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 通过 PowerShell Direct 启动会话</span><span class="sxs-lookup"><span data-stu-id="14f68-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="14f68-137">`Enter-PSSession -HostName foo` 通过 SSH 启动会话</span><span class="sxs-lookup"><span data-stu-id="14f68-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="14f68-138">有关详细信息，请参阅 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) 的文档。</span><span class="sxs-lookup"><span data-stu-id="14f68-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="14f68-139">由于我们要从 macOS 转到 Azure 中的 Ubuntu VM，因此我们将使用 SSH 进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="14f68-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="14f68-140">首先，在集成控制台中，运行 `Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="14f68-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="14f68-141">当提示符的左侧显示 `[<hostname>]` 时，即表示已连接到远程会话。</span><span class="sxs-lookup"><span data-stu-id="14f68-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![对 Enter-PSSession 的调用](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="14f68-143">现在，我们可以执行与编辑本地脚本相同的步骤。</span><span class="sxs-lookup"><span data-stu-id="14f68-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="14f68-144">运行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 以打开远程 `test.ps1` 文件</span><span class="sxs-lookup"><span data-stu-id="14f68-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Open-EditorFile test.ps1 文件](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="14f68-146">编辑文件/设置断点</span><span class="sxs-lookup"><span data-stu-id="14f68-146">Edit the file/set breakpoints</span></span>

   ![编辑并设置断点](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="14f68-148">开始调试 (F5) 远程文件</span><span class="sxs-lookup"><span data-stu-id="14f68-148">Start debugging (F5) the remote file</span></span>

   ![调试远程文件](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="14f68-150">如有任何疑问，可在 [GitHub 存储库](https://github.com/powershell/vscode-powershell)中提问。</span><span class="sxs-lookup"><span data-stu-id="14f68-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>

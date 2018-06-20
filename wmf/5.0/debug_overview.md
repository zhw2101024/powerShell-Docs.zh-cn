---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187096"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="afed6-102">PowerShell 脚本调试中的改进</span><span class="sxs-lookup"><span data-stu-id="afed6-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="afed6-103">在 PowerShell 5.0 中已进行了大量改进来增强调试体验：</span><span class="sxs-lookup"><span data-stu-id="afed6-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="afed6-104">全部中断</span><span class="sxs-lookup"><span data-stu-id="afed6-104">Break All</span></span>

<span data-ttu-id="afed6-105">PowerShell 控制台和 Windows PowerShell ISE 现在可以中断调试器，而运行脚本。</span><span class="sxs-lookup"><span data-stu-id="afed6-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="afed6-106">这在本地和远程会话中很有效。</span><span class="sxs-lookup"><span data-stu-id="afed6-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="afed6-107">在控制台中，按 **Ctrl+Break**。</span><span class="sxs-lookup"><span data-stu-id="afed6-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="afed6-108">在 ISE 中，按 **Ctrl+B**，或使用“调试”->“全部中断”菜单命令。</span><span class="sxs-lookup"><span data-stu-id="afed6-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="afed6-109">Windows PowerShell ISE 中的远程调试和远程文件编辑</span><span class="sxs-lookup"><span data-stu-id="afed6-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="afed6-110">Windows PowerShell ISE 现在可以通过运行 PSEdit 命令，在远程会话中打开并编辑文件。</span><span class="sxs-lookup"><span data-stu-id="afed6-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="afed6-111">例如，你可以在远程会话中打开文件并从命令行进行编辑，如下所示：</span><span class="sxs-lookup"><span data-stu-id="afed6-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="afed6-112">此外，你现在还可以在远程文件中编辑并保存更改，远程文件是你命中断点时在 Windows PowerShell ISE 中自动打开的文件。</span><span class="sxs-lookup"><span data-stu-id="afed6-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="afed6-113">现在，你可以调试在远程计算机上运行的脚本文件，编辑该文件以修复错误，然后重新运行修改后的脚本。</span><span class="sxs-lookup"><span data-stu-id="afed6-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="afed6-114">高级脚本调试</span><span class="sxs-lookup"><span data-stu-id="afed6-114">Advanced Script Debugging</span></span>

<span data-ttu-id="afed6-115">新的高级调试功能使你能够附加到已加载 Windows PowerShell 的任何本地计算机进程，并在该进程中调试任意运行空间。</span><span class="sxs-lookup"><span data-stu-id="afed6-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="afed6-116">运行空间调试</span><span class="sxs-lookup"><span data-stu-id="afed6-116">Runspace Debugging</span></span>

<span data-ttu-id="afed6-117">已添加的新 cmdlet 使你能够列出某个进程中的当前运行空间，并将 Windows PowerShell 控制台或 ISE 调试器附加到该运行空间进行脚本调试：</span><span class="sxs-lookup"><span data-stu-id="afed6-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="afed6-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="afed6-118">Get-Runspace</span></span>
-   <span data-ttu-id="afed6-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="afed6-119">Debug-Runspace</span></span>
-   <span data-ttu-id="afed6-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="afed6-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="afed6-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="afed6-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="afed6-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="afed6-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="afed6-123">附加到承载 PowerShell 的进程</span><span class="sxs-lookup"><span data-stu-id="afed6-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="afed6-124">你现在可以附加到已加载 Windows PowerShell 的任何计算机进程。</span><span class="sxs-lookup"><span data-stu-id="afed6-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="afed6-125">可通过输入与该进程交互的会话执行此操作，类似于你通过运行 Enter-PSSession cmdlet 输入交互式远程会话的操作方式。</span><span class="sxs-lookup"><span data-stu-id="afed6-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="afed6-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="afed6-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="afed6-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="afed6-127">Exit-PSHostProcess</span></span>

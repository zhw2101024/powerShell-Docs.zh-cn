---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 更改计算机状态
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736907"
---
# <a name="changing-computer-state"></a><span data-ttu-id="f6797-103">更改计算机状态</span><span class="sxs-lookup"><span data-stu-id="f6797-103">Changing Computer State</span></span>

<span data-ttu-id="f6797-104">若要在 PowerShell 中重置计算机，请使用标准命令行工具、WMI 或 CIM 类。</span><span class="sxs-lookup"><span data-stu-id="f6797-104">To reset a computer in PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span>
<span data-ttu-id="f6797-105">尽管你使用 PowerShell 仅仅是为了运行该工具，但了解如何在 PowerShell 中更改计算机的电源状态将阐明有关在 PowerShell 中使用外部工具的一些重要详细信息。</span><span class="sxs-lookup"><span data-stu-id="f6797-105">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="f6797-106">锁定计算机</span><span class="sxs-lookup"><span data-stu-id="f6797-106">Locking a Computer</span></span>

<span data-ttu-id="f6797-107">使用标准可用工具直接锁定计算机的唯一方法是调用 **user32.dll** 中的 **LockWorkstation()** 函数：</span><span class="sxs-lookup"><span data-stu-id="f6797-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="f6797-108">此命令将立即锁定工作站。</span><span class="sxs-lookup"><span data-stu-id="f6797-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="f6797-109">它使用 rundll32.exe  ，后者运行 Windows DLL（并保存其库以便重复使用）以运行 `user32.dll`（Windows 管理函数的库）。</span><span class="sxs-lookup"><span data-stu-id="f6797-109">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="f6797-110">如果在启用了“快速用户切换”时锁定工作站（例如在 Windows XP 中），则计算机将显示用户登录屏幕，而不会启动当前用户的屏幕保护程序。</span><span class="sxs-lookup"><span data-stu-id="f6797-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="f6797-111">若要关闭终端服务器上的特定会话，请使用 **tsshutdn.exe** 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="f6797-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="f6797-112">注销当前会话</span><span class="sxs-lookup"><span data-stu-id="f6797-112">Logging Off the Current Session</span></span>

<span data-ttu-id="f6797-113">可以使用多种不同的方法来注销本地系统上的会话。</span><span class="sxs-lookup"><span data-stu-id="f6797-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="f6797-114">最简单的方法是使用远程桌面/终端服务命令行工具 logoff.exe  （若要了解有关详细信息，请在 PowerShell 提示符处键入 `logoff /?`）。</span><span class="sxs-lookup"><span data-stu-id="f6797-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="f6797-115">若要注销当前活动会话，请键入 `logoff` 而不带参数。</span><span class="sxs-lookup"><span data-stu-id="f6797-115">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="f6797-116">你还可以使用具 **shutdown.exe** 工具及其 logoff 选项：</span><span class="sxs-lookup"><span data-stu-id="f6797-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="f6797-117">另一种方法是使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="f6797-117">Another option is to use WMI.</span></span> <span data-ttu-id="f6797-118">Win32_OperatingSystem  类具有 Shutdown  方法。</span><span class="sxs-lookup"><span data-stu-id="f6797-118">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="f6797-119">调用具有 0 标志的方法将启动注销：</span><span class="sxs-lookup"><span data-stu-id="f6797-119">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="f6797-120">有关 Shutdown  方法的详细信息，请参阅 [Win32_OperatingSystem 类的 Shutdown 方法](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="f6797-120">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="f6797-121">关闭或重启计算机</span><span class="sxs-lookup"><span data-stu-id="f6797-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="f6797-122">关闭和重启计算机通常是相同类型的任务。</span><span class="sxs-lookup"><span data-stu-id="f6797-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="f6797-123">关闭计算机的工具通常也可以重启计算机，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="f6797-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="f6797-124">从 PowerShell 重启计算机有两个直接的选项。</span><span class="sxs-lookup"><span data-stu-id="f6797-124">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="f6797-125">使用 tsshutdn.exe  或 shutdown.exe  及其相应参数。</span><span class="sxs-lookup"><span data-stu-id="f6797-125">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="f6797-126">你可以从 `tsshutdn.exe /?` 或 `shutdown.exe /?` 获取详细的使用信息。</span><span class="sxs-lookup"><span data-stu-id="f6797-126">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="f6797-127">也可以直接从 PowerShell 执行关闭和重启操作。</span><span class="sxs-lookup"><span data-stu-id="f6797-127">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="f6797-128">要关闭计算机，请使用 Stop-Computer 命令</span><span class="sxs-lookup"><span data-stu-id="f6797-128">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="f6797-129">要重启操作系统，请使用 Restart-Computer 命令</span><span class="sxs-lookup"><span data-stu-id="f6797-129">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="f6797-130">要强制立即重新启动计算机，请使用 -Force 参数。</span><span class="sxs-lookup"><span data-stu-id="f6797-130">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```

---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 启动 Windows PowerShell
ms.openlocfilehash: d2cb77027f404c5b008a902c5147d018dd741a67
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030450"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="baf2a-103">启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="baf2a-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="baf2a-104">PowerShell 是一个脚本引擎 dll，嵌入到多个主机中。</span><span class="sxs-lookup"><span data-stu-id="baf2a-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="baf2a-105">启动的最常见主机是交互式命令行 PowerShell.exe 和交互式脚本环境 PowerShell_ISE.exe。</span><span class="sxs-lookup"><span data-stu-id="baf2a-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="baf2a-106">若要在 Windows Server® 2012 R2、Windows® 8.1、Windows Server 2012 和 Windows 8 上启动 Windows PowerShell®，请参阅[常见管理任务和导航](https://technet.microsoft.com/library/hh831491.aspx)。</span><span class="sxs-lookup"><span data-stu-id="baf2a-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="baf2a-107">如何在早期版本的 Windows 上启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="baf2a-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="baf2a-108">本部分介绍了如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 上启动 Windows PowerShell 和 Windows PowerShell 集成脚本环境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="baf2a-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="baf2a-109">还介绍了如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中启用 Windows PowerShell ISE 的可选功能。</span><span class="sxs-lookup"><span data-stu-id="baf2a-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="baf2a-110">使用以下任一方法来启动已安装的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="baf2a-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="baf2a-111">在“开始”菜单中</span><span class="sxs-lookup"><span data-stu-id="baf2a-111">From the Start Menu</span></span>

- <span data-ttu-id="baf2a-112">单击“开始”  ，键入 **PowerShell**，然后单击“Windows PowerShell”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="baf2a-113">在“开始”  菜单中，依次单击“开始”  、“所有程序”  、“附件”  、“Windows PowerShell”  文件夹，然后单击“Windows PowerShell”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="baf2a-114">在命令提示符处</span><span class="sxs-lookup"><span data-stu-id="baf2a-114">At the Command Prompt</span></span>

<span data-ttu-id="baf2a-115">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：</span><span class="sxs-lookup"><span data-stu-id="baf2a-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="baf2a-116">你还可以使用 PowerShell.exe 程序的参数来自定义会话。</span><span class="sxs-lookup"><span data-stu-id="baf2a-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="baf2a-117">有关详细信息，请参阅 [PowerShell.exe 命令行帮助](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="baf2a-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="baf2a-118">使用管理权限（“以管理员身份运行”）</span><span class="sxs-lookup"><span data-stu-id="baf2a-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="baf2a-119">单击“**开始**”，键入 **PowerShell**，右键单击“**Windows PowerShell**”，然后单击“**以管理员身份运行**”。</span><span class="sxs-lookup"><span data-stu-id="baf2a-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="baf2a-120">如何在早期版本的 Windows 上启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="baf2a-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="baf2a-121">使用以下任一方法启动 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="baf2a-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="baf2a-122">在“开始”菜单中</span><span class="sxs-lookup"><span data-stu-id="baf2a-122">From the Start Menu</span></span>

- <span data-ttu-id="baf2a-123">单击“开始”  ，键入 **ISE**，然后单击“Windows PowerShell ISE”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="baf2a-124">在“开始”  菜单中，依次单击“开始”  、“所有程序”  、“附件”  、“Windows PowerShell”  文件夹，然后单击“Windows PowerShell ISE”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="baf2a-125">在命令提示符处</span><span class="sxs-lookup"><span data-stu-id="baf2a-125">At the Command Prompt</span></span>

<span data-ttu-id="baf2a-126">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：</span><span class="sxs-lookup"><span data-stu-id="baf2a-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="baf2a-127">或</span><span class="sxs-lookup"><span data-stu-id="baf2a-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="baf2a-128">使用管理权限（“以管理员身份运行”）</span><span class="sxs-lookup"><span data-stu-id="baf2a-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="baf2a-129">单击“**开始**”，键入 **ISE**，右键单击“**Windows PowerShell ISE**”，然后单击“**以管理员身份运行**”。</span><span class="sxs-lookup"><span data-stu-id="baf2a-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="baf2a-130">如何在早期版本的 Windows 上启用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="baf2a-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="baf2a-131">在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，默认情况下，所有版本的 Windows 上都启用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="baf2a-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="baf2a-132">如果尚未启用，则 Windows Management Framework 4.0 或 Windows Management Framework 3.0 会启用它。</span><span class="sxs-lookup"><span data-stu-id="baf2a-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="baf2a-133">在 Windows PowerShell 2.0 中，默认情况下，在 Windows 7 上启用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="baf2a-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="baf2a-134">但是，在 Windows Server 2008 R2 和 Windows Server 2008 上，它是一项可选功能。</span><span class="sxs-lookup"><span data-stu-id="baf2a-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="baf2a-135">若要启用 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中的 Windows PowerShell ISE，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="baf2a-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="baf2a-136">启用 Windows PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="baf2a-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="baf2a-137">启动“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="baf2a-137">Start Server Manager.</span></span>
2. <span data-ttu-id="baf2a-138">单击“功能”  ，然后单击“添加功能”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="baf2a-139">在“选择功能”中，单击“Windows PowerShell 集成脚本环境 (ISE)”</span><span class="sxs-lookup"><span data-stu-id="baf2a-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="baf2a-140">启动 32 位版本的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="baf2a-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="baf2a-141">在 64 位计算机 (**Windows PowerShell (x86)** ) 上安装 Windows PowerShell 时，除 64 位版之外，还将安装 32 位版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="baf2a-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="baf2a-142">运行 Windows PowerShell 时，默认运行 64 位版。</span><span class="sxs-lookup"><span data-stu-id="baf2a-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="baf2a-143">但是，有时可能需要运行 **Windows PowerShell (x86)** ，例如使用需要 32 位版的模块时，或者远程连接到 32 位计算机时。</span><span class="sxs-lookup"><span data-stu-id="baf2a-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="baf2a-144">若要启动 32 位版本的 Windows PowerShell，请使用以下任何过程。</span><span class="sxs-lookup"><span data-stu-id="baf2a-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="baf2a-145">在 Windows Server® 2012 R2 中</span><span class="sxs-lookup"><span data-stu-id="baf2a-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="baf2a-146">在“开始”  屏幕上，键入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="baf2a-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="baf2a-147">单击“Windows PowerShell x86”  磁贴。</span><span class="sxs-lookup"><span data-stu-id="baf2a-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="baf2a-148">在“服务器管理器”  中，从“工具”  菜单中选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-149">在桌面上，将光标移动到右上角，单击“搜索”  ，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-150">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="baf2a-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="baf2a-151">在 Windows Server® 2012 中</span><span class="sxs-lookup"><span data-stu-id="baf2a-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="baf2a-152">在“开始”  屏幕上，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-153">在“服务器管理器”  中，从“工具”  菜单中选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-154">在桌面上，将光标移动到右上角，单击“搜索”  ，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-155">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="baf2a-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="baf2a-156">在 Windows® 8.1 中</span><span class="sxs-lookup"><span data-stu-id="baf2a-156">In Windows® 8.1</span></span>

- <span data-ttu-id="baf2a-157">在“开始”  屏幕上，键入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="baf2a-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="baf2a-158">单击“Windows PowerShell x86”  磁贴。</span><span class="sxs-lookup"><span data-stu-id="baf2a-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="baf2a-159">如果你正在运行 Windows 8.1 的[远程服务器管理工具](https://go.microsoft.com/fwlink/?LinkID=304145)，则也可从“服务器管理器工具”  菜单中打开 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="baf2a-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="baf2a-160">选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-161">在桌面上，将光标移动到右上角，单击“搜索”  ，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-162">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="baf2a-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="baf2a-163">在 Windows® 8 中</span><span class="sxs-lookup"><span data-stu-id="baf2a-163">In Windows® 8</span></span>

- <span data-ttu-id="baf2a-164">在“开始”  屏幕上，将光标移动到右上角，依次单击“设置”  、“磁贴”  ，然后将“显示管理工具”  滑块移动到“是”。</span><span class="sxs-lookup"><span data-stu-id="baf2a-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="baf2a-165">然后，键入 **PowerShell**，单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-166">如果你正在运行 Windows 8 的[远程服务器管理工具](https://www.microsoft.com/download/details.aspx?id=28972)，则也可从“服务器管理器工具”  菜单中打开 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="baf2a-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="baf2a-167">选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-168">在“开始”  屏幕或桌面上，键入 **PowerShell (x86)** ，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="baf2a-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="baf2a-169">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="baf2a-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

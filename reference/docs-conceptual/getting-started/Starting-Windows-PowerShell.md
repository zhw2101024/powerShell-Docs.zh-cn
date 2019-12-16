---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: 启动 Windows PowerShell
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953817"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="7ec82-103">启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ec82-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="7ec82-104">Windows PowerShell 是一个嵌入到多个主机中的脚本引擎 `.DLL`。</span><span class="sxs-lookup"><span data-stu-id="7ec82-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="7ec82-105">启动的最常见主机是交互式命令行 powershell.exe 和交互式脚本环境 powershell_ise.exe   。</span><span class="sxs-lookup"><span data-stu-id="7ec82-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="7ec82-106">若要在 Windows Server® 2012 R2、Windows® 8.1、Windows Server 2012 和 Windows 8 上启动 Windows PowerShell®，请参阅 [Windows 中的常见管理任务和导航](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="7ec82-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="7ec82-107">PowerShell Core 已重命名二进制文件</span><span class="sxs-lookup"><span data-stu-id="7ec82-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="7ec82-108">PowerShell Core（称为 PowerShell）为第 6 版及更高版本，采用开源代码并使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7ec82-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="7ec82-109">受支持的版本在 Windows、macOS 和 Linux 上可用。</span><span class="sxs-lookup"><span data-stu-id="7ec82-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="7ec82-110">自 PowerShell 6 起，PowerShell 二进制文件已分别重命名为 pwsh.exe（适用于 Windows）和 pwsh（适用于 macOS 和 Linux）   。</span><span class="sxs-lookup"><span data-stu-id="7ec82-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="7ec82-111">可以使用 pwsh-preview 启动 PowerShell 预览版  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="7ec82-112">有关详细信息，请参阅 [PowerShell Core 6.0 中的新增功能](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe)和[关于 pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="7ec82-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="7ec82-113">若要查找 PowerShell 7 的 cmdlet 参考文档和安装文档，请使用以下链接：</span><span class="sxs-lookup"><span data-stu-id="7ec82-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="7ec82-114">文档</span><span class="sxs-lookup"><span data-stu-id="7ec82-114">Document</span></span> | <span data-ttu-id="7ec82-115">链接</span><span class="sxs-lookup"><span data-stu-id="7ec82-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="7ec82-116">Cmdlet 参考</span><span class="sxs-lookup"><span data-stu-id="7ec82-116">Cmdlet reference</span></span> | [<span data-ttu-id="7ec82-117">PowerShell 模块浏览器</span><span class="sxs-lookup"><span data-stu-id="7ec82-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="7ec82-118">Windows 安装</span><span class="sxs-lookup"><span data-stu-id="7ec82-118">Windows installation</span></span> | [<span data-ttu-id="7ec82-119">在 Windows 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="7ec82-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="7ec82-120">macOS 安装</span><span class="sxs-lookup"><span data-stu-id="7ec82-120">macOS installation</span></span> | [<span data-ttu-id="7ec82-121">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="7ec82-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="7ec82-122">Linux 安装</span><span class="sxs-lookup"><span data-stu-id="7ec82-122">Linux installation</span></span> | [<span data-ttu-id="7ec82-123">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="7ec82-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="7ec82-124">若要查看其他 PowerShell 版本的相关内容，请参阅[如何使用 PowerShell 文档](../how-to-use-docs.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec82-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="7ec82-125">如何在早期版本的 Windows 上启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ec82-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="7ec82-126">本部分介绍了如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 上启动 Windows PowerShell 和 Windows PowerShell 集成脚本环境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="7ec82-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="7ec82-127">还介绍了如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中启用 Windows PowerShell ISE 的可选功能。</span><span class="sxs-lookup"><span data-stu-id="7ec82-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="7ec82-128">使用以下任一方法来启动已安装的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="7ec82-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="7ec82-129">在“开始”菜单中</span><span class="sxs-lookup"><span data-stu-id="7ec82-129">From the Start Menu</span></span>

- <span data-ttu-id="7ec82-130">单击“开始”  ，键入 **PowerShell**，然后单击“Windows PowerShell”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="7ec82-131">在“开始”  菜单中，依次单击“开始”  、“所有程序”  、“附件”  、“Windows PowerShell”  文件夹，然后单击“Windows PowerShell”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="7ec82-132">在命令提示符处</span><span class="sxs-lookup"><span data-stu-id="7ec82-132">At the Command Prompt</span></span>

<span data-ttu-id="7ec82-133">在 cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入  ：</span><span class="sxs-lookup"><span data-stu-id="7ec82-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="7ec82-134">你还可以使用 powershell.exe 程序的参数来自定义会话  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="7ec82-135">有关详细信息，请参阅 [PowerShell.exe 命令行帮助](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec82-135">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="7ec82-136">使用管理权限（以管理员身份运行）</span><span class="sxs-lookup"><span data-stu-id="7ec82-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="7ec82-137">单击“**开始**”，键入 **PowerShell**，右键单击“**Windows PowerShell**”，然后单击“**以管理员身份运行**”。</span><span class="sxs-lookup"><span data-stu-id="7ec82-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="7ec82-138">如何在早期版本的 Windows 上启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7ec82-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="7ec82-139">使用以下任一方法启动 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="7ec82-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="7ec82-140">在“开始”菜单中</span><span class="sxs-lookup"><span data-stu-id="7ec82-140">From the Start Menu</span></span>

- <span data-ttu-id="7ec82-141">单击“开始”  ，键入 **ISE**，然后单击“Windows PowerShell ISE”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="7ec82-142">在“开始”  菜单中，依次单击“开始”  、“所有程序”  、“附件”  、“Windows PowerShell”  文件夹，然后单击“Windows PowerShell ISE”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="7ec82-143">在命令提示符处</span><span class="sxs-lookup"><span data-stu-id="7ec82-143">At the Command Prompt</span></span>

<span data-ttu-id="7ec82-144">在 cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入  ：</span><span class="sxs-lookup"><span data-stu-id="7ec82-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="7ec82-145">或</span><span class="sxs-lookup"><span data-stu-id="7ec82-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="7ec82-146">使用管理权限（以管理员身份运行）</span><span class="sxs-lookup"><span data-stu-id="7ec82-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="7ec82-147">单击“**开始**”，键入 **ISE**，右键单击“**Windows PowerShell ISE**”，然后单击“**以管理员身份运行**”。</span><span class="sxs-lookup"><span data-stu-id="7ec82-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="7ec82-148">如何在早期版本的 Windows 上启用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7ec82-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="7ec82-149">在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，默认情况下，所有版本的 Windows 上都启用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="7ec82-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="7ec82-150">如果尚未启用，则 Windows Management Framework 4.0 或 Windows Management Framework 3.0 会启用它。</span><span class="sxs-lookup"><span data-stu-id="7ec82-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="7ec82-151">在 Windows PowerShell 2.0 中，默认情况下，在 Windows 7 上启用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="7ec82-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="7ec82-152">但是，在 Windows Server 2008 R2 和 Windows Server 2008 上，它是一项可选功能。</span><span class="sxs-lookup"><span data-stu-id="7ec82-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="7ec82-153">若要启用 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中的 Windows PowerShell ISE，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="7ec82-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="7ec82-154">启用 Windows PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="7ec82-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="7ec82-155">启动“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="7ec82-155">Start Server Manager.</span></span>
2. <span data-ttu-id="7ec82-156">单击“功能”  ，然后单击“添加功能”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="7ec82-157">在“选择功能”中，单击“Windows PowerShell 集成脚本环境 (ISE)”</span><span class="sxs-lookup"><span data-stu-id="7ec82-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="7ec82-158">启动 32 位版本的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ec82-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="7ec82-159">在 64 位计算机 (**Windows PowerShell (x86)** ) 上安装 Windows PowerShell 时，除 64 位版之外，还将安装 32 位版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7ec82-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="7ec82-160">运行 Windows PowerShell 时，默认运行 64 位版。</span><span class="sxs-lookup"><span data-stu-id="7ec82-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="7ec82-161">但是，有时可能需要运行 Windows PowerShell (x86)，例如使用需要 32 位版本的模块时，或者远程连接到 32 位计算机时  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="7ec82-162">若要启动 32 位版本的 Windows PowerShell，请使用以下任何过程。</span><span class="sxs-lookup"><span data-stu-id="7ec82-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="7ec82-163">在 Windows Server® 2012 R2 中</span><span class="sxs-lookup"><span data-stu-id="7ec82-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="7ec82-164">在“开始”  屏幕上，键入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="7ec82-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="7ec82-165">单击“Windows PowerShell x86”  磁贴。</span><span class="sxs-lookup"><span data-stu-id="7ec82-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="7ec82-166">在“服务器管理器”  中，从“工具”  菜单中选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-167">在桌面上，将光标移动到右上角，单击“搜索”  ，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-168">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="7ec82-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="7ec82-169">在 Windows Server® 2012 中</span><span class="sxs-lookup"><span data-stu-id="7ec82-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="7ec82-170">在“开始”  屏幕上，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-171">在“服务器管理器”  中，从“工具”  菜单中选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-172">在桌面上，将光标移动到右上角，单击“搜索”  ，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-173">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="7ec82-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="7ec82-174">在 Windows® 8.1 中</span><span class="sxs-lookup"><span data-stu-id="7ec82-174">In Windows® 8.1</span></span>

- <span data-ttu-id="7ec82-175">在“开始”  屏幕上，键入 **Windows PowerShell (x86)** 。</span><span class="sxs-lookup"><span data-stu-id="7ec82-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="7ec82-176">单击“Windows PowerShell x86”  磁贴。</span><span class="sxs-lookup"><span data-stu-id="7ec82-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="7ec82-177">如果你正在运行 Windows 8.1 的[远程服务器管理工具](https://go.microsoft.com/fwlink/?LinkID=304145)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="7ec82-178">选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-179">在桌面上，将光标移动到右上角，单击“搜索”  ，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-180">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="7ec82-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="7ec82-181">在 Windows® 8 中</span><span class="sxs-lookup"><span data-stu-id="7ec82-181">In Windows® 8</span></span>

- <span data-ttu-id="7ec82-182">在“开始”屏幕上，将光标移动到右上角，依次单击“设置”、“磁贴”，然后将“显示管理工具”滑块移动到“是”      。</span><span class="sxs-lookup"><span data-stu-id="7ec82-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="7ec82-183">然后，键入 **PowerShell**，单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-184">如果你正在运行 Windows 8 的[远程服务器管理工具](https://www.microsoft.com/download/details.aspx?id=28972)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="7ec82-185">选择“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-186">在“开始”  屏幕或桌面上，键入 **PowerShell (x86)** ，然后单击“Windows PowerShell (x86)”  。</span><span class="sxs-lookup"><span data-stu-id="7ec82-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="7ec82-187">通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="7ec82-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

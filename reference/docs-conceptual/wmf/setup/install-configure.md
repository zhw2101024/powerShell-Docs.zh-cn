---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
contributor: keithb
title: 安装和配置 WMF 5.1
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402364"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="b857d-103">安装和配置 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b857d-103">Install and Configure WMF 5.1</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b857d-104">WMF 5.0 已被 WMF 5.1 取代。</span><span class="sxs-lookup"><span data-stu-id="b857d-104">WMF 5.0 is superseded by WMF 5.1.</span></span> <span data-ttu-id="b857d-105">使用 WMF 5.0 的用户必须升级到 WMF 5.1 才能接受支持。</span><span class="sxs-lookup"><span data-stu-id="b857d-105">Users with WMF 5.0 must upgrade to WMF 5.1 to receive support.</span></span>
> <span data-ttu-id="b857d-106">WMF 5.1 需要 .NET Framework 4.5.2 或更高版本  。</span><span class="sxs-lookup"><span data-stu-id="b857d-106">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="b857d-107">安装将成功，但如果未安装 .NET 4.5.2 或更高版本，将无法使用主要功能。</span><span class="sxs-lookup"><span data-stu-id="b857d-107">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="b857d-108">下载和安装 WMF 5.1 包</span><span class="sxs-lookup"><span data-stu-id="b857d-108">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="b857d-109">下载适用于要在其中进行安装的操作系统和体系结构的 WMF 5.1 包：</span><span class="sxs-lookup"><span data-stu-id="b857d-109">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="b857d-110">操作系统</span><span class="sxs-lookup"><span data-stu-id="b857d-110">Operating System</span></span>       | <span data-ttu-id="b857d-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="b857d-111">Prerequisites</span></span>           | <span data-ttu-id="b857d-112">包链接</span><span class="sxs-lookup"><span data-stu-id="b857d-112">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="b857d-113">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b857d-113">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="b857d-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b857d-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="b857d-115">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b857d-115">Windows Server 2012</span></span>    |                         | <span data-ttu-id="b857d-116">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b857d-116">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="b857d-117">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b857d-117">Windows Server 2008 R2</span></span> | <span data-ttu-id="b857d-118">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="b857d-118">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="b857d-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b857d-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="b857d-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="b857d-120">Windows 8.1</span></span>            |                         | <span data-ttu-id="b857d-121">**x64：** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b857d-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="b857d-122">**x86：** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="b857d-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="b857d-123">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="b857d-123">Windows 7 SP1</span></span>          | <span data-ttu-id="b857d-124">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="b857d-124">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="b857d-125">**x64：** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b857d-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="b857d-126">**x86：** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b857d-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- <span data-ttu-id="b857d-133">安装 WMF 5.1 RTM 之前，必须先卸载 WMF 5.1 预览版。</span><span class="sxs-lookup"><span data-stu-id="b857d-133">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="b857d-134">可在 WMF 5.0 或 WMF 4.0 上直接安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="b857d-134">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="b857d-135">在 Windows 7 和 Windows Server 2008 R2 上安装 WMF 5.1 前，无需  安装 WMF 4.0。</span><span class="sxs-lookup"><span data-stu-id="b857d-135">It is **not required** to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="b857d-136">安装适用于 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b857d-136">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="b857d-137">针对 Windows Server 2008 R2 和 Windows 7 的安装说明发生变化，不同于其他包的安装说明。</span><span class="sxs-lookup"><span data-stu-id="b857d-137">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="b857d-138">下文中介绍了针对 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安装说明。</span><span class="sxs-lookup"><span data-stu-id="b857d-138">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a><span data-ttu-id="b857d-139">Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 系统必备</span><span class="sxs-lookup"><span data-stu-id="b857d-139">WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1</span></span>

<span data-ttu-id="b857d-140">若要在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安装 WMF 5.1，必须先安装以下各项：</span><span class="sxs-lookup"><span data-stu-id="b857d-140">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>

- <span data-ttu-id="b857d-141">必须安装最新 Service Pack。</span><span class="sxs-lookup"><span data-stu-id="b857d-141">Latest service pack must be installed.</span></span>
- <span data-ttu-id="b857d-142">**不得**安装 WMF 3.0。</span><span class="sxs-lookup"><span data-stu-id="b857d-142">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="b857d-143">安装 WMF 5.1 来替代 WMF 3.0 会导致 PSModulePath (`$env:PSModulePath`) 丢失，进而可能会导致其他应用无法正常运行  。</span><span class="sxs-lookup"><span data-stu-id="b857d-143">Installing WMF 5.1 over WMF 3.0 will result in the loss of the **PSModulePath** (`$env:PSModulePath`), which can cause other applications to fail.</span></span> <span data-ttu-id="b857d-144">安装 WMF 5.1 前，要么必须先卸载 WMF 3.0，要么必须先保存 PSModulePath，然后在 WMF 5.1 安装完成后进行手动还原  。</span><span class="sxs-lookup"><span data-stu-id="b857d-144">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the **PSModulePath** and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="b857d-145">WMF 5.1 中至少需要[.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)。</span><span class="sxs-lookup"><span data-stu-id="b857d-145">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span></span>
  <span data-ttu-id="b857d-146">可按照下载位置的说明安装 Microsoft .NET Framework 4.5.2。</span><span class="sxs-lookup"><span data-stu-id="b857d-146">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="b857d-147">在 Windows Server 2008 R2 和 Windows 7 上安装 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b857d-147">Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7</span></span>

1. <span data-ttu-id="b857d-148">转到在其中下载了 ZIP 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b857d-148">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="b857d-149">右键单击 ZIP 文件，然后选择“全部提取...”  。ZIP 文件包含两个文件：MSU 和 `Install-WMF5.1.ps1` 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="b857d-149">Right-click on the ZIP file, and select **Extract All...**. The ZIP file contains two files: an MSU and the `Install-WMF5.1.ps1` script file.</span></span> <span data-ttu-id="b857d-150">解压缩 ZIP 文件后，便可以将内容复制到运行 Windows 7 或 Windows Server 2008 R2 的任何一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="b857d-150">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="b857d-151">提取 ZIP 文件内容后，以管理员身份打开 PowerShell，然后导航到包含 ZIP 文件内容的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b857d-151">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="b857d-152">在此文件夹中运行 `Install-WMF5.1.ps1` 脚本，然后按说明操作。</span><span class="sxs-lookup"><span data-stu-id="b857d-152">Run the `Install-WMF5.1.ps1` script in that folder, and follow the instructions.</span></span> <span data-ttu-id="b857d-153">此脚本会在本地计算机上检查系统必备，如果系统必备已满足，则会安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="b857d-153">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="b857d-154">下文中列出了系统必备。</span><span class="sxs-lookup"><span data-stu-id="b857d-154">The prerequisites are listed below.</span></span>

   <span data-ttu-id="b857d-155">`Install-WMF5.1.ps1` 采用以下参数，以简化在 Windows Server 2008 R2 和 Windows 7 上自动执行安装：</span><span class="sxs-lookup"><span data-stu-id="b857d-155">`Install-WMF5.1.ps1` takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

   - <span data-ttu-id="b857d-156">**AcceptEula**：如果包含此参数，将会自动接受但不显示 EULA。</span><span class="sxs-lookup"><span data-stu-id="b857d-156">**AcceptEula**: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
   - <span data-ttu-id="b857d-157">**AllowRestart**：只有在指定 AcceptEula 后，才能使用此参数。</span><span class="sxs-lookup"><span data-stu-id="b857d-157">**AllowRestart**: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="b857d-158">如果包含此参数，并且在安装 WMF 5.1 后需要重启，将在安装完成后不发出提示就立即重启计算机。</span><span class="sxs-lookup"><span data-stu-id="b857d-158">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="b857d-159">WinRM 依赖关系</span><span class="sxs-lookup"><span data-stu-id="b857d-159">WinRM Dependency</span></span>

<span data-ttu-id="b857d-160">Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。</span><span class="sxs-lookup"><span data-stu-id="b857d-160">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="b857d-161">在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="b857d-161">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="b857d-162">若要启用 WinRM，在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="b857d-162">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="b857d-163">安装适用于 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b857d-163">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

### <a name="install-from-windows-file-explorer"></a><span data-ttu-id="b857d-164">从 Windows 文件资源管理器安装</span><span class="sxs-lookup"><span data-stu-id="b857d-164">Install from Windows File Explorer</span></span>

1. <span data-ttu-id="b857d-165">导航到在其中下载了 MSU 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b857d-165">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="b857d-166">双击 MSU 以运行它。</span><span class="sxs-lookup"><span data-stu-id="b857d-166">Double-click the MSU to run it.</span></span>

### <a name="installing-from-the-command-prompt"></a><span data-ttu-id="b857d-167">通过命令提示符进行安装</span><span class="sxs-lookup"><span data-stu-id="b857d-167">Installing from the Command Prompt</span></span>

1. <span data-ttu-id="b857d-168">下载适用于计算机体系结构的正确程序包后，使用提升的用户权限（以管理员身份运行）打开“命令提示符”窗口。</span><span class="sxs-lookup"><span data-stu-id="b857d-168">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="b857d-169">在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的服务器核心安装选项上，命令提示符默认使用提升的用户权限打开。</span><span class="sxs-lookup"><span data-stu-id="b857d-169">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="b857d-170">将目录更改为向其中下载或复制 WMF 5.1 安装包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b857d-170">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="b857d-171">运行下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="b857d-171">Run one of the following commands:</span></span>
   - <span data-ttu-id="b857d-172">在运行 Windows Server 2012 R2 或 Windows 8.1 x64 的计算机上，运行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="b857d-172">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="b857d-173">在运行 Windows Server 2012 的计算机上，运行 `W2K12-KB3191565-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="b857d-173">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="b857d-174">在运行 Windows 8.1 x86 的计算机上，运行 `Win8.1-KB3191564-x86.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="b857d-174">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="b857d-175">安装 WMF 5.1 需要重新启动。</span><span class="sxs-lookup"><span data-stu-id="b857d-175">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="b857d-176">使用 `/quiet` 选项将重新启动系统而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="b857d-176">Using the `/quiet` option will reboot the system without warning.</span></span> <span data-ttu-id="b857d-177">使用 `/norestart` 选项可避免重新启动。</span><span class="sxs-lookup"><span data-stu-id="b857d-177">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="b857d-178">但是，要重新启动才会安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="b857d-178">However, WMF 5.1 will not be installed until you have rebooted.</span></span>

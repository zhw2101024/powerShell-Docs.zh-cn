---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
contributor: keithb
title: 安装和配置 WMF 5.1
ms.openlocfilehash: e5c7968744a442b4be9f1e43a45e91429a6d6165
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676207"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="c2364-103">安装和配置 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c2364-103">Install and Configure WMF 5.1</span></span> #


## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="c2364-104">下载和安装 WMF 5.1 包</span><span class="sxs-lookup"><span data-stu-id="c2364-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="c2364-105">下载适用于要在其中进行安装的操作系统和体系结构的 WMF 5.1 包：</span><span class="sxs-lookup"><span data-stu-id="c2364-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="c2364-106">操作系统</span><span class="sxs-lookup"><span data-stu-id="c2364-106">Operating System</span></span>       | <span data-ttu-id="c2364-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="c2364-107">Prerequisites</span></span>           | <span data-ttu-id="c2364-108">包链接</span><span class="sxs-lookup"><span data-stu-id="c2364-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="c2364-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c2364-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="c2364-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="c2364-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="c2364-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c2364-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="c2364-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="c2364-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="c2364-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c2364-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="c2364-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="c2364-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="c2364-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="c2364-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="c2364-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c2364-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="c2364-117">**x64：**[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="c2364-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="c2364-118">**x86：**[Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="c2364-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="c2364-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="c2364-119">Windows 7 SP1</span></span>          | <span data-ttu-id="c2364-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="c2364-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="c2364-121">**x64：**[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="c2364-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="c2364-122">**x86：**[Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="c2364-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="c2364-129">安装适用于 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c2364-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="c2364-130">**注意：** 针对 Windows Server 2008 R2 和 Windows 7 的安装说明发生变化，不同于其他包的安装说明。</span><span class="sxs-lookup"><span data-stu-id="c2364-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="c2364-131">下文中介绍了针对 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安装说明。</span><span class="sxs-lookup"><span data-stu-id="c2364-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="c2364-132">**在 Windows Server 2008 R2 和 Windows 7 上安装 WMF 5.1**</span><span class="sxs-lookup"><span data-stu-id="c2364-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="c2364-133">转到在其中下载了 ZIP 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2364-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="c2364-134">右键单击 ZIP 文件，然后选择“全部提取...”。</span><span class="sxs-lookup"><span data-stu-id="c2364-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="c2364-135">ZIP 文件中包含 2 个文件：MSU 和 Install-WMF5.1.PS1 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="c2364-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="c2364-136">解压缩 ZIP 文件后，便可以将内容复制到运行 Windows 7 或 Windows Server 2008 R2 的任何一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="c2364-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="c2364-137">提取 ZIP 文件内容后，以管理员身份打开 PowerShell，然后导航到包含 ZIP 文件内容的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2364-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="c2364-138">在此文件夹中运行 Install-Wmf5.1.ps1 脚本，然后按说明操作。</span><span class="sxs-lookup"><span data-stu-id="c2364-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="c2364-139">此脚本会在本地计算机上检查系统必备，如果系统必备已满足，则会安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="c2364-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="c2364-140">下文中列出了系统必备。</span><span class="sxs-lookup"><span data-stu-id="c2364-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="c2364-141">Install-WMF5.1.ps1 采用以下参数，以简化在 Windows Server 2008 R2 和 Windows 7 上自动执行安装：</span><span class="sxs-lookup"><span data-stu-id="c2364-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="c2364-142">AcceptEula如果包括此参数，则最终用户许可协议将自动接受，并将不会显示。</span><span class="sxs-lookup"><span data-stu-id="c2364-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="c2364-143">AllowRestart:如果指定 AcceptEula 后，才可以使用此参数。</span><span class="sxs-lookup"><span data-stu-id="c2364-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="c2364-144">如果包含此参数，并且在安装 WMF 5.1 后需要重启，将在安装完成后不发出提示就立即重启计算机。</span><span class="sxs-lookup"><span data-stu-id="c2364-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="c2364-145">**Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 系统必备**</span><span class="sxs-lookup"><span data-stu-id="c2364-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="c2364-146">若要在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安装 WMF 5.1，必须先安装以下各项：</span><span class="sxs-lookup"><span data-stu-id="c2364-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="c2364-147">必须安装最新 Service Pack。</span><span class="sxs-lookup"><span data-stu-id="c2364-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="c2364-148">**不得**安装 WMF 3.0。</span><span class="sxs-lookup"><span data-stu-id="c2364-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="c2364-149">安装 WMF 5.1 来替代 WMF 3.0 会导致 PSModulePath 丢失，进而可能会导致其他应用程序无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="c2364-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="c2364-150">安装 WMF 5.1 前，要么必须先卸载 WMF 3.0，要么必须先保存 PSModulePath，然后在 WMF 5.1 安装完成后进行手动还原。</span><span class="sxs-lookup"><span data-stu-id="c2364-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="c2364-151">WMF 5.1 中至少需要[.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642)。</span><span class="sxs-lookup"><span data-stu-id="c2364-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="c2364-152">可按照下载位置的说明安装 Microsoft .NET Framework 4.5.2。</span><span class="sxs-lookup"><span data-stu-id="c2364-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="c2364-153">**WinRM 依赖关系**</span><span class="sxs-lookup"><span data-stu-id="c2364-153">**WinRM Dependency**</span></span>

<span data-ttu-id="c2364-154">Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。</span><span class="sxs-lookup"><span data-stu-id="c2364-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="c2364-155">在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="c2364-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="c2364-156">若要启用 WinRM，在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="c2364-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="c2364-157">安装适用于 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c2364-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>
<span data-ttu-id="c2364-158">**在 Windows 资源管理器（或 Windows Server 2012 R2 或 Windows 8.1 中的文件资源管理器）中安装**</span><span class="sxs-lookup"><span data-stu-id="c2364-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="c2364-159">导航到在其中下载了 MSU 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2364-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="c2364-160">双击 MSU 以运行它。</span><span class="sxs-lookup"><span data-stu-id="c2364-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="c2364-161">**通过命令提示符进行安装**</span><span class="sxs-lookup"><span data-stu-id="c2364-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="c2364-162">下载适用于计算机体系结构的正确程序包后，使用提升的用户权限（以管理员身份运行）打开“命令提示符”窗口。</span><span class="sxs-lookup"><span data-stu-id="c2364-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="c2364-163">在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的服务器核心安装选项上，命令提示符默认使用提升的用户权限打开。</span><span class="sxs-lookup"><span data-stu-id="c2364-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="c2364-164">将目录更改为向其中下载或复制 WMF 5.1 安装包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2364-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="c2364-165">运行下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="c2364-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="c2364-166">在运行 Windows Server 2012 R2 或 Windows 8.1 x64 的计算机上，运行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="c2364-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="c2364-167">在运行 Windows Server 2012 的计算机上，运行 `W2K12-KB3191565-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="c2364-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="c2364-168">在运行 Windows 8.1 x86 的计算机上，运行 `Win8.1-KB3191564-x86.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="c2364-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="c2364-169">安装 WMF 5.1 需要重新启动。</span><span class="sxs-lookup"><span data-stu-id="c2364-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="c2364-170">使用 `/quiet` 选项将重新启动系统而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="c2364-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="c2364-171">使用 `/norestart` 选项可避免重新启动。</span><span class="sxs-lookup"><span data-stu-id="c2364-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="c2364-172">但是，要重新启动才会安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="c2364-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>

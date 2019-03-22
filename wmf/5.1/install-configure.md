---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
contributor: keithb
title: 安装和配置 WMF 5.1
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055980"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="ec966-103">安装和配置 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ec966-103">Install and Configure WMF 5.1</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="ec966-104">下载和安装 WMF 5.1 包</span><span class="sxs-lookup"><span data-stu-id="ec966-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="ec966-105">下载适用于要在其中进行安装的操作系统和体系结构的 WMF 5.1 包：</span><span class="sxs-lookup"><span data-stu-id="ec966-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="ec966-106">操作系统</span><span class="sxs-lookup"><span data-stu-id="ec966-106">Operating System</span></span>       | <span data-ttu-id="ec966-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="ec966-107">Prerequisites</span></span>           | <span data-ttu-id="ec966-108">包链接</span><span class="sxs-lookup"><span data-stu-id="ec966-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="ec966-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ec966-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="ec966-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="ec966-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="ec966-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ec966-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="ec966-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="ec966-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="ec966-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ec966-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="ec966-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="ec966-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="ec966-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="ec966-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="ec966-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ec966-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="ec966-117">**x64：**[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="ec966-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="ec966-118">**x86：**[Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="ec966-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="ec966-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="ec966-119">Windows 7 SP1</span></span>          | <span data-ttu-id="ec966-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="ec966-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="ec966-121">**x64：**[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="ec966-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="ec966-122">**x86：**[Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="ec966-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="ec966-129">安装适用于 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ec966-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="ec966-130">针对 Windows Server 2008 R2 和 Windows 7 的安装说明发生变化，不同于其他包的安装说明。</span><span class="sxs-lookup"><span data-stu-id="ec966-130">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="ec966-131">下文中介绍了针对 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安装说明。</span><span class="sxs-lookup"><span data-stu-id="ec966-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="ec966-132">**在 Windows Server 2008 R2 和 Windows 7 上安装 WMF 5.1**</span><span class="sxs-lookup"><span data-stu-id="ec966-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="ec966-133">转到在其中下载了 ZIP 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ec966-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="ec966-134">右键单击 ZIP 文件，然后选择“全部提取...”。</span><span class="sxs-lookup"><span data-stu-id="ec966-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="ec966-135">ZIP 文件中包含 2 个文件：MSU 和 Install-WMF5.1.PS1 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="ec966-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="ec966-136">解压缩 ZIP 文件后，便可以将内容复制到运行 Windows 7 或 Windows Server 2008 R2 的任何一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="ec966-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="ec966-137">提取 ZIP 文件内容后，以管理员身份打开 PowerShell，然后导航到包含 ZIP 文件内容的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ec966-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="ec966-138">在此文件夹中运行 Install-Wmf5.1.ps1 脚本，然后按说明操作。</span><span class="sxs-lookup"><span data-stu-id="ec966-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="ec966-139">此脚本会在本地计算机上检查系统必备，如果系统必备已满足，则会安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="ec966-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="ec966-140">下文中列出了系统必备。</span><span class="sxs-lookup"><span data-stu-id="ec966-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="ec966-141">Install-WMF5.1.ps1 采用以下参数，以简化在 Windows Server 2008 R2 和 Windows 7 上自动执行安装：</span><span class="sxs-lookup"><span data-stu-id="ec966-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="ec966-142">AcceptEula：如果包含此参数，将会自动接受但不显示 EULA。</span><span class="sxs-lookup"><span data-stu-id="ec966-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="ec966-143">AllowRestart：只有在指定 AcceptEula 后，才能使用此参数。</span><span class="sxs-lookup"><span data-stu-id="ec966-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="ec966-144">如果包含此参数，并且在安装 WMF 5.1 后需要重启，将在安装完成后不发出提示就立即重启计算机。</span><span class="sxs-lookup"><span data-stu-id="ec966-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="ec966-145">**Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 系统必备**</span><span class="sxs-lookup"><span data-stu-id="ec966-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="ec966-146">若要在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安装 WMF 5.1，必须先安装以下各项：</span><span class="sxs-lookup"><span data-stu-id="ec966-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="ec966-147">必须安装最新 Service Pack。</span><span class="sxs-lookup"><span data-stu-id="ec966-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="ec966-148">**不得**安装 WMF 3.0。</span><span class="sxs-lookup"><span data-stu-id="ec966-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="ec966-149">安装 WMF 5.1 来替代 WMF 3.0 会导致 PSModulePath 丢失，进而可能会导致其他应用程序无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="ec966-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="ec966-150">安装 WMF 5.1 前，要么必须先卸载 WMF 3.0，要么必须先保存 PSModulePath，然后在 WMF 5.1 安装完成后进行手动还原。</span><span class="sxs-lookup"><span data-stu-id="ec966-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="ec966-151">WMF 5.1 中至少需要[.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642)。</span><span class="sxs-lookup"><span data-stu-id="ec966-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="ec966-152">可按照下载位置的说明安装 Microsoft .NET Framework 4.5.2。</span><span class="sxs-lookup"><span data-stu-id="ec966-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="ec966-153">**WinRM 依赖关系**</span><span class="sxs-lookup"><span data-stu-id="ec966-153">**WinRM Dependency**</span></span>

<span data-ttu-id="ec966-154">Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。</span><span class="sxs-lookup"><span data-stu-id="ec966-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="ec966-155">在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="ec966-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="ec966-156">若要启用 WinRM，在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="ec966-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="ec966-157">安装适用于 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ec966-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

<span data-ttu-id="ec966-158">**在 Windows 资源管理器（或 Windows Server 2012 R2 或 Windows 8.1 中的文件资源管理器）中安装**</span><span class="sxs-lookup"><span data-stu-id="ec966-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="ec966-159">导航到在其中下载了 MSU 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ec966-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="ec966-160">双击 MSU 以运行它。</span><span class="sxs-lookup"><span data-stu-id="ec966-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="ec966-161">**通过命令提示符进行安装**</span><span class="sxs-lookup"><span data-stu-id="ec966-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="ec966-162">下载适用于计算机体系结构的正确程序包后，使用提升的用户权限（以管理员身份运行）打开“命令提示符”窗口。</span><span class="sxs-lookup"><span data-stu-id="ec966-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="ec966-163">在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的服务器核心安装选项上，命令提示符默认使用提升的用户权限打开。</span><span class="sxs-lookup"><span data-stu-id="ec966-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="ec966-164">将目录更改为向其中下载或复制 WMF 5.1 安装包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ec966-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="ec966-165">运行下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="ec966-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="ec966-166">在运行 Windows Server 2012 R2 或 Windows 8.1 x64 的计算机上，运行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="ec966-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="ec966-167">在运行 Windows Server 2012 的计算机上，运行 `W2K12-KB3191565-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="ec966-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="ec966-168">在运行 Windows 8.1 x86 的计算机上，运行 `Win8.1-KB3191564-x86.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="ec966-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="ec966-169">安装 WMF 5.1 需要重新启动。</span><span class="sxs-lookup"><span data-stu-id="ec966-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="ec966-170">使用 `/quiet` 选项将重新启动系统而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="ec966-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="ec966-171">使用 `/norestart` 选项可避免重新启动。</span><span class="sxs-lookup"><span data-stu-id="ec966-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="ec966-172">但是，要重新启动才会安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="ec966-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>

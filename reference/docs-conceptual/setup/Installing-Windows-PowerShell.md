---
ms.date: 2017-08-09
keywords: "powershell, cmdlet, 下载, 安装, 设置, windows 10, windows 8.1, windows 8.0, windows 7"
title: "安装 Windows PowerShell"
ms.openlocfilehash: 781bf50b6ac649e72bcdbb708555275fb7422d94
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="a6bfa-103">安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="a6bfa-104">从 Windows 7 SP1 和 Windows Server 2008 R2 SP1 开始，每个 Windows 中默认随附安装有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="a6bfa-105">希望在计算机中安装 PowerShell 6 (beta) 的 Linux、macOS 和 Windows 用户需要：</span><span class="sxs-lookup"><span data-stu-id="a6bfa-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="a6bfa-106">从 [GitHub](https://github.com/powershell/powershell#get-powershell) 获取适用于指定 OS 和版本的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="a6bfa-107">按照安装说明操作</span><span class="sxs-lookup"><span data-stu-id="a6bfa-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="a6bfa-108">Linux</span><span class="sxs-lookup"><span data-stu-id="a6bfa-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="a6bfa-109">macOS</span><span class="sxs-lookup"><span data-stu-id="a6bfa-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [<span data-ttu-id="a6bfa-110">Windows</span><span class="sxs-lookup"><span data-stu-id="a6bfa-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="a6bfa-111">PowerShell 6 也可用于 Docker；请参阅 [Docker 安装](https://github.com/PowerShell/PowerShell/tree/master/docker)说明。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="a6bfa-112">在 Windows 10、8.1、8.0 和 7 中查找 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="a6bfa-113">有时在 Windows 中查找 PowerShell 控制台或 ISE（集成脚本环境）并非易事，因为其位置会随不同的 Windows 版本而发生移动。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="a6bfa-114">以下表格应有助于在使用的 Windows 版本中查找 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="a6bfa-115">此处列出的所有版本均为发布时的原始版本，没有进行任何更新。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="a6bfa-116">控制台</span><span class="sxs-lookup"><span data-stu-id="a6bfa-116">For Console</span></span>

<span data-ttu-id="a6bfa-117">版本</span><span class="sxs-lookup"><span data-stu-id="a6bfa-117">Version</span></span> | <span data-ttu-id="a6bfa-118">位置</span><span class="sxs-lookup"><span data-stu-id="a6bfa-118">Location</span></span>
-- | --
<span data-ttu-id="a6bfa-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a6bfa-119">Windows 10</span></span> | <span data-ttu-id="a6bfa-120">单击左下角的 Windows 图标，键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="a6bfa-121">Windows 8.1、8.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="a6bfa-122">在开始屏幕上，键入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="a6bfa-123">如果位于桌面，请单击左下角的 Windows 图标，键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="a6bfa-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-124">Windows 7 SP1</span></span> | <span data-ttu-id="a6bfa-125">单击左下角的 Windows 图标，在搜索框中键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="a6bfa-126">ISE</span><span class="sxs-lookup"><span data-stu-id="a6bfa-126">For ISE</span></span>

<span data-ttu-id="a6bfa-127">版本</span><span class="sxs-lookup"><span data-stu-id="a6bfa-127">Version</span></span> | <span data-ttu-id="a6bfa-128">位置</span><span class="sxs-lookup"><span data-stu-id="a6bfa-128">Location</span></span>
-- | --
<span data-ttu-id="a6bfa-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a6bfa-129">Windows 10</span></span> | <span data-ttu-id="a6bfa-130">单击左下角的 Windows 图标，键入 ISE</span><span class="sxs-lookup"><span data-stu-id="a6bfa-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="a6bfa-131">Windows 8.1、8.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="a6bfa-132">在“开始”屏幕上，键入 PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="a6bfa-133">如果位于桌面，请单击左下角的 Windows 图标，键入 PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a6bfa-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="a6bfa-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-134">Windows 7 SP1</span></span> | <span data-ttu-id="a6bfa-135">单击左下角的 Windows 图标，在搜索框中键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="a6bfa-136">在 Windows Server 版本中查找 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="a6bfa-137">从 Windows Server 2008 R2 开始，安装操作系统可不包含图形用户界面 (GUI)。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="a6bfa-138">不含 GUI 的 Windows Server 版本名为“核心”版本，包含 GUI 的版本名为“桌面”版本。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="a6bfa-139">Windows Server 核心版本</span><span class="sxs-lookup"><span data-stu-id="a6bfa-139">Windows Server Core editions</span></span>

<span data-ttu-id="a6bfa-140">在所有核心版本中，登录到服务器时会显示 Windows 命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="a6bfa-141">键入 `powershell` 并按“Enter”可在命令提示符会话内启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="a6bfa-142">键入 `exit` 可终止 PowerShell 会话并返回命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="a6bfa-143">Windows Server 桌面版本</span><span class="sxs-lookup"><span data-stu-id="a6bfa-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="a6bfa-144">在所有桌面版本中，单击左下角的 Windows 图标，键入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="a6bfa-145">将显示控制台和 ISE 选项。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-145">You get both console and ISE options.</span></span>

<span data-ttu-id="a6bfa-146">上述规则的唯一例外是 Windows Server 2008 R2 SP1 中的 ISE；这种情况下，请单击左下角的 Windows 图标，键入 PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="a6bfa-147">如何检查 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="a6bfa-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="a6bfa-148">若要查看已安装的 PowerShell 版本，请启动 PowerShell 控制台（或 ISE），键入 `$PSVersionTable`，然后按“Enter”。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="a6bfa-149">升级现有 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="a6bfa-150">PowerShell 安装包随附于 WMF 安装程序内。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="a6bfa-151">WMF 安装程序版本与 PowerShell 版本一致；不提供 Windows PowerShell 独立安装程序。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="a6bfa-152">如需在 Windows 中更新现有 PowerShell 版本，请使用下表找到要更新至的 PowerShell 版本的安装程序。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="a6bfa-153">Windows</span><span class="sxs-lookup"><span data-stu-id="a6bfa-153">Windows</span></span> | <span data-ttu-id="a6bfa-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-154">PS 3.0</span></span> | <span data-ttu-id="a6bfa-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-155">PS 4.0</span></span> | <span data-ttu-id="a6bfa-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-156">PS 5.0</span></span> | <span data-ttu-id="a6bfa-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="a6bfa-158">Windows 10（参见说明 1）</span><span class="sxs-lookup"><span data-stu-id="a6bfa-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="a6bfa-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a6bfa-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="a6bfa-160">已安装</span><span class="sxs-lookup"><span data-stu-id="a6bfa-160">installed</span></span>
<span data-ttu-id="a6bfa-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-161">Windows 8.1</span></span><br/><span data-ttu-id="a6bfa-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a6bfa-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="a6bfa-163">已安装</span><span class="sxs-lookup"><span data-stu-id="a6bfa-163">installed</span></span> | [<span data-ttu-id="a6bfa-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="a6bfa-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="a6bfa-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="a6bfa-166">Windows 8</span></span><br/><span data-ttu-id="a6bfa-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a6bfa-167">Windows Server 2012</span></span> | <span data-ttu-id="a6bfa-168">已安装</span><span class="sxs-lookup"><span data-stu-id="a6bfa-168">installed</span></span> | [<span data-ttu-id="a6bfa-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="a6bfa-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="a6bfa-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="a6bfa-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-172">Windows 7 SP1</span></span><br/><span data-ttu-id="a6bfa-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="a6bfa-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="a6bfa-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="a6bfa-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="a6bfa-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="a6bfa-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a6bfa-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="a6bfa-178">**说明 1**：</span><span class="sxs-lookup"><span data-stu-id="a6bfa-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="a6bfa-179">Windows 10 初始版本中，由于已启用自动更新，因此 PowerShell 会从版本 5.0 更新至 5.1。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="a6bfa-180">如果 Windows 10 原始版本未通过 Windows 更新进行更新，则 PowerShell 版本为 5.0。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="a6bfa-181">需要 Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-181">Need Azure PowerShell</span></span>

<span data-ttu-id="a6bfa-182">如需要 Azure PowerShell，请先参阅 [Azure PowerShell 概述](https://docs.microsoft.com/en-us/powershell/azure)。</span><span class="sxs-lookup"><span data-stu-id="a6bfa-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="a6bfa-183">或者，可能需要参阅[安装和配置 Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="a6bfa-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="a6bfa-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6bfa-184">See Also</span></span>

- [<span data-ttu-id="a6bfa-185">Windows PowerShell 系统要求</span><span class="sxs-lookup"><span data-stu-id="a6bfa-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="a6bfa-186">启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6bfa-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)

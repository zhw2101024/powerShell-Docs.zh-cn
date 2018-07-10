---
ms.date: 08/09/2017
keywords: powershell, cmdlet, 下载, 安装, 设置, windows 10, windows 8.1, windows 8.0, windows 7
title: 安装 Windows PowerShell
ms.openlocfilehash: e703d3444b1d661c482b314781cf9a1cb16ef7ed
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893515"
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="59a12-103">安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="59a12-104">从 Windows 7 SP1 和 Windows Server 2008 R2 SP1 开始，每个 Windows 中默认随附安装有 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59a12-104">Windows PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="59a12-105">如果你对 PowerShell 6 及更高版本感兴趣，则需要安装 PowerShell Core 而不是 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59a12-105">If you are interested in PowerShell 6 and later, you need to install PowerShell Core instead of Windows PowerShell.</span></span> <span data-ttu-id="59a12-106">关于相应的信息，请参阅[在 Windows 上安装 PowerShell Core](Installing-PowerShell-Core-on-Windows.md)。</span><span class="sxs-lookup"><span data-stu-id="59a12-106">For that, see [Installing PowerShell Core on Windows](Installing-PowerShell-Core-on-Windows.md).</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="59a12-107">在 Windows 10、8.1、8.0 和 7 中查找 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-107">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="59a12-108">有时在 Windows 中查找 PowerShell 控制台或 ISE（集成脚本环境）并非易事，因为其位置会随不同的 Windows 版本而发生移动。</span><span class="sxs-lookup"><span data-stu-id="59a12-108">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="59a12-109">以下表格应有助于在使用的 Windows 版本中查找 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59a12-109">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="59a12-110">此处列出的所有版本均为发布时的原始版本，没有进行任何更新。</span><span class="sxs-lookup"><span data-stu-id="59a12-110">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="59a12-111">控制台</span><span class="sxs-lookup"><span data-stu-id="59a12-111">For Console</span></span>

<span data-ttu-id="59a12-112">版本</span><span class="sxs-lookup"><span data-stu-id="59a12-112">Version</span></span> | <span data-ttu-id="59a12-113">位置</span><span class="sxs-lookup"><span data-stu-id="59a12-113">Location</span></span>
-- | --
<span data-ttu-id="59a12-114">Windows 10</span><span class="sxs-lookup"><span data-stu-id="59a12-114">Windows 10</span></span> | <span data-ttu-id="59a12-115">单击左下角的 Windows 图标，键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-115">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="59a12-116">Windows 8.1、8.0</span><span class="sxs-lookup"><span data-stu-id="59a12-116">Windows 8.1, 8.0</span></span> | <span data-ttu-id="59a12-117">在开始屏幕上，键入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59a12-117">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="59a12-118">如果位于桌面，请单击左下角的 Windows 图标，键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-118">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="59a12-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="59a12-119">Windows 7 SP1</span></span> | <span data-ttu-id="59a12-120">单击左下角的 Windows 图标，在搜索框中键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-120">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="59a12-121">ISE</span><span class="sxs-lookup"><span data-stu-id="59a12-121">For ISE</span></span>

<span data-ttu-id="59a12-122">版本</span><span class="sxs-lookup"><span data-stu-id="59a12-122">Version</span></span> | <span data-ttu-id="59a12-123">位置</span><span class="sxs-lookup"><span data-stu-id="59a12-123">Location</span></span>
-- | --
<span data-ttu-id="59a12-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="59a12-124">Windows 10</span></span> | <span data-ttu-id="59a12-125">单击左下角的 Windows 图标，键入 ISE</span><span class="sxs-lookup"><span data-stu-id="59a12-125">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="59a12-126">Windows 8.1、8.0</span><span class="sxs-lookup"><span data-stu-id="59a12-126">Windows 8.1, 8.0</span></span> | <span data-ttu-id="59a12-127">在“开始”屏幕上，键入 PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="59a12-127">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="59a12-128">如果位于桌面，请单击左下角的 Windows 图标，键入 PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="59a12-128">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="59a12-129">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="59a12-129">Windows 7 SP1</span></span> | <span data-ttu-id="59a12-130">单击左下角的 Windows 图标，在搜索框中键入 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-130">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="59a12-131">在 Windows Server 版本中查找 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-131">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="59a12-132">从 Windows Server 2008 R2 开始，安装操作系统可不包含图形用户界面 (GUI)。</span><span class="sxs-lookup"><span data-stu-id="59a12-132">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="59a12-133">不含 GUI 的 Windows Server 版本名为“核心”版本，包含 GUI 的版本名为“桌面”版本。</span><span class="sxs-lookup"><span data-stu-id="59a12-133">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="59a12-134">Windows Server 核心版本</span><span class="sxs-lookup"><span data-stu-id="59a12-134">Windows Server Core editions</span></span>

<span data-ttu-id="59a12-135">在所有核心版本中，登录到服务器时会显示 Windows 命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="59a12-135">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="59a12-136">键入 `powershell` 并按“Enter”可在命令提示符会话内启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59a12-136">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span>
<span data-ttu-id="59a12-137">键入 `exit` 可终止 PowerShell 会话并返回命令提示符。</span><span class="sxs-lookup"><span data-stu-id="59a12-137">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="59a12-138">Windows Server 桌面版本</span><span class="sxs-lookup"><span data-stu-id="59a12-138">Windows Server Desktop editions</span></span>

<span data-ttu-id="59a12-139">在所有桌面版本中，单击左下角的 Windows 图标，键入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59a12-139">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="59a12-140">将显示控制台和 ISE 选项。</span><span class="sxs-lookup"><span data-stu-id="59a12-140">You get both console and ISE options.</span></span>

<span data-ttu-id="59a12-141">上述规则的唯一例外是 Windows Server 2008 R2 SP1 中的 ISE；这种情况下，请单击左下角的 Windows 图标，键入 PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="59a12-141">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="59a12-142">如何检查 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="59a12-142">How to check the version of PowerShell</span></span>

<span data-ttu-id="59a12-143">若要查看已安装的 PowerShell 版本，请启动 PowerShell 控制台（或 ISE），键入 `$PSVersionTable`，然后按“Enter”。</span><span class="sxs-lookup"><span data-stu-id="59a12-143">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span> <span data-ttu-id="59a12-144">查找 `PSVersion` 值。</span><span class="sxs-lookup"><span data-stu-id="59a12-144">Look for the `PSVersion` value.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="59a12-145">升级现有 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-145">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="59a12-146">PowerShell 安装包随附于 WMF 安装程序内。</span><span class="sxs-lookup"><span data-stu-id="59a12-146">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="59a12-147">WMF 安装程序版本与 PowerShell 版本一致；不提供 Windows PowerShell 独立安装程序。</span><span class="sxs-lookup"><span data-stu-id="59a12-147">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="59a12-148">如需在 Windows 中更新现有 PowerShell 版本，请使用下表找到要更新至的 PowerShell 版本的安装程序。</span><span class="sxs-lookup"><span data-stu-id="59a12-148">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="59a12-149">Windows</span><span class="sxs-lookup"><span data-stu-id="59a12-149">Windows</span></span> | <span data-ttu-id="59a12-150">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="59a12-150">PS 3.0</span></span> | <span data-ttu-id="59a12-151">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="59a12-151">PS 4.0</span></span> | <span data-ttu-id="59a12-152">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="59a12-152">PS 5.0</span></span> | <span data-ttu-id="59a12-153">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="59a12-153">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="59a12-154">Windows 10（参见说明 1）</span><span class="sxs-lookup"><span data-stu-id="59a12-154">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="59a12-155">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="59a12-155">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="59a12-156">已安装</span><span class="sxs-lookup"><span data-stu-id="59a12-156">installed</span></span>
<span data-ttu-id="59a12-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="59a12-157">Windows 8.1</span></span><br/><span data-ttu-id="59a12-158">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="59a12-158">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="59a12-159">已安装</span><span class="sxs-lookup"><span data-stu-id="59a12-159">installed</span></span> | [<span data-ttu-id="59a12-160">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="59a12-160">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="59a12-161">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="59a12-161">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="59a12-162">Windows 8</span><span class="sxs-lookup"><span data-stu-id="59a12-162">Windows 8</span></span><br/><span data-ttu-id="59a12-163">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="59a12-163">Windows Server 2012</span></span> | <span data-ttu-id="59a12-164">已安装</span><span class="sxs-lookup"><span data-stu-id="59a12-164">installed</span></span> | [<span data-ttu-id="59a12-165">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="59a12-165">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="59a12-166">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="59a12-166">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="59a12-167">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="59a12-167">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="59a12-168">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="59a12-168">Windows 7 SP1</span></span><br/><span data-ttu-id="59a12-169">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="59a12-169">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="59a12-170">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="59a12-170">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="59a12-171">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="59a12-171">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="59a12-172">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="59a12-172">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="59a12-173">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="59a12-173">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> <span data-ttu-id="59a12-174">Windows 10 初始版本中，由于已启用自动更新，因此 PowerShell 会从版本 5.0 更新至 5.1。</span><span class="sxs-lookup"><span data-stu-id="59a12-174">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
>
> <span data-ttu-id="59a12-175">如果 Windows 10 原始版本未通过 Windows 更新进行更新，则 PowerShell 版本为 5.0。</span><span class="sxs-lookup"><span data-stu-id="59a12-175">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="59a12-176">需要 Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-176">Need Azure PowerShell</span></span>

<span data-ttu-id="59a12-177">如需要 Azure PowerShell，请先参阅 [Azure PowerShell 概述](/powershell/azure/overview)。</span><span class="sxs-lookup"><span data-stu-id="59a12-177">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](/powershell/azure/overview).</span></span>

<span data-ttu-id="59a12-178">或者，可能需要参阅[安装和配置 Azure PowerShell](/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="59a12-178">Otherwise, what you might need is [Install and configure Azure PowerShell](/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="59a12-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59a12-179">See Also</span></span>

[<span data-ttu-id="59a12-180">Windows PowerShell 系统要求</span><span class="sxs-lookup"><span data-stu-id="59a12-180">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)

[<span data-ttu-id="59a12-181">启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a12-181">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
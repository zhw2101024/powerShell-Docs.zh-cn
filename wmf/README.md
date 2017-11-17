---
title: Windows Management Framework (WMF)
ms.date: 2017-02-14
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 749dd8b19592cb5f40a5aed32d28edeb5cb2dfc9
ms.sourcegitcommit: bb2c52577a519c0599a0b3c961f749fe0df70a45
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="windows-management-framework"></a><span data-ttu-id="c1a48-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="c1a48-103">Windows Management Framework</span></span>

<span data-ttu-id="c1a48-104">Windows Management Framework (WMF) 是跨各种风格的 Windows 和 Windows Server 提供一致的管理接口的传递机制。</span><span class="sxs-lookup"><span data-stu-id="c1a48-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="c1a48-105">使用 WMF 安装时，客户可无缝地在其环境中的各种操作系统之间进行交互操作。</span><span class="sxs-lookup"><span data-stu-id="c1a48-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="c1a48-106">WMF 在给定版本的 Windows 和 Windows Server 中对管理功能进行了更新，这些更新可以安装在较低版本（通常是 2 个较低版本）的 Windows 和 Windows Server 上。</span><span class="sxs-lookup"><span data-stu-id="c1a48-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="c1a48-107">WMF 安装添加和/或更新了以下功能：</span><span class="sxs-lookup"><span data-stu-id="c1a48-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="c1a48-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1a48-108">Windows PowerShell</span></span>
- <span data-ttu-id="c1a48-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="c1a48-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="c1a48-110">Windows PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="c1a48-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="c1a48-111">Windows 远程管理 (WinRM)</span><span class="sxs-lookup"><span data-stu-id="c1a48-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="c1a48-112">Windows 管理规范 (WMI)</span><span class="sxs-lookup"><span data-stu-id="c1a48-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="c1a48-113">Windows PowerShell Web 服务（Management OData IIS 扩展）</span><span class="sxs-lookup"><span data-stu-id="c1a48-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="c1a48-114">软件清单日志记录 (SIL)</span><span class="sxs-lookup"><span data-stu-id="c1a48-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="c1a48-115">服务器管理器 CIM 提供程序</span><span class="sxs-lookup"><span data-stu-id="c1a48-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="c1a48-116">WMF 发行说明</span><span class="sxs-lookup"><span data-stu-id="c1a48-116">WMF Release Notes</span></span>

<span data-ttu-id="c1a48-117">若要了解给定 WMF 的 PowerShell 和其他组件中的各种增强功能，请参阅以下链接以查看发行说明：</span><span class="sxs-lookup"><span data-stu-id="c1a48-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>

- [<span data-ttu-id="c1a48-118">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c1a48-118">WMF 5.1</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="c1a48-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="c1a48-119">WMF 5.0</span></span>](5.0/releasenotes.md)
- [<span data-ttu-id="c1a48-120">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="c1a48-120">WMF 4.0</span></span>](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [<span data-ttu-id="c1a48-121">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="c1a48-121">WMF 3.0</span></span>](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="c1a48-122">各个 Windows 操作系统间的 WMF 可用性</span><span class="sxs-lookup"><span data-stu-id="c1a48-122">WMF Availability Across Windows Operating Systems</span></span>

| <span data-ttu-id="c1a48-123">操作系统版本</span><span class="sxs-lookup"><span data-stu-id="c1a48-123">Operating System Version</span></span> | [<span data-ttu-id="c1a48-124">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c1a48-124">WMF 5.1</span></span>](https://aka.ms/wmf51download) | [<span data-ttu-id="c1a48-125">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="c1a48-125">WMF 5.0</span></span>](https://aka.ms/wmf5download) | [<span data-ttu-id="c1a48-126">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="c1a48-126">WMF 4.0</span></span>](https://aka.ms/wmf4download) |  [<span data-ttu-id="c1a48-127">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="c1a48-127">WMF 3.0</span></span>](https://aka.ms/wmf3download) | [<span data-ttu-id="c1a48-128">WMF 2.0</span><span class="sxs-lookup"><span data-stu-id="c1a48-128">WMF 2.0</span></span>](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="c1a48-129">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c1a48-129">Windows Server 2016</span></span> | <span data-ttu-id="c1a48-130">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-130">Ships in-box</span></span> |  |  |  |  |
| <span data-ttu-id="c1a48-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c1a48-131">Windows 10</span></span> | <span data-ttu-id="c1a48-132">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-132">Ships in-box</span></span> | <span data-ttu-id="c1a48-133">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-133">Ships in-box</span></span>  | | | |  
| <span data-ttu-id="c1a48-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c1a48-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="c1a48-135">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-135">Yes</span></span> | <span data-ttu-id="c1a48-136">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-136">Yes</span></span> | <span data-ttu-id="c1a48-137">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="c1a48-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c1a48-138">Windows 8.1</span></span> | <span data-ttu-id="c1a48-139">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-139">Yes</span></span> | <span data-ttu-id="c1a48-140">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-140">Yes</span></span> |  <span data-ttu-id="c1a48-141">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="c1a48-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c1a48-142">Windows Server 2012</span></span> | <span data-ttu-id="c1a48-143">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-143">Yes</span></span> | <span data-ttu-id="c1a48-144">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-144">Yes</span></span> | <span data-ttu-id="c1a48-145">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-145">Yes</span></span> |  <span data-ttu-id="c1a48-146">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-146">Ships in-box</span></span> | |
| <span data-ttu-id="c1a48-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="c1a48-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="c1a48-148">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-148">Ships in-box</span></span> | |
| <span data-ttu-id="c1a48-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="c1a48-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="c1a48-150">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-150">Yes</span></span> | <span data-ttu-id="c1a48-151">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-151">Yes</span></span> | <span data-ttu-id="c1a48-152">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-152">Yes</span></span> |  <span data-ttu-id="c1a48-153">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-153">Yes</span></span>| <span data-ttu-id="c1a48-154">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-154">Ships in-box</span></span> |
| <span data-ttu-id="c1a48-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="c1a48-155">Windows 7 SP1</span></span>  | <span data-ttu-id="c1a48-156">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-156">Yes</span></span> | <span data-ttu-id="c1a48-157">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-157">Yes</span></span> | <span data-ttu-id="c1a48-158">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-158">Yes</span></span> | <span data-ttu-id="c1a48-159">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-159">Yes</span></span> | <span data-ttu-id="c1a48-160">内置提供</span><span class="sxs-lookup"><span data-stu-id="c1a48-160">Ships in-box</span></span> |
| <span data-ttu-id="c1a48-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="c1a48-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="c1a48-162">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-162">Yes</span></span> | <span data-ttu-id="c1a48-163">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-163">Yes</span></span> |
| <span data-ttu-id="c1a48-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c1a48-164">Windows Vista</span></span> | | | | | <span data-ttu-id="c1a48-165">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-165">Yes</span></span> |
| <span data-ttu-id="c1a48-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="c1a48-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="c1a48-167">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-167">Yes</span></span> |
| <span data-ttu-id="c1a48-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="c1a48-168">Windows XP</span></span> | | | |  | <span data-ttu-id="c1a48-169">是</span><span class="sxs-lookup"><span data-stu-id="c1a48-169">Yes</span></span> |

<span data-ttu-id="c1a48-170">**内置提供**：`specified WMF` 的功能内置于所示的 Windows 和 Windows Server 版本中。</span><span class="sxs-lookup"><span data-stu-id="c1a48-170">**"Ships in-box"**: The features of the `specified WMF` were shipped in the indicated version of  Windows and Windows Server.</span></span>
<span data-ttu-id="c1a48-171">因此，无需在所示的操作系统版本上安装 `specified WMF`。</span><span class="sxs-lookup"><span data-stu-id="c1a48-171">Hence, the `specified WMF` doesn't need to be installed on the indicated operating system versions.</span></span>

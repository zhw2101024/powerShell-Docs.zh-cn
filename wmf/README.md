---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="windows-management-framework"></a><span data-ttu-id="728cb-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="728cb-103">Windows Management Framework</span></span>

<span data-ttu-id="728cb-104">Windows Management Framework (WMF) 是跨各种风格的 Windows 和 Windows Server 提供一致的管理接口的传递机制。</span><span class="sxs-lookup"><span data-stu-id="728cb-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="728cb-105">使用 WMF 安装时，客户可无缝地在其环境中的各种操作系统之间进行交互操作。</span><span class="sxs-lookup"><span data-stu-id="728cb-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="728cb-106">WMF 在给定版本的 Windows 和 Windows Server 中对管理功能进行了更新，这些更新可以安装在较低版本（通常是 2 个较低版本）的 Windows 和 Windows Server 上。</span><span class="sxs-lookup"><span data-stu-id="728cb-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="728cb-107">WMF 安装添加和/或更新了以下功能：</span><span class="sxs-lookup"><span data-stu-id="728cb-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="728cb-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="728cb-108">Windows PowerShell</span></span>
- <span data-ttu-id="728cb-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="728cb-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="728cb-110">Windows PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="728cb-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="728cb-111">Windows 远程管理 (WinRM)</span><span class="sxs-lookup"><span data-stu-id="728cb-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="728cb-112">Windows 管理规范 (WMI)</span><span class="sxs-lookup"><span data-stu-id="728cb-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="728cb-113">Windows PowerShell Web 服务（Management OData IIS 扩展）</span><span class="sxs-lookup"><span data-stu-id="728cb-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="728cb-114">软件清单日志记录 (SIL)</span><span class="sxs-lookup"><span data-stu-id="728cb-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="728cb-115">服务器管理器 CIM 提供程序</span><span class="sxs-lookup"><span data-stu-id="728cb-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="728cb-116">WMF 发行说明</span><span class="sxs-lookup"><span data-stu-id="728cb-116">WMF Release Notes</span></span>
<span data-ttu-id="728cb-117">若要了解给定 WMF 的 PowerShell 和其他组件中的各种增强功能，请参阅以下链接以查看发行说明：</span><span class="sxs-lookup"><span data-stu-id="728cb-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>


- [<span data-ttu-id="728cb-118">WMF 5.1（预览版）</span><span class="sxs-lookup"><span data-stu-id="728cb-118">WMF 5.1 (Preview)</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="728cb-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="728cb-119">WMF 5.0</span></span>](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="728cb-120">各个 Windows 操作系统间的 WMF 可用性</span><span class="sxs-lookup"><span data-stu-id="728cb-120">WMF Availability Across Windows Operating Systems</span></span>

><span data-ttu-id="728cb-121">TODO：在列标题上添加指向特定 WMF DLC 的链接</span><span class="sxs-lookup"><span data-stu-id="728cb-121">TODO: Add links to specific WMF DLC on the column header</span></span>

| <span data-ttu-id="728cb-122">操作系统版本</span><span class="sxs-lookup"><span data-stu-id="728cb-122">Operating System Version</span></span> | [<span data-ttu-id="728cb-123">WMF 5.1 预览版*</span><span class="sxs-lookup"><span data-stu-id="728cb-123">WMF 5.1 Preview*</span></span>]() | [<span data-ttu-id="728cb-124">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="728cb-124">WMF 5.0</span></span>]() | [<span data-ttu-id="728cb-125">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="728cb-125">WMF 4.0</span></span>]() |  [<span data-ttu-id="728cb-126">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="728cb-126">WMF 3.0</span></span>]() | [<span data-ttu-id="728cb-127">WMF (2.0)</span><span class="sxs-lookup"><span data-stu-id="728cb-127">WMF (2.0)</span></span>]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="728cb-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="728cb-128">Windows Server 2016</span></span> | <span data-ttu-id="728cb-129">内置提供*</span><span class="sxs-lookup"><span data-stu-id="728cb-129">Ships in-box*</span></span> | <span data-ttu-id="728cb-130">内置提供*</span><span class="sxs-lookup"><span data-stu-id="728cb-130">Ships in-box*</span></span> |  |  |  |
| <span data-ttu-id="728cb-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="728cb-131">Windows 10</span></span> | <span data-ttu-id="728cb-132">内置提供*</span><span class="sxs-lookup"><span data-stu-id="728cb-132">Ships in-box*</span></span> | <span data-ttu-id="728cb-133">内置提供*</span><span class="sxs-lookup"><span data-stu-id="728cb-133">Ships in-box*</span></span>  | | | |  
| <span data-ttu-id="728cb-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="728cb-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="728cb-135">??</span><span class="sxs-lookup"><span data-stu-id="728cb-135">??</span></span> | <span data-ttu-id="728cb-136">是</span><span class="sxs-lookup"><span data-stu-id="728cb-136">Yes</span></span> | <span data-ttu-id="728cb-137">内置提供</span><span class="sxs-lookup"><span data-stu-id="728cb-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="728cb-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="728cb-138">Windows 8.1</span></span> | <span data-ttu-id="728cb-139">??</span><span class="sxs-lookup"><span data-stu-id="728cb-139">??</span></span> | <span data-ttu-id="728cb-140">是</span><span class="sxs-lookup"><span data-stu-id="728cb-140">Yes</span></span> |  <span data-ttu-id="728cb-141">内置提供</span><span class="sxs-lookup"><span data-stu-id="728cb-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="728cb-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="728cb-142">Windows Server 2012</span></span> | <span data-ttu-id="728cb-143">??</span><span class="sxs-lookup"><span data-stu-id="728cb-143">??</span></span> | <span data-ttu-id="728cb-144">是</span><span class="sxs-lookup"><span data-stu-id="728cb-144">Yes</span></span> | <span data-ttu-id="728cb-145">是</span><span class="sxs-lookup"><span data-stu-id="728cb-145">Yes</span></span> |  <span data-ttu-id="728cb-146">内置提供</span><span class="sxs-lookup"><span data-stu-id="728cb-146">Ships in-box</span></span> | |
| <span data-ttu-id="728cb-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="728cb-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="728cb-148">内置提供</span><span class="sxs-lookup"><span data-stu-id="728cb-148">Ships in-box</span></span> | |
| <span data-ttu-id="728cb-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="728cb-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="728cb-150">??</span><span class="sxs-lookup"><span data-stu-id="728cb-150">??</span></span> | <span data-ttu-id="728cb-151">是</span><span class="sxs-lookup"><span data-stu-id="728cb-151">Yes</span></span> | <span data-ttu-id="728cb-152">是</span><span class="sxs-lookup"><span data-stu-id="728cb-152">Yes</span></span> |  <span data-ttu-id="728cb-153">是</span><span class="sxs-lookup"><span data-stu-id="728cb-153">Yes</span></span>| <span data-ttu-id="728cb-154">内置提供</span><span class="sxs-lookup"><span data-stu-id="728cb-154">Ships in-box</span></span> |
| <span data-ttu-id="728cb-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="728cb-155">Windows 7 SP1</span></span>  | <span data-ttu-id="728cb-156">??</span><span class="sxs-lookup"><span data-stu-id="728cb-156">??</span></span> | <span data-ttu-id="728cb-157">是</span><span class="sxs-lookup"><span data-stu-id="728cb-157">Yes</span></span> | <span data-ttu-id="728cb-158">是</span><span class="sxs-lookup"><span data-stu-id="728cb-158">Yes</span></span> | <span data-ttu-id="728cb-159">是</span><span class="sxs-lookup"><span data-stu-id="728cb-159">Yes</span></span> | <span data-ttu-id="728cb-160">内置提供</span><span class="sxs-lookup"><span data-stu-id="728cb-160">Ships in-box</span></span> |
| <span data-ttu-id="728cb-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="728cb-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="728cb-162">是</span><span class="sxs-lookup"><span data-stu-id="728cb-162">Yes</span></span> | <span data-ttu-id="728cb-163">是</span><span class="sxs-lookup"><span data-stu-id="728cb-163">Yes</span></span> |
| <span data-ttu-id="728cb-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="728cb-164">Windows Vista</span></span> | | | | | <span data-ttu-id="728cb-165">是</span><span class="sxs-lookup"><span data-stu-id="728cb-165">Yes</span></span> |
| <span data-ttu-id="728cb-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="728cb-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="728cb-167">是</span><span class="sxs-lookup"><span data-stu-id="728cb-167">Yes</span></span> |
| <span data-ttu-id="728cb-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="728cb-168">Windows XP</span></span> | | | |  | <span data-ttu-id="728cb-169">是</span><span class="sxs-lookup"><span data-stu-id="728cb-169">Yes</span></span> |

><span data-ttu-id="728cb-170">TODO：解释上表中的 *</span><span class="sxs-lookup"><span data-stu-id="728cb-170">TODO: Explain * in the above table</span></span>

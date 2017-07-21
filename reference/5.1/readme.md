---
ms.date: 2017-06-09
schema: 2.0.0
locale: en-us
keywords: powershell,cmdlet
title: "自述文件"
ms.openlocfilehash: e1abe921f50149f09b55e4aa259023ed7157780a
ms.sourcegitcommit: 9744f9b3c394d210f17ed5d5617d963a6572a540
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2017
---
# <a name="windows-powershell-51"></a><span data-ttu-id="8a68a-103">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8a68a-103">Windows PowerShell 5.1</span></span>

<span data-ttu-id="8a68a-104">更新时间：2016 年 10 月</span><span class="sxs-lookup"><span data-stu-id="8a68a-104">Updated: October, 2016</span></span>
- <span data-ttu-id="8a68a-105">适用于：Windows PowerShell 2.0、Windows PowerShell 3.0、Windows PowerShell 4.0、Windows PowerShell 5.0、Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8a68a-105">Applies To: Windows PowerShell 2.0 , Windows PowerShell 3.0 , Windows PowerShell 4.0 , Windows PowerShell 5.0 , Windows PowerShell 5.1</span></span>

<span data-ttu-id="8a68a-106">本节包含默认情况下随 Windows PowerShell 版本 5.1 一起安装的模块的 cmdlet 帮助、提供程序帮助和概念（“关于”）帮助主题。</span><span class="sxs-lookup"><span data-stu-id="8a68a-106">This section contains the cmdlet help, provider help, and conceptual ("About") help topics for the modules that are installed with Windows PowerShell version 5.1, by default.</span></span>

<span data-ttu-id="8a68a-107">下表显示了每个模块的最新发布版本号的帮助。</span><span class="sxs-lookup"><span data-stu-id="8a68a-107">The table below shows the latest published version number of the Help for each module.</span></span>
<span data-ttu-id="8a68a-108">通过下面的链接或可更新的帮助文件查看帮助。</span><span class="sxs-lookup"><span data-stu-id="8a68a-108">The Help is available through the links below, or as Updatable Help files.</span></span>
<span data-ttu-id="8a68a-109">Windows PowerShell 3.0 中引入了可更新的帮助，使你能够在你的计算机上本地使用最新的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="8a68a-109">Updatable Help was introduced with Windows PowerShell 3.0 and enables you to have the latest Help topics available locally on your computer.</span></span>
<span data-ttu-id="8a68a-110">有关详细信息，请参阅 about_Updatable_Help。</span><span class="sxs-lookup"><span data-stu-id="8a68a-110">See about_Updatable_Help for more information.</span></span>

<span data-ttu-id="8a68a-111">模块</span><span class="sxs-lookup"><span data-stu-id="8a68a-111">Module</span></span> | <span data-ttu-id="8a68a-112">最新版本</span><span class="sxs-lookup"><span data-stu-id="8a68a-112">Latest Version</span></span>
----------------------------- | --------------
[<span data-ttu-id="8a68a-113">ISE</span><span class="sxs-lookup"><span data-stu-id="8a68a-113">ISE</span></span>](ISE/ISE.md) |<span data-ttu-id="8a68a-114">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-114">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-115">Microsoft.PowerShell.Archive</span><span class="sxs-lookup"><span data-stu-id="8a68a-115">Microsoft.PowerShell.Archive</span></span>](Microsoft.PowerShell.Archive/Microsoft.PowerShell.Archive.md) |<span data-ttu-id="8a68a-116">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-116">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-117">Microsoft.PowerShell.Core</span><span class="sxs-lookup"><span data-stu-id="8a68a-117">Microsoft.PowerShell.Core</span></span>](Microsoft.PowerShell.Core/Microsoft.PowerShell.Core.md) |<span data-ttu-id="8a68a-118">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-118">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-119">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="8a68a-119">Microsoft.PowerShell.Diagnostics</span></span>](Microsoft.PowerShell.Diagnostics/Microsoft.PowerShell.Diagnostics.md) |<span data-ttu-id="8a68a-120">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-120">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-121">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="8a68a-121">Microsoft.PowerShell.Host</span></span>](Microsoft.PowerShell.Host/Microsoft.PowerShell.Host.md) |<span data-ttu-id="8a68a-122">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-122">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-123">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="8a68a-123">Microsoft.PowerShell.LocalAccounts</span></span>](Microsoft.PowerShell.LocalAccounts/Microsoft.PowerShell.LocalAccounts.md) |<span data-ttu-id="8a68a-124">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-124">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-125">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="8a68a-125">Microsoft.PowerShell.Management</span></span>](Microsoft.PowerShell.Management/Microsoft.PowerShell.Management.md) |<span data-ttu-id="8a68a-126">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-126">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-127">Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="8a68a-127">Microsoft.PowerShell.ODataUtils</span></span>](Microsoft.PowerShell.ODataUtils/Microsoft.PowerShell.ODataUtils.md) |<span data-ttu-id="8a68a-128">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-128">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-129">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="8a68a-129">Microsoft.PowerShell.Security</span></span>](Microsoft.PowerShell.Security/Microsoft.PowerShell.Security.md) |<span data-ttu-id="8a68a-130">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-130">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-131">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="8a68a-131">Microsoft.PowerShell.Utility</span></span>](Microsoft.PowerShell.Utility/Microsoft.PowerShell.Utility.md) |<span data-ttu-id="8a68a-132">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-132">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-133">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="8a68a-133">Microsoft.WSMan.Management</span></span>](Microsoft.WSMan.Management/Microsoft.WSMan.Management.md) |<span data-ttu-id="8a68a-134">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-134">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-135">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="8a68a-135">PackageManagement</span></span>](PackageManagement/PackageManagement.md) |<span data-ttu-id="8a68a-136">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-136">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-137">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8a68a-137">PowerShellGet</span></span>](PowerShellGet/PowerShellGet.md) |<span data-ttu-id="8a68a-138">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-138">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-139">PSReadline</span><span class="sxs-lookup"><span data-stu-id="8a68a-139">PSReadline</span></span>](PSReadline/PSReadline.md) |<span data-ttu-id="8a68a-140">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-140">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-141">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8a68a-141">PSScheduledJob</span></span>](PSScheduledJob/PSScheduledJob.md) |<span data-ttu-id="8a68a-142">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-142">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-143">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="8a68a-143">PSWorkflow</span></span>](PSWorkflow/PSWorkflow.md) |<span data-ttu-id="8a68a-144">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-144">5.1.0.0</span></span>
[<span data-ttu-id="8a68a-145">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="8a68a-145">PSWorkflowUtility</span></span>](PSWorkflowUtility/PSWorkflowUtility.md) |<span data-ttu-id="8a68a-146">5.1.0.0</span><span class="sxs-lookup"><span data-stu-id="8a68a-146">5.1.0.0</span></span>


##  <a name="see-also"></a><span data-ttu-id="8a68a-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a68a-147">See Also</span></span>
###  <a name="concepts"></a><span data-ttu-id="8a68a-148">概念</span><span class="sxs-lookup"><span data-stu-id="8a68a-148">Concepts</span></span>
<span data-ttu-id="8a68a-149">Windows PowerShell 核心“关于”主题</span><span class="sxs-lookup"><span data-stu-id="8a68a-149">Windows PowerShell Core About Topics</span></span>

###  <a name="other-resources"></a><span data-ttu-id="8a68a-150">其他资源</span><span class="sxs-lookup"><span data-stu-id="8a68a-150">Other Resources</span></span>
<span data-ttu-id="8a68a-151">Windows PowerShell, Windows PowerShell 核心, Windows PowerShell 核心 Cmdlet, 帮助主题, Windows PowerShell 核心“提供程序”帮助主题</span><span class="sxs-lookup"><span data-stu-id="8a68a-151">Windows PowerShell Windows PowerShell Core Windows PowerShell Core Cmdlet Help Topics Windows PowerShell Core Provider Help Topics</span></span>


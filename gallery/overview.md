---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery,psget
title: PowerShell 库
ms.openlocfilehash: cffb2f0182ffe9072f9fbbc7f4cdfcf28de276db
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="97764-103">PowerShell 库</span><span class="sxs-lookup"><span data-stu-id="97764-103">The PowerShell Gallery</span></span>

<span data-ttu-id="97764-104">PowerShell 库是 PowerShell 内容的中心存储库。</span><span class="sxs-lookup"><span data-stu-id="97764-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="97764-105">在 PowerShell 库中，可找到包含 PowerShell 命令和 Desired State Configuration (DSC) 资源的实用 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="97764-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="97764-106">还可找到 PowerShell 脚本，其中一些脚本可能包含 PowerShell 工作流、概述任务组和提供这些任务的序列。</span><span class="sxs-lookup"><span data-stu-id="97764-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="97764-107">某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="97764-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="97764-108">PowerShellGet 概述</span><span class="sxs-lookup"><span data-stu-id="97764-108">PowerShellGet Overview</span></span>

<span data-ttu-id="97764-109">PowerShellGet 模块包含用于发现、安装、更新和发布来自 [PowerShell 库](https://www.PowerShellGallery.com)和其他专用存储库的模块、DSC 资源、角色功能和脚本等 PowerShell 项目的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="97764-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="97764-110">库入门</span><span class="sxs-lookup"><span data-stu-id="97764-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="97764-111">从库安装项需要 PowerShellGet 模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="97764-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="97764-112">请参阅[安装 PowerShellGet](installing-psget.md)，获取完整说明。</span><span class="sxs-lookup"><span data-stu-id="97764-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="97764-113">有关如何在库中使用 PowerShellGet 命令的详细信息，请参阅[入门](getting-started.md)页面。</span><span class="sxs-lookup"><span data-stu-id="97764-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="97764-114">你也可运行 *Update-Help -Module PowerShellGet* 安装这些命令的本地帮助。</span><span class="sxs-lookup"><span data-stu-id="97764-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="97764-115">受支持的操作系统</span><span class="sxs-lookup"><span data-stu-id="97764-115">Supported Operating Systems</span></span>

<span data-ttu-id="97764-116">**PowerShellGet** 模块需要 **PowerShell 3.0 或更高版本**。</span><span class="sxs-lookup"><span data-stu-id="97764-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="97764-117">因此，**PowerShellGet** 需要以下操作系统之一：</span><span class="sxs-lookup"><span data-stu-id="97764-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="97764-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="97764-118">Windows 10</span></span>
- <span data-ttu-id="97764-119">Windows 8.1 专业版</span><span class="sxs-lookup"><span data-stu-id="97764-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="97764-120">Windows 8.1 企业版</span><span class="sxs-lookup"><span data-stu-id="97764-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="97764-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="97764-121">Windows 7 SP1</span></span>
- <span data-ttu-id="97764-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="97764-122">Windows Server 2016</span></span>
- <span data-ttu-id="97764-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="97764-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="97764-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="97764-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="97764-125">**PowerShellGet** 也需要 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="97764-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="97764-126">你可从[此处](https://msdn.microsoft.com/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="97764-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="97764-127">遇到问题？</span><span class="sxs-lookup"><span data-stu-id="97764-127">Got a question?</span></span> <span data-ttu-id="97764-128">有反馈？</span><span class="sxs-lookup"><span data-stu-id="97764-128">Have feedback?</span></span>

<span data-ttu-id="97764-129">可在[入门](getting-started.md)页面找到有关 PowerShell 库和 PowerShellGet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="97764-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="97764-130">请使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供反馈和报告问题。</span><span class="sxs-lookup"><span data-stu-id="97764-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
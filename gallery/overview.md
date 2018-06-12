---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery,psget
title: PowerShell 库
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482924"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="5f56f-103">PowerShell 库</span><span class="sxs-lookup"><span data-stu-id="5f56f-103">The PowerShell Gallery</span></span>

<span data-ttu-id="5f56f-104">PowerShell 库是 PowerShell 内容的中心存储库。</span><span class="sxs-lookup"><span data-stu-id="5f56f-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="5f56f-105">在 PowerShell 库中，可找到包含 PowerShell 命令和 Desired State Configuration (DSC) 资源的实用 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="5f56f-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="5f56f-106">还可找到 PowerShell 脚本，其中一些脚本可能包含 PowerShell 工作流、概述任务组和提供这些任务的序列。</span><span class="sxs-lookup"><span data-stu-id="5f56f-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="5f56f-107">某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="5f56f-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="5f56f-108">PowerShellGet 概述</span><span class="sxs-lookup"><span data-stu-id="5f56f-108">PowerShellGet Overview</span></span>

<span data-ttu-id="5f56f-109">PowerShellGet 模块包含用于发现、安装、更新和发布来自 [PowerShell 库](https://www.PowerShellGallery.com)和其他专用存储库的模块、DSC 资源、角色功能和脚本等 PowerShell 项目的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f56f-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="5f56f-110">库入门</span><span class="sxs-lookup"><span data-stu-id="5f56f-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="5f56f-111">从库安装项需要 PowerShellGet 模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="5f56f-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="5f56f-112">请参阅[安装 PowerShellGet](installing-psget.md)，获取完整说明。</span><span class="sxs-lookup"><span data-stu-id="5f56f-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="5f56f-113">有关如何在库中使用 PowerShellGet 命令的详细信息，请参阅[入门](getting-started.md)页面。</span><span class="sxs-lookup"><span data-stu-id="5f56f-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="5f56f-114">你也可运行 *Update-Help -Module PowerShellGet* 安装这些命令的本地帮助。</span><span class="sxs-lookup"><span data-stu-id="5f56f-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="5f56f-115">受支持的操作系统</span><span class="sxs-lookup"><span data-stu-id="5f56f-115">Supported Operating Systems</span></span>

<span data-ttu-id="5f56f-116">PowerShellGet 模块需要 Windows PowerShell 3.0 或更高版本或 PowerShell Core 6.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="5f56f-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="5f56f-117">针对以下操作系统提供对应的 Windows PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="5f56f-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="5f56f-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5f56f-118">Windows 10</span></span>
- <span data-ttu-id="5f56f-119">Windows 8.1 专业版</span><span class="sxs-lookup"><span data-stu-id="5f56f-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="5f56f-120">Windows 8.1 企业版</span><span class="sxs-lookup"><span data-stu-id="5f56f-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="5f56f-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5f56f-121">Windows 7 SP1</span></span>
- <span data-ttu-id="5f56f-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="5f56f-122">Windows Server 2016</span></span>
- <span data-ttu-id="5f56f-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5f56f-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="5f56f-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="5f56f-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="5f56f-125">**PowerShellGet** 也需要 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="5f56f-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="5f56f-126">你可从[此处](https://msdn.microsoft.com/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="5f56f-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="5f56f-127">PowerShell Core 支持多个操作系统。</span><span class="sxs-lookup"><span data-stu-id="5f56f-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="5f56f-128">请参阅[本文](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/)获取完整列表。</span><span class="sxs-lookup"><span data-stu-id="5f56f-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="5f56f-129">许多托管在库中的模块都支持不同的操作系统并具有附加要求。</span><span class="sxs-lookup"><span data-stu-id="5f56f-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="5f56f-130">有关详细信息，请参阅模块文档。</span><span class="sxs-lookup"><span data-stu-id="5f56f-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="5f56f-131">遇到问题？</span><span class="sxs-lookup"><span data-stu-id="5f56f-131">Got a question?</span></span> <span data-ttu-id="5f56f-132">有反馈？</span><span class="sxs-lookup"><span data-stu-id="5f56f-132">Have feedback?</span></span>

<span data-ttu-id="5f56f-133">可在[入门](getting-started.md)页面找到有关 PowerShell 库和 PowerShellGet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5f56f-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="5f56f-134">请使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供反馈和报告问题。</span><span class="sxs-lookup"><span data-stu-id="5f56f-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery,psget
title: PowerShell 库
ms.openlocfilehash: 9519b8bcca9f43419a33db380c3b852e9bb354ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="35fec-103">PowerShell 库</span><span class="sxs-lookup"><span data-stu-id="35fec-103">The PowerShell Gallery</span></span>

<span data-ttu-id="35fec-104">PowerShell 库是 PowerShell 内容的中心存储库。</span><span class="sxs-lookup"><span data-stu-id="35fec-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="35fec-105">你可以在库中找到新的 PowerShell 命令或 Desired State Configuration (DSC) 资源。</span><span class="sxs-lookup"><span data-stu-id="35fec-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="35fec-106">PowerShellGet 概述</span><span class="sxs-lookup"><span data-stu-id="35fec-106">PowerShellGet Overview</span></span>

<span data-ttu-id="35fec-107">PowerShellGet 模块包含用于发现、安装、更新和发布来自 [PowerShell 库](https://www.PowerShellGallery.com)和其他专用存储库的模块、DSC 资源、角色功能和脚本等 PowerShell 项目的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35fec-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="35fec-108">库入门</span><span class="sxs-lookup"><span data-stu-id="35fec-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="35fec-109">从库安装项需要最新版本的 PowerShellGet 模块，Windows 10、Windows Management Framework (WMF) 5.0 或基于 MSI 的安装程序（适用于 PowerShell 3 和 4）中提供此模块。</span><span class="sxs-lookup"><span data-stu-id="35fec-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="35fec-110">[**获取 Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)、</span><span class="sxs-lookup"><span data-stu-id="35fec-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="35fec-111">[**获取 WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175)，或</span><span class="sxs-lookup"><span data-stu-id="35fec-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="35fec-112">**获取 MSI 安装程序**</span><span class="sxs-lookup"><span data-stu-id="35fec-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="35fec-113">使用最新 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模块，你可以进行以下操作：</span><span class="sxs-lookup"><span data-stu-id="35fec-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="35fec-114">运行 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 和 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) 搜索库中的项</span><span class="sxs-lookup"><span data-stu-id="35fec-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="35fec-115">运行 [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 和 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) 将库中的项保存到系统</span><span class="sxs-lookup"><span data-stu-id="35fec-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="35fec-116">运行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 和 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 安装库中的项</span><span class="sxs-lookup"><span data-stu-id="35fec-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="35fec-117">运行 [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) 和 [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331) 将项上传到库</span><span class="sxs-lookup"><span data-stu-id="35fec-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="35fec-118">运行 [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668) 添加自己的自定义存储库</span><span class="sxs-lookup"><span data-stu-id="35fec-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="35fec-119">有关如何在库中使用 PowerShellGet 命令的详细信息，请参阅[入门](psgallery/psgallery_gettingstarted.md)页面。</span><span class="sxs-lookup"><span data-stu-id="35fec-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="35fec-120">你也可运行 *Update-Help -Module PowerShellGet* 安装这些命令的本地帮助。</span><span class="sxs-lookup"><span data-stu-id="35fec-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="35fec-121">受支持的操作系统</span><span class="sxs-lookup"><span data-stu-id="35fec-121">Supported Operating Systems</span></span>

<span data-ttu-id="35fec-122">**PowerShellGet** 模块需要 **PowerShell 3.0 或更高版本**。</span><span class="sxs-lookup"><span data-stu-id="35fec-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="35fec-123">因此，**PowerShellGet** 需要以下操作系统之一：</span><span class="sxs-lookup"><span data-stu-id="35fec-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="35fec-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="35fec-124">Windows 10</span></span>
- <span data-ttu-id="35fec-125">Windows 8.1 专业版</span><span class="sxs-lookup"><span data-stu-id="35fec-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="35fec-126">Windows 8.1 企业版</span><span class="sxs-lookup"><span data-stu-id="35fec-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="35fec-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="35fec-127">Windows 7 SP1</span></span>
- <span data-ttu-id="35fec-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="35fec-128">Windows Server 2016</span></span>
- <span data-ttu-id="35fec-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="35fec-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="35fec-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="35fec-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="35fec-131">**PowerShellGet** 也需要 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="35fec-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="35fec-132">你可从[此处](https://msdn.microsoft.com/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="35fec-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="35fec-133">遇到问题？</span><span class="sxs-lookup"><span data-stu-id="35fec-133">Got a question?</span></span> <span data-ttu-id="35fec-134">有反馈？</span><span class="sxs-lookup"><span data-stu-id="35fec-134">Have feedback?</span></span>

<span data-ttu-id="35fec-135">可在[入门](psgallery/psgallery_gettingstarted.md)页面找到有关 PowerShell 库和 PowerShellGet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="35fec-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="35fec-136">请使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供反馈和报告问题。</span><span class="sxs-lookup"><span data-stu-id="35fec-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
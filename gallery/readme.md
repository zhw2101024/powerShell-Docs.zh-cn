---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery,psget"
title: "PowerShell 库"
ms.openlocfilehash: 3e324f15b251822163c3ea9b6655767419a5ac4e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="8f4ec-103">PowerShell 库</span><span class="sxs-lookup"><span data-stu-id="8f4ec-103">The PowerShell Gallery</span></span>

<span data-ttu-id="8f4ec-104">PowerShell 库是 PowerShell 内容的中心存储库。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="8f4ec-105">你可以在库中找到新的 PowerShell 命令或 Desired State Configuration (DSC) 资源。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="8f4ec-106">PowerShellGet 概述</span><span class="sxs-lookup"><span data-stu-id="8f4ec-106">PowerShellGet Overview</span></span>

<span data-ttu-id="8f4ec-107">PowerShellGet 模块包含用于发现、安装、更新和发布来自 https://www.PowerShellGallery.com 和其他专用存储库的模块、DSC 资源、角色功能和脚本等 PowerShell 项目的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-107">PowerShellGet module contains cmdlets for discovering, installing, updating and publishing the PowerShell artifacts like Modules, DSC Resources, Role Capabilities and Scripts from the https://www.PowerShellGallery.com and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="8f4ec-108">库入门</span><span class="sxs-lookup"><span data-stu-id="8f4ec-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="8f4ec-109">从库安装项需要最新版本的 PowerShellGet 模块，Windows 10、Windows Management Framework (WMF) 5.0 或基于 MSI 的安装程序（适用于 PowerShell 3 和 4）中提供此模块。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="8f4ec-110">[**获取 Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)、</span><span class="sxs-lookup"><span data-stu-id="8f4ec-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="8f4ec-111">[**获取 WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175)，或</span><span class="sxs-lookup"><span data-stu-id="8f4ec-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="8f4ec-112">**获取 MSI 安装程序**</span><span class="sxs-lookup"><span data-stu-id="8f4ec-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="8f4ec-113">使用最新 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模块，你可以进行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8f4ec-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="8f4ec-114">使用 [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 搜索库中的项</span><span class="sxs-lookup"><span data-stu-id="8f4ec-114">Search through items in the Gallery with [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="8f4ec-115">使用 [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 将库中的项保存到系统</span><span class="sxs-lookup"><span data-stu-id="8f4ec-115">Save items to your system from the Gallery with [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="8f4ec-116">使用 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 安装库中的项</span><span class="sxs-lookup"><span data-stu-id="8f4ec-116">Install items from the Gallery with [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="8f4ec-117">使用 [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 将项上传到库</span><span class="sxs-lookup"><span data-stu-id="8f4ec-117">Upload items to the Gallery with [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="8f4ec-118">使用 [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 添加你自己的自定义存储库</span><span class="sxs-lookup"><span data-stu-id="8f4ec-118">Add your own custom repository with [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>

<span data-ttu-id="8f4ec-119">有关如何在库中使用 PowerShellGet 命令的详细信息，请参阅[入门](psgallery/psgallery_gettingstarted.md)页面。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="8f4ec-120">你也可运行 *Update-Help -Module PowerShellGet* 安装这些命令的本地帮助。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="8f4ec-121">受支持的操作系统</span><span class="sxs-lookup"><span data-stu-id="8f4ec-121">Supported Operating Systems</span></span>

<span data-ttu-id="8f4ec-122">**PowerShellGet** 模块需要 **PowerShell 3.0 或更高版本**。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="8f4ec-123">因此，**PowerShellGet** 需要以下操作系统之一：</span><span class="sxs-lookup"><span data-stu-id="8f4ec-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="8f4ec-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8f4ec-124">Windows 10</span></span>
- <span data-ttu-id="8f4ec-125">Windows 8.1 专业版</span><span class="sxs-lookup"><span data-stu-id="8f4ec-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="8f4ec-126">Windows 8.1 企业版</span><span class="sxs-lookup"><span data-stu-id="8f4ec-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="8f4ec-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8f4ec-127">Windows 7 SP1</span></span>
- <span data-ttu-id="8f4ec-128">Windows Server 2016 TP5</span><span class="sxs-lookup"><span data-stu-id="8f4ec-128">Windows Server 2016 TP5</span></span>
- <span data-ttu-id="8f4ec-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8f4ec-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="8f4ec-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8f4ec-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="8f4ec-131">**PowerShellGet** 也需要 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="8f4ec-132">你可从[此处](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="8f4ec-133">遇到问题？</span><span class="sxs-lookup"><span data-stu-id="8f4ec-133">Got a question?</span></span> <span data-ttu-id="8f4ec-134">有反馈？</span><span class="sxs-lookup"><span data-stu-id="8f4ec-134">Have feedback?</span></span>

<span data-ttu-id="8f4ec-135">可在[入门](psgallery/psgallery_gettingstarted.md)页面找到有关 PowerShell 库和 PowerShellGet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="8f4ec-136">请使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供反馈和报告问题。</span><span class="sxs-lookup"><span data-stu-id="8f4ec-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>


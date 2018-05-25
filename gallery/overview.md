 <span data-ttu-id="effa1-101">和 --- ms.date：2017 年 06 月 12 日 参与者：JKeithB 关键字：gallery，powershell，cmdlet，psgallery，psget 标题：PowerShell 库</span><span class="sxs-lookup"><span data-stu-id="effa1-101">and --- ms.date:  06/12/2017 contributor:  JKeithB keywords:  gallery,powershell,cmdlet,psgallery,psget title:  The PowerShell Gallery</span></span>
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="effa1-102">PowerShell 库</span><span class="sxs-lookup"><span data-stu-id="effa1-102">The PowerShell Gallery</span></span>

<span data-ttu-id="effa1-103">PowerShell 库是 PowerShell 内容的中心存储库。</span><span class="sxs-lookup"><span data-stu-id="effa1-103">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="effa1-104">在 PowerShell 库中，可找到包含 PowerShell 命令和 Desired State Configuration (DSC) 资源的实用 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="effa1-104">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="effa1-105">还可找到 PowerShell 脚本，其中一些脚本可能包含 PowerShell 工作流、概述任务组和提供这些任务的序列。</span><span class="sxs-lookup"><span data-stu-id="effa1-105">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="effa1-106">某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="effa1-106">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="effa1-107">PowerShellGet 概述</span><span class="sxs-lookup"><span data-stu-id="effa1-107">PowerShellGet Overview</span></span>

<span data-ttu-id="effa1-108">PowerShellGet 模块包含用于发现、安装、更新和发布来自 [PowerShell 库](https://www.PowerShellGallery.com)和其他专用存储库的模块、DSC 资源、角色功能和脚本等 PowerShell 项目的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="effa1-108">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="effa1-109">库入门</span><span class="sxs-lookup"><span data-stu-id="effa1-109">Getting Started with the Gallery</span></span>

<span data-ttu-id="effa1-110">从库安装项需要 PowerShellGet 模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="effa1-110">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="effa1-111">请参阅[安装 PowerShellGet](installing-psget.md)，获取完整说明。</span><span class="sxs-lookup"><span data-stu-id="effa1-111">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="effa1-112">有关如何在库中使用 PowerShellGet 命令的详细信息，请参阅[入门](getting-started.md)页面。</span><span class="sxs-lookup"><span data-stu-id="effa1-112">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="effa1-113">你也可运行 *Update-Help -Module PowerShellGet* 安装这些命令的本地帮助。</span><span class="sxs-lookup"><span data-stu-id="effa1-113">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="effa1-114">受支持的操作系统</span><span class="sxs-lookup"><span data-stu-id="effa1-114">Supported Operating Systems</span></span>

<span data-ttu-id="effa1-115">PowerShellGet 模块需要 Windows PowerShell 3.0 或更高版本或 PowerShell Core 6.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="effa1-115">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="effa1-116">针对以下操作系统提供对应的 Windows PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="effa1-116">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="effa1-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="effa1-117">Windows 10</span></span>
- <span data-ttu-id="effa1-118">Windows 8.1 专业版</span><span class="sxs-lookup"><span data-stu-id="effa1-118">Windows 8.1 Pro</span></span>
- <span data-ttu-id="effa1-119">Windows 8.1 企业版</span><span class="sxs-lookup"><span data-stu-id="effa1-119">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="effa1-120">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="effa1-120">Windows 7 SP1</span></span>
- <span data-ttu-id="effa1-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="effa1-121">Windows Server 2016</span></span>
- <span data-ttu-id="effa1-122">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="effa1-122">Windows Server 2012 R2</span></span>
- <span data-ttu-id="effa1-123">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="effa1-123">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="effa1-124">**PowerShellGet** 也需要 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="effa1-124">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="effa1-125">你可从[此处](https://msdn.microsoft.com/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="effa1-125">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="effa1-126">PowerShell Core 支持多个操作系统。</span><span class="sxs-lookup"><span data-stu-id="effa1-126">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="effa1-127">请参阅[本文](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/)获取完整列表。</span><span class="sxs-lookup"><span data-stu-id="effa1-127">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="effa1-128">许多托管在库中的模块都支持不同的操作系统并具有附加要求。</span><span class="sxs-lookup"><span data-stu-id="effa1-128">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="effa1-129">有关详细信息，请参阅模块文档。</span><span class="sxs-lookup"><span data-stu-id="effa1-129">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="effa1-130">遇到问题？</span><span class="sxs-lookup"><span data-stu-id="effa1-130">Got a question?</span></span> <span data-ttu-id="effa1-131">有反馈？</span><span class="sxs-lookup"><span data-stu-id="effa1-131">Have feedback?</span></span>

<span data-ttu-id="effa1-132">可在[入门](getting-started.md)页面找到有关 PowerShell 库和 PowerShellGet 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="effa1-132">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="effa1-133">请使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供反馈和报告问题。</span><span class="sxs-lookup"><span data-stu-id="effa1-133">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

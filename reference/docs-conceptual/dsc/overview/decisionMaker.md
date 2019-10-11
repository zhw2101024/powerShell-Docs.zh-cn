---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于决策者的 Desired State Configuration 概述
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953684"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="f0bd8-103">适用于决策者的 Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="f0bd8-103">Desired State Configuration Overview for Decision Makers</span></span>

<span data-ttu-id="f0bd8-104">本文介绍使用 Windows PowerShell Desired State Configuration (DSC) 给业务带来的好处。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-104">This document describes the business benefits of using Windows PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="f0bd8-105">它不是技术指南。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-105">It is not a technical guide.</span></span>

## <a name="what-is-desired-state-configuration"></a><span data-ttu-id="f0bd8-106">什么是 Desired State Configuration？</span><span class="sxs-lookup"><span data-stu-id="f0bd8-106">What Is Desired State Configuration?</span></span>

<span data-ttu-id="f0bd8-107">PowerShell Desired State Configuration 是基于开放标准的内置于 Windows 中的配置管理平台。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-107">PowerShell Desired State Configuration is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="f0bd8-108">DSC 足够灵活以在部署生命周期的各个阶段（开发、测试、预生产、生产）及扩展期间可靠而一致地运转。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), as well as during scale-out.</span></span>

<span data-ttu-id="f0bd8-109">DSC 以[配置](../configurations/configurations.md)为中心。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-109">DSC centers around [configurations](../configurations/configurations.md).</span></span>
<span data-ttu-id="f0bd8-110">配置是易读的文档，描述了由具有特定特征的计算机（“节点”）组成的环境。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-110">A configuration is an easy-to-read document that describes an environment made up of computers ("nodes") with specific characteristics.</span></span>
<span data-ttu-id="f0bd8-111">这些特性可简单可复杂，或如确保特定 Windows 功能已启用般简单，或如部署 SharePoint 般复杂。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="f0bd8-112">DSC 也内置了监视和报告。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-112">DSC also has monitoring and reporting built in.</span></span>
<span data-ttu-id="f0bd8-113">如果系统不再相容，DSC 会引发警报，并采取措施更正系统。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-desired-state-configuration"></a><span data-ttu-id="f0bd8-114">使用 Desired State Configuration 的优点</span><span class="sxs-lookup"><span data-stu-id="f0bd8-114">Benefits of Using Desired State Configuration</span></span>

<span data-ttu-id="f0bd8-115">配置的设计实现了轻松读取、存储并更新。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-115">Configurations are designed to be easily read, stored, and updated.</span></span>
<span data-ttu-id="f0bd8-116">配置声明目标设备应处于的状态，无需编写如何将其置于该状态的说明。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-116">Configurations declare the state target devices should be in, instead of writing instructions for how to put them in that state.</span></span>
<span data-ttu-id="f0bd8-117">这样用于 DSC 的学习、使用、实现和配置维护的成本都大大降低。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-117">This makes it much less costly to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="f0bd8-118">创建配置意味着，单个位置中的复杂部署步骤将捕获为“单一资料来源”。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-118">Creating configurations means that complex deployment steps are captured as a "single source of truth" in a single location.</span></span>
<span data-ttu-id="f0bd8-119">这使得重复部署一组特定的计算机不易出错。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-119">This makes repeated deployments of a specific set of machines much less error-prone.</span></span>
<span data-ttu-id="f0bd8-120">反之，使部署更快和更可靠会启用复杂部署上的快速周转。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-120">In turn, making deployments faster and more reliable which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="f0bd8-121">配置还可通过 [PowerShell 库](https://powershellgallery.com)共享，这意味着需要完成的工作可能已经存在常见方案和最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-121">Configurations are also shareable via the [PowerShell Gallery](https://powershellgallery.com) meaning common scenarios and best practices might already exist for the work that needs to be done.</span></span>


## <a name="desired-state-configuration-and-devops"></a><span data-ttu-id="f0bd8-122">Desired State Configuration 和 DevOps</span><span class="sxs-lookup"><span data-stu-id="f0bd8-122">Desired State Configuration and DevOps</span></span>

<span data-ttu-id="f0bd8-123">DSC 设计时考虑到 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)后者结合了人员、流程和工具，方便实现快速部署和迭代，旨在向内外部最终用户传递价值。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-123">DSC was designed with [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) in mind, a combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span>
<span data-ttu-id="f0bd8-124">使单个配置定义环境意味着，开发人员可将其要求编码到配置中，并将该配置签入源控件，而操作小组可轻松部署代码，无需经历易出错的手动流程。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-124">Having a single configuration define an environment means that developers can encode their requirements into a configuration, check that configuration into source control, and operation teams can easily deploy code without having to go through error-prone manual processes.</span></span>

<span data-ttu-id="f0bd8-125">配置也是[数据驱动](../configurations/configData.md)的，便于操作人员识别和更改环境，无需开发人员介入。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-125">Configurations are also [data-driven](../configurations/configData.md), which makes it easier for ops to identify and change environments without developer intervention.</span></span>

## <a name="desired-state-configuration-on-premises-and-off-premises"></a><span data-ttu-id="f0bd8-126">本地和非本地 Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="f0bd8-126">Desired State Configuration On-Premises and Off-Premises</span></span>
<span data-ttu-id="f0bd8-127">DSC 可用于管理本地和非本地部署。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-127">DSC can be used to manage both on-premise and off-premise deployments.</span></span>
<span data-ttu-id="f0bd8-128">针对本地解决方案，DSC 拥有[请求服务器](../pull-server/pullServer.md)，可用于集中式管理计算机并报告其状态。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-128">For on-premise solutions, DSC has a [pull server](../pull-server/pullServer.md) that can be used to centralize management of machines and report on their status.</span></span>
<span data-ttu-id="f0bd8-129">针对云解决方案，只要 Windows 可用 DSC 就可用。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-129">For cloud solutions, DSC is usable wherever Windows is usable.</span></span>
<span data-ttu-id="f0bd8-130">Desired State Configuration 还内置有来自 Azure 的特定产品/服务，例如 [Azure 自动化](https://azure.microsoft.com/en-us/documentation/services/automation/)，它可实现 DSC 报告的集中化。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-130">There are also specific offerings from Azure built on Desired State Configuration, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), which centralizes reporting of DSC.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="f0bd8-131">DSC 和兼容性</span><span class="sxs-lookup"><span data-stu-id="f0bd8-131">DSC and Compatibility</span></span>

<span data-ttu-id="f0bd8-132">尽管 DSC 在 Windows Server 2012 R2 中引入，但下层操作系统可通过 Windows Management Framework (WMF) 程序包使用它。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-132">Although DSC was introduced in Windows Server 2012 R2, it is available for down-level operating systems via the Windows Management Framework (WMF) package.</span></span>
<span data-ttu-id="f0bd8-133">有关 WMF 的详细信息，可查看 [PowerShell 主页](/powershell/)。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-133">More information about the WMF can be found on the [PowerShell homepage](/powershell/).</span></span>

<span data-ttu-id="f0bd8-134">DSC 还可以用于管理 Linux。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-134">DSC can also be used to manage Linux.</span></span> <span data-ttu-id="f0bd8-135">有关详细信息，请参阅[适用于 Linux 的 DSC 入门](../getting-started/lnxGettingStarted.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bd8-135">For more information, see [Getting Started with DSC for Linux](../getting-started/lnxGettingStarted.md).</span></span>

---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: Windows PowerShell Desired State Configuration 概述
ms.openlocfilehash: 5c4853cb059ca0cf063a9450f97230732bc56b10
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953634"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="b129e-103">Windows PowerShell Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="b129e-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="b129e-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b129e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b129e-105">DSC 是 PowerShell 中的一个管理平台，可允许通过配置为代码来管理 IT 和开发基础结构。</span><span class="sxs-lookup"><span data-stu-id="b129e-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="b129e-106">有关使用 DSC 的业务优势的概述，请参阅[适用于决策者的 Desired State Configuration 概述](decisionMaker.md)。</span><span class="sxs-lookup"><span data-stu-id="b129e-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="b129e-107">有关使用 DSC 的工程优势的概述，请参阅[适用于工程师的 Desired State Configuration 概述](DscForEngineers.md)。</span><span class="sxs-lookup"><span data-stu-id="b129e-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="b129e-108">要快速使用 DSC，请参阅 [DSC 快速入门](../quickstarts/website-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="b129e-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="b129e-109">关键概念</span><span class="sxs-lookup"><span data-stu-id="b129e-109">Key Concepts</span></span>

<span data-ttu-id="b129e-110">DSC 是一个声明性平台，用于配置、部署和管理系统。</span><span class="sxs-lookup"><span data-stu-id="b129e-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="b129e-111">它包括三个主要组件：</span><span class="sxs-lookup"><span data-stu-id="b129e-111">It consists of three primary components:</span></span>

- <span data-ttu-id="b129e-112">[配置](../configurations/configurations.md)是声明性的 PowerShell 脚本，用于定义和配置资源实例。</span><span class="sxs-lookup"><span data-stu-id="b129e-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="b129e-113">运行配置时，DSC（和配置调用的资源）将“使其如此”，从而确保系统处于配置所规定的状态。</span><span class="sxs-lookup"><span data-stu-id="b129e-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply "make it so", ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="b129e-114">DSC 配置也是幂等的：无论配置声明什么状态，本地配置管理器 (LCM) 都将继续确保计算机已配置为该状态。</span><span class="sxs-lookup"><span data-stu-id="b129e-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="b129e-115">[资源](../resources/resources.md)是 DSC 的“实现器”部分。</span><span class="sxs-lookup"><span data-stu-id="b129e-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="b129e-116">它们包含将配置的目标置于并保持在指定状态的代码。</span><span class="sxs-lookup"><span data-stu-id="b129e-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="b129e-117">资源驻留在 PowerShell 模块内，可编写以便对某项内容进行建模，建模对象可以是一般的文件或 Windows 进程，也可以是在 Azure 中运行的具体 IIS 服务器或 VM。</span><span class="sxs-lookup"><span data-stu-id="b129e-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="b129e-118">[本地配置管理器 (LCM)](../managing-nodes/metaConfig.md) 是 DSC 用来推动资源和配置之间交互的引擎。</span><span class="sxs-lookup"><span data-stu-id="b129e-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="b129e-119">LCM 使用由资源实现的控制流定期轮询系统，以确保配置所定义的状态得以保持。</span><span class="sxs-lookup"><span data-stu-id="b129e-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="b129e-120">如果系统不处于相应状态，LCM 将根据配置调用资源内的代码“使其如此”。</span><span class="sxs-lookup"><span data-stu-id="b129e-120">If the system is out of state, the LCM makes calls to the code in resources to "make it so" according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="b129e-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b129e-121">See Also</span></span>

- [<span data-ttu-id="b129e-122">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="b129e-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="b129e-123">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="b129e-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="b129e-124">配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="b129e-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

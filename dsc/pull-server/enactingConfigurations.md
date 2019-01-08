---
ms.date: 10/16/2017
keywords: dsc,powershell,配置,安装程序
title: 执行配置
ms.openlocfilehash: 4a6e7e511446ab27307683ad3d5676391e7c791c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400974"
---
# <a name="enacting-configurations"></a><span data-ttu-id="1e780-103">执行配置</span><span class="sxs-lookup"><span data-stu-id="1e780-103">Enacting configurations</span></span>

><span data-ttu-id="1e780-104">适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1e780-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1e780-105">有两种执行 PowerShell Desired State Configuration (DSC) 配置的方法：推送模式和请求模式。</span><span class="sxs-lookup"><span data-stu-id="1e780-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="1e780-106">推送模式</span><span class="sxs-lookup"><span data-stu-id="1e780-106">Push mode</span></span>

<span data-ttu-id="1e780-107">![推送模式](../images/pushModel.png "推送模式的工作原理")</span><span class="sxs-lookup"><span data-stu-id="1e780-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="1e780-108">推送模式指的是用户通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 主动将配置应用到目标节点。</span><span class="sxs-lookup"><span data-stu-id="1e780-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="1e780-109">创建并编译配置后，可通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet，并将 cmdlet 的 -Path 参数设置为配置 MOF 所在的路径，从而在推送模式下执行该配置。</span><span class="sxs-lookup"><span data-stu-id="1e780-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="1e780-110">例如，如果配置 MOF 位于 `C:\DSC\Configurations\localhost.mof` 中，则使用以下命令将其应用于本地计算机：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="1e780-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="1e780-111">__注意__：默认情况下，DSC 运行配置作为后台作业。</span><span class="sxs-lookup"><span data-stu-id="1e780-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="1e780-112">若要以交互方式运行此配置，请使用 __-Wait__ 参数调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)。</span><span class="sxs-lookup"><span data-stu-id="1e780-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="1e780-113">请求模式</span><span class="sxs-lookup"><span data-stu-id="1e780-113">Pull mode</span></span>

<span data-ttu-id="1e780-114">![拉取模式](../images/pullModel.png "拉取模式的工作原理")</span><span class="sxs-lookup"><span data-stu-id="1e780-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="1e780-115">在请求模式下，配置请求客户端以从远程请求服务中获取所需的状态配置。</span><span class="sxs-lookup"><span data-stu-id="1e780-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="1e780-116">同样，已将请求服务设置为托管 DSC 服务，并预配了请求服务器所需的配置和资源。</span><span class="sxs-lookup"><span data-stu-id="1e780-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="1e780-117">每个请求客户端都有计划的事件，在节点的配置上定期执行符合性检查。</span><span class="sxs-lookup"><span data-stu-id="1e780-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="1e780-118">首次触发事件时，请求客户端上的本地配置管理器 (LCM) 对请求服务发出请求，获取 LCM 中指定的配置。</span><span class="sxs-lookup"><span data-stu-id="1e780-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="1e780-119">如果请求服务上存在该配置，并通过了初始验证检查，则配置将下载到请求客户端，然后在其上由 LCM 进行执行。</span><span class="sxs-lookup"><span data-stu-id="1e780-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="1e780-120">LCM 会按其 **ConfigurationModeFrequencyMins** 属性指定的时间间隔来定期检查客户端是否符合配置要求。</span><span class="sxs-lookup"><span data-stu-id="1e780-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="1e780-121">LCM 会按其 RefreshModeFrequency 属性指定的时间间隔来定期检查请求服务上的更新配置。</span><span class="sxs-lookup"><span data-stu-id="1e780-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="1e780-122">若要了解如何配置 LCM，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="1e780-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="1e780-123">用于托管请求服务的推荐解决方案是 DSC 云服务，[Azure 自动化](https://azure.microsoft.com/services/automation/)。</span><span class="sxs-lookup"><span data-stu-id="1e780-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="1e780-124">此托管解决方案提供图形管理、报告和集中式管理。</span><span class="sxs-lookup"><span data-stu-id="1e780-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="1e780-125">有关在 Windows Server 上设置请求服务的详细信息，请参阅[设置 DSC Web 请求服务器](pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="1e780-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="1e780-126">但是，请了解，此实现的功能有限，并且需要一些“自助式”集成。</span><span class="sxs-lookup"><span data-stu-id="1e780-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="1e780-127">以下主题说明了请求服务和客户端：</span><span class="sxs-lookup"><span data-stu-id="1e780-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="1e780-128">Azure Automation DSC 概述</span><span class="sxs-lookup"><span data-stu-id="1e780-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="1e780-129">设置 SMB 请求服务器</span><span class="sxs-lookup"><span data-stu-id="1e780-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="1e780-130">配置请求客户端</span><span class="sxs-lookup"><span data-stu-id="1e780-130">Configuring a pull client</span></span>](pullClientConfigID.md)

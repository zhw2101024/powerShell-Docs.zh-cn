---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "执行配置"
ms.openlocfilehash: db82788650186eb82f67b30b24cd45b719bbe314
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="enacting-configurations"></a><span data-ttu-id="5a14a-103">执行配置</span><span class="sxs-lookup"><span data-stu-id="5a14a-103">Enacting configurations</span></span>

><span data-ttu-id="5a14a-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5a14a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5a14a-105">有两种执行 PowerShell Desired State Configuration (DSC) 配置的方法：推送模式和请求模式。</span><span class="sxs-lookup"><span data-stu-id="5a14a-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="5a14a-106">推送模式</span><span class="sxs-lookup"><span data-stu-id="5a14a-106">Push mode</span></span>

<span data-ttu-id="5a14a-107">![推送模式](images/Push.png "推送模式的工作原理")</span><span class="sxs-lookup"><span data-stu-id="5a14a-107">![Push mode](images/Push.png "How push mode works")</span></span>

<span data-ttu-id="5a14a-108">推送模式指的是用户通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 主动将配置应用到目标节点。</span><span class="sxs-lookup"><span data-stu-id="5a14a-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="5a14a-109">创建并编译配置后，可通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet，并将 cmdlet 的 -Path 参数设置为配置 MOF 所在的路径，从而在推送模式下执行该配置。</span><span class="sxs-lookup"><span data-stu-id="5a14a-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span> <span data-ttu-id="5a14a-110">例如，如果配置 MOF 位于 `C:\DSC\Configurations\localhost.mof` 中，则使用以下命令将其应用于本地计算机：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="5a14a-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="5a14a-111">__注意__：默认情况下，DSC 运行配置作为后台作业。</span><span class="sxs-lookup"><span data-stu-id="5a14a-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="5a14a-112">若要以交互方式运行此配置，请使用 __-Wait__ 参数调用 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5a14a-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>


## <a name="pull-mode"></a><span data-ttu-id="5a14a-113">请求模式</span><span class="sxs-lookup"><span data-stu-id="5a14a-113">Pull mode</span></span>

<span data-ttu-id="5a14a-114">![拉取模式](images/Pull.png "拉取模式的工作原理")</span><span class="sxs-lookup"><span data-stu-id="5a14a-114">![Pull Mode](images/Pull.png "How pull mode works")</span></span>

<span data-ttu-id="5a14a-115">在请求模式下，配置请求客户端以从远程请求服务器中获取所需的状态配置。</span><span class="sxs-lookup"><span data-stu-id="5a14a-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull server.</span></span> <span data-ttu-id="5a14a-116">同样，已将请求服务器设置为托管 DSC 服务，并提供了请求服务器所需的配置和资源。</span><span class="sxs-lookup"><span data-stu-id="5a14a-116">Likewise, the pull server has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span> <span data-ttu-id="5a14a-117">每个请求客户端都有计划的任务，在节点的配置上定期执行相容性检查。</span><span class="sxs-lookup"><span data-stu-id="5a14a-117">Each one of the pull clients has a scheduled task that performs a periodic compliance check on the configuration of the node.</span></span> <span data-ttu-id="5a14a-118">首次触发事件时，拉取客户端上的本地配置管理器 (LCM) 对拉取服务器发出请求，以获取 LCM 中指定的配置。</span><span class="sxs-lookup"><span data-stu-id="5a14a-118">When the event is triggered the first time, it the Local Configuration Manager (LCM) on the pull client makes a request to the pull server to get the configuration specified in the LCM.</span></span> <span data-ttu-id="5a14a-119">如果请求服务器上存在该配置，并通过了初始验证检查，则配置将传送到请求客户端，然后在其上由 LCM 进行执行。</span><span class="sxs-lookup"><span data-stu-id="5a14a-119">If that configuration exists on the pull server, and it passes initial validation checks, the configuration is transmitted to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="5a14a-120">LCM 会按其 **ConfigurationModeFrequencyMins** 属性指定的时间间隔来定期检查客户端是否符合配置要求。</span><span class="sxs-lookup"><span data-stu-id="5a14a-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="5a14a-121">LCM 会按其 **RefreshModeFrequency** 属性指定的时间间隔来定期检查拉取服务器上的更新配置。</span><span class="sxs-lookup"><span data-stu-id="5a14a-121">The LCM checks for updated configurations on the pull server at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span> <span data-ttu-id="5a14a-122">若要了解如何配置 LCM，请参阅[配置本地配置管理器](metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="5a14a-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="5a14a-123">若要详细了解如何设置 DSC 拉取服务器，请参阅[设置 DSC Web 拉取服务器](pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="5a14a-123">For more information on setting up a DSC Pull Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="5a14a-124">如果想利用联机服务承载请求服务器功能，请参阅 [Azure 自动化 DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) 服务。</span><span class="sxs-lookup"><span data-stu-id="5a14a-124">If you would prefer to take advantage of an online service to host Pull Server functionality, see the [Azure Automation DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) service.</span></span>

<span data-ttu-id="5a14a-125">以下主题说明了如何设置请求服务器和客户端：</span><span class="sxs-lookup"><span data-stu-id="5a14a-125">The following topics explain how to set up pull servers and clients:</span></span>

- [<span data-ttu-id="5a14a-126">设置 Web 请求服务器</span><span class="sxs-lookup"><span data-stu-id="5a14a-126">Setting up a web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="5a14a-127">设置 SMB 请求服务器</span><span class="sxs-lookup"><span data-stu-id="5a14a-127">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="5a14a-128">配置请求客户端</span><span class="sxs-lookup"><span data-stu-id="5a14a-128">Configuring a pull client</span></span>](pullClientConfigID.md)


---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 在 PowerShell 5.0 及更高版本中使用配置 ID 设置请求客户端
ms.openlocfilehash: bd173a1079b916c450a0292dca7a595a9bcff985
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417235"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="ea6a2-103">在 PowerShell 5.0 及更高版本中使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="ea6a2-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="ea6a2-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ea6a2-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea6a2-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划  。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="ea6a2-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="ea6a2-107">设置请求客户端之前，应设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="ea6a2-108">虽然此顺序不是必需的，不过它帮助进行故障排除，并帮助确保注册成功。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="ea6a2-109">若要设置请求服务器，可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="ea6a2-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="ea6a2-110">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="ea6a2-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="ea6a2-111">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="ea6a2-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="ea6a2-112">每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="ea6a2-113">以下各部分演示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="ea6a2-114">节点的 LCM 刷新时，它会访问配置的位置以下载任何已分配的配置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="ea6a2-115">如果有任何所需资源在节点上不存在，则它会自动从配置的位置下载它们。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="ea6a2-116">如果使用[报表服务器](reportServer.md)配置节点，则它随后会报告操作的状态。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="ea6a2-117">本主题适用于 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="ea6a2-118">有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="ea6a2-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="ea6a2-119">配置请求客户端 LCM</span><span class="sxs-lookup"><span data-stu-id="ea6a2-119">Configure the pull client LCM</span></span>

<span data-ttu-id="ea6a2-120">执行以下任何示例会创建名为 PullClientConfigID  的新输出文件夹，并在其中放入元配置 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="ea6a2-121">在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="ea6a2-122">若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="ea6a2-123">例如：</span><span class="sxs-lookup"><span data-stu-id="ea6a2-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="ea6a2-124">配置 ID</span><span class="sxs-lookup"><span data-stu-id="ea6a2-124">Configuration ID</span></span>

<span data-ttu-id="ea6a2-125">以下示例将 LCM 的 ConfigurationID  属性设置为之前为此目的创建的 Guid  。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="ea6a2-126">LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="ea6a2-127">请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="ea6a2-128">有关详细信息，请参阅[将配置发布到请求服务器 (v4/v5)](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="ea6a2-129">可以使用以下示例，或使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet 创建随机 Guid  。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="ea6a2-130">有关在环境中使用 Guid  的详细信息，请参阅[规划 Guid](/powershell/scripting/dsc/secureserver#guids)。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="ea6a2-131">设置请求客户端以下载配置</span><span class="sxs-lookup"><span data-stu-id="ea6a2-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="ea6a2-132">必须在“请求”  模式下配置每个客户端，并向其提供存储其配置的请求服务器 url。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="ea6a2-133">若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="ea6a2-134">若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="ea6a2-135">有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="ea6a2-136">HTTP DSC 请求服务器</span><span class="sxs-lookup"><span data-stu-id="ea6a2-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="ea6a2-137">下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="ea6a2-138">在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="ea6a2-139">ServerUrl  指定 DSC 请求的 url</span><span class="sxs-lookup"><span data-stu-id="ea6a2-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="ea6a2-140">SMB 共享</span><span class="sxs-lookup"><span data-stu-id="ea6a2-140">SMB Share</span></span>

<span data-ttu-id="ea6a2-141">下面的脚本将 LCM 配置为从 SMB 共享 `\\SMBPullServer\Pull` 请求配置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="ea6a2-142">在该脚本中，ConfigurationRepositoryShare  块定义请求服务器（在此例中只是 SMB 共享）。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="ea6a2-143">设置请求客户端以下载资源</span><span class="sxs-lookup"><span data-stu-id="ea6a2-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="ea6a2-144">如果你在 LCM 配置中只指定 ConfigurationRepositoryWeb  或 ConfigurationRepositoryShare  块（如前面的示例所示），则请求客户端会从用于检索配置的相同位置请求资源。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="ea6a2-145">还可以为资源指定不同的位置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="ea6a2-146">若要将资源位置指定为单独的服务器，请使用 ResourceRepositoryWeb  块。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="ea6a2-147">若要将资源位置指定为 SMB 共享，请使用 ResourceRepositoryShare  块。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="ea6a2-148">可以将 ConfigurationRepositoryWeb  与 ResourceRepositoryShare  ，或是 ConfigurationRepositoryShare  与 ResourceRepositoryWeb  组合使用。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="ea6a2-149">下面未显示这类用法的示例。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="ea6a2-150">HTTP DSC 请求服务器</span><span class="sxs-lookup"><span data-stu-id="ea6a2-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="ea6a2-151">以下元配置将请求客户端配置为从 CONTOSO-PullSrv  获取其配置，并从 CONTOSO-ResourceSrv  获取其资源。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="ea6a2-152">SMB 共享</span><span class="sxs-lookup"><span data-stu-id="ea6a2-152">SMB Share</span></span>

<span data-ttu-id="ea6a2-153">下面的示例演示一个元配置，它将客户端设置为从 SMB 共享 `\\SMBPullServer\Configurations` 请求配置，并从 SMB 共享 `\\SMBPullServer\Resources` 请求资源。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="ea6a2-154">在推送模式下自动下载资源</span><span class="sxs-lookup"><span data-stu-id="ea6a2-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="ea6a2-155">从 PowerShell 5.0 开始，请求客户端可以从 SMB 共享下载模块，即使是针对推送  模式进行配置也是如此。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="ea6a2-156">这在不想设置请求服务器的情形中特别有用。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="ea6a2-157">ResourceRepositoryShare  块可以在不指定 ConfigurationRepositoryShare  的情况下进行使用。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="ea6a2-158">下面的示例演示一个元配置，它将客户端设置为从 SMB 共享 `\\SMBPullServer\Resources` 请求资源。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="ea6a2-159">向节点推送  配置时，它会从指定共享自动下载任何所需资源。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="ea6a2-160">设置请求客户端以报告状态</span><span class="sxs-lookup"><span data-stu-id="ea6a2-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="ea6a2-161">默认情况下，节点不会向已配置的请求服务器发送报告。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="ea6a2-162">虽然你可以将一个请求服务器用于配置、资源和报告，但必须创建 **ReportRepositoryWeb** 块来设置报表。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="ea6a2-163">HTTP DSC 请求服务器</span><span class="sxs-lookup"><span data-stu-id="ea6a2-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="ea6a2-164">下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="ea6a2-165">若要指定报表服务器，请使用 **ReportRepositoryWeb** 块。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="ea6a2-166">报表服务器不能为 SMB 服务器。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="ea6a2-167">以下元配置将请求客户端配置为从 **CONTOSO-PullSrv** 获取其配置、从 **CONTOSO-ResourceSrv** 获取资源、将状态报告发送到 **CONTOSO-ReportSrv**：</span><span class="sxs-lookup"><span data-stu-id="ea6a2-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="ea6a2-168">SMB 共享</span><span class="sxs-lookup"><span data-stu-id="ea6a2-168">SMB Share</span></span>

<span data-ttu-id="ea6a2-169">报表服务器不能为 SMB 共享。</span><span class="sxs-lookup"><span data-stu-id="ea6a2-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea6a2-170">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ea6a2-170">Next Steps</span></span>

<span data-ttu-id="ea6a2-171">配置请求客户端之后，可以使用以下指南执行后续步骤：</span><span class="sxs-lookup"><span data-stu-id="ea6a2-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="ea6a2-172">将配置发布到拉取服务器 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="ea6a2-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="ea6a2-173">打包资源并将其上传到拉取服务器 (v4)</span><span class="sxs-lookup"><span data-stu-id="ea6a2-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="ea6a2-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea6a2-174">See Also</span></span>

* [<span data-ttu-id="ea6a2-175">使用配置名称设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="ea6a2-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

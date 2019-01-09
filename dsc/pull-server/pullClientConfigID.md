---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 设置请求客户端使用配置 Id 在 PowerShell 5.0 及更高版本
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400773"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="7b357-103">设置请求客户端使用配置 Id 在 PowerShell 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="7b357-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="7b357-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7b357-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b357-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。</span><span class="sxs-lookup"><span data-stu-id="7b357-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="7b357-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="7b357-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="7b357-107">设置请求客户端之前, 应设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="7b357-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="7b357-108">但此顺序不是必需的它帮助进行故障排除，并帮助您确保注册成功。</span><span class="sxs-lookup"><span data-stu-id="7b357-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="7b357-109">若要设置请求服务器，可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="7b357-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="7b357-110">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="7b357-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="7b357-111">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="7b357-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="7b357-112">每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。</span><span class="sxs-lookup"><span data-stu-id="7b357-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="7b357-113">以下各节显示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。</span><span class="sxs-lookup"><span data-stu-id="7b357-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="7b357-114">节点的 LCM 刷新时，它将访问配置的位置下载任何已分配的配置。</span><span class="sxs-lookup"><span data-stu-id="7b357-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="7b357-115">如果在节点上不存在任何所需的资源，因此它将自动从配置的位置下载它们。</span><span class="sxs-lookup"><span data-stu-id="7b357-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="7b357-116">如果使用配置节点[报表服务器](reportServer.md)，然后，它将报告操作的状态。</span><span class="sxs-lookup"><span data-stu-id="7b357-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="7b357-117">**注意**：本主题适用于 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="7b357-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="7b357-118">有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="7b357-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="7b357-119">配置请求客户端 LCM</span><span class="sxs-lookup"><span data-stu-id="7b357-119">Configure the pull client LCM</span></span>

<span data-ttu-id="7b357-120">执行任何下面的示例创建名为的新输出文件夹**PullClientConfigID**并放入元配置 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="7b357-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="7b357-121">在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="7b357-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="7b357-122">若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="7b357-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="7b357-123">例如：</span><span class="sxs-lookup"><span data-stu-id="7b357-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="7b357-124">配置 ID</span><span class="sxs-lookup"><span data-stu-id="7b357-124">Configuration ID</span></span>

<span data-ttu-id="7b357-125">以下集示例**ConfigurationID**属性将 lcm **Guid** ，之前创建实现此目的。</span><span class="sxs-lookup"><span data-stu-id="7b357-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="7b357-126">LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。</span><span class="sxs-lookup"><span data-stu-id="7b357-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="7b357-127">请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。</span><span class="sxs-lookup"><span data-stu-id="7b357-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="7b357-128">有关详细信息请参阅[请求服务器 (v4/v5) 的发布配置](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="7b357-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="7b357-129">您可以创建一个随机**Guid**使用的示例，或通过使用[新建 Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b357-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="7b357-130">有关使用详细信息**Guid**在环境中，请参阅[规划 Guid](/powershell/dsc/secureserver#guids)。</span><span class="sxs-lookup"><span data-stu-id="7b357-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="7b357-131">设置请求客户端下载配置</span><span class="sxs-lookup"><span data-stu-id="7b357-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="7b357-132">必须在配置每个客户端**拉取**模式和存储其配置为其提供拉取服务器 url。</span><span class="sxs-lookup"><span data-stu-id="7b357-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="7b357-133">若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。</span><span class="sxs-lookup"><span data-stu-id="7b357-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="7b357-134">若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。</span><span class="sxs-lookup"><span data-stu-id="7b357-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="7b357-135">有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="7b357-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="7b357-136">HTTP DSC 请求服务器</span><span class="sxs-lookup"><span data-stu-id="7b357-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="7b357-137">下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置。</span><span class="sxs-lookup"><span data-stu-id="7b357-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="7b357-138">在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。</span><span class="sxs-lookup"><span data-stu-id="7b357-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="7b357-139">**ServerUrl**指定 DSC 拉取的 url</span><span class="sxs-lookup"><span data-stu-id="7b357-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="7b357-140">SMB 共享</span><span class="sxs-lookup"><span data-stu-id="7b357-140">SMB Share</span></span>

<span data-ttu-id="7b357-141">以下脚本将 LCM 请求配置为从 SMB 共享`\\SMBPullServer\Pull`。</span><span class="sxs-lookup"><span data-stu-id="7b357-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="7b357-142">在脚本中， **ConfigurationRepositoryShare**块定义请求服务器，在这种情况下，即只是 SMB 共享。</span><span class="sxs-lookup"><span data-stu-id="7b357-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="7b357-143">设置请求客户端下载资源</span><span class="sxs-lookup"><span data-stu-id="7b357-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="7b357-144">如果仅指定**ConfigurationRepositoryWeb**或**ConfigurationRepositoryShare**块 （与前面的示例） 在 LCM 配置中，请求客户端将请求从同一个资源它将检索其配置的位置。</span><span class="sxs-lookup"><span data-stu-id="7b357-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="7b357-145">此外可以指定不同的资源的位置。</span><span class="sxs-lookup"><span data-stu-id="7b357-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="7b357-146">若要指定资源位置作为单独的服务器，请使用**ResourceRepositoryWeb**块。</span><span class="sxs-lookup"><span data-stu-id="7b357-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="7b357-147">若要指定资源位置为 SMB 共享，请使用**ResourceRepositoryShare**块。</span><span class="sxs-lookup"><span data-stu-id="7b357-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="7b357-148">你可以组合**ConfigurationRepositoryWeb**与**ResourceRepositoryShare**或**ConfigurationRepositoryShare**与**ResourceRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="7b357-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="7b357-149">下面未显示的此示例。</span><span class="sxs-lookup"><span data-stu-id="7b357-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="7b357-150">HTTP DSC 请求服务器</span><span class="sxs-lookup"><span data-stu-id="7b357-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="7b357-151">以下元配置将请求客户端以获取从其配置**Contoso-pullsrv**和从其资源**Contoso-resourcesrv**。</span><span class="sxs-lookup"><span data-stu-id="7b357-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="7b357-152">SMB 共享</span><span class="sxs-lookup"><span data-stu-id="7b357-152">SMB Share</span></span>

<span data-ttu-id="7b357-153">下面的示例演示从 SMB 共享请求配置为将客户端设置的元配置`\\SMBPullServer\Configurations`，并从 SMB 共享的资源`\\SMBPullServer\Resources`。</span><span class="sxs-lookup"><span data-stu-id="7b357-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="7b357-154">自动下载在推送模式下的资源</span><span class="sxs-lookup"><span data-stu-id="7b357-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="7b357-155">从 PowerShell 5.0 开始，请求客户端可以下载模块从 SMB 共享，即使为配置**推送**模式。</span><span class="sxs-lookup"><span data-stu-id="7b357-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="7b357-156">这是情况下不需要设置拉取服务器中尤其有用。</span><span class="sxs-lookup"><span data-stu-id="7b357-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="7b357-157">**ResourceRepositoryShare**而无需指定可使用块**ConfigurationRepositoryShare**。</span><span class="sxs-lookup"><span data-stu-id="7b357-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="7b357-158">下面的示例显示了将客户端设置提取资源从 SMB 共享的元配置`\\SMBPullServer\Resources`。</span><span class="sxs-lookup"><span data-stu-id="7b357-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="7b357-159">当该节点是**按下**配置时，它将自动下载任何所需的资源，从指定的共享。</span><span class="sxs-lookup"><span data-stu-id="7b357-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="7b357-160">设置请求客户端报告状态</span><span class="sxs-lookup"><span data-stu-id="7b357-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="7b357-161">默认情况下，节点不会向已配置的请求服务器发送报表。</span><span class="sxs-lookup"><span data-stu-id="7b357-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="7b357-162">虽然你可以将一个请求服务器用于配置、资源和报告，但必须创建 **ReportRepositoryWeb** 块来设置报表。</span><span class="sxs-lookup"><span data-stu-id="7b357-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="7b357-163">HTTP DSC 请求服务器</span><span class="sxs-lookup"><span data-stu-id="7b357-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="7b357-164">下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。</span><span class="sxs-lookup"><span data-stu-id="7b357-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="7b357-165">若要指定报表服务器，请使用 **ReportRepositoryWeb** 块。</span><span class="sxs-lookup"><span data-stu-id="7b357-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="7b357-166">报表服务器不能为 SMB 服务器。</span><span class="sxs-lookup"><span data-stu-id="7b357-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="7b357-167">以下元配置将请求客户端配置为从 **CONTOSO-PullSrv** 获取其配置、从 **CONTOSO-ResourceSrv** 获取资源、将状态报告发送到 **CONTOSO-ReportSrv**：</span><span class="sxs-lookup"><span data-stu-id="7b357-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="7b357-168">SMB 共享</span><span class="sxs-lookup"><span data-stu-id="7b357-168">SMB Share</span></span>

<span data-ttu-id="7b357-169">报表服务器不能为 SMB 共享。</span><span class="sxs-lookup"><span data-stu-id="7b357-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7b357-170">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7b357-170">Next Steps</span></span>

<span data-ttu-id="7b357-171">配置请求客户端之后，可以使用以下指南以执行后续步骤：</span><span class="sxs-lookup"><span data-stu-id="7b357-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="7b357-172">将配置发布到拉取服务器 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="7b357-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="7b357-173">打包资源并将其上传到拉取服务器 (v4)</span><span class="sxs-lookup"><span data-stu-id="7b357-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="7b357-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b357-174">See Also</span></span>

* [<span data-ttu-id="7b357-175">使用配置名称设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="7b357-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

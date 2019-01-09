---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 设置请求客户端使用配置名称在 PowerShell 5.0 及更高版本
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400897"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="8b90a-103">设置请求客户端使用配置名称在 PowerShell 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="8b90a-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="8b90a-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8b90a-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b90a-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。</span><span class="sxs-lookup"><span data-stu-id="8b90a-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="8b90a-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="8b90a-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="8b90a-107">设置请求客户端之前, 应设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="8b90a-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="8b90a-108">但此顺序不是必需的它帮助进行故障排除，并帮助您确保注册成功。</span><span class="sxs-lookup"><span data-stu-id="8b90a-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="8b90a-109">若要设置请求服务器，可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="8b90a-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="8b90a-110">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="8b90a-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8b90a-111">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="8b90a-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="8b90a-112">每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。</span><span class="sxs-lookup"><span data-stu-id="8b90a-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="8b90a-113">以下各节显示如何使用 SMB 共享或 HTTP DSC 请求服务器配置请求客户端。</span><span class="sxs-lookup"><span data-stu-id="8b90a-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="8b90a-114">节点的 LCM 刷新时，它将访问配置的位置下载任何已分配的配置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="8b90a-115">如果在节点上不存在任何所需的资源，因此它将自动从配置的位置下载它们。</span><span class="sxs-lookup"><span data-stu-id="8b90a-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="8b90a-116">如果使用配置节点[报表服务器](reportServer.md)，然后，它将报告操作的状态。</span><span class="sxs-lookup"><span data-stu-id="8b90a-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="8b90a-117">**注意**：本主题适用于 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="8b90a-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="8b90a-118">有关设置请求客户端在 PowerShell 4.0 中的信息，请参阅[设置请求客户端在 PowerShell 4.0 中使用配置 ID](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="8b90a-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="8b90a-119">配置请求客户端 LCM</span><span class="sxs-lookup"><span data-stu-id="8b90a-119">Configure the pull client LCM</span></span>

<span data-ttu-id="8b90a-120">执行任何下面的示例创建名为的新输出文件夹**PullClientConfigName**并放入元配置 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="8b90a-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="8b90a-121">在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="8b90a-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="8b90a-122">若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="8b90a-123">例如：</span><span class="sxs-lookup"><span data-stu-id="8b90a-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="8b90a-124">配置名称</span><span class="sxs-lookup"><span data-stu-id="8b90a-124">Configuration Name</span></span>

<span data-ttu-id="8b90a-125">以下集示例**ConfigurationName**为此目的创建的以前编译配置的名称将 LCM 的属性。</span><span class="sxs-lookup"><span data-stu-id="8b90a-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="8b90a-126">**ConfigurationName** LCM 使用请求服务器上查找相应的配置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="8b90a-127">请求服务器上的配置 MOF 文件必须命名为`<ConfigurationName>.mof`，在这种情况下，"ClientConfig.mof"。</span><span class="sxs-lookup"><span data-stu-id="8b90a-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="8b90a-128">有关详细信息，请参阅[请求服务器 (v4/v5) 的发布配置](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="8b90a-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="8b90a-129">设置请求客户端下载配置</span><span class="sxs-lookup"><span data-stu-id="8b90a-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="8b90a-130">必须在配置每个客户端**拉取**模式和存储其配置为其提供拉取服务器 url。</span><span class="sxs-lookup"><span data-stu-id="8b90a-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="8b90a-131">若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。</span><span class="sxs-lookup"><span data-stu-id="8b90a-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="8b90a-132">若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="8b90a-133">有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="8b90a-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="8b90a-134">下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="8b90a-135">在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。</span><span class="sxs-lookup"><span data-stu-id="8b90a-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="8b90a-136">**ServerURL** 属性为请求服务器指定终结点。</span><span class="sxs-lookup"><span data-stu-id="8b90a-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="8b90a-137">**RegistrationKey** 属性是请求服务器的所有客户端节点与该请求服务器之间的共享密钥。</span><span class="sxs-lookup"><span data-stu-id="8b90a-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="8b90a-138">请求服务器上的文件中存储了相同的值。</span><span class="sxs-lookup"><span data-stu-id="8b90a-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="8b90a-139">**注意**：注册密钥仅适用于**web**请求服务器。</span><span class="sxs-lookup"><span data-stu-id="8b90a-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="8b90a-140">对于 SMB 请求服务器，仍必须使用 ConfigurationID。</span><span class="sxs-lookup"><span data-stu-id="8b90a-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="8b90a-141">有关使用 **ConfigurationID** 配置请求服务器的信息，请参阅[使用配置 ID 设置请求客户端](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="8b90a-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="8b90a-142">**ConfigurationNames** 属性是指定用于客户端节点的配置的名称的数组。</span><span class="sxs-lookup"><span data-stu-id="8b90a-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="8b90a-143">**注意：** 如果在 ConfigurationNames 中指定多个值，则必须也在你的配置中指定 PartialConfiguration 块。</span><span class="sxs-lookup"><span data-stu-id="8b90a-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="8b90a-144">有关部分配置的信息，请参阅 [PowerShell Desired State Configuration 部分配置](partialConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="8b90a-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="8b90a-145">设置请求客户端下载资源</span><span class="sxs-lookup"><span data-stu-id="8b90a-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="8b90a-146">如果仅指定**ConfigurationRepositoryWeb**或**ConfigurationRepositoryShare**块 （如在前面的示例） 在 LCM 配置中，请求客户端将请求从相同的资源".mof"文件存储的位置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="8b90a-147">此外可以指定不同的客户端可下载资源的位置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="8b90a-148">若要指定资源服务器，请使用 **ResourceRepositoryWeb**（适用于 Web 请求服务器）或 **ResourceRepositoryShare**（适用于 SMB 请求服务器）块。</span><span class="sxs-lookup"><span data-stu-id="8b90a-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="8b90a-149">下面的示例显示了将客户端设置以从请求的服务器，并从 SMB 共享的资源下载配置的元配置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="8b90a-150">设置请求客户端报告状态</span><span class="sxs-lookup"><span data-stu-id="8b90a-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="8b90a-151">用于配置、 资源和报告，可以使用一个请求服务器。</span><span class="sxs-lookup"><span data-stu-id="8b90a-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="8b90a-152">未配置报告的客户端默认情况下。</span><span class="sxs-lookup"><span data-stu-id="8b90a-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="8b90a-153">若要配置客户端报告状态，您必须创建**ReportRepositoryWeb**块。</span><span class="sxs-lookup"><span data-stu-id="8b90a-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="8b90a-154">下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。</span><span class="sxs-lookup"><span data-stu-id="8b90a-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="8b90a-155">报表服务器不能为 SMB 共享。</span><span class="sxs-lookup"><span data-stu-id="8b90a-155">A report server cannot be an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="8b90a-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b90a-156">See Also</span></span>

* [<span data-ttu-id="8b90a-157">使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="8b90a-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="8b90a-158">设置 DSC Web 请求服务器</span><span class="sxs-lookup"><span data-stu-id="8b90a-158">Setting up a DSC web pull server</span></span>](pullServer.md)

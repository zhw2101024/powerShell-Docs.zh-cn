---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "使用配置名称设置请求客户端"
ms.openlocfilehash: 9bfcac87300d30a59b66e60ed24add32e2420e21
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="76ff3-103">使用配置名称设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="76ff3-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="76ff3-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="76ff3-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="76ff3-105">必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置的 URL。</span><span class="sxs-lookup"><span data-stu-id="76ff3-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="76ff3-106">若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。</span><span class="sxs-lookup"><span data-stu-id="76ff3-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="76ff3-107">若要配置 LCM，可创建一个使用 **DSCLocalConfigurationManager** 特性修饰的特殊类型配置。</span><span class="sxs-lookup"><span data-stu-id="76ff3-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="76ff3-108">有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="76ff3-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="76ff3-109">**请注意**：本主题适用于 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="76ff3-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="76ff3-110">有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="76ff3-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="76ff3-111">下面的脚本将 LCM 配置为从名为“CONTOSO-PullSrv”的服务器请求配置：</span><span class="sxs-lookup"><span data-stu-id="76ff3-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="76ff3-112">在该脚本中，**ConfigurationRepositoryWeb** 块定义了请求服务器。</span><span class="sxs-lookup"><span data-stu-id="76ff3-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="76ff3-113">**ServerURL** 属性为请求服务器指定终结点。</span><span class="sxs-lookup"><span data-stu-id="76ff3-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="76ff3-114">**RegistrationKey** 属性是请求服务器的所有客户端节点与该请求服务器之间的共享密钥。</span><span class="sxs-lookup"><span data-stu-id="76ff3-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="76ff3-115">请求服务器上的文件中存储了相同的值。</span><span class="sxs-lookup"><span data-stu-id="76ff3-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="76ff3-116">**ConfigurationNames** 属性是指定用于客户端节点的配置的名称的数组。</span><span class="sxs-lookup"><span data-stu-id="76ff3-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="76ff3-117">在请求服务器上，必须将此客户端节点的配置 MOF 文件命名为 *ConfigurationNames*.mof，其中 *ConfigurationNames* 的值与你在此元配置中设置的 **ConfigurationNames** 属性的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="76ff3-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="76ff3-118">**注意：**如果你在 **ConfigurationNames** 中指定多个值，则必须也在你的配置中指定 **PartialConfiguration** 块。</span><span class="sxs-lookup"><span data-stu-id="76ff3-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="76ff3-119">有关部分配置的信息，请参阅 [PowerShell Desired State Configuration 部分配置](partialConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="76ff3-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="76ff3-120">此脚本运行后，将创建名为 **PullClientConfigNames** 的新输出文件夹，并在其中放入元配置 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="76ff3-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="76ff3-121">在本例中，会将元配置 MOF 文件命名为 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="76ff3-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="76ff3-122">若要应用配置，请调用 **Set-DscLocalConfigurationManager** cmdlet，并将 **Path** 设置为元配置 MOF 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="76ff3-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="76ff3-123">**注意**：注册密钥仅适用于 Web 请求服务器。</span><span class="sxs-lookup"><span data-stu-id="76ff3-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="76ff3-124">对于 SMB 请求服务器，你仍必须使用 **ConfigurationID**。</span><span class="sxs-lookup"><span data-stu-id="76ff3-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="76ff3-125">有关使用 **ConfigurationID** 配置请求服务器的信息，请参阅[使用配置 ID 设置请求客户端](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="76ff3-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="76ff3-126">资源和报表服务器</span><span class="sxs-lookup"><span data-stu-id="76ff3-126">Resource and report servers</span></span>

<span data-ttu-id="76ff3-127">如果你在 LCM 配置中只指定 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 块（如同上一个示例所示），请求客户端会从指定服务器请求资源，但不会向它发送报表。</span><span class="sxs-lookup"><span data-stu-id="76ff3-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="76ff3-128">虽然你可以将一个请求服务器用于配置、资源和报告，但必须创建 **ReportRepositoryWeb** 块来设置报表。</span><span class="sxs-lookup"><span data-stu-id="76ff3-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="76ff3-129">下面的示例展示了将客户端设置为请求配置和资源并将报表数据发送到一个请求服务器的元配置。</span><span class="sxs-lookup"><span data-stu-id="76ff3-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="76ff3-130">还可以为资源和报告指定不同的请求服务器。</span><span class="sxs-lookup"><span data-stu-id="76ff3-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="76ff3-131">若要指定资源服务器，请使用 **ResourceRepositoryWeb**（适用于 Web 请求服务器）或 **ResourceRepositoryShare**（适用于 SMB 请求服务器）块。</span><span class="sxs-lookup"><span data-stu-id="76ff3-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="76ff3-132">若要指定报表服务器，请使用 **ReportRepositoryWeb** 块。</span><span class="sxs-lookup"><span data-stu-id="76ff3-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="76ff3-133">报表服务器不能为 SMB 服务器。</span><span class="sxs-lookup"><span data-stu-id="76ff3-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="76ff3-134">以下元配置将请求客户端配置为从 **CONTOSO-PullSrv** 获取其配置、从 **CONTOSO-ResourceSrv** 获取资源、将状态报告发送到 **CONTOSO-ReportSrv**：</span><span class="sxs-lookup"><span data-stu-id="76ff3-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="76ff3-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76ff3-135">See Also</span></span>

* [<span data-ttu-id="76ff3-136">使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="76ff3-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="76ff3-137">设置 DSC Web 请求服务器</span><span class="sxs-lookup"><span data-stu-id="76ff3-137">Setting up a DSC web pull server</span></span>](pullServer.md)


---
ms.date: 04/11/2018
keywords: dsc,powershell,配置,安装程序
title: DSC 请求服务
ms.openlocfilehash: 057da50843e79ae31eef4fea1fa58e882a9d1ace
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="efc9f-103">Desired State Configuration 请求服务</span><span class="sxs-lookup"><span data-stu-id="efc9f-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="efc9f-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="efc9f-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efc9f-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。</span><span class="sxs-lookup"><span data-stu-id="efc9f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="efc9f-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="efc9f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="efc9f-107">本地配置管理器可由请求服务解决方案集中管理。</span><span class="sxs-lookup"><span data-stu-id="efc9f-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="efc9f-108">使用此方法时，会向服务注册要管理的节点并在 LCM 设置中指定一个配置。</span><span class="sxs-lookup"><span data-stu-id="efc9f-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="efc9f-109">会将配置以及作为配置依赖项所需的全部 DSC 资源下载到计算机，LCM 将使用它们来管理配置。</span><span class="sxs-lookup"><span data-stu-id="efc9f-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="efc9f-110">有关要管理的计算机的状态信息将上传到服务进行报告。</span><span class="sxs-lookup"><span data-stu-id="efc9f-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="efc9f-111">此概念称为“请求服务”。</span><span class="sxs-lookup"><span data-stu-id="efc9f-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="efc9f-112">请求服务的当前选项包括：</span><span class="sxs-lookup"><span data-stu-id="efc9f-112">The current options for pull service include:</span></span>

- <span data-ttu-id="efc9f-113">Azure 自动化 Desired State Configuration 服务</span><span class="sxs-lookup"><span data-stu-id="efc9f-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="efc9f-114">在 Windows Server 上运行的请求服务</span><span class="sxs-lookup"><span data-stu-id="efc9f-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="efc9f-115">由社区维护的开放源解决方案</span><span class="sxs-lookup"><span data-stu-id="efc9f-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="efc9f-116">SMB 共享</span><span class="sxs-lookup"><span data-stu-id="efc9f-116">An SMB share</span></span>

<span data-ttu-id="efc9f-117">**建议的解决方案**和可用功能最多的选项是 [Azure 自动化 DSC](/azure/automation/automation-dsc-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="efc9f-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="efc9f-118">Azure 服务可以在本地管理私有数据中心或 Azure 和 AWS 等公有云中的节点。</span><span class="sxs-lookup"><span data-stu-id="efc9f-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="efc9f-119">对于服务器无法直接连接到 Internet 的私有环境，请考虑将出站流量限制为仅已发布的 Azure IP 范围（请参阅 [Azure 数据中心 IP 范围](https://www.microsoft.com/en-us/download/details.aspx?id=41653)）。</span><span class="sxs-lookup"><span data-stu-id="efc9f-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="efc9f-120">在 Windows Server 的请求服务上目前暂不可用的在线服务功能包括：</span><span class="sxs-lookup"><span data-stu-id="efc9f-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="efc9f-121">所有数据在传输和静止时均处于加密状态</span><span class="sxs-lookup"><span data-stu-id="efc9f-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="efc9f-122">自动创建和管理客户端证书</span><span class="sxs-lookup"><span data-stu-id="efc9f-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="efc9f-123">用于集中式管理[密码/凭据](/azure/automation/automation-credentials)或[变量](/azure/automation/automation-variables)（例如服务器名称或连接字符串）的机密存储</span><span class="sxs-lookup"><span data-stu-id="efc9f-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="efc9f-124">集中式管理节点 [LCM 配置](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="efc9f-124">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="efc9f-125">将配置集中分配给客户端节点</span><span class="sxs-lookup"><span data-stu-id="efc9f-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="efc9f-126">在投入生产之前，将配置更改发布到“Canary 组”用于测试</span><span class="sxs-lookup"><span data-stu-id="efc9f-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="efc9f-127">图形报告</span><span class="sxs-lookup"><span data-stu-id="efc9f-127">Graphical reporting</span></span>
  - <span data-ttu-id="efc9f-128">DSC 资源粒度级别的状态详细信息</span><span class="sxs-lookup"><span data-stu-id="efc9f-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="efc9f-129">客户端计算机中用于故障排除的详细错误消息</span><span class="sxs-lookup"><span data-stu-id="efc9f-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="efc9f-130">[与 Azure Log Analytics 集成](/azure/automation/automation-dsc-diagnostics)用于警报，与自动化的任务，Android/iOS 应用集成用于报告和警报</span><span class="sxs-lookup"><span data-stu-id="efc9f-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="efc9f-131">Windows Server 中的 DSC 请求服务</span><span class="sxs-lookup"><span data-stu-id="efc9f-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="efc9f-132">可将请求服务配置为在 Windows Server 上运行。</span><span class="sxs-lookup"><span data-stu-id="efc9f-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="efc9f-133">请注意，Windows Server 中包含的请求服务解决方案仅具备存储配置/模块以将报表数据下载并捕获到数据中的功能。</span><span class="sxs-lookup"><span data-stu-id="efc9f-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="efc9f-134">它不具备 Azure 中的服务所提供的许多功能，因此不适合用于评估服务的使用方式。</span><span class="sxs-lookup"><span data-stu-id="efc9f-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="efc9f-135">Windows Server 中提供的请求服务是 IIS 中的一项 Web 服务，当目标节点请求 DSC 配置文件时，此服务通过 OData 接口向这些节点提供它们。</span><span class="sxs-lookup"><span data-stu-id="efc9f-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="efc9f-136">使用请求服务器的要求：</span><span class="sxs-lookup"><span data-stu-id="efc9f-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="efc9f-137">运行的服务器：</span><span class="sxs-lookup"><span data-stu-id="efc9f-137">A server running:</span></span>
  - <span data-ttu-id="efc9f-138">WMF/PowerShell 5.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="efc9f-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="efc9f-139">IIS 服务器角色</span><span class="sxs-lookup"><span data-stu-id="efc9f-139">IIS server role</span></span>
  - <span data-ttu-id="efc9f-140">DSC 服务</span><span class="sxs-lookup"><span data-stu-id="efc9f-140">DSC Service</span></span>
- <span data-ttu-id="efc9f-141">理想情况下，可通过某些方式生成证书，以便保护传递给目标节点上本地配置管理器 (LCM) 的凭据</span><span class="sxs-lookup"><span data-stu-id="efc9f-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="efc9f-142">将 Windows Server 配置为托管请求服务的最佳方式是使用 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="efc9f-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="efc9f-143">下面提供了一个示例脚本。</span><span class="sxs-lookup"><span data-stu-id="efc9f-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="efc9f-144">支持的数据库系统</span><span class="sxs-lookup"><span data-stu-id="efc9f-144">Supported database systems</span></span>

|<span data-ttu-id="efc9f-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="efc9f-145">WMF 4.0</span></span>   |<span data-ttu-id="efc9f-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="efc9f-146">WMF 5.0</span></span>  |<span data-ttu-id="efc9f-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="efc9f-147">WMF 5.1</span></span> |<span data-ttu-id="efc9f-148">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="efc9f-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="efc9f-149">MDB</span><span class="sxs-lookup"><span data-stu-id="efc9f-149">MDB</span></span>     |<span data-ttu-id="efc9f-150">ESENT（默认）、MDB</span><span class="sxs-lookup"><span data-stu-id="efc9f-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="efc9f-151">ESENT（默认）、MDB</span><span class="sxs-lookup"><span data-stu-id="efc9f-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="efc9f-152">ESENT（默认）、SQL Server、MDB</span><span class="sxs-lookup"><span data-stu-id="efc9f-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="efc9f-153">从 [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver) 的版本 17090 开始，SQL Server 成为了请求服务（Windows Feature DSC-Service）的支持选项。</span><span class="sxs-lookup"><span data-stu-id="efc9f-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="efc9f-154">这为缩放未迁移至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) 的大型 DSC 环境提供了新选项。</span><span class="sxs-lookup"><span data-stu-id="efc9f-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="efc9f-155">**注意**：SQL Server 支持不会添加到 WMF 5.1 的以前版本（或更早版本）中，仅在 17090 版本或更高版本的 Windows Server 上提供。</span><span class="sxs-lookup"><span data-stu-id="efc9f-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="efc9f-156">若要将请求服务器配置为使用 SQL Server，可将“SqlProvider”设为 `$true`并将“SqlConnectionString”设为有效的 SQL Server 连接字符串。</span><span class="sxs-lookup"><span data-stu-id="efc9f-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="efc9f-157">有关详细信息，请参阅 [SqlClient 连接字符串](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings)。</span><span class="sxs-lookup"><span data-stu-id="efc9f-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="efc9f-158">若要查看使用 xDscWebService 的 SQL Server 配置的示例，请先阅读[使用 xDscWebService 资源](#using-the-xdscwebservice-resource)，再查看 [GitHub 上的 Sample_xDscWebServiceRegistration_UseSQLProvider.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1)。</span><span class="sxs-lookup"><span data-stu-id="efc9f-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="efc9f-159">使用 xDscWebService 资源</span><span class="sxs-lookup"><span data-stu-id="efc9f-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="efc9f-160">设置 Web 请求服务器的最简单方法是使用包含在 xPSDesiredStateConfiguration 模块中的 xDscWebService 资源。</span><span class="sxs-lookup"><span data-stu-id="efc9f-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="efc9f-161">下列步骤说明如何使用设置 Web 服务的配置中的资源。</span><span class="sxs-lookup"><span data-stu-id="efc9f-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="efc9f-162">调用 [Install-Module](/powershell/module/PowershellGet/Install-Module) 以安装 **xPSDesiredStateConfiguration** 模块。</span><span class="sxs-lookup"><span data-stu-id="efc9f-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="efc9f-163">**请注意**：**Install-Module** 包含在 **PowerShellGet** 模块中，后者纳入 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="efc9f-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="efc9f-164">可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="efc9f-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="efc9f-165">从受信任的证书颁发机构（在所在组织或公共颁发机构中）获取 DSC 请求服务器的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="efc9f-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="efc9f-166">从颁发机构收到的证书通常采用 PFX 格式。</span><span class="sxs-lookup"><span data-stu-id="efc9f-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="efc9f-167">采用默认位置（应是 CERT:\LocalMachine\My），在将成为请求服务器的节点上安装证书。</span><span class="sxs-lookup"><span data-stu-id="efc9f-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="efc9f-168">记下证书指纹。</span><span class="sxs-lookup"><span data-stu-id="efc9f-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="efc9f-169">选择要用作注册密钥的 GUID。</span><span class="sxs-lookup"><span data-stu-id="efc9f-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="efc9f-170">若要使用 PowerShell 生成一个，请在 PS 提示符处输入以下命令，然后按 Enter：“``` [guid]::newGuid()```”或“```New-Guid```”。</span><span class="sxs-lookup"><span data-stu-id="efc9f-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="efc9f-171">此密钥将由客户端节点用作共享密钥，以便在注册过程中进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="efc9f-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="efc9f-172">有关详细信息，请参阅下面的“注册密钥”部分。</span><span class="sxs-lookup"><span data-stu-id="efc9f-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="efc9f-173">在 PowerShell ISE 中，启动 (F5) 以下配置脚本（包含在 xPSDesiredStateConfiguration 模块的示例文件夹中，名为 Sample_xDscWebServiceRegistration.ps1）。</span><span class="sxs-lookup"><span data-stu-id="efc9f-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="efc9f-174">此脚本会设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="efc9f-174">This script sets up the pull server.</span></span>

```powershell
configuration Sample_xDscWebServiceRegistration
{
    param
    (
        [string[]]$NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $certificateThumbPrint,

        [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
    )

    Import-DSCResource -ModuleName xPSDesiredStateConfiguration

    Node $NodeName
    {
        WindowsFeature DSCServiceFeature
        {
            Ensure = "Present"
            Name   = "DSC-Service"
        }

        xDscWebService PSDSCPullServer
        {
            Ensure                  = "Present"
            EndpointName            = "PSDSCPullServer"
            Port                    = 8080
            PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
            CertificateThumbPrint   = $certificateThumbPrint
            ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
            ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
            State                   = "Started"
            DependsOn               = "[WindowsFeature]DSCServiceFeature"
            RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
            AcceptSelfSignedCertificates = $true
            Enable32BitAppOnWin64   = $false
        }

        File RegistrationKeyFile
        {
            Ensure          = 'Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}
```

1. <span data-ttu-id="efc9f-175">运行配置，将 SSL 证书的指纹作为 **certificateThumbPrint** 参数进行传递，并将 GUID 注册密钥作为 **RegistrationKey** 参数进行传递：</span><span class="sxs-lookup"><span data-stu-id="efc9f-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a><span data-ttu-id="efc9f-176">注册密钥</span><span class="sxs-lookup"><span data-stu-id="efc9f-176">Registration Key</span></span>

<span data-ttu-id="efc9f-177">若要允许客户端节点注册到服务器以便使用配置名称代替配置 ID，需将以上配置创建的注册密钥保存在 `C:\Program Files\WindowsPowerShell\DscService` 中名为 `RegistrationKeys.txt` 的文件中。</span><span class="sxs-lookup"><span data-stu-id="efc9f-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="efc9f-178">注册密钥会在初始注册过程中充当由客户端用于请求服务器的共享密钥。</span><span class="sxs-lookup"><span data-stu-id="efc9f-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="efc9f-179">注册成功完成之后，客户端会生成用于唯一地向请求服务器进行身份验证的自签名证书。</span><span class="sxs-lookup"><span data-stu-id="efc9f-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="efc9f-180">此证书的指纹在本地进行存储，并与请求服务器的 URL 关联。</span><span class="sxs-lookup"><span data-stu-id="efc9f-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="efc9f-181">**注意**：PowerShell 4.0 中不支持注册密钥。</span><span class="sxs-lookup"><span data-stu-id="efc9f-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="efc9f-182">为了配置节点以便向请求服务器进行身份验证，注册密钥需要处于将向此请求服务器注册的任何目标节点的元配置中。</span><span class="sxs-lookup"><span data-stu-id="efc9f-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="efc9f-183">请注意，以下元配置中的 **RegistrationKey** 会在目标计算机成功注册之后删除，并且值“140a952b-b9d6-406b-b416-e0f759c9c0e4”必须与请求服务器上的 RegistrationKeys.txt 文件中存储的值匹配。</span><span class="sxs-lookup"><span data-stu-id="efc9f-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="efc9f-184">请始终安全地处理注册密钥值，因为知道它便可以向请求服务器注册任何目标计算机。</span><span class="sxs-lookup"><span data-stu-id="efc9f-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> <span data-ttu-id="efc9f-185">**注意**：**ReportServerWeb** 部分允许将报表数据发送到请求服务器。</span><span class="sxs-lookup"><span data-stu-id="efc9f-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="efc9f-186">元配置文件中缺少 **ConfigurationID** 属性暗示请求服务器支持 V2 版本的请求服务器协议，因此需要初始注册。</span><span class="sxs-lookup"><span data-stu-id="efc9f-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="efc9f-187">相反，存在 **ConfigurationID** 意味着使用 V1 版本的请求服务器协议，不会进行注册处理。</span><span class="sxs-lookup"><span data-stu-id="efc9f-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="efc9f-188">**注意**：在推送方案中，当前版本中存在一个 bug，因此需要在元配置文件中为绝不会向请求服务器注册的节点定义 ConfigurationID 属性。</span><span class="sxs-lookup"><span data-stu-id="efc9f-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="efc9f-189">这会强制使用 V1 请求服务器协议，避免注册失败消息。</span><span class="sxs-lookup"><span data-stu-id="efc9f-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="efc9f-190">放置配置和资源</span><span class="sxs-lookup"><span data-stu-id="efc9f-190">Placing configurations and resources</span></span>

<span data-ttu-id="efc9f-191">请求服务器设置完成之后，在请求服务器配置中通过 **ConfigurationPath** 和 **ModulePath** 属性定义的文件夹是用于放置可供目标节点请求的模块和配置的位置。</span><span class="sxs-lookup"><span data-stu-id="efc9f-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="efc9f-192">这些文件需要采用特定格式，以便请求服务器可正确处理它们。</span><span class="sxs-lookup"><span data-stu-id="efc9f-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="efc9f-193">DSC 资源模块程序包格式</span><span class="sxs-lookup"><span data-stu-id="efc9f-193">DSC resource module package format</span></span>

<span data-ttu-id="efc9f-194">每个资源模块都需要进行压缩并按照 `{Module Name}_{Module Version}.zip` 模式进行命名。</span><span class="sxs-lookup"><span data-stu-id="efc9f-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="efc9f-195">例如，一个名为 xWebAdminstration 并且模块版本为 3.1.2.0 的模块会命名为“xWebAdministration_3.2.1.0.zip”。</span><span class="sxs-lookup"><span data-stu-id="efc9f-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="efc9f-196">每个版本的模块都必须包含在单个 zip 文件中。</span><span class="sxs-lookup"><span data-stu-id="efc9f-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="efc9f-197">由于每个 zip 文件中只有单个版本的资源，因此不支持在 WMF 5.0 中添加的可在单个目录中支持多个模块版本的模块格式。</span><span class="sxs-lookup"><span data-stu-id="efc9f-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="efc9f-198">这意味着在打包 DSC 资源模块以便用于请求服务器之前，需要对目录结构进行少量更改。</span><span class="sxs-lookup"><span data-stu-id="efc9f-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="efc9f-199">WMF 5.0 中包含 DSC 资源的模块默认格式是 {Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'。</span><span class="sxs-lookup"><span data-stu-id="efc9f-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="efc9f-200">为请求服务器进行打包之前，删除 {Module version} 文件夹，让路径变为 {Module Folder}\DscResources\{DSC Resource Folder}\'。</span><span class="sxs-lookup"><span data-stu-id="efc9f-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="efc9f-201">进行此更改之后，按上文所述压缩文件夹，并将这些 zip 文件置于 **ModulePath** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="efc9f-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="efc9f-202">使用 `New-DscChecksum {module zip file}` 可为新添加的模块创建校验和文件。</span><span class="sxs-lookup"><span data-stu-id="efc9f-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="efc9f-203">配置 MOF 格式</span><span class="sxs-lookup"><span data-stu-id="efc9f-203">Configuration MOF format</span></span>

<span data-ttu-id="efc9f-204">配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。</span><span class="sxs-lookup"><span data-stu-id="efc9f-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="efc9f-205">若要创建校验和，请调用 [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="efc9f-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="efc9f-206">该 cmdlet 将接受 **Path** 参数，该参数指定了配置 MOF 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="efc9f-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="efc9f-207">该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="efc9f-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="efc9f-208">如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。</span><span class="sxs-lookup"><span data-stu-id="efc9f-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="efc9f-209">将 MOF 文件及其关联校验和文件置于 ConfigurationPath 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="efc9f-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="efc9f-210">**注意**：如果以任何方式更改配置 MOF 文件，则还必须重新创建校验和文件。</span><span class="sxs-lookup"><span data-stu-id="efc9f-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="efc9f-211">工具</span><span class="sxs-lookup"><span data-stu-id="efc9f-211">Tooling</span></span>

<span data-ttu-id="efc9f-212">为了使请求服务器的设置、验证和管理更加容易，以下工具作为示例包含在最新版本的 xPSDesiredStateConfiguration 模块中：</span><span class="sxs-lookup"><span data-stu-id="efc9f-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="efc9f-213">该模块有助于打包 DSC 资源模块和配置文件以便在请求服务器上使用。</span><span class="sxs-lookup"><span data-stu-id="efc9f-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="efc9f-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="efc9f-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="efc9f-215">以下示例：</span><span class="sxs-lookup"><span data-stu-id="efc9f-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="efc9f-216">验证请求服务器是否配置正确的脚本。</span><span class="sxs-lookup"><span data-stu-id="efc9f-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="efc9f-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="efc9f-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="efc9f-218">请求服务的社区解决方案</span><span class="sxs-lookup"><span data-stu-id="efc9f-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="efc9f-219">DSC 社区已创作多个解决方案来实现请求服务协议。</span><span class="sxs-lookup"><span data-stu-id="efc9f-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="efc9f-220">对于本地环境，这些解决方案使请求服务具有相关功能，使之有机会以渐进式增强方式回馈社区。</span><span class="sxs-lookup"><span data-stu-id="efc9f-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="efc9f-221">Tug</span><span class="sxs-lookup"><span data-stu-id="efc9f-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="efc9f-222">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="efc9f-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="efc9f-223">请求客户端配置</span><span class="sxs-lookup"><span data-stu-id="efc9f-223">Pull client configuration</span></span>

<span data-ttu-id="efc9f-224">以下主题详细描述了如何设置请求客户端：</span><span class="sxs-lookup"><span data-stu-id="efc9f-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="efc9f-225">使用配置 ID 设置 DSC 请求客户端</span><span class="sxs-lookup"><span data-stu-id="efc9f-225">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="efc9f-226">使用配置名称设置 DSC 请求客户端</span><span class="sxs-lookup"><span data-stu-id="efc9f-226">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="efc9f-227">部分配置</span><span class="sxs-lookup"><span data-stu-id="efc9f-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="efc9f-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efc9f-228">See also</span></span>

- [<span data-ttu-id="efc9f-229">Windows PowerShell Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="efc9f-229">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="efc9f-230">执行配置</span><span class="sxs-lookup"><span data-stu-id="efc9f-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="efc9f-231">使用 DSC 报表服务器</span><span class="sxs-lookup"><span data-stu-id="efc9f-231">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="efc9f-232">[[MS-DSCPM]：Desired State Configuration 请求模型协议](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="efc9f-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="efc9f-233">[[MS-DSCPM]：Desired State Configuration 请求模型协议 Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="efc9f-233">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
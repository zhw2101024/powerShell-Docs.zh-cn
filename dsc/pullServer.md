---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "设置 DSC Web 请求服务器"
ms.openlocfilehash: 03d4d148c87854b146091aa0e8d815b8c35def72
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="8827c-103">设置 DSC Web 请求服务器</span><span class="sxs-lookup"><span data-stu-id="8827c-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="8827c-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8827c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8827c-105">DSC Web 请求服务器是 IIS 中的一项 Web 服务，当目标节点请求 DSC 配置文件时，此服务通过 OData 接口向这些节点提供它们。</span><span class="sxs-lookup"><span data-stu-id="8827c-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="8827c-106">使用请求服务器的要求：</span><span class="sxs-lookup"><span data-stu-id="8827c-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="8827c-107">运行的服务器：</span><span class="sxs-lookup"><span data-stu-id="8827c-107">A server running:</span></span>
  - <span data-ttu-id="8827c-108">WMF/PowerShell 5.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="8827c-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="8827c-109">IIS 服务器角色</span><span class="sxs-lookup"><span data-stu-id="8827c-109">IIS server role</span></span>
  - <span data-ttu-id="8827c-110">DSC 服务</span><span class="sxs-lookup"><span data-stu-id="8827c-110">DSC Service</span></span>
* <span data-ttu-id="8827c-111">理想情况下，可通过某些方式生成证书，以便保护传递给目标节点上本地配置管理器 (LCM) 的凭据</span><span class="sxs-lookup"><span data-stu-id="8827c-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="8827c-112">可使用服务器管理器中的添加角色和功能向导或使用 PowerShell 来添加 IIS 服务器角色和 DSC 服务。</span><span class="sxs-lookup"><span data-stu-id="8827c-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="8827c-113">本主题中包含的示例脚本将为你提供这两种方法的步骤。</span><span class="sxs-lookup"><span data-stu-id="8827c-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="8827c-114">使用 xDSCWebService 资源</span><span class="sxs-lookup"><span data-stu-id="8827c-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="8827c-115">设置 Web 请求服务器的最简单方法是使用包含在 xPSDesiredStateConfiguration 模块中的 xWebService 资源。</span><span class="sxs-lookup"><span data-stu-id="8827c-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="8827c-116">下列步骤说明如何使用设置 Web 服务的配置中的资源。</span><span class="sxs-lookup"><span data-stu-id="8827c-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="8827c-117">调用 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) 以安装 **xPSDesiredStateConfiguration** 模块。</span><span class="sxs-lookup"><span data-stu-id="8827c-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="8827c-118">**请注意**：**Install-Module** 包含在 **PowerShellGet** 模块中，后者纳入 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="8827c-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="8827c-119">可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="8827c-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="8827c-120">从受信任的证书颁发机构（在所在组织或公共颁发机构中）获取 DSC 请求服务器的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="8827c-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="8827c-121">从颁发机构收到的证书通常采用 PFX 格式。</span><span class="sxs-lookup"><span data-stu-id="8827c-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="8827c-122">采用默认位置（应是 CERT:\LocalMachine\My），在将成为请求服务器的节点上安装证书。</span><span class="sxs-lookup"><span data-stu-id="8827c-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="8827c-123">记下证书指纹。</span><span class="sxs-lookup"><span data-stu-id="8827c-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="8827c-124">选择要用作注册密钥的 GUID。</span><span class="sxs-lookup"><span data-stu-id="8827c-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="8827c-125">若要使用 PowerShell 生成一个，请在 PS 提示符处输入以下命令，然后按 Enter：“``` [guid]::newGuid()```”或“```New-Guid```”。</span><span class="sxs-lookup"><span data-stu-id="8827c-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="8827c-126">此密钥将由客户端节点用作共享密钥，以便在注册过程中进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="8827c-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="8827c-127">有关详细信息，请参阅下面的“注册密钥”部分。</span><span class="sxs-lookup"><span data-stu-id="8827c-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="8827c-128">在 PowerShell ISE 中，启动 (F5) 以下配置脚本（包含于 **xPSDesiredStateConfiguration** 模块的示例文件夹中，名为 Sample_xDscWebService.ps1）。</span><span class="sxs-lookup"><span data-stu-id="8827c-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="8827c-129">此脚本会设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="8827c-129">This script sets up the pull server.</span></span>
  
    ```powershell
    configuration Sample_xDscPullServer
    { 
        param  
        ( 
                [string[]]$NodeName = 'localhost', 

                [ValidateNotNullOrEmpty()] 
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey 
         ) 
         
         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName 
         { 
             WindowsFeature DSCServiceFeature 
             { 
                 Ensure = 'Present'
                 Name   = 'DSC-Service'             
             } 

             xDscWebService PSDSCPullServer 
             { 
                 Ensure                   = 'Present' 
                 EndpointName             = 'PSDSCPullServer' 
                 Port                     = 8080 
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer" 
                 CertificateThumbPrint    = $certificateThumbPrint          
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration" 
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'     
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="8827c-130">运行配置，将 SSL 证书的指纹作为 **certificateThumbPrint** 参数进行传递，并将 GUID 注册密钥作为 **RegistrationKey** 参数进行传递：</span><span class="sxs-lookup"><span data-stu-id="8827c-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="8827c-131">注册密钥</span><span class="sxs-lookup"><span data-stu-id="8827c-131">Registration Key</span></span>
<span data-ttu-id="8827c-132">若要允许客户端节点注册到服务器以便使用配置名称代替配置 ID，需将以上配置创建的注册密钥保存在 `C:\Program Files\WindowsPowerShell\DscService` 中名为 `RegistrationKeys.txt` 的文件中。</span><span class="sxs-lookup"><span data-stu-id="8827c-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="8827c-133">注册密钥会在初始注册过程中充当由客户端用于请求服务器的共享密钥。</span><span class="sxs-lookup"><span data-stu-id="8827c-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="8827c-134">注册成功完成之后，客户端会生成用于唯一地向请求服务器进行身份验证的自签名证书。</span><span class="sxs-lookup"><span data-stu-id="8827c-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="8827c-135">此证书的指纹在本地进行存储，并与请求服务器的 URL 关联。</span><span class="sxs-lookup"><span data-stu-id="8827c-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="8827c-136">**注意**：PowerShell 4.0 中不支持注册密钥。</span><span class="sxs-lookup"><span data-stu-id="8827c-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="8827c-137">为了配置节点以便向请求服务器进行身份验证，注册密钥需要处于将向此请求服务器注册的任何目标节点的元配置中。</span><span class="sxs-lookup"><span data-stu-id="8827c-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="8827c-138">请注意，以下元配置中的 **RegistrationKey** 会在目标计算机成功注册之后删除，并且值“140a952b-b9d6-406b-b416-e0f759c9c0e4”必须与请求服务器上的 RegistrationKeys.txt 文件中存储的值匹配。</span><span class="sxs-lookup"><span data-stu-id="8827c-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="8827c-139">请始终安全地处理注册密钥值，因为知道它便可以向请求服务器注册任何目标计算机。</span><span class="sxs-lookup"><span data-stu-id="8827c-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }
        
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }   
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> <span data-ttu-id="8827c-140">**注意**：**ReportServerWeb** 部分允许将报表数据发送到请求服务器。</span><span class="sxs-lookup"><span data-stu-id="8827c-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="8827c-141">元配置文件中缺少 **ConfigurationID** 属性暗示请求服务器支持 V2 版本的请求服务器协议，因此需要初始注册。</span><span class="sxs-lookup"><span data-stu-id="8827c-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="8827c-142">相反，存在 **ConfigurationID** 意味着使用 V1 版本的请求服务器协议，不会进行注册处理。</span><span class="sxs-lookup"><span data-stu-id="8827c-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="8827c-143">**注意**：在推送方案中，当前版本中存在一个 bug，因此需要在元配置文件中为绝不会向请求服务器注册的节点定义 ConfigurationID 属性。</span><span class="sxs-lookup"><span data-stu-id="8827c-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="8827c-144">这会强制使用 V1 请求服务器协议，避免注册失败消息。</span><span class="sxs-lookup"><span data-stu-id="8827c-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="8827c-145">放置配置和资源</span><span class="sxs-lookup"><span data-stu-id="8827c-145">Placing configurations and resources</span></span>

<span data-ttu-id="8827c-146">请求服务器设置完成之后，在请求服务器配置中通过 **ConfigurationPath** 和 **ModulePath** 属性定义的文件夹是用于放置可供目标节点请求的模块和配置的位置。</span><span class="sxs-lookup"><span data-stu-id="8827c-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="8827c-147">这些文件需要采用特定格式，以便请求服务器可正确处理它们。</span><span class="sxs-lookup"><span data-stu-id="8827c-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="8827c-148">DSC 资源模块程序包格式</span><span class="sxs-lookup"><span data-stu-id="8827c-148">DSC resource module package format</span></span>

<span data-ttu-id="8827c-149">每个资源模块都需要进行压缩并按照 `{Module Name}_{Module Version}.zip` 模式进行命名。</span><span class="sxs-lookup"><span data-stu-id="8827c-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="8827c-150">例如，一个名为 xWebAdminstration 并且模块版本为 3.1.2.0 的模块会命名为“xWebAdministration_3.2.1.0.zip”。</span><span class="sxs-lookup"><span data-stu-id="8827c-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="8827c-151">每个版本的模块都必须包含在单个 zip 文件中。</span><span class="sxs-lookup"><span data-stu-id="8827c-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="8827c-152">由于每个 zip 文件中只有单个版本的资源，因此不支持在 WMF 5.0 中添加的可在单个目录中支持多个模块版本的模块格式。</span><span class="sxs-lookup"><span data-stu-id="8827c-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="8827c-153">这意味着在打包 DSC 资源模块以便用于请求服务器之前，需要对目录结构进行少量更改。</span><span class="sxs-lookup"><span data-stu-id="8827c-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="8827c-154">WMF 5.0 中包含 DSC 资源的模块默认格式是 {Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'。</span><span class="sxs-lookup"><span data-stu-id="8827c-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="8827c-155">为请求服务器进行打包之前，只需删除 **{Module version}** 文件夹，以便路径成为 {Module Folder}\DscResources\{DSC Resource Folder}\'。</span><span class="sxs-lookup"><span data-stu-id="8827c-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="8827c-156">进行此更改之后，按上文所述压缩文件夹，并将这些 zip 文件置于 **ModulePath** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8827c-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="8827c-157">使用 `new-dscchecksum {module zip file}` 可为新添加的模块创建校验和文件。</span><span class="sxs-lookup"><span data-stu-id="8827c-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="8827c-158">配置 MOF 格式</span><span class="sxs-lookup"><span data-stu-id="8827c-158">Configuration MOF format</span></span> 
<span data-ttu-id="8827c-159">配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。</span><span class="sxs-lookup"><span data-stu-id="8827c-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="8827c-160">若要创建校验和，请调用 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8827c-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="8827c-161">该 cmdlet 将接受 **Path** 参数，该参数指定了配置 MOF 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8827c-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="8827c-162">该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="8827c-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="8827c-163">如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。</span><span class="sxs-lookup"><span data-stu-id="8827c-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="8827c-164">将 MOF 文件及其关联校验和文件置于 **ConfigurationPath** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8827c-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="8827c-165">**注意**：如果以任何方式更改配置 MOF 文件，则还必须重新创建校验和文件。</span><span class="sxs-lookup"><span data-stu-id="8827c-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="8827c-166">工具</span><span class="sxs-lookup"><span data-stu-id="8827c-166">Tooling</span></span>
<span data-ttu-id="8827c-167">为了使请求服务器的设置、验证和管理更加容易，以下工具作为示例包含在最新版本的 xPSDesiredStateConfiguration 模块中：</span><span class="sxs-lookup"><span data-stu-id="8827c-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="8827c-168">该模块有助于打包 DSC 资源模块和配置文件以便在请求服务器上使用。</span><span class="sxs-lookup"><span data-stu-id="8827c-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="8827c-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="8827c-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="8827c-170">以下示例：</span><span class="sxs-lookup"><span data-stu-id="8827c-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="8827c-171">验证请求服务器是否配置正确的脚本。</span><span class="sxs-lookup"><span data-stu-id="8827c-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="8827c-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="8827c-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="8827c-173">请求客户端配置</span><span class="sxs-lookup"><span data-stu-id="8827c-173">Pull client configuration</span></span> 
<span data-ttu-id="8827c-174">以下主题详细描述了如何设置请求客户端：</span><span class="sxs-lookup"><span data-stu-id="8827c-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="8827c-175">使用配置 ID 设置 DSC 请求客户端</span><span class="sxs-lookup"><span data-stu-id="8827c-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="8827c-176">使用配置名称设置 DSC 请求客户端</span><span class="sxs-lookup"><span data-stu-id="8827c-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="8827c-177">部分配置</span><span class="sxs-lookup"><span data-stu-id="8827c-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="8827c-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8827c-178">See also</span></span>
* [<span data-ttu-id="8827c-179">Windows PowerShell Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="8827c-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="8827c-180">执行配置</span><span class="sxs-lookup"><span data-stu-id="8827c-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="8827c-181">使用 DSC 报表服务器</span><span class="sxs-lookup"><span data-stu-id="8827c-181">Using a DSC report server</span></span>](reportServer.md)


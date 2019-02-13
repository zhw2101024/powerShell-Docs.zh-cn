---
ms.date: 04/11/2018
keywords: dsc,powershell,配置,安装程序
title: 设置 DSC SMB 请求服务器
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676185"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="7a52d-103">设置 DSC SMB 请求服务器</span><span class="sxs-lookup"><span data-stu-id="7a52d-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="7a52d-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7a52d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a52d-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。</span><span class="sxs-lookup"><span data-stu-id="7a52d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="7a52d-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="7a52d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="7a52d-107">DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) 请求服务器是计算机托管 SMB 文件共享，可在目标节点提出请求时向它们提供 DSC 配置文件和 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="7a52d-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="7a52d-108">若要将 SMB 请求服务器用于 DSC，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7a52d-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="7a52d-109">在运行 PowerShell 4.0 或更高版本的服务器上设置一个 SMB 文件共享</span><span class="sxs-lookup"><span data-stu-id="7a52d-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="7a52d-110">配置运行 PowerShell 4.0 或更高版本的客户端以从该 SMB 共享进行请求</span><span class="sxs-lookup"><span data-stu-id="7a52d-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="7a52d-111">使用 xSmbShare 资源创建 SMB 文件共享</span><span class="sxs-lookup"><span data-stu-id="7a52d-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="7a52d-112">可通过多种方法来设置 SMB 文件共享，不过我们来了解一下如何使用 DSC 来实现此目标。</span><span class="sxs-lookup"><span data-stu-id="7a52d-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="7a52d-113">安装 xSmbShare 资源</span><span class="sxs-lookup"><span data-stu-id="7a52d-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="7a52d-114">调用 [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet 可以安装 **xSmbShare** 模块。</span><span class="sxs-lookup"><span data-stu-id="7a52d-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="7a52d-115">`Install-Module` 包含在 PowerShellGet 模块中，后者纳入 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="7a52d-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="7a52d-116">可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="7a52d-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="7a52d-117">**xSmbShare** 包含 DSC 资源 **xSmbShare**，后者可用于创建 SMB 文件共享。</span><span class="sxs-lookup"><span data-stu-id="7a52d-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="7a52d-118">创建目录和文件共享</span><span class="sxs-lookup"><span data-stu-id="7a52d-118">Create the directory and file share</span></span>

<span data-ttu-id="7a52d-119">下面的配置使用 **File** 资源创建共享目录，并使用 **xSmbShare** 资源创建 SMB 共享：</span><span class="sxs-lookup"><span data-stu-id="7a52d-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="7a52d-120">此配置会创建该目录`C:\DscSmbShare`，如果它尚不存在，然后将该目录用作 SMB 文件共享。</span><span class="sxs-lookup"><span data-stu-id="7a52d-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="7a52d-121">**FullAccess**应授予给任何需要写入或从文件共享中删除的帐户。</span><span class="sxs-lookup"><span data-stu-id="7a52d-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="7a52d-122">**ReadAccess**必须授予给所有从共享获取配置和/或 DSC 资源的客户端节点。</span><span class="sxs-lookup"><span data-stu-id="7a52d-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="7a52d-123">DSC 以系统帐户默认运行，因此计算机本身必须有权访问共享。</span><span class="sxs-lookup"><span data-stu-id="7a52d-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="7a52d-124">向请求客户端授予文件系统访问权限</span><span class="sxs-lookup"><span data-stu-id="7a52d-124">Give file system access to the pull client</span></span>

<span data-ttu-id="7a52d-125">向客户端节点授予 **ReadAccess** 可允许该节点访问 SMB 共享，但不允许其访问此共享中的文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="7a52d-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="7a52d-126">你必须显式授予客户端节点访问 SMB 共享文件夹和子文件夹。</span><span class="sxs-lookup"><span data-stu-id="7a52d-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="7a52d-127">我们可以使用 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 模块中包含的 **cNtfsPermissionEntry** 资源进行添加，对 DSC 执行此操作。</span><span class="sxs-lookup"><span data-stu-id="7a52d-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="7a52d-128">下面的配置添加了 **cNtfsPermissionEntry** 块，用于向请求客户端授予 ReadAndExecute 访问权限：</span><span class="sxs-lookup"><span data-stu-id="7a52d-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="7a52d-129">放置配置和资源</span><span class="sxs-lookup"><span data-stu-id="7a52d-129">Placing configurations and resources</span></span>

<span data-ttu-id="7a52d-130">将希望客户端节点请求的所有配置 MOF 文件和/或 DSC 资源保存在 SMB 共享文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7a52d-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="7a52d-131">所有配置 MOF 文件都必须命名为 *ConfigurationID*.mof，其中 *ConfigurationID* 是目标节点的 LCM 的 **ConfigurationID** 属性值。</span><span class="sxs-lookup"><span data-stu-id="7a52d-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="7a52d-132">若要详细了解如何设置请求客户端，请参阅[使用配置 ID 设置请求客户端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="7a52d-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7a52d-133">如果你使用的是 SMB 请求服务器，则必须使用配置 ID。</span><span class="sxs-lookup"><span data-stu-id="7a52d-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="7a52d-134">SMB 不支持配置名称。</span><span class="sxs-lookup"><span data-stu-id="7a52d-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="7a52d-135">每个资源模块都需要进行压缩并按照 `{Module Name}_{Module Version}.zip` 模式进行命名。</span><span class="sxs-lookup"><span data-stu-id="7a52d-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="7a52d-136">例如，一个名为 xWebAdminstration 并且模块版本为 3.1.2.0 的模块会命名为“xWebAdministration_3.2.1.0.zip”。</span><span class="sxs-lookup"><span data-stu-id="7a52d-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="7a52d-137">每个版本的模块都必须包含在单个 zip 文件中。</span><span class="sxs-lookup"><span data-stu-id="7a52d-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="7a52d-138">不支持单独的 zip 文件中的模块的版本。</span><span class="sxs-lookup"><span data-stu-id="7a52d-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="7a52d-139">在打包 DSC 资源模块以便用于请求服务器之前, 需要对目录结构进行少量更改。</span><span class="sxs-lookup"><span data-stu-id="7a52d-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="7a52d-140">包含 WMF 5.0 中 DSC 资源的模块的默认格式为 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`。</span><span class="sxs-lookup"><span data-stu-id="7a52d-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="7a52d-141">为请求服务器打包前，只需删除 `{Module version}` 文件夹，以使路径变为 `{Module Folder}\DscResources\{DSC Resource Folder}\`。</span><span class="sxs-lookup"><span data-stu-id="7a52d-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="7a52d-142">进行此更改之后，按上文所述压缩文件夹，并将这些 zip 文件置于 SMB 共享文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7a52d-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="7a52d-143">创建 MOF 校验和</span><span class="sxs-lookup"><span data-stu-id="7a52d-143">Creating the MOF checksum</span></span>

<span data-ttu-id="7a52d-144">配置 MOF 文件需要与校验和文件配对，以使目标节点上的 LCM 可以验证配置。</span><span class="sxs-lookup"><span data-stu-id="7a52d-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="7a52d-145">若要创建校验和，请调用 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a52d-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="7a52d-146">该 cmdlet 将采用 `Path` 参数，指定配置 MOF 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7a52d-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="7a52d-147">该 cmdlet 将创建名为 `ConfigurationMOFName.mof.checksum` 的校验和文件，其中 `ConfigurationMOFName` 是配置 mof 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="7a52d-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="7a52d-148">如果指定文件夹中存在多个配置 MOF 文件，则将为该文件夹中的每个配置分别创建校验和。</span><span class="sxs-lookup"><span data-stu-id="7a52d-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="7a52d-149">校验和文件与配置 MOF 文件必须位于同一目录中（默认为 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`）且具有相同名称（校验文件附加有 `.checksum` 扩展名）。</span><span class="sxs-lookup"><span data-stu-id="7a52d-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="7a52d-150">如果以任何方式更改配置 MOF 文件，则还必须重新创建校验和文件。</span><span class="sxs-lookup"><span data-stu-id="7a52d-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="7a52d-151">设置 SMB 请求客户端</span><span class="sxs-lookup"><span data-stu-id="7a52d-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="7a52d-152">若要设置从 SMB 共享请求获取配置和/或资源的客户端，可使用指定从哪个共享中请求获取配置和 DSC 资源的 **ConfigurationRepositoryShare** 和 **ResourceRepositoryShare** 代码块，配置客户端的本地配置管理器 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="7a52d-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="7a52d-153">有关配置 LCM 的详细信息，请参阅[使用配置 ID 设置请求客户端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="7a52d-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7a52d-154">为简单起见，此示例使用 PSDscAllowPlainTextPassword，以允许将明文密码传递到 Credential 参数。</span><span class="sxs-lookup"><span data-stu-id="7a52d-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="7a52d-155">有关更安全传递凭据的信息，请参阅[配置数据中的凭据选项](../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="7a52d-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="7a52d-156">即使仅请求资源，也必须在 SMB 请求服务器的 metaconfiguration“设置”块中指定“ConfigurationID”。</span><span class="sxs-lookup"><span data-stu-id="7a52d-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a><span data-ttu-id="7a52d-157">致谢</span><span class="sxs-lookup"><span data-stu-id="7a52d-157">Acknowledgements</span></span>

<span data-ttu-id="7a52d-158">特别感谢下列人员：</span><span class="sxs-lookup"><span data-stu-id="7a52d-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="7a52d-159">Mike F. Robbins，其有关将 SMB 用于 DSC 的文章帮助告知本主题中的内容。</span><span class="sxs-lookup"><span data-stu-id="7a52d-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="7a52d-160">他的博客是 [Mike F Robbins](http://mikefrobbins.com/)。</span><span class="sxs-lookup"><span data-stu-id="7a52d-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="7a52d-161">Serge Nikalaichyk，他是 **cNtfsAccessControl** 模块的作者。</span><span class="sxs-lookup"><span data-stu-id="7a52d-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="7a52d-162">此模块的来源位于 [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl)。</span><span class="sxs-lookup"><span data-stu-id="7a52d-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a52d-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a52d-163">See also</span></span>

[<span data-ttu-id="7a52d-164">Windows PowerShell Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="7a52d-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="7a52d-165">执行配置</span><span class="sxs-lookup"><span data-stu-id="7a52d-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="7a52d-166">使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="7a52d-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 发布到拉取服务器使用配置 Id (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400420"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="01208-103">发布到拉取服务器使用配置 Id (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="01208-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="01208-104">以下各节假定您已设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="01208-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="01208-105">如果不设置拉取服务器，则可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="01208-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="01208-106">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="01208-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="01208-107">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="01208-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="01208-108">每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。</span><span class="sxs-lookup"><span data-stu-id="01208-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="01208-109">本文将演示如何上传的资源，以便它们可供下载，并配置客户端会自动下载资源。</span><span class="sxs-lookup"><span data-stu-id="01208-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="01208-110">当该节点的收到的已分配的配置，通过**拉取**或**推送**(v5)，则会自动下载所需的 LCM 中指定的位置中的配置的任何资源。</span><span class="sxs-lookup"><span data-stu-id="01208-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="01208-111">编译配置</span><span class="sxs-lookup"><span data-stu-id="01208-111">Compile Configurations</span></span>

<span data-ttu-id="01208-112">存储的第一步[配置](../configurations/configurations.md)拉取服务器上，将其编译为".mof"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="01208-113">若要进行配置，泛型类型，并适用于多个客户端，使用`localhost`节点块中。</span><span class="sxs-lookup"><span data-stu-id="01208-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="01208-114">下面的示例演示使用的配置 shell`localhost`而不是特定的客户端名称。</span><span class="sxs-lookup"><span data-stu-id="01208-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="01208-115">编译通用配置后，您应该有"localhost.mof"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="01208-116">重命名的 MOF 文件</span><span class="sxs-lookup"><span data-stu-id="01208-116">Renaming the MOF file</span></span>

<span data-ttu-id="01208-117">可以存储在通过拉服务器配置".mof"文件**ConfigurationName**或**ConfigurationID**。</span><span class="sxs-lookup"><span data-stu-id="01208-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="01208-118">根据您计划如何设置请求客户端，您可以选择下面正确重命名已编译".mof"文件的一个章节。</span><span class="sxs-lookup"><span data-stu-id="01208-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="01208-119">配置 Id (GUID)</span><span class="sxs-lookup"><span data-stu-id="01208-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="01208-120">将需要重命名为"localhost.mof"文件"<GUID>.mof"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="01208-121">您可以创建一个随机**Guid**使用的示例，或通过使用[新建 Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01208-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="01208-122">示例输出</span><span class="sxs-lookup"><span data-stu-id="01208-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="01208-123">然后可以重命名你使用任何可接受的方法的".mof"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="01208-124">以下示例中，使用[重命名项](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01208-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="01208-125">有关使用详细信息**Guid**在环境中，请参阅[规划 Guid](/powershell/dsc/secureserver#guids)。</span><span class="sxs-lookup"><span data-stu-id="01208-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="01208-126">配置名称</span><span class="sxs-lookup"><span data-stu-id="01208-126">Configuration Names</span></span>

<span data-ttu-id="01208-127">将需要重命名为"localhost.mof"文件"<Configuration Name>.mof"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="01208-128">在以下示例中，使用上一节中的配置名称。</span><span class="sxs-lookup"><span data-stu-id="01208-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="01208-129">然后可以重命名你使用任何可接受的方法的".mof"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="01208-130">以下示例中，使用[重命名项](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01208-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="01208-131">创建校验和</span><span class="sxs-lookup"><span data-stu-id="01208-131">Create the CheckSum</span></span>

<span data-ttu-id="01208-132">每个".mof"文件存储在请求服务器或 SMB 共享上需要有一个关联".checksum"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="01208-133">此文件可让客户端知道当关联".mof"文件已更改，应重新下载。</span><span class="sxs-lookup"><span data-stu-id="01208-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="01208-134">您可以创建**CheckSum**与[New-dscchecksum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01208-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="01208-135">您还可以运行`New-DSCCheckSum`针对使用的文件的目录`-Path`参数。</span><span class="sxs-lookup"><span data-stu-id="01208-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="01208-136">如果已存在校验和，可以强制它重新创建与`-Force`参数。</span><span class="sxs-lookup"><span data-stu-id="01208-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="01208-137">以下示例指定一个包含上一节中的".mof"文件的目录，并使用`-Force`参数。</span><span class="sxs-lookup"><span data-stu-id="01208-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="01208-138">将显示任何输出，但是现在应看到"<GUID or Configuration Name>。 mof.checksum"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="01208-139">MOF 文件和校验和的存储位置</span><span class="sxs-lookup"><span data-stu-id="01208-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="01208-140">DSC HTTP 请求服务器上</span><span class="sxs-lookup"><span data-stu-id="01208-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="01208-141">当您设置在 HTTP 请求服务器，如中所述[设置 DSC HTTP 请求服务器](pullServer.md)，指定的目录**ModulePath**并**ConfigurationPath**密钥。</span><span class="sxs-lookup"><span data-stu-id="01208-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="01208-142">**ConfigurationPath**键指示应在其中存储的任何".mof"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="01208-143">**ConfigurationPath**指示应在其中存储的任何".mof"文件和".checksum"文件。</span><span class="sxs-lookup"><span data-stu-id="01208-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="01208-144">在 SMB 共享</span><span class="sxs-lookup"><span data-stu-id="01208-144">On an SMB Share</span></span>

<span data-ttu-id="01208-145">如果您设置了请求的客户端使用 SMB 共享，指定**ConfigurationRepositoryShare**。</span><span class="sxs-lookup"><span data-stu-id="01208-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="01208-146">所有".mof"文件和".checksum"文件然后应存储在**SourcePath**目录从**ConfigurationRepositoryShare**块。</span><span class="sxs-lookup"><span data-stu-id="01208-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="01208-147">后续步骤</span><span class="sxs-lookup"><span data-stu-id="01208-147">Next Steps</span></span>

<span data-ttu-id="01208-148">接下来，想要配置请求客户端请求指定的配置。</span><span class="sxs-lookup"><span data-stu-id="01208-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="01208-149">有关详细信息，请参阅以下指南：</span><span class="sxs-lookup"><span data-stu-id="01208-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="01208-150">设置请求客户端使用配置 Id (v4)</span><span class="sxs-lookup"><span data-stu-id="01208-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="01208-151">设置请求客户端使用配置 Id (v5)</span><span class="sxs-lookup"><span data-stu-id="01208-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="01208-152">设置请求客户端使用配置名称 (v5)</span><span class="sxs-lookup"><span data-stu-id="01208-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="01208-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01208-153">See also</span></span>

- [<span data-ttu-id="01208-154">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="01208-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="01208-155">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="01208-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="01208-156">包和上传到请求服务器的资源</span><span class="sxs-lookup"><span data-stu-id="01208-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)

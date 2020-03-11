---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 打包资源并将其上传到拉取服务器
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278489"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="14c65-103">打包资源并将其上传到拉取服务器</span><span class="sxs-lookup"><span data-stu-id="14c65-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="14c65-104">以下部分假定你已设置拉取服务器。</span><span class="sxs-lookup"><span data-stu-id="14c65-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="14c65-105">如果尚未设置拉取服务器，则可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="14c65-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="14c65-106">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="14c65-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="14c65-107">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="14c65-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="14c65-108">每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。</span><span class="sxs-lookup"><span data-stu-id="14c65-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="14c65-109">本文将演示如何上传资源以便下载，以及如何将客户端配置为自动下载资源。</span><span class="sxs-lookup"><span data-stu-id="14c65-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="14c65-110">当节点通过“拉取”  或“推送”  (v5) 接收已分配的配置时，将从 LCM 中指定的位置自动下载配置所需的任何资源。</span><span class="sxs-lookup"><span data-stu-id="14c65-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="14c65-111">包资源模块</span><span class="sxs-lookup"><span data-stu-id="14c65-111">Package Resource Modules</span></span>

<span data-ttu-id="14c65-112">可供客户端下载的每个资源必须存储在“.zip”文件中。</span><span class="sxs-lookup"><span data-stu-id="14c65-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="14c65-113">下面的示例将显示使用 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) 资源所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="14c65-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="14c65-114">如果有任何使用 PowerShell 4.0 的客户端，则将需要展开资源文件夹结构并删除任何版本的文件夹。</span><span class="sxs-lookup"><span data-stu-id="14c65-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="14c65-115">有关详细信息，请参阅[多个资源版本](../configurations/import-dscresource.md#multiple-resource-versions)。</span><span class="sxs-lookup"><span data-stu-id="14c65-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="14c65-116">可以使用喜欢的任何实用工具、脚本或方法压缩资源目录。</span><span class="sxs-lookup"><span data-stu-id="14c65-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="14c65-117">在 Windows 中，可以  右键单击“xPSDesiredStateConfiguration”目录，然后依次选择“发送到”和“压缩文件夹”。</span><span class="sxs-lookup"><span data-stu-id="14c65-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![右键单击](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="14c65-119">命名资源存档</span><span class="sxs-lookup"><span data-stu-id="14c65-119">Naming the Resource Archive</span></span>

<span data-ttu-id="14c65-120">资源存档需要采用以下格式命名：</span><span class="sxs-lookup"><span data-stu-id="14c65-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="14c65-121">在上面的示例中，“xPSDesiredStateConfiguration.zip”应重命名为“xPSDesiredStateConfiguration_8.4.4.0.zip”。</span><span class="sxs-lookup"><span data-stu-id="14c65-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="14c65-122">创建校验和</span><span class="sxs-lookup"><span data-stu-id="14c65-122">Create CheckSums</span></span>

<span data-ttu-id="14c65-123">压缩并重命名资源模块后，需要创建校验和  。</span><span class="sxs-lookup"><span data-stu-id="14c65-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="14c65-124">客户端上的 LCM 使用校验和  来确定该资源是否已更改，以及是否需要重新下载。</span><span class="sxs-lookup"><span data-stu-id="14c65-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="14c65-125">可以使用 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet 创建校验和  ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="14c65-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="14c65-126">不会显示任何输出，但现在应看到“xPSDesiredStateConfiguration_8.4.4.0.zip.checksum”。</span><span class="sxs-lookup"><span data-stu-id="14c65-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="14c65-127">也可以使用 `-Path` 参数对文件的目录运行 `New-DSCCheckSum`。</span><span class="sxs-lookup"><span data-stu-id="14c65-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="14c65-128">如果校验和已存在，则可以强制使用 `-Force` 参数重新创建校验和。</span><span class="sxs-lookup"><span data-stu-id="14c65-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="14c65-129">存储资源存档的位置</span><span class="sxs-lookup"><span data-stu-id="14c65-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="14c65-130">在 DSC HTTP 拉取服务器上</span><span class="sxs-lookup"><span data-stu-id="14c65-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="14c65-131">当按照[设置 DSC HTTP 拉取服务器](pullServer.md)中所述设置 HTTP 拉取服务器时，指定 ModulePath  和 ConfigurationPath  键的目录。</span><span class="sxs-lookup"><span data-stu-id="14c65-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="14c65-132">ConfigurationPath  键指示应存储任何“.mof”文件的位置。</span><span class="sxs-lookup"><span data-stu-id="14c65-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="14c65-133">ModulePath  键指示应存储任何 DSC 资源模块的位置。</span><span class="sxs-lookup"><span data-stu-id="14c65-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="14c65-134">在 SMB 共享上</span><span class="sxs-lookup"><span data-stu-id="14c65-134">On an SMB Share</span></span>

<span data-ttu-id="14c65-135">如果在设置拉取客户端时指定了 ResourceRepositoryShare  ，则将存档和校验和存储在 ResourceRepositoryShare  块的 SourcePath  目录中。</span><span class="sxs-lookup"><span data-stu-id="14c65-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="14c65-136">如果在设置拉取客户端时仅指定了 ConfigurationRepositoryShare  ，则将存档和校验和存储在 ConfigurationRepositoryShare  块的 SourcePath  目录中。</span><span class="sxs-lookup"><span data-stu-id="14c65-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="14c65-137">正在更新资源</span><span class="sxs-lookup"><span data-stu-id="14c65-137">Updating resources</span></span>

<span data-ttu-id="14c65-138">可以强制节点通过更改存档名称中的版本号或创建新的校验和来更新其资源。</span><span class="sxs-lookup"><span data-stu-id="14c65-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="14c65-139">拉取客户端将在 LCM 刷新后检查所需资源的较新版本，以及更新的校验和。</span><span class="sxs-lookup"><span data-stu-id="14c65-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="14c65-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14c65-140">See also</span></span>

- [<span data-ttu-id="14c65-141">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="14c65-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="14c65-142">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="14c65-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

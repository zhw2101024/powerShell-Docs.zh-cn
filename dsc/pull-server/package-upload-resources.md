---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 包和上传到请求服务器的资源
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400395"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="64fdd-103">包和上传到请求服务器的资源</span><span class="sxs-lookup"><span data-stu-id="64fdd-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="64fdd-104">以下各节假定您已设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="64fdd-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="64fdd-105">如果不设置拉取服务器，则可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="64fdd-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="64fdd-106">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="64fdd-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="64fdd-107">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="64fdd-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="64fdd-108">每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。</span><span class="sxs-lookup"><span data-stu-id="64fdd-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="64fdd-109">本文将演示如何上传的资源，以便它们可供下载，并配置客户端会自动下载资源。</span><span class="sxs-lookup"><span data-stu-id="64fdd-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="64fdd-110">当该节点的收到的已分配的配置，通过**拉取**或**推送**(v5)，则会自动下载所需的 LCM 中指定的位置中的配置的任何资源。</span><span class="sxs-lookup"><span data-stu-id="64fdd-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="64fdd-111">包资源模块</span><span class="sxs-lookup"><span data-stu-id="64fdd-111">Package Resource Modules</span></span>

<span data-ttu-id="64fdd-112">可用于客户端要下载每个资源必须存储在".zip"文件。</span><span class="sxs-lookup"><span data-stu-id="64fdd-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="64fdd-113">下面的示例将显示使用所需的步骤[xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0)资源。</span><span class="sxs-lookup"><span data-stu-id="64fdd-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="64fdd-114">如果必须使用 PowerShell 4.0 的任何客户端，需要 flaten 资源文件夹结构，并删除任何版本的文件夹。</span><span class="sxs-lookup"><span data-stu-id="64fdd-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="64fdd-115">有关详细信息，请参阅[多个资源版本](../configurations/import-dscresource.md#multiple-resource-versions)。</span><span class="sxs-lookup"><span data-stu-id="64fdd-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="64fdd-116">可以压缩使用任何实用程序、 脚本或您喜欢的方法的资源目录。</span><span class="sxs-lookup"><span data-stu-id="64fdd-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="64fdd-117">在 Windows 中，你可以*右键单击*"xPSDesiredStateConfiguration"目录，然后选择"发送到"，然后"压缩文件夹"。</span><span class="sxs-lookup"><span data-stu-id="64fdd-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![右键单击](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="64fdd-119">命名资源存档</span><span class="sxs-lookup"><span data-stu-id="64fdd-119">Naming the Resource Archive</span></span>

<span data-ttu-id="64fdd-120">资源存档需要具有以下格式命名：</span><span class="sxs-lookup"><span data-stu-id="64fdd-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="64fdd-121">在上面的示例中，"xPSDesiredStateConfiguration.zip"应为已重命名"xPSDesiredStateConfiguration_8.4.4.0.zip"。</span><span class="sxs-lookup"><span data-stu-id="64fdd-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="64fdd-122">创建校验和</span><span class="sxs-lookup"><span data-stu-id="64fdd-122">Create CheckSums</span></span>

<span data-ttu-id="64fdd-123">一旦已压缩并重命名的资源模块，需要创建**校验和**。</span><span class="sxs-lookup"><span data-stu-id="64fdd-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="64fdd-124">**校验和**使用，通过在客户端上的 LCM 以确定该资源已更改，以及是否需要再次下载。</span><span class="sxs-lookup"><span data-stu-id="64fdd-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="64fdd-125">您可以创建**CheckSum**与[New-dscchecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="64fdd-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="64fdd-126">将显示任何输出，但是现在应看到"xPSDesiredStateConfiguration_8.4.4.0.zip.checksum"。</span><span class="sxs-lookup"><span data-stu-id="64fdd-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="64fdd-127">您还可以运行`New-DSCCheckSum`针对使用的文件的目录`-Path`参数。</span><span class="sxs-lookup"><span data-stu-id="64fdd-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="64fdd-128">如果已存在校验和，可以强制它重新创建与`-Force`参数。</span><span class="sxs-lookup"><span data-stu-id="64fdd-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="64fdd-129">存储资源存档位置</span><span class="sxs-lookup"><span data-stu-id="64fdd-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="64fdd-130">DSC HTTP 请求服务器上</span><span class="sxs-lookup"><span data-stu-id="64fdd-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="64fdd-131">当您设置在 HTTP 请求服务器，如中所述[设置 DSC HTTP 请求服务器](pullServer.md)，指定的目录**ModulePath**并**ConfigurationPath**密钥。</span><span class="sxs-lookup"><span data-stu-id="64fdd-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="64fdd-132">**ConfigurationPath**键指示应在其中存储的任何".mof"文件。</span><span class="sxs-lookup"><span data-stu-id="64fdd-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="64fdd-133">**ModulePath**指示应在其中存储任何 DSC 资源模块。</span><span class="sxs-lookup"><span data-stu-id="64fdd-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="64fdd-134">在 SMB 共享</span><span class="sxs-lookup"><span data-stu-id="64fdd-134">On an SMB Share</span></span>

<span data-ttu-id="64fdd-135">如果指定了**ResourceRepositoryShare**，当您请求的客户端，设置存储存档和中的校验和时**SourcePath**目录从**ResourceRepositoryShare**块。</span><span class="sxs-lookup"><span data-stu-id="64fdd-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="64fdd-136">如果仅指定**ConfigurationRepositoryShare**，当您请求的客户端，设置存储存档和中的校验和时**SourcePath**目录从**ConfigurationRepositoryShare**块。</span><span class="sxs-lookup"><span data-stu-id="64fdd-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="64fdd-137">正在更新资源</span><span class="sxs-lookup"><span data-stu-id="64fdd-137">Updating resources</span></span>

<span data-ttu-id="64fdd-138">您可以强制的节点，以更新其资源通过更改存档文件的名称中的版本号或创建新的校验和。</span><span class="sxs-lookup"><span data-stu-id="64fdd-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="64fdd-139">请求客户端将检查所需资源的较新版本，以及更新校验和，请在其 LCM 刷新时。</span><span class="sxs-lookup"><span data-stu-id="64fdd-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="64fdd-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64fdd-140">See also</span></span>

- [<span data-ttu-id="64fdd-141">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="64fdd-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="64fdd-142">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="64fdd-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

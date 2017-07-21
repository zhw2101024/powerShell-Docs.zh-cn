---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_gettingstarted
ms.openlocfilehash: 6b2119a736cc428598c245526e5af970d86af998
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2017
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="8023b-103">PowerShell 库入门</span><span class="sxs-lookup"><span data-stu-id="8023b-103">Get Started with the PowerShell Gallery</span></span>

## <a name="what-is-the-powershell-gallery"></a><span data-ttu-id="8023b-104">PowerShell 库是什么？</span><span class="sxs-lookup"><span data-stu-id="8023b-104">What is the PowerShell Gallery?</span></span>

<span data-ttu-id="8023b-105">PowerShell 库是 PowerShell 内容的中心存储库。</span><span class="sxs-lookup"><span data-stu-id="8023b-105">The PowerShell Gallery is the central repository for PowerShell content.</span></span>
<span data-ttu-id="8023b-106">在 PowerShell 库中，可找到包含 PowerShell 命令和 Desired State Configuration (DSC) 资源的实用 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="8023b-106">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span> <span data-ttu-id="8023b-107">还可找到 PowerShell 脚本，其中一些脚本可能包含 PowerShell 工作流、概述任务组和提供这些任务的序列。</span><span class="sxs-lookup"><span data-stu-id="8023b-107">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span>
<span data-ttu-id="8023b-108">某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="8023b-108">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="requirements"></a><span data-ttu-id="8023b-109">要求</span><span class="sxs-lookup"><span data-stu-id="8023b-109">Requirements</span></span>

<span data-ttu-id="8023b-110">从 PowerShell 库将项下载到系统需要 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模块。</span><span class="sxs-lookup"><span data-stu-id="8023b-110">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module.</span></span> <span data-ttu-id="8023b-111">可在以下任何一项中找到 PowerShellGet 模块。</span><span class="sxs-lookup"><span data-stu-id="8023b-111">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="8023b-112">从 PowerShell 库下载项时无需登录。</span><span class="sxs-lookup"><span data-stu-id="8023b-112">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

-   [<span data-ttu-id="8023b-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8023b-113">Windows 10</span></span>](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [<span data-ttu-id="8023b-114">Windows Management Framework 5.0</span><span class="sxs-lookup"><span data-stu-id="8023b-114">Windows Management Framework 5.0</span></span>](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [<span data-ttu-id="8023b-115">MSI 安装程序（适用于 PowerShell 3 和 4）</span><span class="sxs-lookup"><span data-stu-id="8023b-115">MSI Installer (for PowerShell 3 and 4)</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="8023b-116">PowerShellGet 还需要 [NuGet 提供程序](http://go.microsoft.com/fwlink/?LinkId=722208)来运行 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="8023b-116">PowerShellGet also requires the [NuGet provider](http://go.microsoft.com/fwlink/?LinkId=722208) to work with the PowerShell Gallery.</span></span> <span data-ttu-id="8023b-117">如果 NuGet 提供程序未处于下列一个位置中，初次使用 PowerShellGet 时，系统会自动提示安装 NuGet 提供程序：</span><span class="sxs-lookup"><span data-stu-id="8023b-117">You will be prompted to install the NuGet provider automatically upon first use of PowerShellGet if the NuGet provider is not in one of the following locations:</span></span>

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

<span data-ttu-id="8023b-118">也可以运行 `Install-PackageProvider -Name NuGet -Force`，以自动下载和安装 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="8023b-118">Or, you can run `Install-PackageProvider -Name NuGet -Force` to automate the download and installation of the NuGet provider.</span></span>

  
<span data-ttu-id="8023b-119">如果 NuGet 版本低于 2.8.5.201，则需调用以下 PowerShell cmdlet 来安装并切换到 NuGet 最新版本。</span><span class="sxs-lookup"><span data-stu-id="8023b-119">If you have a version older than 2.8.5.201 of NuGet, you will need to call the following PowerShell cmdlets to install and switch to the latest version of NuGet.</span></span>

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  <span data-ttu-id="8023b-120">从以上安装位置删除旧版 NuGet。</span><span class="sxs-lookup"><span data-stu-id="8023b-120">Delete the older version of NuGet from the above installed location.</span></span>

<span data-ttu-id="8023b-121">有关详细信息，请参阅 <http://oneget.org/>。</span><span class="sxs-lookup"><span data-stu-id="8023b-121">For more information, see <http://oneget.org/> .</span></span>

  
<span data-ttu-id="8023b-122">注意：由于打包格式的更改，建议更新到最新版本的 PowerShellGet 和 PackageManagement 来安装最近已更新的项。</span><span class="sxs-lookup"><span data-stu-id="8023b-122">Note: Due to changes in packaging formats, we recommend you update to the latest version of PowerShellGet and PackageManagement to install items that have been updated recently.</span></span> <span data-ttu-id="8023b-123">PowerShellGet 包含在 Windows 10 中，可在[此处](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="8023b-123">PowerShellGet is included in Windows 10, which you can learn more about [here](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).</span></span>
<span data-ttu-id="8023b-124">PowerShellGet 也是 Windows Management Framework (WMF) 5.0 的一部分，可在[此处](http://go.microsoft.com/fwlink/?LinkId=398175)进行下载。</span><span class="sxs-lookup"><span data-stu-id="8023b-124">PowerShellGet is also part of the Windows Management Framework (WMF) 5.0, which you can download [here](http://go.microsoft.com/fwlink/?LinkId=398175).</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="8023b-125">从 PowerShell 库中发现项</span><span class="sxs-lookup"><span data-stu-id="8023b-125">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="8023b-126">可通过使用本网站上的“搜索”或浏览“模块和脚本”页查找 PowerShell 库中的项。</span><span class="sxs-lookup"><span data-stu-id="8023b-126">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="8023b-127">还可使用 `-Repository PSGallery` 运行 [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet（具体取决于项的类型），从而查找 PowerShell 库中的项。</span><span class="sxs-lookup"><span data-stu-id="8023b-127">You can also find items from the PowerShell Gallery by running the [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="8023b-128">可以使用 [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 的以下参数筛选库中结果</span><span class="sxs-lookup"><span data-stu-id="8023b-128">Filtering results from the Gallery can be done by using the following parameters of [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>

- <span data-ttu-id="8023b-129">名称</span><span class="sxs-lookup"><span data-stu-id="8023b-129">Name</span></span>
- <span data-ttu-id="8023b-130">AllVersions</span><span class="sxs-lookup"><span data-stu-id="8023b-130">AllVersions</span></span>
- <span data-ttu-id="8023b-131">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="8023b-131">MinimumVersion</span></span>
- <span data-ttu-id="8023b-132">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="8023b-132">RequiredVersion</span></span>
- <span data-ttu-id="8023b-133">标记</span><span class="sxs-lookup"><span data-stu-id="8023b-133">Tag</span></span>
- <span data-ttu-id="8023b-134">包括</span><span class="sxs-lookup"><span data-stu-id="8023b-134">Includes</span></span>
- <span data-ttu-id="8023b-135">DscResource</span><span class="sxs-lookup"><span data-stu-id="8023b-135">DscResource</span></span>
- <span data-ttu-id="8023b-136">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="8023b-136">RoleCapability</span></span>
- <span data-ttu-id="8023b-137">命令</span><span class="sxs-lookup"><span data-stu-id="8023b-137">Command</span></span>
- <span data-ttu-id="8023b-138">筛选</span><span class="sxs-lookup"><span data-stu-id="8023b-138">Filter</span></span>

<span data-ttu-id="8023b-139">如果只想发现库中的特定 DSC 资源，可运行 [**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8023b-139">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.</span></span>
<span data-ttu-id="8023b-140">[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 会返回库中所包含的 DSC 资源上的数据。</span><span class="sxs-lookup"><span data-stu-id="8023b-140">[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) returns data on DSC resources contained in the Gallery.</span></span> <span data-ttu-id="8023b-141">由于 DSC 资源始终作为模块的一部分进行传递，因此仍需要运行 [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 来安装这些 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="8023b-141">Because DSC resources are always delivered as part of a module, you still need to run [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="8023b-142">了解 PowerShell 库中的项</span><span class="sxs-lookup"><span data-stu-id="8023b-142">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="8023b-143">找到感兴趣的项后，你可能希望了解与其有关的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8023b-143">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="8023b-144">可检查库中该项的特定页来了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="8023b-144">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="8023b-145">在该页上可查看该项中上传的所有元数据。</span><span class="sxs-lookup"><span data-stu-id="8023b-145">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="8023b-146">项的元数据由项作者提供，Microsoft 不会进行验证。</span><span class="sxs-lookup"><span data-stu-id="8023b-146">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="8023b-147">项的所有者紧密关联到发布该项的 PowerShell 库帐户，比作者字段更可信。</span><span class="sxs-lookup"><span data-stu-id="8023b-147">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="8023b-148">如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。</span><span class="sxs-lookup"><span data-stu-id="8023b-148">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="8023b-149">如果运行的是 [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 或 [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)，可以在返回的 PSGetModuleInfo 对象中查看此数据。</span><span class="sxs-lookup"><span data-stu-id="8023b-149">If you're running [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) or [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="8023b-150">例如，运行 [**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 会返回库中 PSReadLine 模块上的数据。</span><span class="sxs-lookup"><span data-stu-id="8023b-150">For example, running [**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="8023b-151">从 PowerShell 库中下载项</span><span class="sxs-lookup"><span data-stu-id="8023b-151">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="8023b-152">从 PowerShell 库中下载项时，议使用下列过程：</span><span class="sxs-lookup"><span data-stu-id="8023b-152">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="8023b-153">检查</span><span class="sxs-lookup"><span data-stu-id="8023b-153">Inspect</span></span>

<span data-ttu-id="8023b-154">若要从库中下载项进行检查，请运行 [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 或 [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet，具体取决于项类型。</span><span class="sxs-lookup"><span data-stu-id="8023b-154">To download an item from the Gallery for inspection, run either the [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) or [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet, depending on the item type.</span></span> <span data-ttu-id="8023b-155">此操作可本地保存项而不进行安装，并且可以检查项内容。</span><span class="sxs-lookup"><span data-stu-id="8023b-155">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="8023b-156">请记得手动删除已保存的项。</span><span class="sxs-lookup"><span data-stu-id="8023b-156">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="8023b-157">某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="8023b-157">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span> <span data-ttu-id="8023b-158">Microsoft 建议安装前检查库中项的内容和代码。</span><span class="sxs-lookup"><span data-stu-id="8023b-158">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="8023b-159">如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。</span><span class="sxs-lookup"><span data-stu-id="8023b-159">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="8023b-160">安装</span><span class="sxs-lookup"><span data-stu-id="8023b-160">Install</span></span>

<span data-ttu-id="8023b-161">若要安装库中的项进行使用，请运行 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 或 [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet，具体取决于项类型。</span><span class="sxs-lookup"><span data-stu-id="8023b-161">To install an item from the Gallery for use, run either the [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) or [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet, depending on the item type.</span></span>

<span data-ttu-id="8023b-162">默认情况下，[Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 将模块安装到 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="8023b-162">[**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span> <span data-ttu-id="8023b-163">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="8023b-163">This requires an administrator account.</span></span> <span data-ttu-id="8023b-164">如果添加 `-Scope
CurrentUser` 参数，模块将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="8023b-164">If you add the `-Scope
CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="8023b-165">默认情况下，[Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 将脚本安装到 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="8023b-165">[**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span> <span data-ttu-id="8023b-166">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="8023b-166">This requires an administrator account.</span></span> <span data-ttu-id="8023b-167">如果添加 `-Scope
CurrentUser` 参数，脚本将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="8023b-167">If you add the `-Scope
CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="8023b-168">默认情况下，[Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 安装最新版项。</span><span class="sxs-lookup"><span data-stu-id="8023b-168">By default, [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installs the most current version of an item.</span></span> <span data-ttu-id="8023b-169">若要安装旧版项，请添加 `-RequiredVersion` 参数。</span><span class="sxs-lookup"><span data-stu-id="8023b-169">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="8023b-170">在来宾群集上部署</span><span class="sxs-lookup"><span data-stu-id="8023b-170">Deploy</span></span>

<span data-ttu-id="8023b-171">若要将项从 PowerShell 库部署到 Azure 自动化，请单击项详细信息页上的“部署到 Azure 自动化”。</span><span class="sxs-lookup"><span data-stu-id="8023b-171">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="8023b-172">这会将你重定向到 Azure 管理门户，在此可使用 Azure 帐户凭据登录。</span><span class="sxs-lookup"><span data-stu-id="8023b-172">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="8023b-173">请注意，部署具有依赖关系的项会将所有依赖关系部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="8023b-173">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="8023b-174">通过将 **AzureAutomationNotSupported** 标记添加到项元数据可禁用“部署到 Azure 自动化”按钮。</span><span class="sxs-lookup"><span data-stu-id="8023b-174">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="8023b-175">若要了解有关 Azure 自动化的详细信息，请参阅 [Azure 自动化网站](http://azure.microsoft.com/en-us/services/automation/)。</span><span class="sxs-lookup"><span data-stu-id="8023b-175">To learn more about Azure Automation, see the [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="8023b-176">更新来自 PowerShell 库中的项</span><span class="sxs-lookup"><span data-stu-id="8023b-176">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="8023b-177">若要更新从 PowerShell 库中安装的项，请运行 [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 或 [Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8023b-177">To update items installed from the PowerShell Gallery, run either the [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) or [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.</span></span> <span data-ttu-id="8023b-178">如果不使用其他任何参数运行，[Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 尝试通过运行 [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 来更新每个已安装的模块。</span><span class="sxs-lookup"><span data-stu-id="8023b-178">When run without any additional parameters, [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) attempts to update each module installed by running [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).</span></span>
<span data-ttu-id="8023b-179">若要选择性地更新模块，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="8023b-179">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="8023b-180">同样，如果不使用其他任何参数运行，[Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 也会尝试通过运行 [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 来更新每个已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="8023b-180">Similarly, when run without any additional parameters, [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) also attempts to update each script installed by running [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).</span></span>
<span data-ttu-id="8023b-181">若要选择性地更新脚本，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="8023b-181">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="8023b-182">列出从 PowerShell 库中安装的项</span><span class="sxs-lookup"><span data-stu-id="8023b-182">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="8023b-183">若要查找从 PowerShell 库中安装的模块，请运行 [**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8023b-183">To find out which modules you have installed from the PowerShell Gallery, run the [**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.</span></span> <span data-ttu-id="8023b-184">该命令会列出系统上所有已直接从 PowerShell 库安装的模块。</span><span class="sxs-lookup"><span data-stu-id="8023b-184">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="8023b-185">同样，若要查找从 PowerShell 库已安装的脚本，请运行 [**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8023b-185">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.</span></span> <span data-ttu-id="8023b-186">此命令会列出系统上所有已直接从 PowerShell 库安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="8023b-186">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>


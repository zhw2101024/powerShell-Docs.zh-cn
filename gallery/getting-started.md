---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: c3aafe9e76eda9acdd4787f63dc0f8c71a20d02a
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="3a32c-103">PowerShell 库入门</span><span class="sxs-lookup"><span data-stu-id="3a32c-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="3a32c-104">从 PowerShell 库将项下载到系统需要 [PowerShellGet](/powershell/module/powershellget) 模块。</span><span class="sxs-lookup"><span data-stu-id="3a32c-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="3a32c-105">可在以下任何一项中找到 PowerShellGet 模块。</span><span class="sxs-lookup"><span data-stu-id="3a32c-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="3a32c-106">从 PowerShell 库下载项时无需登录。</span><span class="sxs-lookup"><span data-stu-id="3a32c-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="3a32c-107">从 PowerShell 库中发现项</span><span class="sxs-lookup"><span data-stu-id="3a32c-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="3a32c-108">可通过使用本网站上的“搜索”或浏览“模块和脚本”页查找 PowerShell 库中的项。</span><span class="sxs-lookup"><span data-stu-id="3a32c-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="3a32c-109">还可以使用 `-Repository PSGallery` 运行 [Find-Module][] 和 [Find-Script][] cmdlet（具体视项类型而定），从而查找 PowerShell 库中的项。</span><span class="sxs-lookup"><span data-stu-id="3a32c-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="3a32c-110">可使用以下参数从库筛选结果：</span><span class="sxs-lookup"><span data-stu-id="3a32c-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="3a32c-111">名称</span><span class="sxs-lookup"><span data-stu-id="3a32c-111">Name</span></span>
- <span data-ttu-id="3a32c-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="3a32c-112">AllVersions</span></span>
- <span data-ttu-id="3a32c-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3a32c-113">MinimumVersion</span></span>
- <span data-ttu-id="3a32c-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3a32c-114">RequiredVersion</span></span>
- <span data-ttu-id="3a32c-115">标记</span><span class="sxs-lookup"><span data-stu-id="3a32c-115">Tag</span></span>
- <span data-ttu-id="3a32c-116">包括</span><span class="sxs-lookup"><span data-stu-id="3a32c-116">Includes</span></span>
- <span data-ttu-id="3a32c-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="3a32c-117">DscResource</span></span>
- <span data-ttu-id="3a32c-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="3a32c-118">RoleCapability</span></span>
- <span data-ttu-id="3a32c-119">命令</span><span class="sxs-lookup"><span data-stu-id="3a32c-119">Command</span></span>
- <span data-ttu-id="3a32c-120">筛选</span><span class="sxs-lookup"><span data-stu-id="3a32c-120">Filter</span></span>

<span data-ttu-id="3a32c-121">如果只想发现库中的特定 DSC 资源，可运行 [Find-DscResource] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a32c-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="3a32c-122">Find-DscResource 会返回库中 DSC 资源的相关数据。</span><span class="sxs-lookup"><span data-stu-id="3a32c-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="3a32c-123">由于 DSC 资源始终作为模块的部分进行传递，所以仍需运行 [Install-Module][] 来安装这些 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="3a32c-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="3a32c-124">了解 PowerShell 库中的项</span><span class="sxs-lookup"><span data-stu-id="3a32c-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="3a32c-125">找到感兴趣的项后，你可能希望了解与其有关的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3a32c-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="3a32c-126">可检查库中该项的特定页来了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="3a32c-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="3a32c-127">在该页上可查看该项中上传的所有元数据。</span><span class="sxs-lookup"><span data-stu-id="3a32c-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="3a32c-128">项的元数据由项作者提供，Microsoft 不会进行验证。</span><span class="sxs-lookup"><span data-stu-id="3a32c-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="3a32c-129">项的所有者紧密关联到发布该项的 PowerShell 库帐户，比作者字段更可信。</span><span class="sxs-lookup"><span data-stu-id="3a32c-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="3a32c-130">如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。</span><span class="sxs-lookup"><span data-stu-id="3a32c-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="3a32c-131">如果运行 [Find-Module][] 或 [Find-Script][]，则可在返回的 PSGetModuleInfo 对象中查看该数据。</span><span class="sxs-lookup"><span data-stu-id="3a32c-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="3a32c-132">例如，运行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` 会返回库中 PSReadLine 模块的相关数据。</span><span class="sxs-lookup"><span data-stu-id="3a32c-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="3a32c-133">从 PowerShell 库中下载项</span><span class="sxs-lookup"><span data-stu-id="3a32c-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="3a32c-134">从 PowerShell 库中下载项时，议使用下列过程：</span><span class="sxs-lookup"><span data-stu-id="3a32c-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="3a32c-135">检查</span><span class="sxs-lookup"><span data-stu-id="3a32c-135">Inspect</span></span>

<span data-ttu-id="3a32c-136">若要下载库中的项以供检查，请运行 [Save-Module][] 或 [Save-Script][] cmdlet，具体视项类型而定。</span><span class="sxs-lookup"><span data-stu-id="3a32c-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="3a32c-137">此操作可本地保存项而不进行安装，并且可以检查项内容。</span><span class="sxs-lookup"><span data-stu-id="3a32c-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="3a32c-138">请记得手动删除已保存的项。</span><span class="sxs-lookup"><span data-stu-id="3a32c-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="3a32c-139">某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="3a32c-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="3a32c-140">Microsoft 建议安装前检查库中项的内容和代码。</span><span class="sxs-lookup"><span data-stu-id="3a32c-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="3a32c-141">如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。</span><span class="sxs-lookup"><span data-stu-id="3a32c-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="3a32c-142">安装</span><span class="sxs-lookup"><span data-stu-id="3a32c-142">Install</span></span>

<span data-ttu-id="3a32c-143">若要安装库中的项以供使用，请运行 [Install-Module][] 或 [Install-Script][] cmdlet，具体视项类型而定。</span><span class="sxs-lookup"><span data-stu-id="3a32c-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="3a32c-144">默认情况下，[Install-Module][] 将模块安装到 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="3a32c-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="3a32c-145">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="3a32c-145">This requires an administrator account.</span></span> <span data-ttu-id="3a32c-146">如果添加 `-Scope CurrentUser` 参数，模块将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="3a32c-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="3a32c-147">默认情况下，[Install-Script][] 将脚本安装到 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="3a32c-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="3a32c-148">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="3a32c-148">This requires an administrator account.</span></span> <span data-ttu-id="3a32c-149">如果添加 `-Scope CurrentUser` 参数，脚本将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="3a32c-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="3a32c-150">默认情况下，[Install-Module][] 和 [Install-Script][] 安装项的最新版本。</span><span class="sxs-lookup"><span data-stu-id="3a32c-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="3a32c-151">若要安装旧版项，请添加 `-RequiredVersion` 参数。</span><span class="sxs-lookup"><span data-stu-id="3a32c-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="3a32c-152">在来宾群集上部署</span><span class="sxs-lookup"><span data-stu-id="3a32c-152">Deploy</span></span>

<span data-ttu-id="3a32c-153">若要将项从 PowerShell 库部署到 Azure 自动化，请单击项详细信息页上的“部署到 Azure 自动化”。</span><span class="sxs-lookup"><span data-stu-id="3a32c-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="3a32c-154">这会将你重定向到 Azure 管理门户，在此可使用 Azure 帐户凭据登录。</span><span class="sxs-lookup"><span data-stu-id="3a32c-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="3a32c-155">请注意，部署具有依赖关系的项会将所有依赖关系部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="3a32c-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="3a32c-156">通过将 **AzureAutomationNotSupported** 标记添加到项元数据可禁用“部署到 Azure 自动化”按钮。</span><span class="sxs-lookup"><span data-stu-id="3a32c-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="3a32c-157">若要了解有关 Azure 自动化的详细信息，请参阅 [Azure 自动化](/azure/automation)文档。</span><span class="sxs-lookup"><span data-stu-id="3a32c-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="3a32c-158">更新来自 PowerShell 库中的项</span><span class="sxs-lookup"><span data-stu-id="3a32c-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="3a32c-159">若要更新从 PowerShell 库中安装的项，请运行 [Update-Module][] 或 [Update-Script][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a32c-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="3a32c-160">如果不使用其他任何参数运行，[Update-Module][] 尝试通过运行 [Install-Module][] 来更新每个已安装的模块。</span><span class="sxs-lookup"><span data-stu-id="3a32c-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="3a32c-161">若要选择性地更新模块，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="3a32c-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="3a32c-162">同样，如果不使用其他任何参数运行，[Update-Script][] 也会尝试通过运行 [Install-Script][] 来更新每个已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="3a32c-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="3a32c-163">若要选择性地更新脚本，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="3a32c-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="3a32c-164">列出从 PowerShell 库中安装的项</span><span class="sxs-lookup"><span data-stu-id="3a32c-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="3a32c-165">若要确定已安装 PowerShell 库中的哪些模块，请运行 [Get-InstalledModule][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a32c-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="3a32c-166">该命令会列出系统上所有已直接从 PowerShell 库安装的模块。</span><span class="sxs-lookup"><span data-stu-id="3a32c-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="3a32c-167">同样，若要确定已安装 PowerShell 库中的哪些脚本，请运行 [Get-InstalledScript][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a32c-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="3a32c-168">此命令会列出系统上所有已直接从 PowerShell 库安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="3a32c-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
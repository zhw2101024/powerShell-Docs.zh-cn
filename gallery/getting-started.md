---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: PowerShell 库入门
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225669"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="e6efe-103">PowerShell 库入门</span><span class="sxs-lookup"><span data-stu-id="e6efe-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="e6efe-104">从 PowerShell 库安装包的正确方法是使用 [PowerShellGet](/powershell/module/powershellget) 模块中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6efe-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="e6efe-105">从 PowerShell 库下载项时无需登录。</span><span class="sxs-lookup"><span data-stu-id="e6efe-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="e6efe-106">可直接从 PowerShell 库下载包，但不推荐此方法。</span><span class="sxs-lookup"><span data-stu-id="e6efe-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="e6efe-107">有关详细信息，请参阅[手动包下载](/powershell/gallery/how-to/working-with-packages/manual-download)。</span><span class="sxs-lookup"><span data-stu-id="e6efe-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="e6efe-108">从 PowerShell 库中发现包</span><span class="sxs-lookup"><span data-stu-id="e6efe-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="e6efe-109">可通过使用本网站上的“搜索”控件或浏览“模块和脚本”页查找 PowerShell 库中的包。</span><span class="sxs-lookup"><span data-stu-id="e6efe-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="e6efe-110">还可以使用 `-Repository PSGallery` 运行 [Find-Module][] 和 [Find-Script][] cmdlet（具体视项类型而定），来查找 PowerShell 库中的包。</span><span class="sxs-lookup"><span data-stu-id="e6efe-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="e6efe-111">可使用以下参数从库筛选结果：</span><span class="sxs-lookup"><span data-stu-id="e6efe-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="e6efe-112">名称</span><span class="sxs-lookup"><span data-stu-id="e6efe-112">Name</span></span>
- <span data-ttu-id="e6efe-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="e6efe-113">AllVersions</span></span>
- <span data-ttu-id="e6efe-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e6efe-114">MinimumVersion</span></span>
- <span data-ttu-id="e6efe-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e6efe-115">RequiredVersion</span></span>
- <span data-ttu-id="e6efe-116">标记</span><span class="sxs-lookup"><span data-stu-id="e6efe-116">Tag</span></span>
- <span data-ttu-id="e6efe-117">包括</span><span class="sxs-lookup"><span data-stu-id="e6efe-117">Includes</span></span>
- <span data-ttu-id="e6efe-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="e6efe-118">DscResource</span></span>
- <span data-ttu-id="e6efe-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e6efe-119">RoleCapability</span></span>
- <span data-ttu-id="e6efe-120">Command</span><span class="sxs-lookup"><span data-stu-id="e6efe-120">Command</span></span>
- <span data-ttu-id="e6efe-121">筛选</span><span class="sxs-lookup"><span data-stu-id="e6efe-121">Filter</span></span>

<span data-ttu-id="e6efe-122">如果只想发现库中的特定 DSC 资源，可运行 [Find-DscResource] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6efe-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="e6efe-123">Find-DscResource 会返回库中 DSC 资源的相关数据。</span><span class="sxs-lookup"><span data-stu-id="e6efe-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="e6efe-124">由于 DSC 资源始终作为模块的部分进行传递，所以仍需运行 [Install-Module][] 来安装这些 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="e6efe-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="e6efe-125">了解 PowerShell 库中的包</span><span class="sxs-lookup"><span data-stu-id="e6efe-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="e6efe-126">找到感兴趣的包后，你可能想要了解更多有关信息。</span><span class="sxs-lookup"><span data-stu-id="e6efe-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="e6efe-127">可检查库中该包的特定页来了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="e6efe-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="e6efe-128">在该页上可查看该包中上载的所有元数据。</span><span class="sxs-lookup"><span data-stu-id="e6efe-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="e6efe-129">此元数据由包作者提供，Microsoft 不会对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="e6efe-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="e6efe-130">包的所有者紧密关联到用于发布该包的 PowerShell 库帐户，比“作者”字段更可信。</span><span class="sxs-lookup"><span data-stu-id="e6efe-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="e6efe-131">如果发现发布的包不可信，请单击该包页面上的“报告滥用行为”。</span><span class="sxs-lookup"><span data-stu-id="e6efe-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="e6efe-132">如果运行 [Find-Module][] 或 [Find-Script][]，则可在返回的 PSGetModuleInfo 对象中查看该数据。</span><span class="sxs-lookup"><span data-stu-id="e6efe-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="e6efe-133">例如，运行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="e6efe-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="e6efe-134">返回库中 PSReadLine 模块的数据。</span><span class="sxs-lookup"><span data-stu-id="e6efe-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="e6efe-135">从 PowerShell 库下载包</span><span class="sxs-lookup"><span data-stu-id="e6efe-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="e6efe-136">从 PowerShell 库下载包时，建议执行下列过程：</span><span class="sxs-lookup"><span data-stu-id="e6efe-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="e6efe-137">检查</span><span class="sxs-lookup"><span data-stu-id="e6efe-137">Inspect</span></span>

<span data-ttu-id="e6efe-138">若要下载库中的包以供检查，请运行 [Save-Module][] 或 [Save-Script][] cmdlet，具体视包类型而定。</span><span class="sxs-lookup"><span data-stu-id="e6efe-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="e6efe-139">此操作可本地保存包而不进行安装，并且可以检查包内容。</span><span class="sxs-lookup"><span data-stu-id="e6efe-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="e6efe-140">请记得手动删除已保存的包。</span><span class="sxs-lookup"><span data-stu-id="e6efe-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="e6efe-141">其中一些包由 Microsoft 编写，另一些包由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="e6efe-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="e6efe-142">Microsoft 建议安装前检查库中包的内容和代码。</span><span class="sxs-lookup"><span data-stu-id="e6efe-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="e6efe-143">如果发现发布的包不可信，请单击该包页面上的“报告滥用行为”。</span><span class="sxs-lookup"><span data-stu-id="e6efe-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="e6efe-144">安装</span><span class="sxs-lookup"><span data-stu-id="e6efe-144">Install</span></span>

<span data-ttu-id="e6efe-145">若要安装库中的包以供使用，请运行 [Install-Module][] 或 [Install-Script][] cmdlet，具体视包类型而定。</span><span class="sxs-lookup"><span data-stu-id="e6efe-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="e6efe-146">默认情况下，[Install-Module][] 将模块安装到 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="e6efe-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="e6efe-147">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="e6efe-147">This requires an administrator account.</span></span> <span data-ttu-id="e6efe-148">如果添加 `-Scope CurrentUser` 参数，模块将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="e6efe-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="e6efe-149">默认情况下，[Install-Script][] 将脚本安装到 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="e6efe-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="e6efe-150">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="e6efe-150">This requires an administrator account.</span></span> <span data-ttu-id="e6efe-151">如果添加 `-Scope CurrentUser` 参数，脚本将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="e6efe-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="e6efe-152">默认情况下，[Install-Module][] 和 [Install-Script][] 安装最新版包。</span><span class="sxs-lookup"><span data-stu-id="e6efe-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="e6efe-153">若要安装旧版包，请添加 `-RequiredVersion` 参数。</span><span class="sxs-lookup"><span data-stu-id="e6efe-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="e6efe-154">在来宾群集上部署</span><span class="sxs-lookup"><span data-stu-id="e6efe-154">Deploy</span></span>

<span data-ttu-id="e6efe-155">若要将包从 PowerShell 库部署到 Azure 自动化，请单击包详细信息页上的“部署到 Azure 自动化”。</span><span class="sxs-lookup"><span data-stu-id="e6efe-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="e6efe-156">这会将你重定向到 Azure 管理门户，可使用 Azure 帐户凭据登录该门户。</span><span class="sxs-lookup"><span data-stu-id="e6efe-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="e6efe-157">请注意，部署具有依赖关系的包会将所有依赖关系部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="e6efe-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="e6efe-158">通过将 AzureAutomationNotSupported 标记添加到包元数据可禁用“部署到 Azure 自动化”按钮。</span><span class="sxs-lookup"><span data-stu-id="e6efe-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="e6efe-159">若要了解有关 Azure 自动化的详细信息，请参阅 [Azure 自动化](/azure/automation)文档。</span><span class="sxs-lookup"><span data-stu-id="e6efe-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="e6efe-160">从 PowerShell 库更新包</span><span class="sxs-lookup"><span data-stu-id="e6efe-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="e6efe-161">若要更新从 PowerShell 库安装的包，请运行 [Update-Module][] 或 [Update-Script][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6efe-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="e6efe-162">如果不使用其他任何参数运行，[Update-Module][] 尝试通过运行 [Install-Module][] 来更新每个已安装的模块。</span><span class="sxs-lookup"><span data-stu-id="e6efe-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="e6efe-163">若要选择性地更新模块，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="e6efe-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="e6efe-164">同样，如果不使用其他任何参数运行，[Update-Script][] 也会尝试通过运行 [Install-Script][] 来更新每个已安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="e6efe-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="e6efe-165">若要选择性地更新脚本，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="e6efe-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="e6efe-166">列出从 PowerShell 库安装的包</span><span class="sxs-lookup"><span data-stu-id="e6efe-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="e6efe-167">若要确定已安装 PowerShell 库中的哪些模块，请运行 [Get-InstalledModule][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6efe-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="e6efe-168">该命令会列出系统上所有已直接从 PowerShell 库安装的模块。</span><span class="sxs-lookup"><span data-stu-id="e6efe-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="e6efe-169">同样，若要确定已安装 PowerShell 库中的哪些脚本，请运行 [Get-InstalledScript][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6efe-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="e6efe-170">此命令会列出系统上所有已直接从 PowerShell 库安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="e6efe-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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

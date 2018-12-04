---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: PowerShell 库入门
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: 1082b13115c5c5be4b76574ba55307b3e567983f
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52576883"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="13977-103">PowerShell 库入门</span><span class="sxs-lookup"><span data-stu-id="13977-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="13977-104">PowerShell 库是包含脚本、 模块和 DSC 资源可以下载并将它们的包存储库。</span><span class="sxs-lookup"><span data-stu-id="13977-104">The PowerShell Gallery is a package repository containing scripts, modules, and DSC resources you can download and leverage.</span></span> <span data-ttu-id="13977-105">使用中的 cmdlet [PowerShellGet](/powershell/module/powershellget)模块从 PowerShell 库安装包。</span><span class="sxs-lookup"><span data-stu-id="13977-105">You use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module to install packages from the PowerShell Gallery.</span></span> <span data-ttu-id="13977-106">从 PowerShell 库下载项时无需登录。</span><span class="sxs-lookup"><span data-stu-id="13977-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="13977-107">可直接从 PowerShell 库下载包，但不推荐此方法。</span><span class="sxs-lookup"><span data-stu-id="13977-107">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="13977-108">有关详细信息，请参阅[手动包下载](/powershell/gallery/how-to/working-with-packages/manual-download)。</span><span class="sxs-lookup"><span data-stu-id="13977-108">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="13977-109">从 PowerShell 库中发现包</span><span class="sxs-lookup"><span data-stu-id="13977-109">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="13977-110">可以通过使用 PowerShell 库中找到包**搜索**PowerShell 库上的控件[主页](https://www.powershellgallery.com)，或通过浏览模块和脚本从[包页](https://www.powershellgallery.com/packages).</span><span class="sxs-lookup"><span data-stu-id="13977-110">You can find packages in the PowerShell Gallery by using the **Search** control on the PowerShell Gallery's [home page](https://www.powershellgallery.com), or by browsing through the Modules and Scripts from the [Packages page](https://www.powershellgallery.com/packages).</span></span> <span data-ttu-id="13977-111">此外可以通过运行查找 PowerShell 库中的包[Find-module][]， [Find-dscresource]，并[Find-script][] cmdlet，具体取决于包类型使用`-Repository PSGallery`。</span><span class="sxs-lookup"><span data-stu-id="13977-111">You can also find packages from the PowerShell Gallery by running the [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlets, depending on the package type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="13977-112">可以使用以下参数来筛选库中的结果：</span><span class="sxs-lookup"><span data-stu-id="13977-112">You can filter results from the Gallery by using the following parameters:</span></span>

- <span data-ttu-id="13977-113">名称</span><span class="sxs-lookup"><span data-stu-id="13977-113">Name</span></span>
- <span data-ttu-id="13977-114">AllVersions</span><span class="sxs-lookup"><span data-stu-id="13977-114">AllVersions</span></span>
- <span data-ttu-id="13977-115">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="13977-115">MinimumVersion</span></span>
- <span data-ttu-id="13977-116">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="13977-116">RequiredVersion</span></span>
- <span data-ttu-id="13977-117">标记</span><span class="sxs-lookup"><span data-stu-id="13977-117">Tag</span></span>
- <span data-ttu-id="13977-118">包括</span><span class="sxs-lookup"><span data-stu-id="13977-118">Includes</span></span>
- <span data-ttu-id="13977-119">DscResource</span><span class="sxs-lookup"><span data-stu-id="13977-119">DscResource</span></span>
- <span data-ttu-id="13977-120">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="13977-120">RoleCapability</span></span>
- <span data-ttu-id="13977-121">Command</span><span class="sxs-lookup"><span data-stu-id="13977-121">Command</span></span>
- <span data-ttu-id="13977-122">筛选</span><span class="sxs-lookup"><span data-stu-id="13977-122">Filter</span></span>

<span data-ttu-id="13977-123">如果只想发现库中的特定 DSC 资源，可运行 [Find-DscResource] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13977-123">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="13977-124">Find-DscResource 会返回库中 DSC 资源的相关数据。</span><span class="sxs-lookup"><span data-stu-id="13977-124">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="13977-125">由于 DSC 资源始终作为模块的部分进行传递，所以仍需运行 [Install-Module][] 来安装这些 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="13977-125">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="13977-126">了解 PowerShell 库中的包</span><span class="sxs-lookup"><span data-stu-id="13977-126">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="13977-127">找到感兴趣的包后，你可能想要了解更多有关信息。</span><span class="sxs-lookup"><span data-stu-id="13977-127">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="13977-128">可检查库中该包的特定页来了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="13977-128">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="13977-129">在该页上可查看该包中上载的所有元数据。</span><span class="sxs-lookup"><span data-stu-id="13977-129">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="13977-130">此元数据由包作者提供，Microsoft 不会对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="13977-130">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="13977-131">包的所有者紧密关联到用于发布该包的 PowerShell 库帐户，比“作者”字段更可信。</span><span class="sxs-lookup"><span data-stu-id="13977-131">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="13977-132">如果发现发布的包不可信，请单击该包页面上的“报告滥用行为”。</span><span class="sxs-lookup"><span data-stu-id="13977-132">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="13977-133">如果运行 [Find-Module][] 或 [Find-Script][]，则可在返回的 PSGetModuleInfo 对象中查看该数据。</span><span class="sxs-lookup"><span data-stu-id="13977-133">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="13977-134">例如，运行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="13977-134">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="13977-135">返回库中 PSReadLine 模块的数据。</span><span class="sxs-lookup"><span data-stu-id="13977-135">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="13977-136">从 PowerShell 库下载包</span><span class="sxs-lookup"><span data-stu-id="13977-136">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="13977-137">从 PowerShell 库下载包时，建议执行下列过程：</span><span class="sxs-lookup"><span data-stu-id="13977-137">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="13977-138">检查</span><span class="sxs-lookup"><span data-stu-id="13977-138">Inspect</span></span>

<span data-ttu-id="13977-139">若要下载库中的包以供检查，请运行 [Save-Module][] 或 [Save-Script][] cmdlet，具体视包类型而定。</span><span class="sxs-lookup"><span data-stu-id="13977-139">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="13977-140">此操作可本地保存包而不进行安装，并且可以检查包内容。</span><span class="sxs-lookup"><span data-stu-id="13977-140">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="13977-141">请记得手动删除已保存的包。</span><span class="sxs-lookup"><span data-stu-id="13977-141">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="13977-142">其中一些包由 Microsoft 编写，另一些包由 PowerShell 社区编写。</span><span class="sxs-lookup"><span data-stu-id="13977-142">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="13977-143">Microsoft 建议安装前检查库中包的内容和代码。</span><span class="sxs-lookup"><span data-stu-id="13977-143">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="13977-144">如果发现发布的包不可信，请单击该包页面上的“报告滥用行为”。</span><span class="sxs-lookup"><span data-stu-id="13977-144">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="13977-145">安装</span><span class="sxs-lookup"><span data-stu-id="13977-145">Install</span></span>

<span data-ttu-id="13977-146">若要安装库中的包以供使用，请运行 [Install-Module][] 或 [Install-Script][] cmdlet，具体视包类型而定。</span><span class="sxs-lookup"><span data-stu-id="13977-146">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="13977-147">默认情况下，[Install-Module][] 将模块安装到 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="13977-147">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="13977-148">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="13977-148">This requires an administrator account.</span></span> <span data-ttu-id="13977-149">如果添加 `-Scope CurrentUser` 参数，模块将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="13977-149">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="13977-150">默认情况下，[Install-Script][] 将脚本安装到 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="13977-150">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="13977-151">此操作需要管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="13977-151">This requires an administrator account.</span></span> <span data-ttu-id="13977-152">如果添加 `-Scope CurrentUser` 参数，脚本将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="13977-152">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="13977-153">默认情况下，[Install-Module][] 和 [Install-Script][] 安装最新版包。</span><span class="sxs-lookup"><span data-stu-id="13977-153">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="13977-154">若要安装旧版包，请添加 `-RequiredVersion` 参数。</span><span class="sxs-lookup"><span data-stu-id="13977-154">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="13977-155">在来宾群集上部署</span><span class="sxs-lookup"><span data-stu-id="13977-155">Deploy</span></span>

<span data-ttu-id="13977-156">若要部署到 Azure 自动化 PowerShell 库中的包，请单击**Azure 自动化**，然后单击**部署到 Azure 自动化**包详细信息页上。</span><span class="sxs-lookup"><span data-stu-id="13977-156">To deploy a package from the PowerShell Gallery to Azure Automation, click **Azure Automation**, then click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="13977-157">你将重定向到 Azure 管理门户中你在其中登录通过使用 Azure 帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="13977-157">You are redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="13977-158">请注意，部署具有依赖项包将所有依赖项部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="13977-158">Note that deploying packages with dependencies deploys all the dependencies to Azure Automation.</span></span> <span data-ttu-id="13977-159">通过将 AzureAutomationNotSupported 标记添加到包元数据可禁用“部署到 Azure 自动化”按钮。</span><span class="sxs-lookup"><span data-stu-id="13977-159">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="13977-160">若要了解有关 Azure 自动化的详细信息，请参阅 [Azure 自动化](/azure/automation)文档。</span><span class="sxs-lookup"><span data-stu-id="13977-160">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="13977-161">从 PowerShell 库更新包</span><span class="sxs-lookup"><span data-stu-id="13977-161">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="13977-162">若要更新从 PowerShell 库安装的包，请运行 [Update-Module][] 或 [Update-Script][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13977-162">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="13977-163">当运行不带任何其他参数时，尝试更新通过运行安装的所有模块 [都更新模块] [] [Install-module][]。</span><span class="sxs-lookup"><span data-stu-id="13977-163">When run without any additional parameters, [Update-Module][] attempts to update all modules installed by running [Install-Module][].</span></span> <span data-ttu-id="13977-164">若要选择性地更新模块，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="13977-164">To selectively update modules, add the `-Name` parameter.</span></span> 

<span data-ttu-id="13977-165">同样，当运行时不使用任何其他参数，[更新脚本] [] 还会尝试更新所有脚本运行安装[Install-script][]。</span><span class="sxs-lookup"><span data-stu-id="13977-165">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update all scripts installed by running [Install-Script][].</span></span> <span data-ttu-id="13977-166">若要选择性地更新脚本，请添加 `-Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="13977-166">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="13977-167">列出从 PowerShell 库安装的包</span><span class="sxs-lookup"><span data-stu-id="13977-167">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="13977-168">若要确定已安装 PowerShell 库中的哪些模块，请运行 [Get-InstalledModule][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13977-168">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="13977-169">该命令会列出系统上所有已直接从 PowerShell 库安装的模块。</span><span class="sxs-lookup"><span data-stu-id="13977-169">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="13977-170">同样，若要确定已安装 PowerShell 库中的哪些脚本，请运行 [Get-InstalledScript][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13977-170">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="13977-171">此命令会列出系统上所有已直接从 PowerShell 库安装的脚本。</span><span class="sxs-lookup"><span data-stu-id="13977-171">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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

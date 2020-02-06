---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: PowerShell 库常见问题解答
ms.openlocfilehash: 70e2220bd68b351e0b09dd3c59901104f7874335
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818118"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="7c524-103">常见问题</span><span class="sxs-lookup"><span data-stu-id="7c524-103">Frequently Asked Questions</span></span>

## <a name="what-is-a-powershell-module"></a><span data-ttu-id="7c524-104">PowerShell 模块是什么？</span><span class="sxs-lookup"><span data-stu-id="7c524-104">What is a PowerShell module?</span></span>

<span data-ttu-id="7c524-105">PowerShell 模块是包含某些 PowerShell 功能的可重复使用程序包。</span><span class="sxs-lookup"><span data-stu-id="7c524-105">A PowerShell module is a reusable package containing some PowerShell functionality.</span></span> <span data-ttu-id="7c524-106">PowerShell 中的所有内容（函数、变量、DSC 资源等）都可打包在模块中。</span><span class="sxs-lookup"><span data-stu-id="7c524-106">Everything in PowerShell (functions, variables, DSC resources, etc.) can be packaged in modules.</span></span> <span data-ttu-id="7c524-107">通常，模块是包含特定路径上存储的特定类型文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c524-107">Typically, modules are folders containing specific types of files stored on a specific path.</span></span> <span data-ttu-id="7c524-108">共有几种不同的 PowerShell 模块类型。</span><span class="sxs-lookup"><span data-stu-id="7c524-108">There are a few different types of PowerShell modules out there.</span></span>

## <a name="what-is-a-powershell-script"></a><span data-ttu-id="7c524-109">PowerShell 脚本是什么？</span><span class="sxs-lookup"><span data-stu-id="7c524-109">What is a PowerShell script?</span></span>

<span data-ttu-id="7c524-110">PowerShell 脚本是存储在.ps1 文件中的一系列命令，用于启用重用和共享。</span><span class="sxs-lookup"><span data-stu-id="7c524-110">A PowerShell script is a series of commands that are stored in a .ps1 file to enable reuse and sharing.</span></span> <span data-ttu-id="7c524-111">PowerShell 工作流也是 PowerShell 脚本，可概述任务组和提供这些任务的序列。</span><span class="sxs-lookup"><span data-stu-id="7c524-111">PowerShell workflows are also PowerShell scripts, which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="7c524-112">有关详细信息，请访问 [Getting Started with PowerShell Workflow](https://technet.microsoft.com/library/jj134242.aspx)（PowerShell 工作流入门）。</span><span class="sxs-lookup"><span data-stu-id="7c524-112">For more information, please visit [Getting Started with PowerShell Workflow](https://technet.microsoft.com/library/jj134242.aspx).</span></span>

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a><span data-ttu-id="7c524-113">PowerShell 脚本 与 PowerShell 模块有何不同？</span><span class="sxs-lookup"><span data-stu-id="7c524-113">How are PowerShell Scripts different from PowerShell Modules?</span></span>

<span data-ttu-id="7c524-114">通常模块更适合共享，但我们正启用脚本共享使向社区贡献工作流和脚本变得更加容易。</span><span class="sxs-lookup"><span data-stu-id="7c524-114">Modules are generally better for sharing, but we are enabling script sharing to make it easier for you to contribute workflows and scripts to the community.</span></span> <span data-ttu-id="7c524-115">有关详细信息，请参阅以下博客：</span><span class="sxs-lookup"><span data-stu-id="7c524-115">For more information, see the following blogs:</span></span>

- [<span data-ttu-id="7c524-116">不编写脚本，编写 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="7c524-116">Don't Write Scripts, Write PowerShell Modules</span></span>](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [<span data-ttu-id="7c524-117">了解 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="7c524-117">Understanding PowerShell Modules</span></span>](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a><span data-ttu-id="7c524-118">如何发布到 PowerShell 库？</span><span class="sxs-lookup"><span data-stu-id="7c524-118">How can I publish to the PowerShell Gallery?</span></span>

<span data-ttu-id="7c524-119">必须先在 PowerShell 库中注册帐户，然后才能将包发布到库中。</span><span class="sxs-lookup"><span data-stu-id="7c524-119">You must register an account in the PowerShell Gallery before you can publish packages to the Gallery.</span></span> <span data-ttu-id="7c524-120">这是因为发布包需要注册时提供的 NuGetApiKey。</span><span class="sxs-lookup"><span data-stu-id="7c524-120">This is because publishing packages requires a NuGetApiKey, which is provided upon registration.</span></span> <span data-ttu-id="7c524-121">若要注册，请使用个人、工作或学校帐户登录到 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="7c524-121">To register, use your personal, work, or school account to sign in to the PowerShell Gallery.</span></span> <span data-ttu-id="7c524-122">第一次登录时需要一次性注册过程。</span><span class="sxs-lookup"><span data-stu-id="7c524-122">A one-time registration process is required when you sign in for the first time.</span></span> <span data-ttu-id="7c524-123">此后，个人资料页上会提供 NuGetApiKey。</span><span class="sxs-lookup"><span data-stu-id="7c524-123">Afterwards, your NuGetApiKey is available on your profile page.</span></span>

<span data-ttu-id="7c524-124">在库中注册后，使用 [Publish-Module][] 或 [Publish-Script][] cmdlet 将包发布到库中。</span><span class="sxs-lookup"><span data-stu-id="7c524-124">Once you have registered in the Gallery, use the [Publish-Module][] or [Publish-Script][] cmdlets to publish your package to the Gallery.</span></span>
<span data-ttu-id="7c524-125">有关如何运行这些 cmdlet 的详细信息，请访问“发布”选项卡，或阅读 [Publish-Module][] 和 [Publish-Script][] 文档。</span><span class="sxs-lookup"><span data-stu-id="7c524-125">For more details on how to run these cmdlets, visit the Publish tab, or read the [Publish-Module][] and [Publish-Script][] documentation.</span></span>

<span data-ttu-id="7c524-126">安装或保存包无需注册或登录到库。 </span><span class="sxs-lookup"><span data-stu-id="7c524-126">**You do not need to register or sign in to the Gallery to install or save packages.**</span></span>

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a><span data-ttu-id="7c524-127">尝试将项发布到 PowerShell 库时，出现“无法处理请求。</span><span class="sxs-lookup"><span data-stu-id="7c524-127">I received "Failed to process request.</span></span> <span data-ttu-id="7c524-128">‘指定的 API 密钥无效或无权限访问指定的包。’。</span><span class="sxs-lookup"><span data-stu-id="7c524-128">'The specified API key is invalid or does not have permission to access the specified package.'.</span></span> <span data-ttu-id="7c524-129">远程服务器返回了错误：(403) 已禁止。”</span><span class="sxs-lookup"><span data-stu-id="7c524-129">The remote server returned an error: (403) Forbidden."</span></span> <span data-ttu-id="7c524-130">错误。</span><span class="sxs-lookup"><span data-stu-id="7c524-130">error when I tried to publish a package to the PowerShell Gallery.</span></span> <span data-ttu-id="7c524-131">这是什么意思？</span><span class="sxs-lookup"><span data-stu-id="7c524-131">What does that mean?</span></span>

<span data-ttu-id="7c524-132">出现该错误的原因可能如下：</span><span class="sxs-lookup"><span data-stu-id="7c524-132">This error can occur for the following reasons:</span></span>

- <span data-ttu-id="7c524-133">指定的 API 密钥无效。 </span><span class="sxs-lookup"><span data-stu-id="7c524-133">**The specified API key is invalid.**</span></span>
     <span data-ttu-id="7c524-134">请确保帐户中指定了有效的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="7c524-134">Ensure that you have specified the valid API key from your account.</span></span> <span data-ttu-id="7c524-135">若要获取 API 密钥，请查看个人资料页。</span><span class="sxs-lookup"><span data-stu-id="7c524-135">To get your API key, view your profile page.</span></span>
- <span data-ttu-id="7c524-136">指定的包名称不属于你。 </span><span class="sxs-lookup"><span data-stu-id="7c524-136">**The specified package name is not owned by you.**</span></span>
     <span data-ttu-id="7c524-137">如果已确认 API 密钥正确无误，则可能是因为已存在一个具有与你尝试使用的名称相同的包。</span><span class="sxs-lookup"><span data-stu-id="7c524-137">If you have confirmed that your API key is correct, then there may already exist a package with the same name as the one you are trying to use.</span></span> <span data-ttu-id="7c524-138">该包可能被其所有者取消列出，在这种情况下，该包不会出现在任何搜索结果中。</span><span class="sxs-lookup"><span data-stu-id="7c524-138">The package may have been unlisted by the owner, in which case it will not appear in any search results.</span></span> <span data-ttu-id="7c524-139">若要确定具有相同名称的包已经存在，请打开浏览器并导航至该包的详细信息页：`https://www.powershellgallery.com/packages/<packageName>`。</span><span class="sxs-lookup"><span data-stu-id="7c524-139">To determine if a package with the same name already exists, open a browser and navigate to the package's details page: `https://www.powershellgallery.com/packages/<packageName>`.</span></span> <span data-ttu-id="7c524-140">例如，直接导航至 `https://www.powershellgallery.com/packages/pester` 将进入 Pester 模块的详细信息页上，无论其列出与否。</span><span class="sxs-lookup"><span data-stu-id="7c524-140">For example, navigating directly to `https://www.powershellgallery.com/packages/pester` will take you to the Pester module's details page, whether it is unlisted or not.</span></span> <span data-ttu-id="7c524-141">如果具有冲突名称的包已经存在且被取消列出，则可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7c524-141">If a package with a conflicting name already exists and is unlisted, you can:</span></span>
    - <span data-ttu-id="7c524-142">选择其他包名称。</span><span class="sxs-lookup"><span data-stu-id="7c524-142">Select another name for your package.</span></span>
    - <span data-ttu-id="7c524-143">联系现有包的所有者。</span><span class="sxs-lookup"><span data-stu-id="7c524-143">Contact the owners of the existing package.</span></span>

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a><span data-ttu-id="7c524-144">为什么昨天可使用个人帐户登录而现在却无法登陆？</span><span class="sxs-lookup"><span data-stu-id="7c524-144">Why can't I sign in with my personal account, but I could sign in yesterday?</span></span>

<span data-ttu-id="7c524-145">请注意库帐户不会适应主电子邮件别名的更改。</span><span class="sxs-lookup"><span data-stu-id="7c524-145">Please be aware that your gallery account does not accommodate changes to your primary email alias.</span></span> <span data-ttu-id="7c524-146">有关详细信息，请参阅 [Microsoft 电子邮件别名](https://windows.microsoft.com/windows/outlook/add-alias-account)。</span><span class="sxs-lookup"><span data-stu-id="7c524-146">For more information, see [Microsoft Email Aliases](https://windows.microsoft.com/windows/outlook/add-alias-account).</span></span>

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a><span data-ttu-id="7c524-147">为什么选中“包”选项卡上所有“类别”复选框时没有显示所有库包？</span><span class="sxs-lookup"><span data-stu-id="7c524-147">Why don't I see all the gallery packages when I select all the Category checkboxes on the packages tab?</span></span>

<span data-ttu-id="7c524-148">选中“类别”复选框即表示“我想查看此类别中所有的包”。</span><span class="sxs-lookup"><span data-stu-id="7c524-148">By selecting a Category checkbox, you are stating "I would like to see all packages in this category."</span></span> <span data-ttu-id="7c524-149">仅会显示所选类别中的包。</span><span class="sxs-lookup"><span data-stu-id="7c524-149">Only the packages in the selected categories will be displayed.</span></span> <span data-ttu-id="7c524-150">同样，选中所有的“类别”复选框即表示“我想查看所有类别中所有的包”。</span><span class="sxs-lookup"><span data-stu-id="7c524-150">So similarly, by selecting all the Category checkboxes, you are stating "I would like to see all packages in any category."</span></span> <span data-ttu-id="7c524-151">但库中的一些包不属于所列出的任何类别，因而不会显示在结果中。</span><span class="sxs-lookup"><span data-stu-id="7c524-151">But some packages in the gallery do not belong to any of the categories listed, so they will not appear in the results.</span></span> <span data-ttu-id="7c524-152">若要查看库中的所有包，请取消选中所有类别，或再次选择“包”选项卡。</span><span class="sxs-lookup"><span data-stu-id="7c524-152">To see all packages in the gallery, uncheck all the Categories, or select the packages tab again.</span></span>

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a><span data-ttu-id="7c524-153">将模块发布到 PowerShell 库中有什么要求？</span><span class="sxs-lookup"><span data-stu-id="7c524-153">What are the requirements to publish a module to the PowerShell Gallery?</span></span>

<span data-ttu-id="7c524-154">任何种类的 PowerShell 模块（脚本模块、二进制模块或清单模块）都可发布到库中。</span><span class="sxs-lookup"><span data-stu-id="7c524-154">Any kind of PowerShell module (script modules, binary modules, or manifest modules) can be published to the gallery.</span></span>
<span data-ttu-id="7c524-155">若要发布模块，PowerShellGet 需要了解该模块的版本、说明、作者和许可方式等信息。</span><span class="sxs-lookup"><span data-stu-id="7c524-155">To publish a module, PowerShellGet needs to know a few things about it - the version, description, author, and how it is licensed.</span></span>
<span data-ttu-id="7c524-156">从模块清单  (.psd1) 文件或 [Publish-Module][] cmdlet 的 LicenseUri  参数的值的部分发布过程中读取此信息。</span><span class="sxs-lookup"><span data-stu-id="7c524-156">This information is read as part of the publishing process from the *module manifest* (.psd1) file, or from the value of the [Publish-Module][] cmdlet's **LicenseUri** parameter.</span></span>
<span data-ttu-id="7c524-157">所有发布到库中的模块必须具有模块清单。</span><span class="sxs-lookup"><span data-stu-id="7c524-157">All modules published to the Gallery must have module manifests.</span></span>
<span data-ttu-id="7c524-158">清单中包含以下信息的任何模块都可发布到库中：</span><span class="sxs-lookup"><span data-stu-id="7c524-158">Any module that includes the following information in its manifest can be published to the Gallery:</span></span>

- <span data-ttu-id="7c524-159">版本</span><span class="sxs-lookup"><span data-stu-id="7c524-159">Version</span></span>
- <span data-ttu-id="7c524-160">说明</span><span class="sxs-lookup"><span data-stu-id="7c524-160">Description</span></span>
- <span data-ttu-id="7c524-161">作者</span><span class="sxs-lookup"><span data-stu-id="7c524-161">Author</span></span>
- <span data-ttu-id="7c524-162">一个该模块许可条款的 URI，或作为该清单的 PrivateData  的一部分，或在 [Publish-Module][] cmdlet 的 LicenseUri  参数中。</span><span class="sxs-lookup"><span data-stu-id="7c524-162">A URI to the license terms of the module, either as part of the **PrivateData** section of the manifest, or in the **LicenseUri** parameter of the [Publish-Module][] cmdlet.</span></span>

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a><span data-ttu-id="7c524-163">如何创建格式正确的模块清单？</span><span class="sxs-lookup"><span data-stu-id="7c524-163">How do I create a correctly-formatted module manifest?</span></span>

<span data-ttu-id="7c524-164">创建模块清单最简单的方法是运行 [New-ModuleManifest][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c524-164">The easiest way to create a module manifest is to run the [New-ModuleManifest][] cmdlet.</span></span> <span data-ttu-id="7c524-165">PowerShell 5.0 或更高版本中，New-ModuleManifest 会生成格式正确的模块清单，其中包含 **ProjectUri**、**LicenseUri**、**Tags** 等有用元数据的空白字段。</span><span class="sxs-lookup"><span data-stu-id="7c524-165">In PowerShell 5.0 or newer, New-ModuleManifest generates a correctly-formatted module manifest with blank fields for useful metadata like **ProjectUri**, **LicenseUri**, and **Tags**.</span></span> <span data-ttu-id="7c524-166">只需填写空值，或使用生成的清单作为正确格式的示例。</span><span class="sxs-lookup"><span data-stu-id="7c524-166">Simply fill in the blanks, or use the generated manifest as an example of correct formatting.</span></span>

<span data-ttu-id="7c524-167">若要验证是否已正确填写所有必需的元数据字段，请使用 [Test-ModuleManifest][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c524-167">To verify that all required metadata fields have been properly filled, use the [Test-ModuleManifest][] cmdlet.</span></span>

<span data-ttu-id="7c524-168">若要更新模块清单文件字段，请使用 [Update-ModuleManifest][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c524-168">To update the module manifest file fields, use the [Update-ModuleManifest][] cmdlet.</span></span>

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a><span data-ttu-id="7c524-169">将脚本发布到库中有什么要求？</span><span class="sxs-lookup"><span data-stu-id="7c524-169">What are the requirements to publish a script to the Gallery?</span></span>

<span data-ttu-id="7c524-170">任何种类的 PowerShell 脚本（脚本或工作流）都可发布到库中。</span><span class="sxs-lookup"><span data-stu-id="7c524-170">Any kind of PowerShell script (scripts or workflows) can be published to the gallery.</span></span>
<span data-ttu-id="7c524-171">若要发布脚本，PowerShellGet 需要了解该脚本的版本、说明、作者和许可方式等信息。</span><span class="sxs-lookup"><span data-stu-id="7c524-171">To publish a script, PowerShellGet needs to know a few things about it - the version, description, author, and how it is licensed.</span></span>
<span data-ttu-id="7c524-172">从脚本文件的 PSScriptInfo 部分  或 [Publish-Script][] cmdlet 的 LicenseUri  参数的值的部分发布过程中读取此信息。</span><span class="sxs-lookup"><span data-stu-id="7c524-172">This information is read as part of the publishing process from the script file's *PSScriptInfo* section, or from the value of the [Publish-Script][] cmdlet's **LicenseUri** parameter.</span></span>
<span data-ttu-id="7c524-173">所有发布到库中的脚本必须具有元数据信息。</span><span class="sxs-lookup"><span data-stu-id="7c524-173">All scripts published to the Gallery must have metadata information.</span></span>
<span data-ttu-id="7c524-174">PSScriptInfo 部分中包括以下信息的任何脚本都可发布到库中：</span><span class="sxs-lookup"><span data-stu-id="7c524-174">Any script that includes the following information in its PSScriptInfo section can be published to the Gallery:</span></span>

- <span data-ttu-id="7c524-175">版本</span><span class="sxs-lookup"><span data-stu-id="7c524-175">Version</span></span>
- <span data-ttu-id="7c524-176">说明</span><span class="sxs-lookup"><span data-stu-id="7c524-176">Description</span></span>
- <span data-ttu-id="7c524-177">作者</span><span class="sxs-lookup"><span data-stu-id="7c524-177">Author</span></span>
- <span data-ttu-id="7c524-178">一个该脚本许可条款的 URI，或作为此脚本的 PSScriptInfo  的一部分，或在 [Publish-Script][] cmdlet 的 LicenseUri  参数中。</span><span class="sxs-lookup"><span data-stu-id="7c524-178">A URI to the license terms of the script, either as part of the **PSScriptInfo** section of the script, or in the **LicenseUri** parameter of the [Publish-Script][] cmdlet.</span></span>

## <a name="how-do-i-search"></a><span data-ttu-id="7c524-179">如何搜索？</span><span class="sxs-lookup"><span data-stu-id="7c524-179">How do I search?</span></span>

<span data-ttu-id="7c524-180">在文本框中键入要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="7c524-180">Type what you are looking for in the text box.</span></span> <span data-ttu-id="7c524-181">例如，如要查找与 Azure SQL 相关的模块，只需键入“azure sql”。</span><span class="sxs-lookup"><span data-stu-id="7c524-181">For example, if you want to find modules that are related to Azure SQL, just type "azure sql".</span></span> <span data-ttu-id="7c524-182">搜索引擎会在所有已发布的包（包括标题、说明和元数据）中查找这些关键字。</span><span class="sxs-lookup"><span data-stu-id="7c524-182">Our search engine will look for those keywords in all published packages, including titles, descriptions and across metadata.</span></span> <span data-ttu-id="7c524-183">然后，根据加权质量分，搜索引擎将显示最接近的匹配。</span><span class="sxs-lookup"><span data-stu-id="7c524-183">Then, based on a weighted quality score, it will display the closest matches.</span></span> <span data-ttu-id="7c524-184">你也可以在以下字段的搜索查询中使用 field:"value" 语法按指定字段进行搜索：</span><span class="sxs-lookup"><span data-stu-id="7c524-184">You can also search by specific field using field:"value" syntax in the search query for the following fields:</span></span>

- <span data-ttu-id="7c524-185">Tags</span><span class="sxs-lookup"><span data-stu-id="7c524-185">Tags</span></span>
- <span data-ttu-id="7c524-186">函数</span><span class="sxs-lookup"><span data-stu-id="7c524-186">Functions</span></span>
- <span data-ttu-id="7c524-187">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7c524-187">Cmdlets</span></span>
- <span data-ttu-id="7c524-188">DscResources</span><span class="sxs-lookup"><span data-stu-id="7c524-188">DscResources</span></span>
- <span data-ttu-id="7c524-189">PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="7c524-189">PowerShellVersion</span></span>

<span data-ttu-id="7c524-190">例如，搜索 PowerShellVersion:"2.0" 时，仅会显示与 PowerShellVersion 2.0 相容（基于其模块/脚本清单）的结果。</span><span class="sxs-lookup"><span data-stu-id="7c524-190">So, for example, when you search for PowerShellVersion:"2.0" only results that are compatible with PowerShellVersion 2.0 (based on their module/script manifest) will be displayed.</span></span>

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a><span data-ttu-id="7c524-191">如何创建格式正确的脚本文件？</span><span class="sxs-lookup"><span data-stu-id="7c524-191">How do I create a correctly-formatted script file?</span></span>

<span data-ttu-id="7c524-192">创建格式正确的脚本文件最简单的方法是运行 [New-ScriptFileInfo][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c524-192">The easiest way to create a properly-formatted script file is to run the [New-ScriptFileInfo][] cmdlet.</span></span> <span data-ttu-id="7c524-193">PowerShell 5.0 中，New-ScriptFileInfo 会生成格式正确的脚本文件，其中包含 **ProjectUri**、**LicenseUri**、**Tags** 等有用元数据的空白字段。</span><span class="sxs-lookup"><span data-stu-id="7c524-193">In PowerShell 5.0, New-ScriptFileInfo generates a correctly-formatted script file with blank fields for useful metadata like **ProjectUri**, **LicenseUri**, and **Tags**.</span></span> <span data-ttu-id="7c524-194">只需填写空值，或使用生成的脚本文件作为正确格式的示例。</span><span class="sxs-lookup"><span data-stu-id="7c524-194">Simply fill in the blanks, or use the generated script file as an example of correct formatting.</span></span>

<span data-ttu-id="7c524-195">若要验证是否已正确填写所有必需的元数据字段，请使用 [Test-ScriptFileInfo][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c524-195">To verify that all required metadata fields have been properly filled, use the [Test-ScriptFileInfo][] cmdlet.</span></span>

<span data-ttu-id="7c524-196">若要更新脚本元数据字段，请使用 [Update-ScriptFileInfo][] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c524-196">To update the script metadata fields, use the [Update-ScriptFileInfo][] cmdlet.</span></span>

## <a name="what-other-types-of-powershell-modules-exist"></a><span data-ttu-id="7c524-197">还有哪些其他类型的 PowerShell 模块？</span><span class="sxs-lookup"><span data-stu-id="7c524-197">What other types of PowerShell Modules exist?</span></span>

<span data-ttu-id="7c524-198">术语 PowerShell 模块也指执行实际功能的文件。</span><span class="sxs-lookup"><span data-stu-id="7c524-198">The term PowerShell module also refers to the files that implement actual functionality.</span></span> <span data-ttu-id="7c524-199">脚本模块文件 (.psm1) 包含 PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="7c524-199">Script module files (.psm1) contain PowerShell code.</span></span> <span data-ttu-id="7c524-200">二进制模块文件 (.dll) 包含已编译的代码。</span><span class="sxs-lookup"><span data-stu-id="7c524-200">Binary module files (.dll) contain compiled code.</span></span>

<span data-ttu-id="7c524-201">可这样理解：封装模块的文件夹即是模块文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c524-201">Here is one way to think about it: the folder that encapsulates the module is the module folder.</span></span> <span data-ttu-id="7c524-202">模块文件夹包含描述该文件夹内容的模块清单 (.psd1)。</span><span class="sxs-lookup"><span data-stu-id="7c524-202">The module folder can contain a module manifest (.psd1) that describes the contents of the folder.</span></span> <span data-ttu-id="7c524-203">实际完成工作的文件是脚本模块文件 (.psm1) 和二进制模块文件 (.dll)。</span><span class="sxs-lookup"><span data-stu-id="7c524-203">The files that actually do the work are the script module files (.psm1) and the binary module files (.dll).</span></span> <span data-ttu-id="7c524-204">DSC 资源位于特定的子文件夹中，并作为脚本模块文件或二进制文件执行。</span><span class="sxs-lookup"><span data-stu-id="7c524-204">DSC resources are located in a specific sub-folder, and are implemented as script module files or binary module files.</span></span>

<span data-ttu-id="7c524-205">库中所有模块包含模块清单，且其中大多数模块包含脚本模块文件或二进制模块文件。</span><span class="sxs-lookup"><span data-stu-id="7c524-205">All of the modules in the Gallery contain module manifests, and most of these modules contain script module files or binary module files.</span></span> <span data-ttu-id="7c524-206">由于这些不同的含义，术语模块可能会造成混淆。</span><span class="sxs-lookup"><span data-stu-id="7c524-206">The term module can be confusing because of these different meanings.</span></span> <span data-ttu-id="7c524-207">除非明确说明，否则此页上所有使用的“模块”一词都指包含这些文件的模块文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c524-207">Unless explicitly stated otherwise, all uses of the word module on this page refer to the module folder containing these files.</span></span>

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a><span data-ttu-id="7c524-208">PackageManagement 与 PowerShellGet 有何关联？</span><span class="sxs-lookup"><span data-stu-id="7c524-208">How does PackageManagement relate to PowerShellGet?</span></span> <span data-ttu-id="7c524-209">（高级回答）</span><span class="sxs-lookup"><span data-stu-id="7c524-209">(High Level Answer)</span></span>

<span data-ttu-id="7c524-210">PackageManagement 是使用任何程序包管理器的一个公共接口。</span><span class="sxs-lookup"><span data-stu-id="7c524-210">PackageManagement is a common interface for working with any package manager.</span></span> <span data-ttu-id="7c524-211">最后，无论是处理 PowerShell 模块、MSI、Ruby gem、NuGet 包还是 Perl 模块，都可使用 PackageManagement 命令（Find-Package 和 Install-Package）进行查找和安装。</span><span class="sxs-lookup"><span data-stu-id="7c524-211">Eventually, whether you're dealing with PowerShell modules, MSIs, Ruby gems, NuGet packages, or Perl modules, you should be able to use PackageManagement's commands (Find-Package and Install-Package) to find and install them.</span></span> <span data-ttu-id="7c524-212">每个插入 PackageManagement 的程序包管理器都具有一个程序包提供程序，因而 PackageManagement 可实现该操作。</span><span class="sxs-lookup"><span data-stu-id="7c524-212">PackageManagement does this by having a package provider for each package manager that plugs into PackageManagement.</span></span> <span data-ttu-id="7c524-213">提供程序完成所有的实际工作；它们从存储库中提取内容，并本地安装内容。</span><span class="sxs-lookup"><span data-stu-id="7c524-213">Providers do all of the actual work; they fetch content from repositories, and install the content locally.</span></span> <span data-ttu-id="7c524-214">通常，程序包提供程序环绕处理给定程序包类型的现有程序包管理器工具。</span><span class="sxs-lookup"><span data-stu-id="7c524-214">Often, package providers simply wrap around the existing package manager tools for a given package type.</span></span>

<span data-ttu-id="7c524-215">PowerShellGet 是 PowerShell 包的包管理器。</span><span class="sxs-lookup"><span data-stu-id="7c524-215">PowerShellGet is the package manager for PowerShell packages.</span></span>
<span data-ttu-id="7c524-216">存在一个通过 PackageManagement 揭示 PowerShellGet 功能的 PSModule 程序包提供程序。</span><span class="sxs-lookup"><span data-stu-id="7c524-216">There is a PSModule package provider that exposes PowerShellGet functionality through PackageManagement.</span></span>
<span data-ttu-id="7c524-217">因此，可运行 [Install-Module][] 或 Install-Package -Provider PSModule 来从 PowerShell 库安装模块。</span><span class="sxs-lookup"><span data-stu-id="7c524-217">Because of this, you can either run [Install-Module][] or Install-Package -Provider PSModule to install a module from the PowerShell Gallery.</span></span>
<span data-ttu-id="7c524-218">特定 PowerShellGet 功能（包括 [Update-Module][] 和 [Publish-Module][]）无法通过 PackageManagement 命令访问。</span><span class="sxs-lookup"><span data-stu-id="7c524-218">Certain PowerShellGet functionality, including [Update-Module][] and [Publish-Module][], cannot be accessed through PackageManagement commands.</span></span>

<span data-ttu-id="7c524-219">总之，PowerShellGet 仅侧重于提供优质 PowerShell 内容的程序包管理体验。</span><span class="sxs-lookup"><span data-stu-id="7c524-219">In summary, PowerShellGet is solely focused on having a premium package management experience for PowerShell content.</span></span> <span data-ttu-id="7c524-220">PackageManagement 侧重于通过一组工具公开所有的包管理体验。</span><span class="sxs-lookup"><span data-stu-id="7c524-220">PackageManagement is focused on exposing all package management experiences through one general set of tools.</span></span> <span data-ttu-id="7c524-221">如对此回答不满意，可在本文档底部的 **PackageManagement 与 PowerShellGet 有何关联？** 部分中查看更详尽的回答。</span><span class="sxs-lookup"><span data-stu-id="7c524-221">If you find this answer unsatisfying, there is a long answer at the bottom of this document, in the **How does PackageManagement actually relate to PowerShellGet?** section.</span></span>

<span data-ttu-id="7c524-222">有关详细信息，请访问 [PackageManagement 项目页](https://oneget.org/)。</span><span class="sxs-lookup"><span data-stu-id="7c524-222">For more information, please visit the [PackageManagement project page](https://oneget.org/).</span></span>

## <a name="how-does-nuget-relate-to-powershellget"></a><span data-ttu-id="7c524-223">NuGet 与 PowerShellGet 有何关联？</span><span class="sxs-lookup"><span data-stu-id="7c524-223">How does NuGet relate to PowerShellGet?</span></span>

<span data-ttu-id="7c524-224">PowerShell 库是 [NuGet Gallery](https://www.nuget.org/)（NuGet 库）的修改版本。</span><span class="sxs-lookup"><span data-stu-id="7c524-224">The PowerShell Gallery is a modified version of the [NuGet Gallery](https://www.nuget.org/).</span></span> <span data-ttu-id="7c524-225">PowerShellGet 使用 NuGet 提供程序支持基于 NuGet 的存储库，例如 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="7c524-225">PowerShellGet uses NuGet provider to work with NuGet based repositories like the PowerShell Gallery.</span></span>

<span data-ttu-id="7c524-226">可对任何有效的 NuGet 存储库或文件共享使用 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="7c524-226">You can use PowerShellGet against any valid NuGet repository or file share.</span></span> <span data-ttu-id="7c524-227">只需通过运行 [Register-PSRepository][] cmdlet 添加此存储库。</span><span class="sxs-lookup"><span data-stu-id="7c524-227">You simply need to add the repository by running the [Register-PSRepository][] cmdlet.</span></span>

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a><span data-ttu-id="7c524-228">这是否意味着可以使用 NuGet.exe 来处理库？</span><span class="sxs-lookup"><span data-stu-id="7c524-228">Does that mean I can use NuGet.exe to work with the Gallery?</span></span>

<span data-ttu-id="7c524-229">是的。</span><span class="sxs-lookup"><span data-stu-id="7c524-229">Yes.</span></span>

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a><span data-ttu-id="7c524-230">PackageManagement 与 PowerShellGet 有何关联？</span><span class="sxs-lookup"><span data-stu-id="7c524-230">How does PackageManagement actually relate to PowerShellGet?</span></span> <span data-ttu-id="7c524-231">（技术细节）</span><span class="sxs-lookup"><span data-stu-id="7c524-231">(Technical Details)</span></span>

<span data-ttu-id="7c524-232">事实上，PowerShellGet 很大程度上利用了 PackageManagement 基础结构。</span><span class="sxs-lookup"><span data-stu-id="7c524-232">Under the hood, PowerShellGet heavily leverages PackageManagement infrastructure.</span></span>

<span data-ttu-id="7c524-233">在 PowerShell cmdlet 层，[Install-Module][] 实际上是 Install-Package -Provider PSModule 的薄包装器。</span><span class="sxs-lookup"><span data-stu-id="7c524-233">At the PowerShell cmdlet layer, [Install-Module][] is actually a thin wrapper around Install-Package -Provider PSModule.</span></span>

<span data-ttu-id="7c524-234">在 PackageManagement 程序包提供程序层，PSModule 程序包提供程序实际调用到其他 PackageManagement 程序包提供程序。</span><span class="sxs-lookup"><span data-stu-id="7c524-234">At the PackageManagement package provider layer, the PSModule package provider actually calls into other PackageManagement package providers.</span></span> <span data-ttu-id="7c524-235">例如，使用基于 NuGet 的库（例如 PowerShell 库）时，PSModule 程序包提供程序会使用 NuGet 程序包提供程序作用于该存储库。</span><span class="sxs-lookup"><span data-stu-id="7c524-235">For example, when you are working with NuGet-based galleries (such as the PowerShell Gallery), the PSModule package provider uses the NuGet Package Provider to work with the repository.</span></span>

![PowerShellGet 体系结构](Images/powershellgetArchitecture.png)

<span data-ttu-id="7c524-237">图 1：PowerShellGet 体系结构</span><span class="sxs-lookup"><span data-stu-id="7c524-237">Figure 1: PowerShellGet Architecture</span></span>

## <a name="what-is-required-to-run-powershellget"></a><span data-ttu-id="7c524-238">运行 PowerShellGet 有什么要求？</span><span class="sxs-lookup"><span data-stu-id="7c524-238">What is required to run PowerShellGet?</span></span>

<span data-ttu-id="7c524-239">通常，建议选取最新版本的 PowerShellGet 模块（请注意其需要.NET 4.5）。</span><span class="sxs-lookup"><span data-stu-id="7c524-239">In general we recommend picking the latest version of PowerShellGet module (note that it requires .NET 4.5).</span></span>

<span data-ttu-id="7c524-240">**PowerShellGet** 模块需要 **PowerShell 3.0 或更高版本**。</span><span class="sxs-lookup"><span data-stu-id="7c524-240">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="7c524-241">因此，**PowerShellGet** 需要以下操作系统之一：</span><span class="sxs-lookup"><span data-stu-id="7c524-241">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="7c524-242">Windows 10</span><span class="sxs-lookup"><span data-stu-id="7c524-242">Windows 10</span></span>
- <span data-ttu-id="7c524-243">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="7c524-243">Windows 8.1 Pro</span></span>
- <span data-ttu-id="7c524-244">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="7c524-244">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="7c524-245">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="7c524-245">Windows 7 SP1</span></span>
- <span data-ttu-id="7c524-246">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="7c524-246">Windows Server 2016</span></span>
- <span data-ttu-id="7c524-247">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7c524-247">Windows Server 2012 R2</span></span>
- <span data-ttu-id="7c524-248">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="7c524-248">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="7c524-249">**PowerShellGet** 也需要 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7c524-249">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="7c524-250">你可从[此处](https://msdn.microsoft.com/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7c524-250">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a><span data-ttu-id="7c524-251">能否保留将来要发布的包的名称？</span><span class="sxs-lookup"><span data-stu-id="7c524-251">Is it possible to reserve names for packages that will be published in future?</span></span>

<span data-ttu-id="7c524-252">不能抢占包名称。</span><span class="sxs-lookup"><span data-stu-id="7c524-252">It is not possible to squat package names.</span></span> <span data-ttu-id="7c524-253">如果认为现有包占用的名称更适合你的包，可尝试[联系包的所有者](./how-to/working-with-packages/contacting-package-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="7c524-253">If you feel that an existing package has taken the name which suits your package more, try [contacting the owner of the package](./how-to/working-with-packages/contacting-package-owners.md).</span></span> <span data-ttu-id="7c524-254">如果你在几周内没有收到回复，可以联系支持部门，PowerShell 库团队会对此进行调查。</span><span class="sxs-lookup"><span data-stu-id="7c524-254">If you didn't get response within a couple of weeks, you can contact support and the PowerShell Gallery team will look in to it.</span></span>

## <a name="how-do-i-claim-ownership-for-packages"></a><span data-ttu-id="7c524-255">如何索取包的所有权？</span><span class="sxs-lookup"><span data-stu-id="7c524-255">How do I claim ownership for packages?</span></span>

<span data-ttu-id="7c524-256">有关详细信息，请查看 PowerShellGallery.com 上的[管理包所有者](./how-to/publishing-packages/managing-package-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="7c524-256">Check out [Managing Package Owners on PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md) for details.</span></span>

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a><span data-ttu-id="7c524-257">如何处理违反包许可证的包所有者？</span><span class="sxs-lookup"><span data-stu-id="7c524-257">How do I deal with a package owner who is violating my package license?</span></span>

<span data-ttu-id="7c524-258">我们鼓励 PowerShell 社区一起解决包所有者之间可能出现的任何争议。</span><span class="sxs-lookup"><span data-stu-id="7c524-258">We encourage the PowerShell community to work together to resolve any disputes that may arise between package owners and the owners of other packages.</span></span>  <span data-ttu-id="7c524-259">PowerShellGallery.com 管理员进行调解之前，我们希望你遵循我们精心指定的[争议解决过程](./how-to/getting-support/dispute-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="7c524-259">We have crafted a [dispute resolution process](./how-to/getting-support/dispute-resolution.md) that we ask you to follow before PowerShellGallery.com administrators intercede.</span></span>

[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Update-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Update-ModuleManifest

[Install-Module]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publish-Module]: /powershell/module/PowershellGet/Publish-Module
[Publish-Script]: /powershell/module/PowershellGet/Publish-Script
[Register-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-Module]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo

---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery,psget
title: 使用本地 PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619191"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="3b25c-103">使用本地 PowerShellGet 存储库</span><span class="sxs-lookup"><span data-stu-id="3b25c-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="3b25c-104">PowerShellGet 模块支持存储库之外 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="3b25c-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="3b25c-105">这些 cmdlet 支持以下方案：</span><span class="sxs-lookup"><span data-stu-id="3b25c-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="3b25c-106">在您的环境中使用支持一组受信任的、 预先经过验证的 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="3b25c-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="3b25c-107">测试生成 PowerShell 模块或脚本的 CI/CD 管道</span><span class="sxs-lookup"><span data-stu-id="3b25c-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="3b25c-108">为不能访问 internet 的系统提供的 PowerShell 脚本和模块</span><span class="sxs-lookup"><span data-stu-id="3b25c-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="3b25c-109">本文介绍如何设置本地 PowerShell 存储库。</span><span class="sxs-lookup"><span data-stu-id="3b25c-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="3b25c-110">本文还介绍了[OfflinePowerShellGetDeploy][] PowerShell 库中可用的模块。</span><span class="sxs-lookup"><span data-stu-id="3b25c-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="3b25c-111">此模块包含用于安装到本地存储库的最新版本的 PowerShellGet cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b25c-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="3b25c-112">本地存储库类型</span><span class="sxs-lookup"><span data-stu-id="3b25c-112">Local repository types</span></span>

<span data-ttu-id="3b25c-113">有两种方法来创建本地 PSRepository: NuGet 服务器或文件共享。</span><span class="sxs-lookup"><span data-stu-id="3b25c-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="3b25c-114">每种类型都有优点和缺点：</span><span class="sxs-lookup"><span data-stu-id="3b25c-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="3b25c-115">NuGet 服务器</span><span class="sxs-lookup"><span data-stu-id="3b25c-115">NuGet Server</span></span>

| <span data-ttu-id="3b25c-116">优点</span><span class="sxs-lookup"><span data-stu-id="3b25c-116">Advantages</span></span>| <span data-ttu-id="3b25c-117">缺点</span><span class="sxs-lookup"><span data-stu-id="3b25c-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="3b25c-118">精确模拟 powershell 库功能</span><span class="sxs-lookup"><span data-stu-id="3b25c-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="3b25c-119">多层应用程序需要规划的操作和支持</span><span class="sxs-lookup"><span data-stu-id="3b25c-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="3b25c-120">NuGet 与 Visual Studio 中，其他工具集成</span><span class="sxs-lookup"><span data-stu-id="3b25c-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="3b25c-121">身份验证模型和所需的 NuGet 帐户管理</span><span class="sxs-lookup"><span data-stu-id="3b25c-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="3b25c-122">NuGet 支持中的元数据`.Nupkg`包</span><span class="sxs-lookup"><span data-stu-id="3b25c-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="3b25c-123">发布操作要求 API 密钥管理和维护</span><span class="sxs-lookup"><span data-stu-id="3b25c-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="3b25c-124">提供搜索、 包管理，等等。</span><span class="sxs-lookup"><span data-stu-id="3b25c-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="3b25c-125">文件共享</span><span class="sxs-lookup"><span data-stu-id="3b25c-125">File Share</span></span>

| <span data-ttu-id="3b25c-126">优点</span><span class="sxs-lookup"><span data-stu-id="3b25c-126">Advantages</span></span>| <span data-ttu-id="3b25c-127">缺点</span><span class="sxs-lookup"><span data-stu-id="3b25c-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="3b25c-128">易于设置、 备份和维护</span><span class="sxs-lookup"><span data-stu-id="3b25c-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="3b25c-129">使用 PowerShellGet 的元数据不可用</span><span class="sxs-lookup"><span data-stu-id="3b25c-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="3b25c-130">简单安全模型的共享上的用户权限</span><span class="sxs-lookup"><span data-stu-id="3b25c-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="3b25c-131">除了基本文件共享没有用户界面</span><span class="sxs-lookup"><span data-stu-id="3b25c-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="3b25c-132">例如，现有的项目替换为任何约束</span><span class="sxs-lookup"><span data-stu-id="3b25c-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="3b25c-133">有限的安全和没有录制的内容更新者</span><span class="sxs-lookup"><span data-stu-id="3b25c-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="3b25c-134">PowerShellGet 适用于类型和支持查找的版本和依赖项安装。</span><span class="sxs-lookup"><span data-stu-id="3b25c-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="3b25c-135">但是，一些适用于 PowerShell 库的功能不适用于基本 NuGet 服务器或文件共享。</span><span class="sxs-lookup"><span data-stu-id="3b25c-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="3b25c-136">所有内容是一个包的脚本、 模块、 DSC 资源或角色功能没有差异。</span><span class="sxs-lookup"><span data-stu-id="3b25c-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="3b25c-137">文件共享服务器不能查看包元数据，包括标记。</span><span class="sxs-lookup"><span data-stu-id="3b25c-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="3b25c-138">创建本地存储库</span><span class="sxs-lookup"><span data-stu-id="3b25c-138">Creating a local repository</span></span>

<span data-ttu-id="3b25c-139">以下文章列出了用于设置你自己的 NuGet 服务器的步骤。</span><span class="sxs-lookup"><span data-stu-id="3b25c-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="3b25c-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="3b25c-140">[NuGet.Server][]</span></span>

<span data-ttu-id="3b25c-141">按照添加包的点之前的步骤。</span><span class="sxs-lookup"><span data-stu-id="3b25c-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="3b25c-142">有关步骤[发布包](#publishing-to-a-local-repository)本文稍后介绍。</span><span class="sxs-lookup"><span data-stu-id="3b25c-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="3b25c-143">对于文件基于共享的存储库，请确保你的用户有权访问文件共享。</span><span class="sxs-lookup"><span data-stu-id="3b25c-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="3b25c-144">注册本地存储库</span><span class="sxs-lookup"><span data-stu-id="3b25c-144">Registering a local repository</span></span>

<span data-ttu-id="3b25c-145">可以使用存储库之前，它必须使用注册`Register-PSRepository`命令。</span><span class="sxs-lookup"><span data-stu-id="3b25c-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="3b25c-146">在下面的示例**InstallationPolicy**设置为*受信任*，假定您信任您自己的存储库。</span><span class="sxs-lookup"><span data-stu-id="3b25c-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="3b25c-147">记下两个命令的处理方式的区别**ScriptSourceLocation**。</span><span class="sxs-lookup"><span data-stu-id="3b25c-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="3b25c-148">文件共享基于存储库，对于**SourceLocation**并**ScriptSourceLocation**必须匹配。</span><span class="sxs-lookup"><span data-stu-id="3b25c-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="3b25c-149">对于基于 web 的存储库，它们必须不同，因此，在此示例中的尾随"/"添加到**SourceLocation**。</span><span class="sxs-lookup"><span data-stu-id="3b25c-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="3b25c-150">如果您想新建的 PSRepository 为默认存储库，必须取消注册所有其他 PSRepositories。</span><span class="sxs-lookup"><span data-stu-id="3b25c-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="3b25c-151">例如：</span><span class="sxs-lookup"><span data-stu-id="3b25c-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="3b25c-152">PowerShell 库存储库名称 PSGallery' 保留供。</span><span class="sxs-lookup"><span data-stu-id="3b25c-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="3b25c-153">可以取消注册 PSGallery，但不能重复使用任何其他存储库的名称 PSGallery。</span><span class="sxs-lookup"><span data-stu-id="3b25c-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="3b25c-154">如果需要还原 PSGallery，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3b25c-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="3b25c-155">发布到本地存储库</span><span class="sxs-lookup"><span data-stu-id="3b25c-155">Publishing to a local repository</span></span>

<span data-ttu-id="3b25c-156">一旦注册本地 PSRepository 后，您可以将发布到本地 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="3b25c-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="3b25c-157">有两个主要发布方案： 发布你自己的模块和发布提供 PSGallery 的模块。</span><span class="sxs-lookup"><span data-stu-id="3b25c-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="3b25c-158">发布您编写的模块</span><span class="sxs-lookup"><span data-stu-id="3b25c-158">Publishing a module you authored</span></span>

<span data-ttu-id="3b25c-159">使用`Publish-Module`和`Publish-Script`对于 PowerShell 库所做的相同方式将你的模块发布到本地 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="3b25c-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="3b25c-160">指定你的代码的位置</span><span class="sxs-lookup"><span data-stu-id="3b25c-160">Specify the location for your code</span></span>
- <span data-ttu-id="3b25c-161">提供 API 密钥</span><span class="sxs-lookup"><span data-stu-id="3b25c-161">Supply an API key</span></span>
- <span data-ttu-id="3b25c-162">指定存储库名称。</span><span class="sxs-lookup"><span data-stu-id="3b25c-162">Specify the repository name.</span></span> <span data-ttu-id="3b25c-163">例如，`-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="3b25c-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="3b25c-164">必须在 NuGet 服务器中创建一个帐户，然后登录以进行生成并保存的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="3b25c-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="3b25c-165">为文件共享，NuGetApiKey 值中使用任何非空字符串。</span><span class="sxs-lookup"><span data-stu-id="3b25c-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="3b25c-166">示例：</span><span class="sxs-lookup"><span data-stu-id="3b25c-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="3b25c-167">若要确保安全，API 密钥不应在脚本中硬编码。</span><span class="sxs-lookup"><span data-stu-id="3b25c-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="3b25c-168">使用安全的密钥管理系统。</span><span class="sxs-lookup"><span data-stu-id="3b25c-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="3b25c-169">发布模块从 PSGallery</span><span class="sxs-lookup"><span data-stu-id="3b25c-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="3b25c-170">若要发布到本地 PSRepository PSGallery 提供模块，可以使用保存包 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b25c-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="3b25c-171">指定包的名称</span><span class="sxs-lookup"><span data-stu-id="3b25c-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="3b25c-172">作为提供程序指定 NuGet</span><span class="sxs-lookup"><span data-stu-id="3b25c-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="3b25c-173">PSGallery 位置指定为源 （ https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="3b25c-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="3b25c-174">指定本地存储库的路径</span><span class="sxs-lookup"><span data-stu-id="3b25c-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="3b25c-175">例如：</span><span class="sxs-lookup"><span data-stu-id="3b25c-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="3b25c-176">如果本地 PSRepository 是基于 web 的则需要使用 nuget.exe 来发布的其他步骤。</span><span class="sxs-lookup"><span data-stu-id="3b25c-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="3b25c-177">请参阅有关使用文档[nuget.exe][]。</span><span class="sxs-lookup"><span data-stu-id="3b25c-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="3b25c-178">在断开连接的系统上安装 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="3b25c-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="3b25c-179">部署 PowerShellGet 会要求系统以与 internet 断开的环境中很困难。</span><span class="sxs-lookup"><span data-stu-id="3b25c-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="3b25c-180">PowerShellGet 有一个引导过程的第一次使用它将安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="3b25c-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="3b25c-181">PowerShell 库中的 OfflinePowerShellGetDeploy 模块提供了支持此启动过程中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b25c-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="3b25c-182">若要启动离线部署，需要：</span><span class="sxs-lookup"><span data-stu-id="3b25c-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="3b25c-183">下载并安装 OfflinePowerShellGetDeploy 在连接 internet 的系统和断开连接的系统</span><span class="sxs-lookup"><span data-stu-id="3b25c-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="3b25c-184">下载 PowerShellGet 和其依赖 internet 连接的系统使用`Save-PowerShellGetForOffline`cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b25c-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="3b25c-185">将从连接 internet 的系统的 PowerShellGet 和其依赖项复制到断开连接的系统</span><span class="sxs-lookup"><span data-stu-id="3b25c-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="3b25c-186">使用`Install-PowerShellGetOffline`上断开连接的系统，PowerShellGet 和其依赖项放入适当的文件夹</span><span class="sxs-lookup"><span data-stu-id="3b25c-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="3b25c-187">以下命令使用`Save-PowerShellGetForOffline`可将所有组件都放入一个文件夹 `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="3b25c-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="3b25c-188">此时，您必须进行的内容`F:\OfflinePowerShellGet`供您断开连接的系统。</span><span class="sxs-lookup"><span data-stu-id="3b25c-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="3b25c-189">运行`Install-PowerShellGetOffline`cmdlet 来断开连接的系统上安装 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="3b25c-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="3b25c-190">不要在 PowerShell 会话中运行这些命令之前运行 PowerShellGet 至关重要。</span><span class="sxs-lookup"><span data-stu-id="3b25c-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="3b25c-191">PowerShellGet 加载到会话中，不能更新组件。</span><span class="sxs-lookup"><span data-stu-id="3b25c-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="3b25c-192">如果执行意外启动 PowerShellGet，请退出并重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3b25c-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="3b25c-193">运行这些命令后，已准备好将 PowerShellGet 发布到本地存储库。</span><span class="sxs-lookup"><span data-stu-id="3b25c-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="3b25c-194">若要确保安全，API 密钥不应在脚本中硬编码。</span><span class="sxs-lookup"><span data-stu-id="3b25c-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="3b25c-195">使用安全的密钥管理系统。</span><span class="sxs-lookup"><span data-stu-id="3b25c-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference

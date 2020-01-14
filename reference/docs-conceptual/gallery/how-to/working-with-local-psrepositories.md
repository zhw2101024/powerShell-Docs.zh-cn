---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery,psget
title: 使用本地 PSRepository
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415821"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="be3a2-103">使用专用 PowerShellGet 存储库</span><span class="sxs-lookup"><span data-stu-id="be3a2-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="be3a2-104">PowerShellGet 模块支持 PowerShell 库以外的存储库。</span><span class="sxs-lookup"><span data-stu-id="be3a2-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="be3a2-105">这些 cmdlet 支持以下场景：</span><span class="sxs-lookup"><span data-stu-id="be3a2-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="be3a2-106">支持在环境中使用一组受信任的、预先验证的 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="be3a2-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="be3a2-107">测试构建 PowerShell 模块或脚本的 CI/CD 管道</span><span class="sxs-lookup"><span data-stu-id="be3a2-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="be3a2-108">将 PowerShell 脚本和模块交付给无法访问 Internet 的系统</span><span class="sxs-lookup"><span data-stu-id="be3a2-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="be3a2-109">提供仅供你的组织使用的 PowerShell 脚本和模块</span><span class="sxs-lookup"><span data-stu-id="be3a2-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="be3a2-110">本文介绍如何设置本地 PowerShell 存储库。</span><span class="sxs-lookup"><span data-stu-id="be3a2-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="be3a2-111">本文还介绍了可以从 PowerShell 库获得的 [OfflinePowerShellGetDeploy][] 模块。</span><span class="sxs-lookup"><span data-stu-id="be3a2-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="be3a2-112">该模块包含 cmdlet，用于将 PowerShellGet 的最新版本安装到本地存储库中。</span><span class="sxs-lookup"><span data-stu-id="be3a2-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="be3a2-113">本地存储库类型</span><span class="sxs-lookup"><span data-stu-id="be3a2-113">Local repository types</span></span>

<span data-ttu-id="be3a2-114">有两种方法可以创建本地 PSRepository：NuGet 服务器或文件共享。</span><span class="sxs-lookup"><span data-stu-id="be3a2-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="be3a2-115">每种类型都有优点和缺点：</span><span class="sxs-lookup"><span data-stu-id="be3a2-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="be3a2-116">NuGet 服务器</span><span class="sxs-lookup"><span data-stu-id="be3a2-116">NuGet Server</span></span>

| <span data-ttu-id="be3a2-117">优点</span><span class="sxs-lookup"><span data-stu-id="be3a2-117">Advantages</span></span>| <span data-ttu-id="be3a2-118">缺点</span><span class="sxs-lookup"><span data-stu-id="be3a2-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="be3a2-119">精确模拟 powershell 库功能</span><span class="sxs-lookup"><span data-stu-id="be3a2-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="be3a2-120">多层应用需要操作规划和支持</span><span class="sxs-lookup"><span data-stu-id="be3a2-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="be3a2-121">NuGet 与 Visual Studio 等其他工具集成</span><span class="sxs-lookup"><span data-stu-id="be3a2-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="be3a2-122">需要身份验证模型和 NuGet 帐户管理</span><span class="sxs-lookup"><span data-stu-id="be3a2-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="be3a2-123">NuGet 支持 `.Nupkg` 包中的元数据</span><span class="sxs-lookup"><span data-stu-id="be3a2-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="be3a2-124">发布需要进行 API 密钥管理和维护</span><span class="sxs-lookup"><span data-stu-id="be3a2-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="be3a2-125">提供搜索、包管理等。</span><span class="sxs-lookup"><span data-stu-id="be3a2-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="be3a2-126">文件共享</span><span class="sxs-lookup"><span data-stu-id="be3a2-126">File Share</span></span>

| <span data-ttu-id="be3a2-127">优点</span><span class="sxs-lookup"><span data-stu-id="be3a2-127">Advantages</span></span>| <span data-ttu-id="be3a2-128">缺点</span><span class="sxs-lookup"><span data-stu-id="be3a2-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="be3a2-129">易于设置、备份和维护</span><span class="sxs-lookup"><span data-stu-id="be3a2-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="be3a2-130">PowerShellGet 使用的元数据不可用</span><span class="sxs-lookup"><span data-stu-id="be3a2-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="be3a2-131">简单安全模型 - 用户的共享权限</span><span class="sxs-lookup"><span data-stu-id="be3a2-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="be3a2-132">除了基本文件共享之外，没有 UI</span><span class="sxs-lookup"><span data-stu-id="be3a2-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="be3a2-133">没有诸如替换现有项之类的约束</span><span class="sxs-lookup"><span data-stu-id="be3a2-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="be3a2-134">有限的安全性且没有有关用户更新内容的记录</span><span class="sxs-lookup"><span data-stu-id="be3a2-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="be3a2-135">PowerShellGet 适用于任一类型，并支持查找版本和依赖项安装。</span><span class="sxs-lookup"><span data-stu-id="be3a2-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="be3a2-136">但是，一些适用于 PowerShell 库的功能不适用于基本 NuGet 服务器或文件共享。</span><span class="sxs-lookup"><span data-stu-id="be3a2-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="be3a2-137">所有内容都是一个包 - 不区分脚本、模块、DSC 资源或角色功能。</span><span class="sxs-lookup"><span data-stu-id="be3a2-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="be3a2-138">文件共享服务器不能查看包元数据，包括标记。</span><span class="sxs-lookup"><span data-stu-id="be3a2-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="be3a2-139">创建本地存储库</span><span class="sxs-lookup"><span data-stu-id="be3a2-139">Creating a local repository</span></span>

<span data-ttu-id="be3a2-140">以下文章列出了设置自己的 NuGet 服务器的步骤。</span><span class="sxs-lookup"><span data-stu-id="be3a2-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="be3a2-141">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="be3a2-141">[NuGet.Server][]</span></span>

<span data-ttu-id="be3a2-142">按照以下步骤操作，直到添加包为止。</span><span class="sxs-lookup"><span data-stu-id="be3a2-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="be3a2-143">本文稍后会介绍有关[发布包](#publishing-to-a-local-repository)的步骤。</span><span class="sxs-lookup"><span data-stu-id="be3a2-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="be3a2-144">对于基于文件共享的存储库，请确保用户有权访问文件共享。</span><span class="sxs-lookup"><span data-stu-id="be3a2-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="be3a2-145">注册本地存储库</span><span class="sxs-lookup"><span data-stu-id="be3a2-145">Registering a local repository</span></span>

<span data-ttu-id="be3a2-146">在使用存储库之前，必须使用 `Register-PSRepository` 命令对其进行注册。</span><span class="sxs-lookup"><span data-stu-id="be3a2-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="be3a2-147">在下面的示例中，假定你信任自己的存储库，将“InstallationPolicy”  设置为“受信任”  。</span><span class="sxs-lookup"><span data-stu-id="be3a2-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="be3a2-148">请注意这两个命令处理 ScriptSourceLocation  方式的差异。</span><span class="sxs-lookup"><span data-stu-id="be3a2-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="be3a2-149">对于基于文件共享的存储库，SourceLocation  和 ScriptSourceLocation  必须匹配。</span><span class="sxs-lookup"><span data-stu-id="be3a2-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="be3a2-150">对于基于 Web 的存储库，它们必须不同，因此，在此示例中，在 SourceLocation  中添加了一个尾随的“/”。</span><span class="sxs-lookup"><span data-stu-id="be3a2-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="be3a2-151">如果希望将新创建的 PSRepository 作为默认存储库，则必须注销所有其他 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="be3a2-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="be3a2-152">例如：</span><span class="sxs-lookup"><span data-stu-id="be3a2-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="be3a2-153">保留了存储库名称“PSGallery”以供 PowerShell 库使用。</span><span class="sxs-lookup"><span data-stu-id="be3a2-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="be3a2-154">可以注销 PSGallery，但不能对任何其他存储库重用名称 PSGallery。</span><span class="sxs-lookup"><span data-stu-id="be3a2-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="be3a2-155">如需还原 PSGallery，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="be3a2-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="be3a2-156">发布到本地存储库</span><span class="sxs-lookup"><span data-stu-id="be3a2-156">Publishing to a local repository</span></span>

<span data-ttu-id="be3a2-157">一旦注册本地 PSRepository，就可以将其发布到本地 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="be3a2-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="be3a2-158">有两个主要发布方案：发布你自己的模块和发布 PSGallery 中的模块。</span><span class="sxs-lookup"><span data-stu-id="be3a2-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="be3a2-159">发布自己编写的模块</span><span class="sxs-lookup"><span data-stu-id="be3a2-159">Publishing a module you authored</span></span>

<span data-ttu-id="be3a2-160">使用 `Publish-Module` 和 `Publish-Script` 将模块发布到本地 PSRepository，具体方法与对 PowerShell 库执行的操作相同。</span><span class="sxs-lookup"><span data-stu-id="be3a2-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="be3a2-161">指定代码的位置</span><span class="sxs-lookup"><span data-stu-id="be3a2-161">Specify the location for your code</span></span>
- <span data-ttu-id="be3a2-162">提供 API 密钥</span><span class="sxs-lookup"><span data-stu-id="be3a2-162">Supply an API key</span></span>
- <span data-ttu-id="be3a2-163">指定存储库名称。</span><span class="sxs-lookup"><span data-stu-id="be3a2-163">Specify the repository name.</span></span> <span data-ttu-id="be3a2-164">例如： `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="be3a2-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="be3a2-165">必须在 NuGet 服务器中创建一个帐户，然后登录以生成并保存 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="be3a2-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="be3a2-166">对于文件共享，请对 NuGetApiKey 值使用任何非空字符串。</span><span class="sxs-lookup"><span data-stu-id="be3a2-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="be3a2-167">示例：</span><span class="sxs-lookup"><span data-stu-id="be3a2-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="be3a2-168">若要确保安全，不应在脚本中对 API 密钥进行硬编码。</span><span class="sxs-lookup"><span data-stu-id="be3a2-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="be3a2-169">使用安全的密钥管理系统。</span><span class="sxs-lookup"><span data-stu-id="be3a2-169">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="be3a2-170">从 PSGallery 发布模块</span><span class="sxs-lookup"><span data-stu-id="be3a2-170">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="be3a2-171">要将模块从 PSGallery 发布到本地 PSRepository，可以使用“Save-Package”cmdlet。</span><span class="sxs-lookup"><span data-stu-id="be3a2-171">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="be3a2-172">指定包的名称</span><span class="sxs-lookup"><span data-stu-id="be3a2-172">Specify the Name of the Package</span></span>
- <span data-ttu-id="be3a2-173">指定“NuGet”作为提供程序</span><span class="sxs-lookup"><span data-stu-id="be3a2-173">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="be3a2-174">将 PSGallery 位置指定为源 (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="be3a2-174">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="be3a2-175">指定本地存储库的路径</span><span class="sxs-lookup"><span data-stu-id="be3a2-175">Specify the path to your local Repository</span></span>

<span data-ttu-id="be3a2-176">示例：</span><span class="sxs-lookup"><span data-stu-id="be3a2-176">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="be3a2-177">如果本地 PSRepository 基于 Web，则需要另外执行一个使用 nuget.exe 的步骤才能进行发布。</span><span class="sxs-lookup"><span data-stu-id="be3a2-177">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="be3a2-178">请参阅有关使用 [nuget.exe][] 的文档。</span><span class="sxs-lookup"><span data-stu-id="be3a2-178">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="be3a2-179">在断开连接的系统上安装 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="be3a2-179">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="be3a2-180">在要求系统与 Internet 断开连接的环境中，部署 PowerShellGet 非常困难。</span><span class="sxs-lookup"><span data-stu-id="be3a2-180">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="be3a2-181">PowerShellGet 有一个启动过程，它会在第一次使用时安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="be3a2-181">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="be3a2-182">PowerShell 库中的 OfflinePowerShellGetDeploy 模块提供了支持此启动过程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="be3a2-182">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="be3a2-183">若要启动离线部署，需要：</span><span class="sxs-lookup"><span data-stu-id="be3a2-183">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="be3a2-184">在连接 Internet 的系统和断开连接的系统上下载并安装 OfflinePowerShellGetDeploy</span><span class="sxs-lookup"><span data-stu-id="be3a2-184">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="be3a2-185">使用 `Save-PowerShellGetForOffline` cmdlet 在连接 Internet 的系统上下载 PowerShellGet 及其依赖项</span><span class="sxs-lookup"><span data-stu-id="be3a2-185">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="be3a2-186">将 PowerShellGet 及其依赖项从连接 Internet 的系统复制到断开连接的系统</span><span class="sxs-lookup"><span data-stu-id="be3a2-186">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="be3a2-187">在断开连接的系统上使用 `Install-PowerShellGetOffline`，将 PowerShellGet 及其依赖项置于适当的文件夹中</span><span class="sxs-lookup"><span data-stu-id="be3a2-187">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="be3a2-188">以下命令使用 `Save-PowerShellGetForOffline` 将所有组件都放入文件夹 `f:\OfflinePowerShellGet` 中</span><span class="sxs-lookup"><span data-stu-id="be3a2-188">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="be3a2-189">此时，必须使 `F:\OfflinePowerShellGet` 的内容对断开连接的系统可用。</span><span class="sxs-lookup"><span data-stu-id="be3a2-189">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="be3a2-190">运行 `Install-PowerShellGetOffline` cmdlet 在断开连接的系统上安装 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="be3a2-190">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="be3a2-191">在运行这些命令之前，不要在 PowerShell 会话中运行 PowerShellGet，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="be3a2-191">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="be3a2-192">一旦 PowerShellGet 加载到会话中，就无法更新组件。</span><span class="sxs-lookup"><span data-stu-id="be3a2-192">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="be3a2-193">如果意外启动 PowerShellGet，请退出并重启 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="be3a2-193">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="be3a2-194">运行这些命令后，便可以将 PowerShellGet 发布到本地存储库。</span><span class="sxs-lookup"><span data-stu-id="be3a2-194">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="be3a2-195">使用打包解决方案托管 PowerShellGet 存储库</span><span class="sxs-lookup"><span data-stu-id="be3a2-195">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="be3a2-196">你还可以使用打包解决方案（如 Azure Artifacts）来托管专用或公用的 PowerShellGet 存储库。</span><span class="sxs-lookup"><span data-stu-id="be3a2-196">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="be3a2-197">有关详细信息和说明，请参阅 [Azure Artifacts 文档](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library)。</span><span class="sxs-lookup"><span data-stu-id="be3a2-197">For more information and instructions, see the [Azure Artifacts documentation](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be3a2-198">若要确保安全，不应在脚本中对 API 密钥进行硬编码。</span><span class="sxs-lookup"><span data-stu-id="be3a2-198">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="be3a2-199">使用安全的密钥管理系统。</span><span class="sxs-lookup"><span data-stu-id="be3a2-199">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference

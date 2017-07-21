---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
title: "WMF 5.1 中的新方案和功能"
ms.openlocfilehash: 02c27711c886916da56bb382b1bc0187f1e30805
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="3aa1d-103">WMF 5.1 中的新方案和功能</span><span class="sxs-lookup"><span data-stu-id="3aa1d-103">New Scenarios and Features in WMF 5.1</span></span> #

> <span data-ttu-id="3aa1d-104">注意：此信息是预发布版本，可能会进行更改。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="3aa1d-105">PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="3aa1d-105">PowerShell Editions</span></span> ##
<span data-ttu-id="3aa1d-106">从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="3aa1d-107">**桌面版：**以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="3aa1d-108">**核心版：**以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="3aa1d-109">**详细了解如何使用 PowerShell 版本**</span><span class="sxs-lookup"><span data-stu-id="3aa1d-109">**Learn more about using PowerShell Editions**</span></span>
- [<span data-ttu-id="3aa1d-110">确定正在运行的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="3aa1d-110">Determine running edition of PowerShell</span></span>]()
- [<span data-ttu-id="3aa1d-111">声明模块与特定 PowerShell 版本的兼容性</span><span class="sxs-lookup"><span data-stu-id="3aa1d-111">Declare a module's compatibility to specific PowerShell versions</span></span>]()
- [<span data-ttu-id="3aa1d-112">按 CompatiblePSEditions 筛选 Get-Module 结果</span><span class="sxs-lookup"><span data-stu-id="3aa1d-112">Filter Get-Module results by CompatiblePSEditions</span></span>]()
- [<span data-ttu-id="3aa1d-113">阻止脚本执行，除非在 PowerShell 的兼容版本上运行</span><span class="sxs-lookup"><span data-stu-id="3aa1d-113">Prevent script execution unless run on a compatible edition of PowerShell</span></span>]()

## <a name="catalog-cmdlets"></a><span data-ttu-id="3aa1d-114">目录 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3aa1d-114">Catalog Cmdlets</span></span>  

<span data-ttu-id="3aa1d-115">在 [Microsoft.PowerShell.Security](https://technet.microsoft.com/en-us/library/hh847877.aspx) 模块中新增了两个新 cmdlet；这两个 cmdlet 可用于生成和验证 Windows 目录文件。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](https://technet.microsoft.com/en-us/library/hh847877.aspx) module; these generate and validate Windows catalog files.</span></span>  

###<a name="new-filecatalog"></a><span data-ttu-id="3aa1d-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="3aa1d-116">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="3aa1d-117">New-FileCatalog 用于为文件夹和文件集合创建 Windows 目录文件。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span> <span data-ttu-id="3aa1d-118">该目录文件包含指定路径中的所有文件的哈希值。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-118">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="3aa1d-119">用户可以分发文件夹集合以及代表这些文件夹的对应的目录文件。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="3aa1d-120">该信息对于验证自目录创建以来是否对文件夹进行了任何更改很有用。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="3aa1d-121">支持目录版本 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-121">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="3aa1d-122">版本 1 使用 SHA1 哈希算法来创建文件哈希值；版本 2 则使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="3aa1d-123">Windows Server 2008 R2 或 Windows 7 不支持目录版本 2。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="3aa1d-124">你应在 Windows 8、Windows Server 2012 及更高版本的操作系统上使用目录版本 2。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>  

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="3aa1d-125">这将创建目录文件。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-125">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="3aa1d-126">若要验证目录文件（上面示例中的 Pester.cat 文件）的完整性，应使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet 对其进行签名。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


###<a name="test-filecatalog"></a><span data-ttu-id="3aa1d-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="3aa1d-127">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="3aa1d-128">Test-FileCatalog 用于验证代表一组文件夹的目录。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span> 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="3aa1d-129">此 cmdlet 将目录中找到的所有文件的哈希值及其相对路径与磁盘中的进行比较。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="3aa1d-130">如果它检测到文件哈希值和路径之间存在任何不匹配，将返回状态 ValidationFailed。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="3aa1d-131">用户可通过使用 *-Detailed* 参数检索所有这些信息。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="3aa1d-132">它还在“签名”属性中显示目录的签名状态，该结果与针对目录文件调用 [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet 的结果相同。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="3aa1d-133">用户也可以使用 -FilesToSkip 参数在验证过程中跳过任何文件。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span> 


## <a name="module-analysis-cache"></a><span data-ttu-id="3aa1d-134">模块分析缓存</span><span class="sxs-lookup"><span data-stu-id="3aa1d-134">Module Analysis Cache</span></span> ##
<span data-ttu-id="3aa1d-135">从 WMF 5.1 开始，PowerShell 针对用于缓存有关模块的数据（如它导出的命令）的文件提供了控制。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="3aa1d-136">默认情况下，此缓存存储在文件 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 中。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="3aa1d-137">缓存通常在启动时进行读取（同时搜索命令），在模块导入一段时间之后在后台线程上进行写入。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="3aa1d-138">若要更改缓存的默认位置，可在启动 PowerShell 前，设置 `$env:PSModuleAnalysisCachePath` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="3aa1d-139">对此环境变量进行的更改只影响子进程。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-139">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="3aa1d-140">值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="3aa1d-141">若要禁用文件缓存，请将此值设置为无效位置，例如：</span><span class="sxs-lookup"><span data-stu-id="3aa1d-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="3aa1d-142">这会将路径设置为无效设备。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-142">This sets the path to an invalid device.</span></span> <span data-ttu-id="3aa1d-143">如果 PowerShell 无法写入路径，则不会返回任何错误，不过你可能会看到通过使用跟踪器进行报告的错误：</span><span class="sxs-lookup"><span data-stu-id="3aa1d-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="3aa1d-144">从缓存写出时，PowerShell 会检查不再存在的模块以避免进行不必要的大型缓存。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="3aa1d-145">有时不需要这些检查，在这种情况下可以通过设置关闭它们：</span><span class="sxs-lookup"><span data-stu-id="3aa1d-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="3aa1d-146">此环境变量的设置会在当前进程中立即生效。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-146">Setting this environment variable will take effect immediately in the current process.</span></span>

##<a name="specifying-module-version"></a><span data-ttu-id="3aa1d-147">指定模块版本</span><span class="sxs-lookup"><span data-stu-id="3aa1d-147">Specifying module version</span></span>

<span data-ttu-id="3aa1d-148">在 WMF 5.1 中，`using module` 的行为方式与 PowerShell 中其他与模块相关的构造相同。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="3aa1d-149">以前无法指定特定模块版本；如果有多个版本存在，则这会导致错误。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>


<span data-ttu-id="3aa1d-150">在 WMF 5.1 中：</span><span class="sxs-lookup"><span data-stu-id="3aa1d-150">In WMF 5.1:</span></span>

* <span data-ttu-id="3aa1d-151">可以使用 `ModuleSpecification` [哈希表](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-151">You can use `ModuleSpecification` [hash table](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx).</span></span> <span data-ttu-id="3aa1d-152">此哈希表具有与 `Get-Module -FullyQualifiedName` 相同的格式。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="3aa1d-153">**示例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="3aa1d-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="3aa1d-154">如果有多个版本的模块，则 PowerShell 会使用与 `Import-Module` **相同的解析逻辑**，不会返回错误 - - 行为与 `Import-Module` 和 `Import-DscResource` 相同。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>


##<a name="improvements-to-pester"></a><span data-ttu-id="3aa1d-155">针对 Pester 的改进</span><span class="sxs-lookup"><span data-stu-id="3aa1d-155">Improvements to Pester</span></span>
<span data-ttu-id="3aa1d-156">在 WMF 5.1 中，PowerShell 随附的 Pester 版本从 3.3.5 更新到 3.4.0，并且添加了一个提交：https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e，从而改善了 Nano 服务器上的 Pester 的行为。</span><span class="sxs-lookup"><span data-stu-id="3aa1d-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span> 

<span data-ttu-id="3aa1d-157">你可以通过检查 https://github.com/pester/Pester/blob/master/CHANGELOG.md 上的 ChangeLog.md 文件查看从版本 3.3.5 到 3.4.0 的更改</span><span class="sxs-lookup"><span data-stu-id="3aa1d-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>


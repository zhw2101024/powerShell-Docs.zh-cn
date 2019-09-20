---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.x 发行说明
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147577"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="10d82-103">Windows Management Framework (WMF) 5.x 发行说明</span><span class="sxs-lookup"><span data-stu-id="10d82-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="10d82-104">WMF 5.0 更改</span><span class="sxs-lookup"><span data-stu-id="10d82-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="10d82-105">PowerShell 5.0 添加了新的结构化信息  流</span><span class="sxs-lookup"><span data-stu-id="10d82-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="10d82-106">对 DSC 的改进包括以下四个新 DSC 资源：</span><span class="sxs-lookup"><span data-stu-id="10d82-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="10d82-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="10d82-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="10d82-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="10d82-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="10d82-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="10d82-109">ServiceSet</span></span>
  - <span data-ttu-id="10d82-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="10d82-110">ProcessSet</span></span>
- <span data-ttu-id="10d82-111">添加了 Just Enough Administration 以通过 PowerShell 远程处理实现基于角色的管理</span><span class="sxs-lookup"><span data-stu-id="10d82-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="10d82-112">PowerShell 5.0 扩展了语言以包括用户定义的类和枚举</span><span class="sxs-lookup"><span data-stu-id="10d82-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="10d82-113">改进了 PowerShell ISE 中的调试功能并添加了远程调试</span><span class="sxs-lookup"><span data-stu-id="10d82-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="10d82-114">添加了 PowerShellGet 和 PackageManagement 模块</span><span class="sxs-lookup"><span data-stu-id="10d82-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="10d82-115">增强了 PowerShell 脚本日志记录和脚本</span><span class="sxs-lookup"><span data-stu-id="10d82-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="10d82-116">添加了加密消息语法 cmdlet</span><span class="sxs-lookup"><span data-stu-id="10d82-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="10d82-117">WMF 5.0 包括适用于 Windows 的 NetworkSwitchManager 模块</span><span class="sxs-lookup"><span data-stu-id="10d82-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="10d82-118">添加了 Microsoft.PowerShell.ODataUtils 模块</span><span class="sxs-lookup"><span data-stu-id="10d82-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="10d82-119">添加了对软件清单日志记录 (SIL) 的支持</span><span class="sxs-lookup"><span data-stu-id="10d82-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="10d82-120">提供新的或更新的 cmdlet 以响应用户请求和问题</span><span class="sxs-lookup"><span data-stu-id="10d82-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="10d82-121">WMF 5.1 更改</span><span class="sxs-lookup"><span data-stu-id="10d82-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="10d82-122">WMF 5.1 包括与 Windows Server 2016 一起发行的 PowerShell、WMI、WinRM 以及软件清单日志记录 (SIL) 组件。</span><span class="sxs-lookup"><span data-stu-id="10d82-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="10d82-123">WMF 5.1 可安装在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 和 2012 R2 上，并提供了对 WMF 5.0 的多个改进，其中包括：</span><span class="sxs-lookup"><span data-stu-id="10d82-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="10d82-124">新 cmdlet</span><span class="sxs-lookup"><span data-stu-id="10d82-124">New cmdlets</span></span>
- <span data-ttu-id="10d82-125">PowerShellGet 改进包括强制签名模块和安装 JEA 模块</span><span class="sxs-lookup"><span data-stu-id="10d82-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="10d82-126">PackageManagement 增加了对容器、CBS 安装程序、基于 EXE 的安装程序、CAB 包的支持</span><span class="sxs-lookup"><span data-stu-id="10d82-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="10d82-127">DSC 和 PowerShell 类的调试改进</span><span class="sxs-lookup"><span data-stu-id="10d82-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="10d82-128">安全增强包括强制执行来自请求服务器和使用 PowerShellGet cmdlet 时的目录签名模块</span><span class="sxs-lookup"><span data-stu-id="10d82-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="10d82-129">响应大量的用户请求和问题</span><span class="sxs-lookup"><span data-stu-id="10d82-129">Responses to a number of user requests and issues</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10d82-130">在 Windows Server 2008 或 Windows 7 上安装 WMF 5.1 之前，请确认未安装 WMF 3.0。</span><span class="sxs-lookup"><span data-stu-id="10d82-130">Before you install WMF 5.1 on Windows Server 2008 or Windows 7, confirm that WMF 3.0 isn't installed.</span></span> <span data-ttu-id="10d82-131">有关详细信息，请参阅 [Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 系统必备](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1)。</span><span class="sxs-lookup"><span data-stu-id="10d82-131">For more information, see [WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="10d82-132">PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="10d82-132">PowerShell Editions</span></span>

<span data-ttu-id="10d82-133">从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。</span><span class="sxs-lookup"><span data-stu-id="10d82-133">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="10d82-134">**桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="10d82-134">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="10d82-135">**核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="10d82-135">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="10d82-136">详细了解如何使用 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="10d82-136">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="10d82-137">使用 $PSVersionTable 确定正在运行的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="10d82-137">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="10d82-138">使用 PSEdition 参数按 CompatiblePSEditions 筛选 Get-Module 结果</span><span class="sxs-lookup"><span data-stu-id="10d82-138">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="10d82-139">阻止脚本执行，除非在 PowerShell 的兼容版本上运行</span><span class="sxs-lookup"><span data-stu-id="10d82-139">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="10d82-140">声明模块与特定 PowerShell 版本的兼容性</span><span class="sxs-lookup"><span data-stu-id="10d82-140">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="10d82-141">模块分析缓存</span><span class="sxs-lookup"><span data-stu-id="10d82-141">Module Analysis Cache</span></span>

<span data-ttu-id="10d82-142">从 WMF 5.1 开始，PowerShell 针对用于缓存有关模块的数据（如它导出的命令）的文件提供了控制。</span><span class="sxs-lookup"><span data-stu-id="10d82-142">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="10d82-143">默认情况下，此缓存存储在文件 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 中。</span><span class="sxs-lookup"><span data-stu-id="10d82-143">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="10d82-144">缓存通常在启动时进行读取（同时搜索命令），在模块导入一段时间之后在后台线程上进行写入。</span><span class="sxs-lookup"><span data-stu-id="10d82-144">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="10d82-145">若要更改缓存的默认位置，可在启动 PowerShell 前，设置 `$env:PSModuleAnalysisCachePath` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="10d82-145">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="10d82-146">对此环境变量进行的更改只影响子进程。</span><span class="sxs-lookup"><span data-stu-id="10d82-146">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="10d82-147">值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。</span><span class="sxs-lookup"><span data-stu-id="10d82-147">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="10d82-148">若要禁用文件缓存，请将此值设置为无效位置，例如：</span><span class="sxs-lookup"><span data-stu-id="10d82-148">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="10d82-149">这会将路径设置为无效设备。</span><span class="sxs-lookup"><span data-stu-id="10d82-149">This sets the path to an invalid device.</span></span> <span data-ttu-id="10d82-150">如果 PowerShell 无法写入路径，则不会返回任何错误，不过你可能会看到通过使用跟踪器进行报告的错误：</span><span class="sxs-lookup"><span data-stu-id="10d82-150">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="10d82-151">从缓存写出时，PowerShell 会检查不再存在的模块以避免进行不必要的大型缓存。</span><span class="sxs-lookup"><span data-stu-id="10d82-151">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="10d82-152">有时不需要这些检查，在这种情况下可以通过设置关闭它们：</span><span class="sxs-lookup"><span data-stu-id="10d82-152">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="10d82-153">此环境变量的设置会在当前进程中立即生效。</span><span class="sxs-lookup"><span data-stu-id="10d82-153">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="10d82-154">指定模块版本</span><span class="sxs-lookup"><span data-stu-id="10d82-154">Specifying module version</span></span>

<span data-ttu-id="10d82-155">在 WMF 5.1 中，`using module` 的行为方式与 PowerShell 中其他与模块相关的构造相同。</span><span class="sxs-lookup"><span data-stu-id="10d82-155">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="10d82-156">以前无法指定特定模块版本；如果有多个版本存在，则这会导致错误。</span><span class="sxs-lookup"><span data-stu-id="10d82-156">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="10d82-157">在 WMF 5.1 中：</span><span class="sxs-lookup"><span data-stu-id="10d82-157">In WMF 5.1:</span></span>

- <span data-ttu-id="10d82-158">可以使用 [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。</span><span class="sxs-lookup"><span data-stu-id="10d82-158">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

  <span data-ttu-id="10d82-159">此哈希表具有与 `Get-Module -FullyQualifiedName` 相同的格式。</span><span class="sxs-lookup"><span data-stu-id="10d82-159">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="10d82-160">**示例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="10d82-160">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="10d82-161">如果有多个版本的模块，则 PowerShell 会使用与 `Import-Module` **相同的解析逻辑**，不会返回错误 - - 行为与 `Import-Module` 和 `Import-DscResource` 相同。</span><span class="sxs-lookup"><span data-stu-id="10d82-161">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="10d82-162">针对 Pester 的改进</span><span class="sxs-lookup"><span data-stu-id="10d82-162">Improvements to Pester</span></span>

<span data-ttu-id="10d82-163">在 WMF 5.1 中，PowerShell 随附的 Pester 版本已从 3.3.5 更新到 3.4.0。</span><span class="sxs-lookup"><span data-stu-id="10d82-163">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="10d82-164">此更新会在 Nano Server 上启用更好的 Pester 行为。</span><span class="sxs-lookup"><span data-stu-id="10d82-164">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="10d82-165">可以通过在 GitHub 存储库中检查 [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) 查看 Pest 的更改。</span><span class="sxs-lookup"><span data-stu-id="10d82-165">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>

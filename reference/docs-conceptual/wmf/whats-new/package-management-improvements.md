---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.1 中对包管理的改进
ms.openlocfilehash: cb19c2d71391b5729ce9d73fc6b033270f8db307
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325118"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="312e2-103">WMF 5.1 中对包管理的改进</span><span class="sxs-lookup"><span data-stu-id="312e2-103">Improvements to Package Management in WMF 5.1</span></span>

<span data-ttu-id="312e2-104">以下是 WMF 5.1 中所做的修复：</span><span class="sxs-lookup"><span data-stu-id="312e2-104">The following are the fixes made in the WMF 5.1:</span></span>

## <a name="version-alias"></a><span data-ttu-id="312e2-105">版本别名</span><span class="sxs-lookup"><span data-stu-id="312e2-105">Version Alias</span></span>

<span data-ttu-id="312e2-106">**情形**：如果在系统上安装了包 P1 的版本 1.0 和 2.0，并且要卸载版本 1.0，则会运行 `Uninstall-Package -Name P1 -Version 1.0`，并且预计在运行该 cmdlet 之后将卸载版本 1.0。</span><span class="sxs-lookup"><span data-stu-id="312e2-106">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="312e2-107">但是结果是卸载了版本 2.0。</span><span class="sxs-lookup"><span data-stu-id="312e2-107">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="312e2-108">出现此问题是因为 `-Version` 参数是 `-MinimumVersion` 参数的别名。</span><span class="sxs-lookup"><span data-stu-id="312e2-108">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="312e2-109">当 PackageManagement 查找具有最低版本 1.0 的合格包时，它会返回最新版本。</span><span class="sxs-lookup"><span data-stu-id="312e2-109">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="312e2-110">在正常情况下需要此行为，因为查找最新版本通常是所需结果。</span><span class="sxs-lookup"><span data-stu-id="312e2-110">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="312e2-111">但是，它不应该应用于 `Uninstall-Package` 情况。</span><span class="sxs-lookup"><span data-stu-id="312e2-111">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="312e2-112">**解决方案**：在 PackageManagement（也称为 OneGet）和 PowerShellGet 中完全删除了 `-Version`</span><span class="sxs-lookup"><span data-stu-id="312e2-112">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="312e2-113">别名。</span><span class="sxs-lookup"><span data-stu-id="312e2-113">OneGet) and PowerShellGet.</span></span>

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="312e2-114">多个用于启动 NuGet 提供程序的提示</span><span class="sxs-lookup"><span data-stu-id="312e2-114">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="312e2-115">**情形**：在计算机上首次运行 `Find-Module`、`Install-Module` 或其他 PackageManagement cmdlet 时，PackageManagement 会尝试启动 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="312e2-115">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="312e2-116">它这样做是因为 PowerShellGet 提供程序还使用 NuGet 提供程序来下载 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="312e2-116">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span>
<span data-ttu-id="312e2-117">PackageManagement 随后会提示用户输入安装 NuGet 提供程序的权限。</span><span class="sxs-lookup"><span data-stu-id="312e2-117">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="312e2-118">用户选择“yes”进行启动之后，会安装最新版本的 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="312e2-118">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="312e2-119">但是在某些情况下，当在计算机上安装了旧版本的 NuGet 提供程序时，较旧版本的 NuGet 有时会先加载到 PowerShell 会话中（这是 PackageManagement 中的争用条件）。</span><span class="sxs-lookup"><span data-stu-id="312e2-119">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="312e2-120">但是 PowerShellGet 需要更新版本的 NuGet 提供程序才可正常运行，因此 PowerShellGet 会要求 PackageManagement 再次启动 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="312e2-120">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span>
<span data-ttu-id="312e2-121">这会导致出现多个用于启动 NuGet 提供程序的提示。</span><span class="sxs-lookup"><span data-stu-id="312e2-121">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="312e2-122">**解决方案**：在 WMF 5.1 中，PackageManagement 加载最新版本的 NuGet 提供程序，以避免出现多个要求启动 NuGet 提供程序的提示。</span><span class="sxs-lookup"><span data-stu-id="312e2-122">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="312e2-123">还可以通过手动删除旧版本的 NuGet 提供程序（NuGet-Anycpu.exe，如果在 $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies 中存在）来解决此问题</span><span class="sxs-lookup"><span data-stu-id="312e2-123">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="312e2-124">在仅具有 intranet 访问的计算机上支持 PackageManagement</span><span class="sxs-lookup"><span data-stu-id="312e2-124">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="312e2-125">**情形**：对于企业情形，人们在没有 Internet 访问，而是只有 Intranet 的环境中工作。</span><span class="sxs-lookup"><span data-stu-id="312e2-125">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="312e2-126">在 WMF 5.0 中，PackageManagement 不支持这种情况。</span><span class="sxs-lookup"><span data-stu-id="312e2-126">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="312e2-127">**情形**：在 WMF 5.0 中，PackageManagement 不支持仅具有 Intranet（但没有 Internet）访问的计算机。</span><span class="sxs-lookup"><span data-stu-id="312e2-127">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="312e2-128">**解决方案**：在 WMF 5.1 中，可以按照以下步骤允许 Intranet 计算机使用 PackageManagement：</span><span class="sxs-lookup"><span data-stu-id="312e2-128">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="312e2-129">使用 `Install-PackageProvider -Name NuGet`，通过具有 Internet 连接的其他计算机下载 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="312e2-129">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="312e2-130">在 `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` 或 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget` 下找到 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="312e2-130">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="312e2-131">将二进制文件复制到 Intranet 计算机可以访问的文件夹或网络共享位置，然后使用 `Install-PackageProvider -Name NuGet -Source <Path to folder>` 安装 NuGet 提供程序。</span><span class="sxs-lookup"><span data-stu-id="312e2-131">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


## <a name="event-logging-improvements"></a><span data-ttu-id="312e2-132">事件日志记录改进</span><span class="sxs-lookup"><span data-stu-id="312e2-132">Event logging improvements</span></span>

<span data-ttu-id="312e2-133">安装包时，你会更改计算机的状态。</span><span class="sxs-lookup"><span data-stu-id="312e2-133">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="312e2-134">在 WMF 5.1 中，PackageManagement 现在针对 `Install-Package`、`Uninstall-Package` 和 `Save-Package` 活动将事件记录到 Windows 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="312e2-134">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="312e2-135">对于 PowerShell，事件日志是相同的，即 `Microsoft-Windows-PowerShell, Operational`。</span><span class="sxs-lookup"><span data-stu-id="312e2-135">The Event log is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

## <a name="support-for-basic-authentication"></a><span data-ttu-id="312e2-136">对基本身份验证的支持</span><span class="sxs-lookup"><span data-stu-id="312e2-136">Support for basic authentication</span></span>

<span data-ttu-id="312e2-137">在 WMF 5.1 中，PackageManagement 支持从需要基本身份验证的存储库查找和安装包。</span><span class="sxs-lookup"><span data-stu-id="312e2-137">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="312e2-138">可以向 `Find-Package` 和 `Install-Package` cmdlet 提供凭据。</span><span class="sxs-lookup"><span data-stu-id="312e2-138">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="312e2-139">例如：</span><span class="sxs-lookup"><span data-stu-id="312e2-139">For example:</span></span>

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="312e2-140">支持在代理后面使用 PackageManagement</span><span class="sxs-lookup"><span data-stu-id="312e2-140">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="312e2-141">在 WMF 5.1 中，PackageManagement 现在采用新的代理参数 `-ProxyCredential` 和 `-Proxy`。</span><span class="sxs-lookup"><span data-stu-id="312e2-141">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="312e2-142">使用这些参数可以向 PackageManagement cmdlets 指定代理 URL 和凭据。</span><span class="sxs-lookup"><span data-stu-id="312e2-142">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="312e2-143">默认情况下，会使用系统代理设置。</span><span class="sxs-lookup"><span data-stu-id="312e2-143">By default, system proxy settings are used.</span></span> <span data-ttu-id="312e2-144">例如：</span><span class="sxs-lookup"><span data-stu-id="312e2-144">For example:</span></span>

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```

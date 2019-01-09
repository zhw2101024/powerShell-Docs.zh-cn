---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: 库,powershell,cmdlet,psgallery
title: 具有兼容 PowerShell 版本或操作系统包
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747698"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="bf638-103">具有兼容 PowerShell 版本或操作系统包</span><span class="sxs-lookup"><span data-stu-id="bf638-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="bf638-104">从版本 5.1 开始，PowerShell 提供了各种版本，表现出不同的功能集和平台兼容性。</span><span class="sxs-lookup"><span data-stu-id="bf638-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="bf638-105">搜索的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="bf638-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="bf638-106">两个 Powershell 版本是：</span><span class="sxs-lookup"><span data-stu-id="bf638-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="bf638-107">Desktop Edition.NET Framework 上构建，并提供与面向新版的 Server Core 等的 Windows 和 Windows 桌面的完整占用空间减小版本上运行的 PowerShell 脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="bf638-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="bf638-108">**核心版：**.NET Core 上生成，并提供与面向版本的 Nano Server 等的 Windows 和 Windows IoT 的占用空间减少的版本上运行的 PowerShell 脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="bf638-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="bf638-109">PowerShell 库允许您为特定 PowerShell 版本筛选兼容包</span><span class="sxs-lookup"><span data-stu-id="bf638-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="bf638-110">如果包具有兼容 PSEditions 指定，它们被列为 PowerShell Editions 的一部分包显示页和包的结果。</span><span class="sxs-lookup"><span data-stu-id="bf638-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="bf638-111">您还可以使用 PowerShell 的兼容包的搜索。</span><span class="sxs-lookup"><span data-stu-id="bf638-111">You can also search for compatible packages using PowerShell.</span></span>

![具有 PSEditions 的项显示页](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="bf638-113">搜索的库 UI 中的包适用于 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="bf638-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="bf638-114">使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的包。</span><span class="sxs-lookup"><span data-stu-id="bf638-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="bf638-115">使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。</span><span class="sxs-lookup"><span data-stu-id="bf638-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![在结果中搜索兼容 Core PSEdition 的项](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="bf638-117">使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。</span><span class="sxs-lookup"><span data-stu-id="bf638-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![在结果中搜索兼容 Desktop PSEdition 的项](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="bf638-119">搜索以查找使用 PowerShell 的兼容版本的包</span><span class="sxs-lookup"><span data-stu-id="bf638-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="bf638-120">可以指定标记 PowerShell 版本和操作系统进行筛选。</span><span class="sxs-lookup"><span data-stu-id="bf638-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="bf638-121">您使用`Find-Package`cmdlet 指定`-Tag`参数来指定 edition （和 OS） 您的目标。</span><span class="sxs-lookup"><span data-stu-id="bf638-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="bf638-122">喜欢这个：</span><span class="sxs-lookup"><span data-stu-id="bf638-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="bf638-123">搜索由操作系统</span><span class="sxs-lookup"><span data-stu-id="bf638-123">Searching by Operating System</span></span> 

<span data-ttu-id="bf638-124">由于 PowerShell Core 是适用于 Windows、 Linux 和 MacOS，库中的包可能会针对这些操作系统任意组合进行设计。</span><span class="sxs-lookup"><span data-stu-id="bf638-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="bf638-125">在库 UI 中使用以下 searchs 标记查找包由操作系统标记：</span><span class="sxs-lookup"><span data-stu-id="bf638-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="bf638-126">标记：“Windows”</span><span class="sxs-lookup"><span data-stu-id="bf638-126">Tags: "Windows"</span></span>
- <span data-ttu-id="bf638-127">标记：“Linux”</span><span class="sxs-lookup"><span data-stu-id="bf638-127">Tags: "Linux"</span></span>
- <span data-ttu-id="bf638-128">标记：“MacOS”</span><span class="sxs-lookup"><span data-stu-id="bf638-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="bf638-129">可以指定这些标记`Find-Module`（和 PowerShellGet 模块中的其他 cmdlet），如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf638-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="bf638-130">搜索多个兼容性</span><span class="sxs-lookup"><span data-stu-id="bf638-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="bf638-131">您可以查找使用语法中具有多个兼容的包：</span><span class="sxs-lookup"><span data-stu-id="bf638-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="bf638-132">标记"1>""Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="bf638-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="bf638-133">例如，如果您要查找与我的 Windows 和 Linux 计算机运行的 PowerShell Core 兼容性包，使用搜索标记：</span><span class="sxs-lookup"><span data-stu-id="bf638-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="bf638-134">标记"PSEdition_Core""Windows""Linux"</span><span class="sxs-lookup"><span data-stu-id="bf638-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="bf638-135">若要使用 PowerShell 进行搜索，可以使用`Find-Module`（和 PowerShellGet 模块中的其他 cmdlet），如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf638-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="bf638-136">有关创作和查找兼容的 PowerShell 版本的包的更多详细信息</span><span class="sxs-lookup"><span data-stu-id="bf638-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="bf638-137">PSEditions 模块</span><span class="sxs-lookup"><span data-stu-id="bf638-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="bf638-138">PSEditions 脚本</span><span class="sxs-lookup"><span data-stu-id="bf638-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)

---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: 库,powershell,cmdlet,psgallery
title: 具有兼容 PowerShell 版本或操作系统的包
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328438"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="a18de-103">具有兼容 PowerShell 版本或操作系统的包</span><span class="sxs-lookup"><span data-stu-id="a18de-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="a18de-104">从版本 5.1 开始，PowerShell 提供了各种版本，表现出不同的功能集和平台兼容性。</span><span class="sxs-lookup"><span data-stu-id="a18de-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="a18de-105">按 PowerShell 版本搜索</span><span class="sxs-lookup"><span data-stu-id="a18de-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="a18de-106">两个 PowerShell 版本是：</span><span class="sxs-lookup"><span data-stu-id="a18de-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="a18de-107">**桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="a18de-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="a18de-108">**核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="a18de-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="a18de-109">PowerShell 库允许筛选对特定 PowerShell 版本兼容的包</span><span class="sxs-lookup"><span data-stu-id="a18de-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="a18de-110">如果某个包已指定兼容的 PSEditions，则会在包显示页和包结果中将其列为“PowerShell 版本”的一部分。</span><span class="sxs-lookup"><span data-stu-id="a18de-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="a18de-111">还可以使用 PowerShell 搜索兼容包。</span><span class="sxs-lookup"><span data-stu-id="a18de-111">You can also search for compatible packages using PowerShell.</span></span>

![具有 PSEditions 的项显示页](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="a18de-113">在库 UI 中搜索在 PowerShell Core 上工作的包</span><span class="sxs-lookup"><span data-stu-id="a18de-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="a18de-114">使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的包。</span><span class="sxs-lookup"><span data-stu-id="a18de-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="a18de-115">使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。</span><span class="sxs-lookup"><span data-stu-id="a18de-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![在结果中搜索兼容 Core PSEdition 的项](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="a18de-117">使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。</span><span class="sxs-lookup"><span data-stu-id="a18de-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![在结果中搜索兼容 Desktop PSEdition 的项](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="a18de-119">使用 PowerShell 搜索包以查找兼容版本</span><span class="sxs-lookup"><span data-stu-id="a18de-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="a18de-120">可以指定标记以针对 PowerShell 版本和操作系统进行筛选。</span><span class="sxs-lookup"><span data-stu-id="a18de-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="a18de-121">可使用 `Find-Package` cmdlet，指定 `-Tag` 参数来指定作为目标的版本（和操作系统）。</span><span class="sxs-lookup"><span data-stu-id="a18de-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="a18de-122">类似于下面这样：</span><span class="sxs-lookup"><span data-stu-id="a18de-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="a18de-123">按操作系统搜索</span><span class="sxs-lookup"><span data-stu-id="a18de-123">Searching by Operating System</span></span>

<span data-ttu-id="a18de-124">由于 PowerShell Core 适用于 Windows、Linux 和 MacOS，因此可以针对这些操作系统的任意组合设计库中的包。</span><span class="sxs-lookup"><span data-stu-id="a18de-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="a18de-125">在库 UI 中，使用以下搜索标记查找按操作系统进行标记的包：</span><span class="sxs-lookup"><span data-stu-id="a18de-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="a18de-126">标记：“Windows”</span><span class="sxs-lookup"><span data-stu-id="a18de-126">Tags: "Windows"</span></span>
- <span data-ttu-id="a18de-127">标记：“Linux”</span><span class="sxs-lookup"><span data-stu-id="a18de-127">Tags: "Linux"</span></span>
- <span data-ttu-id="a18de-128">标记：“MacOS”</span><span class="sxs-lookup"><span data-stu-id="a18de-128">Tags: "MacOS"</span></span>

<span data-ttu-id="a18de-129">可以对 `Find-Module`（以及 PowerShellGet 模块中的其他 cmdlet）指定这些标记，类似于下面这样：</span><span class="sxs-lookup"><span data-stu-id="a18de-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="a18de-130">搜索多个兼容性</span><span class="sxs-lookup"><span data-stu-id="a18de-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="a18de-131">可以使用以下语法查找具有多个兼容性的包：</span><span class="sxs-lookup"><span data-stu-id="a18de-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="a18de-132">标记："Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="a18de-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="a18de-133">例如，如果要查找具有在 Windows 和 Linux 计算机上运行的 PowerShell Core 兼容性的包，请使用搜索标记：</span><span class="sxs-lookup"><span data-stu-id="a18de-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="a18de-134">标记："PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="a18de-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="a18de-135">若要使用 PowerShell 进行搜索，可以使用 `Find-Module`（以及 PowerShellGet 模块中的其他 cmdlet），类似于下面这样：</span><span class="sxs-lookup"><span data-stu-id="a18de-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="a18de-136">有关创作和查找兼容的 PowerShell 版本的包的更多详细信息</span><span class="sxs-lookup"><span data-stu-id="a18de-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="a18de-137">PSEditions 模块</span><span class="sxs-lookup"><span data-stu-id="a18de-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="a18de-138">PSEditions 脚本</span><span class="sxs-lookup"><span data-stu-id="a18de-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)

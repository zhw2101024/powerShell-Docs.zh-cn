---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: 具有兼容 PowerShell 版本的项
ms.openlocfilehash: dd2c67417994e960845f7cef09320a0f688a0212
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="e4092-103">具有兼容 PowerShell 版本的项</span><span class="sxs-lookup"><span data-stu-id="e4092-103">Items with compatible PowerShell Editions</span></span>

<span data-ttu-id="e4092-104">从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。</span><span class="sxs-lookup"><span data-stu-id="e4092-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="e4092-105">**桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="e4092-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="e4092-106">**核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="e4092-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="e4092-107">PowerShell 库提取支持的 PSEditions 元数据，并允许筛选兼容特定 PowerShell 版本的项</span><span class="sxs-lookup"><span data-stu-id="e4092-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="e4092-108">如果某个项已指定兼容的 PSEditions，则会在项显示页和项结果中将其显示为“PowerShell Editions”的一部分。</span><span class="sxs-lookup"><span data-stu-id="e4092-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>

![具有 PSEditions 的项显示页](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="e4092-110">搜索在 PowerShellCore 上工作的库 UI 中的项</span><span class="sxs-lookup"><span data-stu-id="e4092-110">Search for items in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="e4092-111">使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的项。</span><span class="sxs-lookup"><span data-stu-id="e4092-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="e4092-112">使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。</span><span class="sxs-lookup"><span data-stu-id="e4092-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![在结果中搜索兼容 Core PSEdition 的项](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="e4092-114">使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。</span><span class="sxs-lookup"><span data-stu-id="e4092-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![在结果中搜索兼容 Desktop PSEdition 的项](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="e4092-116">有关创作和查找兼容 PowerShell 版本的项的详细信息</span><span class="sxs-lookup"><span data-stu-id="e4092-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="e4092-117">PSEditions 模块</span><span class="sxs-lookup"><span data-stu-id="e4092-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="e4092-118">PSEditions 脚本</span><span class="sxs-lookup"><span data-stu-id="e4092-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
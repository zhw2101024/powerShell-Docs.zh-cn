---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_pseditions
ms.openlocfilehash: 6634da5c2dadee9c0c6470b3d3e8883e6d02160f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="items-with-compatible-powershell-editions" class="xliff"></a>
# 具有兼容 PowerShell 版本的项
从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：**以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：**以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

<a id="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions" class="xliff"></a>
## PowerShell 库提取支持的 PSEditions 元数据，并允许筛选兼容特定 PowerShell 版本的项

如果某个项已指定兼容的 PSEditions，则会在项显示页和项结果中将其显示为“PowerShell Editions”的一部分。
![具有 PSEditions 的项显示页](Images/ItemDisplayPageWithPSEditions.PNG)

<a id="search-for-items-in-the-gallery-ui-which-works-on-powershellcore" class="xliff"></a>
## 搜索在 PowerShellCore 上工作的库 UI 中的项
使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的项。

<a id="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition" class="xliff"></a>
### 使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。
![在结果中搜索兼容 Core PSEdition 的项](Images/SearchResultsWithPSEditions.PNG)

<a id="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition" class="xliff"></a>
### 使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。
![在结果中搜索兼容 Desktop PSEdition 的项](Images/SearchResultsWithPSEdition_Desktop.PNG)

<a id="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions" class="xliff"></a>
## 有关创作和查找兼容 PowerShell 版本的项的详细信息
<a id="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd" class="xliff"></a>
### [PSEditions 模块](../psget/module/modulewithpseditionsupport.md)
<a id="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd" class="xliff"></a>
### [PSEditions 脚本](../psget/script/scriptwithpseditionsupport.md)


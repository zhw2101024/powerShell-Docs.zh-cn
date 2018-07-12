---
ms.date: 06/12/2017
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: cmdlet 故障排除
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892468"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="09e0d-103">cmdlet 故障排除</span><span class="sxs-lookup"><span data-stu-id="09e0d-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="09e0d-104">如何解决“警告: 无法下载包‘你的包名称’”问题</span><span class="sxs-lookup"><span data-stu-id="09e0d-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="09e0d-105">收到 `Install-Module` 或 `Update-Module` 有时在某些计算机上失败的报告。</span><span class="sxs-lookup"><span data-stu-id="09e0d-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="09e0d-106">根据我们的调查，此问题与网络连接有关。</span><span class="sxs-lookup"><span data-stu-id="09e0d-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="09e0d-107">最近，我们更新了 NuGet 提供程序，使其可以可靠地下载包。</span><span class="sxs-lookup"><span data-stu-id="09e0d-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="09e0d-108">你可以按照以下说明安装 NuGet 提供程序的最新版本，然后安装或更新你的模块。</span><span class="sxs-lookup"><span data-stu-id="09e0d-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="09e0d-109">下面，我们使用“Azure”模块作为示例。</span><span class="sxs-lookup"><span data-stu-id="09e0d-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
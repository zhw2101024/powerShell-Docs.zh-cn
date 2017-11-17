---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="e463a-103">如何解决“警告: 无法下载包‘你的包名称’”问题？</span><span class="sxs-lookup"><span data-stu-id="e463a-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="e463a-104">据报告，Install-Module 或 Update-Module 在某些计算机上有时会失败。</span><span class="sxs-lookup"><span data-stu-id="e463a-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="e463a-105">根据我们的调查，此问题与网络连接有关。</span><span class="sxs-lookup"><span data-stu-id="e463a-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="e463a-106">最近，我们更新了 NuGet 提供程序，使其可以可靠地下载包。</span><span class="sxs-lookup"><span data-stu-id="e463a-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="e463a-107">你可以按照以下说明安装 NuGet 提供程序的最新版本，然后安装或更新你的模块。</span><span class="sxs-lookup"><span data-stu-id="e463a-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="e463a-108">下面，我们使用“Azure”模块作为示例。</span><span class="sxs-lookup"><span data-stu-id="e463a-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```


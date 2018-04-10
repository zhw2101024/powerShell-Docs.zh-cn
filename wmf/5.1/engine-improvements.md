---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
title: WMF 5.1 中的 PowerShell 引擎改进
ms.openlocfilehash: 3c69c4e13f64683f743eb78b0c9e177ff5b3a771
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="ff748-103">PowerShell 引擎改进</span><span class="sxs-lookup"><span data-stu-id="ff748-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="ff748-104">在 WMF 5.1 中，实现了针对核心 PowerShell 引擎的以下改进：</span><span class="sxs-lookup"><span data-stu-id="ff748-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="ff748-105">性能</span><span class="sxs-lookup"><span data-stu-id="ff748-105">Performance</span></span> ##

<span data-ttu-id="ff748-106">性能在一些重要方面得到了改进：</span><span class="sxs-lookup"><span data-stu-id="ff748-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="ff748-107">启动</span><span class="sxs-lookup"><span data-stu-id="ff748-107">Startup</span></span>
- <span data-ttu-id="ff748-108">向 ForEach-Object 和 Where-Object 这类 cmdlet 进行管道传递的速度大约提供了 50%</span><span class="sxs-lookup"><span data-stu-id="ff748-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span>

<span data-ttu-id="ff748-109">一些示例改进（结果可能因你的硬件而异）：</span><span class="sxs-lookup"><span data-stu-id="ff748-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="ff748-110">方案</span><span class="sxs-lookup"><span data-stu-id="ff748-110">Scenario</span></span> | <span data-ttu-id="ff748-111">5.0 时间（毫秒）</span><span class="sxs-lookup"><span data-stu-id="ff748-111">5.0 Time (ms)</span></span> | <span data-ttu-id="ff748-112">5.1 时间（毫秒）</span><span class="sxs-lookup"><span data-stu-id="ff748-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="ff748-113">900</span><span class="sxs-lookup"><span data-stu-id="ff748-113">900</span></span> | <span data-ttu-id="ff748-114">250</span><span class="sxs-lookup"><span data-stu-id="ff748-114">250</span></span> |
| <span data-ttu-id="ff748-115">PowerShell 首次运行：`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="ff748-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="ff748-116">30000</span><span class="sxs-lookup"><span data-stu-id="ff748-116">30000</span></span> | <span data-ttu-id="ff748-117">13000</span><span class="sxs-lookup"><span data-stu-id="ff748-117">13000</span></span> |
| <span data-ttu-id="ff748-118">构建的命令分析缓存：`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="ff748-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="ff748-119">7000</span><span class="sxs-lookup"><span data-stu-id="ff748-119">7000</span></span> | <span data-ttu-id="ff748-120">520</span><span class="sxs-lookup"><span data-stu-id="ff748-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="ff748-121">1400</span><span class="sxs-lookup"><span data-stu-id="ff748-121">1400</span></span> | <span data-ttu-id="ff748-122">750</span><span class="sxs-lookup"><span data-stu-id="ff748-122">750</span></span> |

> <span data-ttu-id="ff748-123">注意：与启动相关的更改可能会影响某些不支持的方案。</span><span class="sxs-lookup"><span data-stu-id="ff748-123">Note One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="ff748-124">PowerShell 不再读取文件 `$pshome\*.ps1xml` -- 这些文件已转换为 C#，以避免处理 XML 文件的某些文件和 CPU 开销。</span><span class="sxs-lookup"><span data-stu-id="ff748-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
<span data-ttu-id="ff748-125">这些文件仍存在，以同时支持 V2，因此如果更改文件内容，则不会对 V5 产生任何影响，只会影响 V2。</span><span class="sxs-lookup"><span data-stu-id="ff748-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
<span data-ttu-id="ff748-126">请注意，更改这些文件的内容从来都不是受支持的方案。</span><span class="sxs-lookup"><span data-stu-id="ff748-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="ff748-127">另一个显著更改是 PowerShell 如何为系统上安装的模块缓存导出的命令和其他信息。</span><span class="sxs-lookup"><span data-stu-id="ff748-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="ff748-128">以前，此缓存存储在目录 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 中。</span><span class="sxs-lookup"><span data-stu-id="ff748-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="ff748-129">在 WMF 5.1 中，此缓存是单个文件 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`。</span><span class="sxs-lookup"><span data-stu-id="ff748-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="ff748-130">有关详细信息，请参阅[模块分析缓存](scenarios-features.md#module-analysis-cache)。</span><span class="sxs-lookup"><span data-stu-id="ff748-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>
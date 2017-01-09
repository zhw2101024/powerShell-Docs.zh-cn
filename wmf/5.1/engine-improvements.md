---
title: "WMF 5.1 中的 PowerShell 引擎改进"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: c8ad4ac8f3c7bf705114edc06c1b85846336dfff
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
#<a name="powershell-engine-improvements"></a>PowerShell 引擎改进

在 WMF 5.1 中，实现了针对核心 PowerShell 引擎的以下改进：


## <a name="performance"></a>性能 ##

性能在一些重要方面得到了改进：

- 启动
- 向 ForEach-Object 和 Where-Object 这类 cmdlet 进行管道传递的速度大约提供了 50% 

一些示例改进（结果可能因你的硬件而异）： 

| 方案 | 5.0 时间（毫秒） | 5.1 时间（毫秒） |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell 首次运行：`powershell -command "Unknown-Command"` | 30000 | 13000 |
| 构建的命令分析缓存：`powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
> 注意：与启动相关的更改可能会影响某些不支持的方案。 
> PowerShell 不再读取文件 `$pshome\*.ps1xml` -- 这些文件已转换为 C#，以避免处理 XML 文件的某些文件和 CPU 开销。 
这些文件仍存在，以同时支持 V2，因此如果更改文件内容，则不会对 V5 产生任何影响，只会影响 V2。 
请注意，更改这些文件的内容从来都不是受支持的方案。

另一个显著更改是 PowerShell 如何为系统上安装的模块缓存导出的命令和其他信息。 以前，此缓存存储在目录 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 中。 在 WMF 5.1 中，此缓存是单个文件 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`。
有关详细信息，请参阅[模块分析缓存](scenarios-features.md#module-analysis-cache)。

---
title: "WMF 5.1 中的新方案和功能（预览版）"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 01d7ac9815a8650f36150e36b4f6942f451dc368

---

# WMF 5.1 中的新方案和功能（预览版） #

> 注意：此信息是预发布版本，可能会进行更改。

## PowerShell 版本 ##
从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：**以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：**以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

**详细了解如何使用 PowerShell 版本**
- [确定正在运行的 PowerShell 版本]()
- [声明模块与特定 PowerShell 版本的兼容性]()
- [按 CompatiblePSEditions 筛选 Get-Module 结果]()
- [阻止脚本执行，除非在 PowerShell 的兼容版本上运行]()

## 目录 Cmdlet  

在 [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) 模块中新增了两个新 cmdlet；这两个 cmdlet 可用于生成和验证 windows 目录文件。  

###New-FileCatalog 
--------------------------------

New File 目录用于为文件夹和文件集合创建 windows 目录文件。 该目录文件包含指定路径中的所有文件的哈希值。 用户可以分发文件夹集合以及代表这些文件夹的对应的目录文件。 该信息对于验证自目录创建以来是否对文件夹进行了任何更改很有用。    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
支持目录版本 1 和 2。 版本 1 使用 SHA1 哈希算法来创建文件哈希值；版本 2 则使用 SHA256。 Windows Server 2008 R2 或 Windows 7 不支持目录版本 2。 你应在 Windows 8、Windows Server 2012 及更高版本的操作系统上使用目录版本 2。  

![](../../images/NewFileCatalog.jpg)

这将创建目录文件。 

![](../../images/CatalogFile1.jpg)  

![](../../images/CatalogFile2.jpg) 

若要验证目录文件（上面示例中的 Pester.cat 文件）的完整性，应使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet 对其进行签名。   


###Test-FileCatalog 
--------------------------------

Test File 目录用于验证代表一组文件夹的目录。 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../../images/TestFileCatalog.jpg)

此 cmdlet 将目录中找到的所有文件的哈希值及其相对路径与磁盘中的进行比较。 如果它检测到文件哈希值和路径之间存在任何不匹配，将返回状态 ValidationFailed。 用户可以使用 -Detailed 标志检索所有该信息。 它还在“签名”字段中显示目录的签名状态，该结果与针对目录文件调用 [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet 的结果相同。 用户也可以使用 -FilesToSkip 参数在验证过程中跳过任何文件。 


## 模块分析缓存 ##
从 WMF 5.1 开始，PowerShell 针对用于缓存有关模块的数据（如它导出的命令）的文件提供了控制。

默认情况下，此缓存存储在文件 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 中。
缓存通常在启动时进行读取（同时搜索命令），在模块导入一段时间之后在后台线程上进行写入。

若要更改缓存的默认位置，请在启动 PowerShell 之前设置环境变量 PSModuleAnalysisCachePath。 对此环境变量进行的更改只影响子进程。
值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。
若要禁用文件缓存，请将此值设置为无效位置，例如：

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

这会将路径设置为无效设备。 如果 PowerShell 无法写入路径，则不会返回任何错误，不过你可能会看到通过跟踪器进行报告的错误：

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

从缓存写出时，PowerShell 会检查不再存在的模块以避免进行不必要的大型缓存。
有时不需要这些检查，在这种情况下可以通过设置关闭它们

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此环境变量的设置会在当前进程中立即生效。

##指定模块版本

在 WMF 5.1 中，`using module` 的行为方式与 PowerShell 中其他与模块相关的构造相同。 以前无法指定特定模块版本；如果有多个版本存在，则这会导致错误。


在 WMF 5.1 中：

* 可以使用 `ModuleSpecification` [哈希表](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)。 此哈希表具有与 `Get-Module -FullyQualifiedName` 相同的格式。

**例如：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 如果有多个版本的模块，则 PowerShell 会使用与 `Import-Module` **相同的解析逻辑**，不会返回错误 - - 行为与 `Import-Module` 和 `Import-DscResource` 相同。








##针对 Pester 的改进
在 WMF 5.1 中，PowerShell 随附的 Pester 版本从 3.3.5 更新到 3.4.0，并且添加了一个提交：https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e，从而改善了 Nano 上的 Pester 的行为。 

你可以通过检查 https://github.com/pester/Pester/blob/master/CHANGELOG.md 上的 ChangeLog.md 文件查看从版本 3.3.5 到 3.4.0 的更改



<!--HONumber=Jul16_HO3-->



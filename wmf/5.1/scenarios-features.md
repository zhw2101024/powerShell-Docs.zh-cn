---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.1 中的新方案和功能
ms.openlocfilehash: 77b439e61c5802f8ddbc4a0f39923cc8c0c36fe9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>WMF 5.1 中的新方案和功能

> 注意：此信息是预发布版本，可能会进行更改。

## <a name="powershell-editions"></a>PowerShell 版本

从 5.1 版本开始，PowerShell 在具有不同功能集和平台兼容性的不同版本中可用。

- **桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

**详细了解如何使用 PowerShell 版本**

- [使用 $PSVersionTable 确定正在运行的 PowerShell 版本](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [使用 PSEdition 参数按 CompatiblePSEditions 筛选 Get-Module 结果](/powershell/module/microsoft.powershell.core/get-module)
- [阻止脚本执行，除非在 PowerShell 的兼容版本上运行](/powershell/gallery/psget/script/scriptwithpseditionsupport)
- [声明模块与特定 PowerShell 版本的兼容性](/powershell/gallery/psget/module/modulewithpseditionsupport)

## <a name="catalog-cmdlets"></a>目录 Cmdlet

在 [Microsoft.PowerShell.Security](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security) 模块中新增了两个新 cmdlet；这两个 cmdlet 可用于生成和验证 Windows 目录文件。

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

New-FileCatalog 用于为文件夹和文件集合创建 Windows 目录文件。
该目录文件包含指定路径中的所有文件的哈希值。
用户可以分发文件夹集合以及代表这些文件夹的对应的目录文件。
该信息对于验证自目录创建以来是否对文件夹进行了任何更改很有用。

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

支持目录版本 1 和 2。
版本 1 使用 SHA1 哈希算法来创建文件哈希值；版本 2 则使用 SHA256。
Windows Server 2008 R2 或 Windows 7 不支持目录版本 2。
你应在 Windows 8、Windows Server 2012 及更高版本的操作系统上使用目录版本 2。

![](../images/NewFileCatalog.jpg)

这将创建目录文件。

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

若要验证目录文件（上面示例中的 Pester.cat 文件）的完整性，应使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet 对其进行签名。

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test-FileCatalog 用于验证代表一组文件夹的目录。

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

此 cmdlet 将目录中找到的所有文件的哈希值及其相对路径与磁盘中的进行比较。
如果它检测到文件哈希值和路径之间存在任何不匹配，将返回状态 ValidationFailed。
用户可通过使用 *-Detailed* 参数检索所有这些信息。
它还在“签名”属性中显示目录的签名状态，该结果与针对目录文件调用 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet 的结果相同。
用户也可以使用 -FilesToSkip 参数在验证过程中跳过任何文件。

## <a name="module-analysis-cache"></a>模块分析缓存

从 WMF 5.1 开始，PowerShell 针对用于缓存有关模块的数据（如它导出的命令）的文件提供了控制。

默认情况下，此缓存存储在文件 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 中。
缓存通常在启动时进行读取（同时搜索命令），在模块导入一段时间之后在后台线程上进行写入。

若要更改缓存的默认位置，可在启动 PowerShell 前，设置 `$env:PSModuleAnalysisCachePath` 环境变量。
对此环境变量进行的更改只影响子进程。
值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。
若要禁用文件缓存，请将此值设置为无效位置，例如：

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

这会将路径设置为无效设备。
如果 PowerShell 无法写入路径，则不会返回任何错误，不过你可能会看到通过使用跟踪器进行报告的错误：

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

从缓存写出时，PowerShell 会检查不再存在的模块以避免进行不必要的大型缓存。
有时不需要这些检查，在这种情况下可以通过设置关闭它们：

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此环境变量的设置会在当前进程中立即生效。

## <a name="specifying-module-version"></a>指定模块版本

在 WMF 5.1 中，`using module` 的行为方式与 PowerShell 中其他与模块相关的构造相同。
以前无法指定特定模块版本；如果有多个版本存在，则这会导致错误。

在 WMF 5.1 中：

- 可以使用 [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290)。
此哈希表具有与 `Get-Module -FullyQualifiedName` 相同的格式。

**示例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- 如果有多个版本的模块，则 PowerShell 会使用与 `Import-Module` **相同的解析逻辑**，不会返回错误 - - 行为与 `Import-Module` 和 `Import-DscResource` 相同。

## <a name="improvements-to-pester"></a>针对 Pester 的改进

在 WMF 5.1 中，PowerShell 随附的 Pester 版本从 3.3.5 更新到 3.4.0，并且添加了一个提交：https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e，从而改善了 Nano 服务器上的 Pester 的行为。

可以通过在 https://github.com/pester/Pester/blob/master/CHANGELOG.md 处检查 ChangeLog.md 文件查看版本 3.3.5 到 3.4.0 的更改

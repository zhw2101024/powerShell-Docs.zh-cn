---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.x 发行说明
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848157"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5.x 发行说明

## <a name="wmf-50-changes"></a>WMF 5.0 更改

- PowerShell 5.0 添加了新的结构化信息  流
- 对 DSC 的改进包括以下四个新 DSC 资源：
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- 添加了 Just Enough Administration 以通过 PowerShell 远程处理实现基于角色的管理
- PowerShell 5.0 扩展了语言以包括用户定义的类和枚举
- 改进了 PowerShell ISE 中的调试功能并添加了远程调试
- 添加了 PowerShellGet 和 PackageManagement 模块
- 增强了 PowerShell 脚本日志记录和脚本
- 添加了加密消息语法 cmdlet
- WMF 5.0 包括适用于 Windows 的 NetworkSwitchManager 模块
- 添加了 Microsoft.PowerShell.ODataUtils 模块
- 添加了对软件清单日志记录 (SIL) 的支持
- 提供新的或更新的 cmdlet 以响应用户请求和问题

## <a name="wmf-51-changes"></a>WMF 5.1 更改

WMF 5.1 包括与 Windows Server 2016 一起发行的 PowerShell、WMI、WinRM 以及软件清单日志记录 (SIL) 组件。 WMF 5.1 可安装在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 和 2012 R2 上，并提供了对 WMF 5.0 的多个改进，其中包括：

- 新 cmdlet
- PowerShellGet 改进包括强制签名模块和安装 JEA 模块
- PackageManagement 增加了对容器、CBS 安装程序、基于 EXE 的安装程序、CAB 包的支持
- DSC 和 PowerShell 类的调试改进
- 安全增强包括强制执行来自请求服务器和使用 PowerShellGet cmdlet 时的目录签名模块
- 响应大量的用户请求和问题

> [!IMPORTANT]
> 在 Windows Server 2008 或 Windows 7 上安装 WMF 5.1 之前，请确认未安装 WMF 3.0。 有关详细信息，请参阅 [Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 系统必备](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1)。

## <a name="powershell-editions"></a>PowerShell 版本

从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

### <a name="learn-more-about-using-powershell-editions"></a>详细了解如何使用 PowerShell 版本

- [使用 $PSVersionTable 确定正在运行的 PowerShell 版本](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [使用 PSEdition 参数按 CompatiblePSEditions 筛选 Get-Module 结果](/powershell/module/microsoft.powershell.core/get-module)
- [阻止脚本执行，除非在 PowerShell 的兼容版本上运行](/powershell/gallery/concepts/script-psedition-support)
- [声明模块与特定 PowerShell 版本的兼容性](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>模块分析缓存

从 WMF 5.1 开始，PowerShell 针对用于缓存有关模块的数据（如它导出的命令）的文件提供了控制。

默认情况下，此缓存存储在文件 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 中。 缓存通常在启动时进行读取（同时搜索命令），在模块导入一段时间之后在后台线程上进行写入。

若要更改缓存的默认位置，可在启动 PowerShell 前，设置 `$env:PSModuleAnalysisCachePath` 环境变量。 对此环境变量进行的更改只影响子进程。 值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。 若要禁用文件缓存，请将此值设置为无效位置，例如：

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

这会将路径设置为无效设备。 如果 PowerShell 无法写入路径，则不会返回任何错误，不过你可能会看到通过使用跟踪器进行报告的错误：

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

从缓存写出时，PowerShell 会检查不再存在的模块以避免进行不必要的大型缓存。 有时不需要这些检查，在这种情况下可以通过设置关闭它们：

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此环境变量的设置会在当前进程中立即生效。

## <a name="specifying-module-version"></a>指定模块版本

在 WMF 5.1 中，`using module` 的行为方式与 PowerShell 中其他与模块相关的构造相同。
以前无法指定特定模块版本；如果有多个版本存在，则这会导致错误。

在 WMF 5.1 中：

- 可以使用 [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。

  此哈希表具有与 `Get-Module -FullyQualifiedName` 相同的格式。

  **示例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- 如果有多个版本的模块，则 PowerShell 会使用与 `Import-Module` **相同的解析逻辑**，不会返回错误 - - 行为与 `Import-Module` 和 `Import-DscResource` 相同。

## <a name="improvements-to-pester"></a>针对 Pester 的改进

在 WMF 5.1 中，PowerShell 随附的 Pester 版本已从 3.3.5 更新到 3.4.0。
此更新会在 Nano Server 上启用更好的 Pester 行为。

可以通过在 GitHub 存储库中检查 [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) 查看 Pest 的更改。

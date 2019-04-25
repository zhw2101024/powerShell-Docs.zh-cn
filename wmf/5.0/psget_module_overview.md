---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057462"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>使用 PowerShellGet 进行 PowerShell 模块发现、安装和盘存

此版本的 WMF 中包括了 PowerShellGet：
-   Find-Module 可以使用 -Tag 参数对模块元数据进行筛选
-   Find-Module 可以使用 -Filter 参数对存储库特定搜索语言进行筛选
-   Find-Module 可以使用 -Command、-DscResource 和 -Includes 参数根据模块内容进行筛选
-   Find-DscResource 可以发现存储库中的单个 DSC 资源
-   支持使用 NuGet 从文件共享安装，且支持发布到文件共享

## <a name="example-commands"></a>示例命令
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>PowerShellGet 中的新增功能
-   PowerShell 5.0 或更高版本上的并行版本支持
-   模块依赖项安装支持
-   三个新的 cmdlet
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module

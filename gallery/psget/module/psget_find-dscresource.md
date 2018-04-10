---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 库,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a>Find-DscResource

在模块中查找 DSC 资源。

## <a name="description"></a>说明

Find-DscResource cmdlet 查找已注册的存储库中与指定条件匹配的模块中所包含的[所需状态配置 (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) 资源。
对于此 cmdlet 查找的每个模块，Find-DscResource 返回一个 PSGetDscResourceInfo 对象，可以将其通过管道传递到 Install-Module 以安装包含此 cmdlet 返回的资源的模块。

DSC 是 Windows PowerShell 中的新管理平台，可用于部署和管理软件服务的配置数据，并管理这些服务的运行的环境。

Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。 资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。

资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。 资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。

- Find-DscResource 可使用版本参数 MinimumVersion、RequiredVersion、AllVersions 进行筛选。
  - 这些参数彼此排斥。
  - 这些版本参数只允许具有单个模块名称，而不能具有任何通配符。
  - 如果未指定 RequiredVersion 参数，Find-DscResource 将返回等于或高于指定的最低版本的最新版本的模块或最新版本的模块（若未指定最低版本）。
  - 如果指定了 RequiredVersion 参数，Find-DscResource 仅返回与指定版本完全匹配的模块。
- Find-DscResource 可使用 -Tag 参数对模块元数据进行筛选
- Find-DscResource 可使用 -Filter 参数对存储库特定搜索语言进行筛选。
- Find-DscResource 可从所有或少数已注册存储库中对模块进行筛选。

## <a name="cmdlet-syntax"></a>Cmdlet 语法
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 联机帮助参考

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>示例命令
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```
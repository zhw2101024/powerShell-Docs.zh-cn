---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Find-Command
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a>Find-Command

查找模块中的 PowerShell 命令。

## <a name="description"></a>说明
Find-Command cmdlet 会查找 cmdlet、别名、函数和工作流等 PowerShell 命令。 Find-Command 搜索已注册存储库中的模块。
对于此 cmdlet 找到的每个命令，将返回一个 PSGetCommandInfo 对象。 可将 PSGetCommandInfo 对象传递给 Install-Module cmdlet 以安装包含此命令的模块。

- Find-Command 可使用版本参数 MinimumVersion、RequiredVersion、AllVersions 进行筛选。
  - 这些参数彼此排斥。
  - 这些版本参数只允许具有单个模块名称，而不能具有任何通配符。
  - 如果未指定 RequiredVersion 参数，Find-Command 将返回等于或高于指定的最低版本的最新版本的模块或最新版本的模块（若未指定最低版本）。
  - 如果指定了 RequiredVersion 参数，Find-Command 仅返回与指定版本完全匹配的模块。
- Find-Command 可使用 -Tag 参数对模块元数据进行筛选
- Find-Command 可使用 -Filter 参数对存储库特定搜索语言进行筛选。
- Find-Command 可从所有或少数的已注册的存储库中对模块进行筛选。

## <a name="cmdlet-syntax"></a>Cmdlet 语法
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 联机帮助参考

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>示例命令
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```


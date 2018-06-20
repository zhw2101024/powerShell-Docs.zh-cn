---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: 影响 PowerShell 库 UI 的项清单值
ms.openlocfilehash: 39522396b179c54b981e6292cddacec27b32506c
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048194"
---
# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>影响 PowerShell 库 UI 的项清单值

本主题向发布者提供有关如何修改其 PowerShell 库发布的清单，以便影响 PowerShellGet cmdlet 和 PowerShell 库 UI 的功能的摘要信息。
此内容按照更改将出现的位置进行组织，从中心部分开始，然后是左侧的导航区域。 有一个涵盖标记的详细信息部分，它标识重要标记以及一些较常用的标记。
有两个提供清单示例的主题：

- 有关模块，请参阅[更新模块清单](https://docs.microsoft.com/powershell/gallery/psget/module/psget_update-modulemanifest)
- 有关脚本，请参阅[使用元数据创建脚本文件](https://docs.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>由清单控制的 PowerShell 库功能元素

下表显示由发布者控制的 PowerShell 库项页 UI 的元素。
每个项指示它可能由模块清单还是脚本清单进行控制。

| UI 元素 | 说明 | 模块 | 脚本 |
| --- | --- | --- | --- |
| **标题** | 这是发布到库的项的名称  | 否 | 否 |
| **版本** | 显示的版本是元数据中的版本字符串以及预发布版本（如果已指定）。 模块清单中版本的主要部分是 ModuleVersion。 对于脚本，它被标识为 .VERSION。 如果指定了预发布版本字符串，则会将其追加到模块的 ModuleVersion，或者指定为脚本的 .VERSION 的一部分。 有一个用于指定[模块](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule)和[脚本](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript)中的预发布字符串的文档 | 是 | 是 |
| **描述** | 这是模块清单中的描述，在脚本文件清单中是 .DESCRIPTION | 是 | 是 |
| **需要接受许可证** | 模块可以通过以下方式要求用户接受许可证：使用 RequireLicenseAcceptance = $true 修改模块清单，提供 LicenseURI，并提供模块文件夹的根目录中的 license.txt 文件。 [需要接受许可证](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance)主题提供了其他信息。 | 是 | 否 |
| **发行说明** | 对于模块，此信息可从 PSData\PrivateData 下的 ReleaseNotes 部分获得。 在脚本清单中，它是 .RELEASENOTES 元素。 | 是 | 是 |
| **所有者** | 所有者是可以更新 PowerShell 库中项的用户列表。 所有者列表不包含在项清单中。 其他文档描述如何[管理项所有者](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners)。 | 否 | 否 |
| **作者** | 这作为作者包含在模块清单中，作为 .AUTHOR 包含在脚本清单中。 作者字段通常用于指定与项关联的公司或组织。 | 是 | 是 |
| **版权** | 这是模块清单中的版权字段和脚本清单中的 .COPYRIGHT。 | 是 | 是 |
| **文件列表** | 将文件列表发布到 PowerShell 库时可从包中获得。 不可通过清单信息对其进行控制。 注意：PowerShell 库中的每个项列出了一个附加的 .nuspec 文件，在系统上安装对应项后该文件不存在。 这是对应项的 Nuget 包清单，可能会被忽略。 | 否 | 否 |
| **标记** | 对于模块，标记都包含在 PSData\PrivateData 下。 对于脚本，该部分被标记为 .TAGS。 请注意，标记不能包含空格，即使它们已用引号引起来。 标记具有其他要求和含义，这些内容将在本主题后面的“标记详细信息”部分中描述。 | 是 | 是 |
| **Cmdlet** | 这可使用 CmdletsToExport 在模块清单中提供。 请注意，最佳做法是明确列出各项，而不是使用通配符“*”，因为这样将为用户提高负载模块性能。 | 是 | 否 |
| **函数** | 这可使用 FunctionsToExport 在模块清单中提供。 请注意，最佳做法是明确列出各项，而不是使用通配符“*”，因为这样将为用户提高负载模块性能。 | 是 | 否 |
| **DSC 资源** | 对于将在 PowerShell 版本 5.0 及更高版本上使用的模块，这可使用 DscResourcesToExport 在清单中提供。 如果模块要在 PowerShell 4 中使用，则不应使用 DSCResourcesToExport，因为它不是受支持的清单键。 （DSC 在 PowerShell 4 之前不可用。） | 是 | 否 |
| **工作流** | 工作流作为脚本发布到 PowerShell 库，并在代码中标识为工作流（有关示例，请参阅 [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1)）。 这不可由清单进行控制。 | 否 | 否 |
| **角色功能** | 当发布到 PowerShell 库的模块包含一个或多个由 JEA 使用的角色功能 (.psrc) 文件时，将会列出此元素。 有关[角色功能](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities)的更多详细信息，请参阅 JEA 文档。 | 是 | 否 |
| **PowerShell 版本** | 这在脚本或模块清单中指定。 对于设计用于 PowerShell 5.0 及更低版本的模块，这使用标记进行控制。 对于桌面，使用标记 PSEdition_Desktop；对于核心，使用标记 PSEdition_Core。 对于仅在 PowerShell 5.1 及更高版本中使用的模块，主清单中存在 CompatiblePSEditions 键。 有关更多详细信息，请查看 [PowerShell Get 文档](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport)中的 PS 版本功能。 | 是 | 是 |
| **依赖项** | 依赖项是 PowerShell 库中的模块，它们在模块中被声明为 RequiredModules，在脚本清单中被声明为 #Requires –Module（名称）。 | 是 | 是 |
| **最低 Powershell 版本** | 这可以在模块清单中指定为 PowerShellVersion | 是 | 否 |
| **版本历史记录** | 版本历史记录反映对 PowerShell 库中模块的更新。 如果使用“删除”功能隐藏项的版本，则除项所有者以外，该版本将不会显示在版本历史记录中。 | 否 | 否 |
| **项目网站** | 通过指定 ProjectURI，为模块清单的 Privatedata\PSData 部分中的模块提供项目网站。 在脚本清单中，通过指定 .PROJECTURI 对其进行控制。 | 是 | 是 |
| **许可证** | 通过指定 LicenseURI，为模块清单的 Privatedata\PSData 部分中的模块提供许可证链接。 在脚本清单中，通过指定 .LICENSEURI 对其进行控制。 请务必注意，如果许可证未通过 LicenseURI 或未在模块内提供，则 PowerShell 库的使用条款将指定该项的使用条款。 有关详细信息，请参阅使用条款。 | 是 | 是 |

## <a name="editing-item-details"></a>编辑项详细信息

PowerShell 库编辑项页允许发布者更改为某项显示的若干字段，具体为：

- 标题
- 说明
- 摘要
- 图标 URL
- 项目主页 URL
- 作者
- 版权
- 标记
- 发行说明
- 需要许可证

通常不建议使用此方法，除非需要更正较旧版本的模块的显示内容时。
获取该模块的用户将会看到元数据与 PowerShell 库中显示的内容不匹配，这将引发有关该项的问题。
通常，这将导致查询发送到项所有者以确认更改。
强烈建议任何时候使用此方法都应发布具有相同更改的新版本的项。

## <a name="tag-details"></a>标记详细信息

标记是使用者用来查找项的简单字符串。
标记在与同一主题相关的多个项中一致地使用时最具价值。 使用同一个词的多种形式（例如 database 和 databases，或 test 和 testing）通常没有什么好处。
标记是单个词不区分大小写的字符串，并且不能包含空格。 如果存在你认为用户会搜索的短语，请将其添加到该项的描述中，然后将在搜索结果中找到该短语。 如果你尝试提高可读性，请使用帕斯卡命名法、连字符、下划线或句点。 谨慎创建长而复杂的异常标记，因为通常会出现拼写错误。

有一些标记需要特别注意，因为 PowerShell 库和 PowerShellGet cmdlet 会以不同方式对待它们。 PSEdition_Desktop 和 PSEdition_Core 是特定的示例，如上所述。

如上所述，标记在特定情况下提供最大的价值，并在许多项中一致地使用。
作为发布者尝试找到要使用的最佳标记，最简单的方法是在 PowerShell 库中搜索你正在考虑的标记。
理想情况下，将返回许多项，并且项的描述将与你使用的该关键词一致。

以下是截至 2017 年 12 月 14 日一些最常用的标记，可供参考。
在某些情况下，在标记旁边列出了类似但可能不太理想的选项。
最佳做法是使用“首选标记”，因为这样将导致较少的噪音，并为使用者带来更好的搜索结果。


| **首选标记** | **替代项和说明** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration 太长，因此不够理想 |
| **ResourceManager** | ARM 用于描述处理器组，不应该用于 Azure 资源管理器 | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automation** |  |
| **REST** |  |
| **ActiveDirectory** | 当前不会单独使用 AD  |
| **SQLServer** |  |
| **DBA** |  |
| **安全** | Defense 不太精确 |
| **Database** | Databases（复数）不太可取 |
| **DevOps** |  |
| **Windows** |  |
| **Build** |  |
| **Deployment** | Deploy 某种程度上不太常用 |
| **Cloud** |  |
| **GIT** |  |
| **Test** | Testing 不太可取 |
| **VersionControl** | Version 不太精确，但使用更频繁  |
| **Logging** | Logging 首选用作一项操作 |
| **日志** | Log 首选用作一件东西 |
| **Backup** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Storage** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Network** | Networking 非常相似，不经常使用 |
| **SharePoint** |  |
| **Reporting** | Reporting 是一项操作，Report 是一件东西 |
| **Report** | Report 是一件东西 |
| **WinRM** |  |
| **Monitoring** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Color** |  |
| **DNS** |  |
| **Office365** | 拼写出 Office 是可取的。 O365 虽然更短，但不经常使用 | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | HyperV 很少用作标记 |
| **Configuration** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Firewall** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | 主要用于 AzureRM 模块 |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |
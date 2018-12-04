---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: PowerShell 库入门
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: 1082b13115c5c5be4b76574ba55307b3e567983f
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52576883"
---
# <a name="getting-started-with-the-powershell-gallery"></a>PowerShell 库入门

PowerShell 库是包含脚本、 模块和 DSC 资源可以下载并将它们的包存储库。 使用中的 cmdlet [PowerShellGet](/powershell/module/powershellget)模块从 PowerShell 库安装包。 从 PowerShell 库下载项时无需登录。

> [!NOTE]
> 可直接从 PowerShell 库下载包，但不推荐此方法。
> 有关详细信息，请参阅[手动包下载](/powershell/gallery/how-to/working-with-packages/manual-download)。

## <a name="discovering-packages-from-the-powershell-gallery"></a>从 PowerShell 库中发现包

可以通过使用 PowerShell 库中找到包**搜索**PowerShell 库上的控件[主页](https://www.powershellgallery.com)，或通过浏览模块和脚本从[包页](https://www.powershellgallery.com/packages). 此外可以通过运行查找 PowerShell 库中的包[Find-module][]， [Find-dscresource]，并[Find-script][] cmdlet，具体取决于包类型使用`-Repository PSGallery`。

可以使用以下参数来筛选库中的结果：

- 名称
- AllVersions
- MinimumVersion
- RequiredVersion
- 标记
- 包括
- DscResource
- RoleCapability
- Command
- 筛选

如果只想发现库中的特定 DSC 资源，可运行 [Find-DscResource] cmdlet。 Find-DscResource 会返回库中 DSC 资源的相关数据。
由于 DSC 资源始终作为模块的部分进行传递，所以仍需运行 [Install-Module][] 来安装这些 DSC 资源。

## <a name="learning-about-packages-in-the-powershell-gallery"></a>了解 PowerShell 库中的包

找到感兴趣的包后，你可能想要了解更多有关信息。 可检查库中该包的特定页来了解详细信息。 在该页上可查看该包中上载的所有元数据。 此元数据由包作者提供，Microsoft 不会对其进行验证。 包的所有者紧密关联到用于发布该包的 PowerShell 库帐户，比“作者”字段更可信。

如果发现发布的包不可信，请单击该包页面上的“报告滥用行为”。

如果运行 [Find-Module][] 或 [Find-Script][]，则可在返回的 PSGetModuleInfo 对象中查看该数据。 例如，运行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
返回库中 PSReadLine 模块的数据。

## <a name="downloading-packages-from-the-powershell-gallery"></a>从 PowerShell 库下载包

从 PowerShell 库下载包时，建议执行下列过程：

### <a name="inspect"></a>检查

若要下载库中的包以供检查，请运行 [Save-Module][] 或 [Save-Script][] cmdlet，具体视包类型而定。 此操作可本地保存包而不进行安装，并且可以检查包内容。 请记得手动删除已保存的包。

其中一些包由 Microsoft 编写，另一些包由 PowerShell 社区编写。
Microsoft 建议安装前检查库中包的内容和代码。

如果发现发布的包不可信，请单击该包页面上的“报告滥用行为”。

### <a name="install"></a>安装

若要安装库中的包以供使用，请运行 [Install-Module][] 或 [Install-Script][] cmdlet，具体视包类型而定。

默认情况下，[Install-Module][] 将模块安装到 `$env:ProgramFiles\WindowsPowerShell\Modules`。
此操作需要管理员帐户。 如果添加 `-Scope CurrentUser` 参数，模块将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。

默认情况下，[Install-Script][] 将脚本安装到 `$env:ProgramFiles\WindowsPowerShell\Scripts`。
此操作需要管理员帐户。 如果添加 `-Scope CurrentUser` 参数，脚本将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。

默认情况下，[Install-Module][] 和 [Install-Script][] 安装最新版包。
若要安装旧版包，请添加 `-RequiredVersion` 参数。

### <a name="deploy"></a>在来宾群集上部署

若要部署到 Azure 自动化 PowerShell 库中的包，请单击**Azure 自动化**，然后单击**部署到 Azure 自动化**包详细信息页上。 你将重定向到 Azure 管理门户中你在其中登录通过使用 Azure 帐户凭据。 请注意，部署具有依赖项包将所有依赖项部署到 Azure 自动化。 通过将 AzureAutomationNotSupported 标记添加到包元数据可禁用“部署到 Azure 自动化”按钮。

若要了解有关 Azure 自动化的详细信息，请参阅 [Azure 自动化](/azure/automation)文档。

## <a name="updating-packages-from-the-powershell-gallery"></a>从 PowerShell 库更新包

若要更新从 PowerShell 库安装的包，请运行 [Update-Module][] 或 [Update-Script][] cmdlet。 当运行不带任何其他参数时，尝试更新通过运行安装的所有模块 [都更新模块] [] [Install-module][]。 若要选择性地更新模块，请添加 `-Name` 参数。 

同样，当运行时不使用任何其他参数，[更新脚本] [] 还会尝试更新所有脚本运行安装[Install-script][]。 若要选择性地更新脚本，请添加 `-Name` 参数。

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>列出从 PowerShell 库安装的包

若要确定已安装 PowerShell 库中的哪些模块，请运行 [Get-InstalledModule][] cmdlet。 该命令会列出系统上所有已直接从 PowerShell 库安装的模块。

同样，若要确定已安装 PowerShell 库中的哪些脚本，请运行 [Get-InstalledScript][] cmdlet。 此命令会列出系统上所有已直接从 PowerShell 库安装的脚本。

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script

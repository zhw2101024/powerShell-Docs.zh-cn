---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: PowerShell 库入门
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523008"
---
# <a name="get-started-with-the-powershell-gallery"></a>PowerShell 库入门

在 PowerShell 库安装项的正确方法是使用 [PowerShellGet](/powershell/module/powershellget) 模块中的 cmdlet。 从 PowerShell 库下载项时无需登录。

> [!NOTE]
> 可直接从 PowerShell 库下载包，但不推荐此方法。 有关详细信息，请参阅[手动包下载](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md)。  


## <a name="discovering-items-from-the-powershell-gallery"></a>从 PowerShell 库中发现项

可通过使用本网站上的“搜索”或浏览“模块和脚本”页查找 PowerShell 库中的项。 还可以使用 `-Repository PSGallery` 运行 [Find-Module][] 和 [Find-Script][] cmdlet（具体视项类型而定），从而查找 PowerShell 库中的项。

可使用以下参数从库筛选结果：

- 名称
- AllVersions
- MinimumVersion
- RequiredVersion
- 标记
- 包括
- DscResource
- RoleCapability
- 命令
- 筛选

如果只想发现库中的特定 DSC 资源，可运行 [Find-DscResource] cmdlet。 Find-DscResource 会返回库中 DSC 资源的相关数据。
由于 DSC 资源始终作为模块的部分进行传递，所以仍需运行 [Install-Module][] 来安装这些 DSC 资源。

## <a name="learning-about-items-in-the-powershell-gallery"></a>了解 PowerShell 库中的项

找到感兴趣的项后，你可能希望了解与其有关的详细信息。 可检查库中该项的特定页来了解详细信息。 在该页上可查看该项中上传的所有元数据。 项的元数据由项作者提供，Microsoft 不会进行验证。 项的所有者紧密关联到发布该项的 PowerShell 库帐户，比作者字段更可信。

如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。

如果运行 [Find-Module][] 或 [Find-Script][]，则可在返回的 PSGetModuleInfo 对象中查看该数据。 例如，运行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
返回库中 PSReadLine 模块的数据。

## <a name="downloading-items-from-the-powershell-gallery"></a>从 PowerShell 库中下载项

从 PowerShell 库中下载项时，议使用下列过程：

### <a name="inspect"></a>检查

若要下载库中的项以供检查，请运行 [Save-Module][] 或 [Save-Script][] cmdlet，具体视项类型而定。 此操作可本地保存项而不进行安装，并且可以检查项内容。 请记得手动删除已保存的项。

某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。
Microsoft 建议安装前检查库中项的内容和代码。

如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。

### <a name="install"></a>安装

若要安装库中的项以供使用，请运行 [Install-Module][] 或 [Install-Script][] cmdlet，具体视项类型而定。

默认情况下，[Install-Module][] 将模块安装到 `$env:ProgramFiles\WindowsPowerShell\Modules`。
此操作需要管理员帐户。 如果添加 `-Scope CurrentUser` 参数，模块将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。

默认情况下，[Install-Script][] 将脚本安装到 `$env:ProgramFiles\WindowsPowerShell\Scripts`。
此操作需要管理员帐户。 如果添加 `-Scope CurrentUser` 参数，脚本将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。

默认情况下，[Install-Module][] 和 [Install-Script][] 安装项的最新版本。
若要安装旧版项，请添加 `-RequiredVersion` 参数。

### <a name="deploy"></a>在来宾群集上部署

若要将项从 PowerShell 库部署到 Azure 自动化，请单击项详细信息页上的“部署到 Azure 自动化”。 这会将你重定向到 Azure 管理门户，在此可使用 Azure 帐户凭据登录。 请注意，部署具有依赖关系的项会将所有依赖关系部署到 Azure 自动化。 通过将 **AzureAutomationNotSupported** 标记添加到项元数据可禁用“部署到 Azure 自动化”按钮。

若要了解有关 Azure 自动化的详细信息，请参阅 [Azure 自动化](/azure/automation)文档。

## <a name="updating-items-from-the-powershell-gallery"></a>更新来自 PowerShell 库中的项

若要更新从 PowerShell 库中安装的项，请运行 [Update-Module][] 或 [Update-Script][] cmdlet。 如果不使用其他任何参数运行，[Update-Module][] 尝试通过运行 [Install-Module][] 来更新每个已安装的模块。 若要选择性地更新模块，请添加 `-Name` 参数。

同样，如果不使用其他任何参数运行，[Update-Script][] 也会尝试通过运行 [Install-Script][] 来更新每个已安装的脚本。 若要选择性地更新脚本，请添加 `-Name` 参数。

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>列出从 PowerShell 库中安装的项

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
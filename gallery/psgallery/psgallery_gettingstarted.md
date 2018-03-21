---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_gettingstarted
ms.openlocfilehash: 2117712b0081db4a21f8480b458a499ed84dc512
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>PowerShell 库入门

## <a name="what-is-the-powershell-gallery"></a>PowerShell 库是什么？

PowerShell 库是 PowerShell 内容的中心存储库。
在 PowerShell 库中，可找到包含 PowerShell 命令和 Desired State Configuration (DSC) 资源的实用 PowerShell 模块。 还可找到 PowerShell 脚本，其中一些脚本可能包含 PowerShell 工作流、概述任务组和提供这些任务的序列。
某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。

## <a name="requirements"></a>要求

从 PowerShell 库将项下载到系统需要 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模块。 可在以下任何一项中找到 PowerShellGet 模块。 从 PowerShell 库下载项时无需登录。

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI 安装程序（适用于 PowerShell 3 和 4）](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet 还需要 [NuGet 提供程序](http://go.microsoft.com/fwlink/?LinkId=722208)来运行 PowerShell 库。 如果 NuGet 提供程序未处于下列一个位置中，初次使用 PowerShellGet 时，系统会自动提示安装 NuGet 提供程序：

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

也可以运行 `Install-PackageProvider -Name NuGet -Force`，以自动下载和安装 NuGet 提供程序。

  
如果 NuGet 版本低于 2.8.5.201，则需调用以下 PowerShell cmdlet 来安装并切换到 NuGet 最新版本。

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  从以上安装位置删除旧版 NuGet。

有关详细信息，请参阅 <http://oneget.org/>。

  
注意：由于打包格式的更改，建议更新到最新版本的 PowerShellGet 和 PackageManagement 来安装最近已更新的项。 PowerShellGet 包含在 Windows 10 中，可在[此处](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)了解详细信息。
PowerShellGet 也是 Windows Management Framework (WMF) 5.0 的一部分，可在[此处](http://go.microsoft.com/fwlink/?LinkId=398175)进行下载。

## <a name="discovering-items-from-the-powershell-gallery"></a>从 PowerShell 库中发现项

可通过使用本网站上的“搜索”或浏览“模块和脚本”页查找 PowerShell 库中的项。 还可以使用 `-Repository PSGallery` 运行 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 和 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlet（具体视项类型而定），从而查找 PowerShell 库中的项。

通过使用 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 和 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) 的以下参数可从库中筛选结果

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

如果只想发现库中的特定 DSC 资源，可运行 [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet。
[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) 会返回库中 DSC 资源的相关数据。 由于 DSC 资源始终作为模块的部分进行传递，所以仍需运行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 来安装这些 DSC 资源。

## <a name="learning-about-items-in-the-powershell-gallery"></a>了解 PowerShell 库中的项

找到感兴趣的项后，你可能希望了解与其有关的详细信息。 可检查库中该项的特定页来了解详细信息。 在该页上可查看该项中上传的所有元数据。 项的元数据由项作者提供，Microsoft 不会进行验证。 项的所有者紧密关联到发布该项的 PowerShell 库帐户，比作者字段更可信。

如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。

如果运行 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 或 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)，则可在返回的 PSGetModuleInfo 对象中查看该数据。
例如，运行 `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` 会返回库中 PSReadLine 模块的相关数据。

## <a name="downloading-items-from-the-powershell-gallery"></a>从 PowerShell 库中下载项

从 PowerShell 库中下载项时，议使用下列过程：

### <a name="inspect"></a>检查

若要下载库中的项以供检查，请运行 [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 或 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet，具体视项类型而定。 此操作可本地保存项而不进行安装，并且可以检查项内容。 请记得手动删除已保存的项。

某些项由 Microsoft 编写，其他项由 PowerShell 社区编写。 Microsoft 建议安装前检查库中项的内容和代码。

如果发现发布的项不可信，请单击该项页面上的“举报不良信息”。

### <a name="install"></a>安装

若要安装库中的项以供使用，请运行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 或 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet，具体视项类型而定。

默认情况下，[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 将模块安装到 `$env:ProgramFiles\WindowsPowerShell\Modules`。 此操作需要管理员帐户。 如果添加 `-Scope
CurrentUser` 参数，模块将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。

默认情况下，[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 将脚本安装到 `$env:ProgramFiles\WindowsPowerShell\Scripts`。 此操作需要管理员帐户。 如果添加 `-Scope
CurrentUser` 参数，脚本将安装到 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。

默认情况下，[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 和 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 安装项的最新版本。 若要安装旧版项，请添加 `-RequiredVersion` 参数。

### <a name="deploy"></a>在来宾群集上部署

若要将项从 PowerShell 库部署到 Azure 自动化，请单击项详细信息页上的“部署到 Azure 自动化”。 这会将你重定向到 Azure 管理门户，在此可使用 Azure 帐户凭据登录。 请注意，部署具有依赖关系的项会将所有依赖关系部署到 Azure 自动化。 通过将 **AzureAutomationNotSupported** 标记添加到项元数据可禁用“部署到 Azure 自动化”按钮。

若要了解有关 Azure 自动化的详细信息，请参阅 [Azure 自动化网站](http://azure.microsoft.com/services/automation/)。

## <a name="updating-items-from-the-powershell-gallery"></a>更新来自 PowerShell 库中的项

若要更新从 PowerShell 库中安装的项，请运行 [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) 或 [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet。 不使用任何其他参数运行时，通过运行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663)，[Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) 会尝试更新每个已安装模块。
若要选择性地更新模块，请添加 `-Name` 参数。

同样，不使用任何其他参数运行时，通过运行 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)，[Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) 也会尝试更新每个已安装脚本。
若要选择性地更新脚本，请添加 `-Name` 参数。

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>列出从 PowerShell 库中安装的项

若要确定已安装 PowerShell 库中的哪些模块，请运行 [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet。 该命令会列出系统上所有已直接从 PowerShell 库安装的模块。

同样，若要确定已安装 PowerShell 库中的哪些脚本，请运行 [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet。 此命令会列出系统上所有已直接从 PowerShell 库安装的脚本。


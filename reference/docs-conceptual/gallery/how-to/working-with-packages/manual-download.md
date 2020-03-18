---
ms.date: 09/11/2018
contributor: JKeithB
keywords: 库, powershell, psgallery
title: 手动包下载
ms.openlocfilehash: e562f5b94b4d2caa7d31269a324e417d1a9e844a
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278695"
---
# <a name="manual-package-download"></a>手动包下载

PowerShell 库支持直接下载网站中的包而无需使用 PowerShellGet cmdlet。 可以将任何包下载为 NuGet 包 (`.nupkg`) 文件，然后可以将该文件复制到内部存储库。

> [!NOTE]
> 手动包下载并非  旨在替代 `Install-Module` cmdlet。
> 下载包不会安装模块或脚本。 下载的 NuGet 包中不包含依赖项。 以下说明仅供参考。

## <a name="using-manual-download-to-acquire-a-package"></a>使用手动下载以获取包

每个页面都有一个手动下载链接，如下所示：

![手动下载](media/manual-download/packagedisplaypagewithpseditions.png)

若要手动下载，请单击“下载原始 nupkg 文件”  。 将包的副本复制到名称为 `<name>.<version>.nupkg` 的浏览器的下载文件夹中。

NuGet 包是一个 ZIP 存档，其中的额外文件包含有关包内容的信息。 某些浏览器（如 Internet Explorer）会自动将 `.nupkg` 文件扩展名替换为 `.zip`。 要展开包，请根据需要将 `.nupkg` 文件重命名为 `.zip`，然后将内容提取到本地文件夹。

NuGet 包文件包含以下特定于 NuGet  的元素，这些元素不是原始打包代码的一部分：

- 名为 `_rels` 的文件夹 - 包含列出依赖项的 `.rels` 文件
- 名为 `package` 的文件夹 - 包含特定于 NuGet 的数据
- 名为 `[Content_Types].xml` 的文件 - 描述 PowerShellGet 等扩展如何与 NuGet 一起使用
- 名为 `<name>.nuspec` 的文件 - 包含大量元数据

## <a name="installing-powershell-modules-from-a-nuget-package"></a>从 NuGet 包安装 PowerShell 模块

> [!NOTE]
> 这些说明并未给出与运行 `Install-Module` 相同的结果  。 这些说明满足最低要求。 它们并非 `Install-Module` 的替代品。
> `Install-Module` 执行的某些步骤不包括在内。

最简单的方法是从文件夹中删除特定于 NuGet 的元素。 删除元素将保留由包创建者创建的 PowerShell 代码。
有关特定于 NuGet 的元素的列表，请参阅[使用手动下载以获取包](#using-manual-download-to-acquire-a-package)。

步骤如下：

1. 取消阻止 Internet 下载的 NuGet 包 (`.nupkg`) 文件，例如使用 `Unblock-File -Path C:\Downloads\module.nupkg` cmdlet。
2. 将 NuGet 包的内容提取到本地文件夹。
2. 从文件夹中删除特定于 NuGet 的元素。
3. 重命名文件夹。 默认文件夹名称通常是 `<name>.<version>`。 若将模块标记为预发布版本，则版本可包含 `-prerelease`。 将文件夹重命名为模块名称。 例如，`azurerm.storage.5.0.4-preview` 重命名为 `azurerm.storage`。
4. 将文件夹复制到 `$env:PSModulePath value` 中的一个文件夹。 `$env:PSModulePath` 是以分号分隔的一组路径，PowerShell 应在这些路径中查找模块。

> [!IMPORTANT]
> 手动下载不包括模块所需的任何依赖项。 若包具有依赖项，则必须在系统上安装它们才能使此模块正常工作。 PowerShell 库显示包所需的所有依赖项。

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>在 NuGet 包安装 PowerShell 脚本

> [!NOTE]
> 这些说明并未给出与运行 `Install-Script` 相同的结果  。 这些说明满足最低要求。 它们并非 `Install-Script` 的替代品。

最简单的方法是提取 NuGet 包，然后直接使用脚本。

步骤如下：

1. 取消阻止 Internet 下载的 NuGet 包 (`.nupkg`) 文件，例如使用 `Unblock-File -Path C:\Downloads\package.nupkg` cmdlet。
2. 提取 NuGet 包的内容。
2. 文件夹中的 `.PS1` 文件可直接从此位置使用。
3. 可删除文件夹中特定于 NuGet 的元素。

有关特定于 NuGet 的元素的列表，请参阅[使用手动下载以获取包](#using-manual-download-to-acquire-a-package)。

> [!IMPORTANT]
> 手动下载不包括模块所需的任何依赖项。 若包具有依赖项，则必须在系统上安装它们才能使此模块正常工作。 PowerShell 库显示包所需的所有依赖项。

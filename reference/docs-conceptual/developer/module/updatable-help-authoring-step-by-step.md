---
title: 可更新的帮助创作：分步 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366986"
---
# <a name="updatable-help-authoring-step-by-step"></a>可更新帮助创作：分步

此文档列出了创作可更新帮助的过程中的步骤。

## <a name="authoring-updatable-help-step-by-step"></a>创作可更新帮助：分步

可更新帮助是为最终用户设计的，但它还为模块作者和帮助编写人员提供了显著的好处，包括添加内容、修复错误、在多个 UI 区域性中交付以及响应用户注释和请求的能力，长时间之后模块已寄送。 本主题介绍如何打包和上传帮助文件，以便用户可以使用[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[get-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 下载和安装帮助文件。

以下步骤概述了支持可更新帮助的过程。

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>步骤1：查找帮助文件的 Internet 站点

创建可更新帮助的第一步是在 Internet 位置查找模块的帮助文件。 实际上，可以使用两个不同的位置。 可以在一个 Internet 位置将模块的帮助信息文件（HelpInfo XML）保存在一个 Internet 位置，并将帮助内容 CAB 文件保留在另一个 Internet 位置。 模块的所有帮助内容 CAB 文件都必须位于同一位置。 可以将不同模块的帮助内容 CAB 文件放置在同一位置。

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>步骤2：将 HelpInfoURI 键添加到模块清单

将**HelpInfoURI**键添加到模块清单中。 键的值是模块的 HelpInfo XML 信息文件位置的统一资源标识符（URI）。 为安全，该地址必须以 "http" 或 "https" 开头。 URI 应指定 Internet 位置，但不得包含 HelpInfo XML 文件名。

例如：

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>步骤3：创建 HelpInfo XML 文件

HelpInfo XML 信息文件包含帮助文件的 Internet 位置的 URI，以及每个受支持的 UI 区域性中的模块的最新帮助文件的版本号。 每个 Windows PowerShell 模块都有一个 HelpInfo XML 文件。 更新帮助文件时，请编辑或替换 HelpInfo XML 文件;不添加另一个。 有关详细信息，请参阅[如何创建 HELPINFO XML 文件](./how-to-create-a-helpinfo-xml-file.md)。

### <a name="step-4-sign-your-help-files"></a>步骤4：签署帮助文件

数字签名并不是必需的，但在您共享文件时，这是最佳做法建议。

### <a name="step-5-create-cab-files"></a>步骤5：创建 CAB 文件

使用创建 cabinet 文件（.cab）的工具（如 MakeCab）来创建。CAB 文件，其中包含模块的帮助文件。 为每个支持的 UI 区域性中的帮助文件创建单独的 CAB 文件。 有关详细信息，请参阅[如何准备可更新的帮助 CAB 文件](./how-to-prepare-updatable-help-cab-files.md)。

### <a name="step-6-upload-your-files"></a>步骤6：上传文件

若要发布新的或更新的帮助文件，请将 CAB 文件上传到 HelpInfo XML 文件中的**HelpContentUri**元素所指定的 Internet 位置。 然后，将 HelpInfo XML 文件上传到由模块清单中的**HelpInfoUri**键的值指定的 Internet 位置。

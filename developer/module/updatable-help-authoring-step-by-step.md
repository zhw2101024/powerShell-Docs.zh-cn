---
title: 可更新帮助创作：Step-by-Step | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082118"
---
# <a name="updatable-help-authoring-step-by-step"></a>可更新帮助创作：分步指南

此文档列出了创作可更新帮助的过程中的步骤。

## <a name="authoring-updatable-help-step-by-step"></a>创作可更新的帮助：分步指南

可更新的帮助，专门用于最终用户，但它还提供对模块作者的好处很明显，帮助编写器，包括能够添加内容，修复错误，提供在多个 UI 区域性，并响应用户注释和请求，长时间后模块已发货。 本主题介绍如何打包并上传的帮助文件，以便用户可以下载并使用安装[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。

以下步骤概述了支持可更新帮助的过程。

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>步骤 1：为帮助文件中查找 Internet 的站点

创建可更新帮助的第一步是查找您的模块的帮助文件的 Internet 位置。 实际上，您可以使用两个不同位置。 您可以将一个 Internet 位置和另一个 Internet 位置的帮助内容的 CAB 文件保留您的模块的帮助信息文件 (HelpInfo XML-如下所述)。 所有帮助内容 CAB 文件的模块必须都位于同一位置。 可以将不同的模块的帮助内容 CAB 文件放在相同的位置。

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>步骤 2：将 HelpInfoURI 密钥添加到模块清单

添加**HelpInfoURI**向模块清单键。 键的值是位置的您的模块的 HelpInfo XML 信息文件的统一资源标识符 (URI)。 为了安全，地址必须以"http"或"https"开头。 URI 应指定 Internet 位置，但不能包含 HelpInfo XML 文件名称。

例如：

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>步骤 3:创建 HelpInfo XML 文件

HelpInfo XML 信息文件包含您的帮助文件和每个受支持的 UI 区域性中模块的最新帮助文件的版本号的 Internet 位置的 URI。 每个 Windows PowerShell 模块具有一个 HelpInfo XML 文件。 当您更新您的帮助文件时，编辑或替换 HelpInfo XML 文件中;不添加另一个。 有关详细信息，请参阅[如何创建 HelpInfo XML 文件](./how-to-create-a-helpinfo-xml-file.md)。

### <a name="step-4-sign-your-help-files"></a>步骤 4:登录您的帮助文件

数字签名不是必需的但它们是建议的最佳做法，只要共享文件。

### <a name="step-5-create-cab-files"></a>步骤 5:创建 CAB 文件

使用创建 cabinet (.cab) 文件，如 MakeCab.exe，若要创建的工具。包含有关你的模块的帮助文件的 CAB 文件。 每个受支持的 UI 区域性中创建单独的 CAB 文件适用于帮助文件。 有关详细信息，请参阅[如何准备可更新帮助的 CAB 文件](./how-to-prepare-updatable-help-cab-files.md)。

### <a name="step-6-upload-your-files"></a>步骤 6:将文件上传

若要发布新的或更新的帮助文件，请将 CAB 文件上载到由指定的 Internet 位置**HelpContentUri** HelpInfo XML 文件中的元素。 然后，将 HelpInfo XML 文件上传到的值所指定的 Internet 位置**HelpInfoUri**密钥模块清单中。

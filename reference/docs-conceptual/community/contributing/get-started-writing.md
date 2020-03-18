---
title: 开始参与撰写 PowerShell 文档
description: 本文简要介绍如何作为参与者开始参与撰写 PowerShell 文档。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 95eb2c3157a99fcb6560914da8464022e1b64fad
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060302"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>开始参与撰写 PowerShell 文档

本文简要介绍如何作为参与者开始参与撰写 PowerShell 文档。

## <a name="powershell-docs-structure"></a>PowerShell-Docs 结构

[PowerShell-Docs 存储库][psdocs]分为两组内容。 Git 分支用于管理发布文档的方式和时间。

### <a name="reference-content"></a>参考内容

参考内容是 PowerShell 中提供的 cmdlet 的 PowerShell cmdlet 参考。
[参考][ref]收集在版本文件夹（5.1、6、7.0 和 7.1）中。 此内容仅包含随 PowerShell 提供的模块的 cmdlet 参考。 此内容还用于创建 `Get-Help` cmdlet 显示的帮助信息。

> [!NOTE]
> 参考内容的目录 (TOC) 由发布系统自动生成。 无需更新 TOC。

### <a name="conceptual-content"></a>概念性内容

概念性文档包括以下内容：

- 发行说明
- 设置说明
- 示例脚本和操作说明文章
- DSC 文档
- SDK 文档

[概念性文档][conceptual]不是按版本组织的。 将显示 PowerShell 每个版本的所有文章。 我们正在努力创建版本特定的文章。 如果文档提供该功能，则本指南将更新，并提供相应的信息。

> [!NOTE]
> 每当添加、删除或重命名概念性文章时，目录必须更新并包含在拉取请求中。

## <a name="using-git-branches"></a>使用 git 分支

PowerShell-Docs 的默认分支是 `staging` 分支。 对工作分支所做的更改先合并到 `staging` 分支中，再进行发布。 `staging` 分支大约一周合并一次到 `live` 分支中。 `live` 分支包含发布到 docs.microsoft.com 的内容。 不应直接在 `live` 分支中进行更改。

若要将仅适用于尚未发布的 PowerShell 版本的更改提交到文档，请检查该版本是否有发布分支。 适用于特定的未来版本的所有更改都应以发布分支为目标。 发布分支的名称模式如下所示：`release-<version>`。

在开始任何更改之前，请在 PowerShell-Docs 存储库的本地副本中创建工作分支。 这应该是[分支克隆][fork]。 在创建工作分支之前，请务必同步本地存储库。 应从 `staging` 或 `release` 分支的更新副本创建工作分支。

使要提交的更改遵循中心参与者指南的[进行更改][making-changes]部分中的进程。

### <a name="creating-new-articles"></a>创建新文章

必须为要参与撰写的任何新文档创建 GitHub 问题。 查看现有问题，以确保避免重复性工作。 分配给某人的问题被视为“正在进行”。 如果想要协作解决某个问题，请联系分配给该问题的人员。

类似于 PowerShell [RFC 过程][rfc]，在编写内容之前创建问题可确保你不会花费大量时间和精力处理 PowerShell-Docs 团队拒绝的内容。 这样，我们就可以与你就内容的范围以及该内容应在 PowerShell 文档中的适当位置进行协商。

### <a name="updating-existing-articles"></a>更新现有文章

如果适用，cmdlet 参考文章在所有版本的 PowerShell 中都是重复的。 在报告有关 cmdlet 参考或 `About_` 文章的问题时，必须指定哪些版本受到此问题影响。 GitHub 中的问题模板包含版本的清单。 使用复选框可指定哪些版本的内容受到影响。 针对影响多个版本内容的问题向文章提交更改时，必须将相应的更改应用于文件的每个版本。

## <a name="next-steps"></a>后续步骤

请参阅[提交拉取请求](pull-requests.md)

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
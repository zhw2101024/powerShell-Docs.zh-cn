---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="unlisting-items"></a>取消列出项

**为什么未显示从 PowerShell 库删除项的选项？**

PowerShell 库不支持用户永久删除其项。 这让其他人能够依赖你的项而无需担心将来可能产生的中断。 例如，如果 Pester 模块依赖 Azure 模块，而 Azure 模块从库中删除，那么用户将不能使用 Pester 模块。

你无法删除项，但可将其取消列出。

**在 PowerShell 库中取消列出项的作用是什么？**

在 PowerShell 库中取消列出项（例如模块或脚本）会将其从“项”选项卡中删除。
此外，使用搜索栏将无法发现取消列出的项。
下载取消列出的项的唯一方法是指定项的精确名称和版本。
因此，取消列出的项将不会破坏依赖它的其他模块或脚本。

若要取消列出项，可访问项详细信息页，选择“删除项”。 取消选中“列出”复选框，单击“保存”。

**如何删除项？**

如果你遇到有必要删除项的情况，请与 PowerShell 库管理员联系。
正当的删除情况包括：
- 侵犯版权问题。
- 项包含可能有害的内容。
- 项包含敏感数据。

若要向 PowerShell 库管理员提交删除项请求，请访问项的详细信息页面并选择“联系支持人员”。  



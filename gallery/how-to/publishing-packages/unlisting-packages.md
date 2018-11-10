---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 取消列出包
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003674"
---
# <a name="unlisting-packages"></a>取消列出包

为什么未显示从 PowerShell 库删除包的选项？

PowerShell 库不支持用户永久删除其包。
这让其他人能够依赖你的包而无需担心将来可能产生的中断。
例如，如果 Pester 模块依赖 Azure 模块，而 Azure 模块从库中删除，那么用户将不能使用 Pester 模块。

无法删除包，但可将其取消列出。

在 PowerShell 库中取消列出包的作用是什么？

在 PowerShell 库中取消列出包（例如模块或脚本）会将其从“包”选项卡中移除。此外，使用搜索栏将无法发现取消列出的包。
下载取消列出的包的唯一方法是指定包的确切名称和版本。
因此，取消列出的包将不会中断依赖它的其他模块或脚本。

若要取消列出包，可访问包详细信息页，选择“删除模块”。 取消选中“列出”复选框，单击“保存”。

如何移除包？

如果遇到有必要删除包的情况，请与 PowerShell 库管理员联系。
正当的删除情况包括：
- 侵犯版权问题。
- 包包含可能有害的内容。
- 包包含敏感数据。

若要向 PowerShell 库管理员提交删除包请求，请访问包的详细信息页并选择“联系支持人员”。

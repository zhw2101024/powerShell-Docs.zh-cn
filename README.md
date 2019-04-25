---
ms.openlocfilehash: 6e36e6599e36218ce2a925dceda7aa0ee6811057
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068821"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 开放源代码行为准则

此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。
有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)，或如果有任何其他问题或意见，请与 [opencode@microsoft.com ](mailto:opencode@microsoft.com) 联系。

[![生成状态](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>PowerShell 文档

欢迎使用 PowerShell 文档存储库，其中包含官方 PowerShell 文档。

## <a name="repository-structure"></a>存储库结构

此存储库中的以下每个顶级文件夹都包含一个发布到 [Microsoft Docs](https://docs.microsoft.com/powershell) 的 DocSet。

- [/developer/](https://docs.microsoft.com/powershell/developer/) 是 PowerShell SDK 文档的未来之家
  - 我们正在从 MSDN 迁移此内容
- [/dsc/](https://docs.microsoft.com/powershell/dsc/) 对应于 Desired State Configuration 功能
- [/gallery/](https://docs.microsoft.com/powershell/gallery) 对应于 [PowerShell 库](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) 对应于 Just Enough Administration 功能
- [/reference/](https://docs.microsoft.com/powershell/scripting/) 对应于跨版本 3.0、4.0、5.0、5.1 和 6.0 的 PowerShell 概念主题和模块参考
  - 此内容也是 `Get-Help` cmdlet 检索的帮助内容的来源
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme) 包含 Windows Management Framework 的发行说明，该软件包用于将 PowerShell 的新版本分发到之前版本的 Windows。

## <a name="contributing"></a>贡献文档

通过[拉取请求](https://help.github.com/articles/using-pull-requests/)到临时分支，我们正积极将贡献文档并入此存储库。
请注意在提交拉取请求前，必须签订[文档贡献许可协议](https://cla.microsoft.com/)，以确保社区成员可免费使用你的文档。

若要详细了解如何参与，请阅读[参与者指南](CONTRIBUTING.md)。
参与者指南详细介绍了如何参与撰写文档、推荐的工具以及样式和格式设置要求。
请使用“问题和提取请求”模板来帮助文档在各版本之间保持一致性。

## <a name="licenses"></a>许可证

此项目有两个许可证文件。
MIT 许可证适用于包含在此存储库中的代码。
Creative Commons 许可证适用于文档。
---
ms.openlocfilehash: 6e36e6599e36218ce2a925dceda7aa0ee6811057
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068821"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="a77ce-101">Microsoft 开放源代码行为准则</span><span class="sxs-lookup"><span data-stu-id="a77ce-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="a77ce-102">此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="a77ce-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="a77ce-103">有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)，或如果有任何其他问题或意见，请与 [opencode@microsoft.com ](mailto:opencode@microsoft.com) 联系。</span><span class="sxs-lookup"><span data-stu-id="a77ce-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

<span data-ttu-id="a77ce-104">[![生成状态](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span><span class="sxs-lookup"><span data-stu-id="a77ce-104">[![Build status](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="a77ce-105">PowerShell 文档</span><span class="sxs-lookup"><span data-stu-id="a77ce-105">PowerShell Documentation</span></span>

<span data-ttu-id="a77ce-106">欢迎使用 PowerShell 文档存储库，其中包含官方 PowerShell 文档。</span><span class="sxs-lookup"><span data-stu-id="a77ce-106">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="a77ce-107">存储库结构</span><span class="sxs-lookup"><span data-stu-id="a77ce-107">Repository Structure</span></span>

<span data-ttu-id="a77ce-108">此存储库中的以下每个顶级文件夹都包含一个发布到 [Microsoft Docs](https://docs.microsoft.com/powershell) 的 DocSet。</span><span class="sxs-lookup"><span data-stu-id="a77ce-108">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="a77ce-109">[/developer/](https://docs.microsoft.com/powershell/developer/) 是 PowerShell SDK 文档的未来之家</span><span class="sxs-lookup"><span data-stu-id="a77ce-109">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="a77ce-110">我们正在从 MSDN 迁移此内容</span><span class="sxs-lookup"><span data-stu-id="a77ce-110">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="a77ce-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) 对应于 Desired State Configuration 功能</span><span class="sxs-lookup"><span data-stu-id="a77ce-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="a77ce-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) 对应于 [PowerShell 库](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="a77ce-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="a77ce-113">[/jea/](https://docs.microsoft.com/powershell/jea/) 对应于 Just Enough Administration 功能</span><span class="sxs-lookup"><span data-stu-id="a77ce-113">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="a77ce-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) 对应于跨版本 3.0、4.0、5.0、5.1 和 6.0 的 PowerShell 概念主题和模块参考</span><span class="sxs-lookup"><span data-stu-id="a77ce-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="a77ce-115">此内容也是 `Get-Help` cmdlet 检索的帮助内容的来源</span><span class="sxs-lookup"><span data-stu-id="a77ce-115">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="a77ce-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) 包含 Windows Management Framework 的发行说明，该软件包用于将 PowerShell 的新版本分发到之前版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="a77ce-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="a77ce-117">贡献文档</span><span class="sxs-lookup"><span data-stu-id="a77ce-117">Contributing</span></span>

<span data-ttu-id="a77ce-118">通过[拉取请求](https://help.github.com/articles/using-pull-requests/)到临时分支，我们正积极将贡献文档并入此存储库。</span><span class="sxs-lookup"><span data-stu-id="a77ce-118">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="a77ce-119">请注意在提交拉取请求前，必须签订[文档贡献许可协议](https://cla.microsoft.com/)，以确保社区成员可免费使用你的文档。</span><span class="sxs-lookup"><span data-stu-id="a77ce-119">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="a77ce-120">若要详细了解如何参与，请阅读[参与者指南](CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="a77ce-120">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="a77ce-121">参与者指南详细介绍了如何参与撰写文档、推荐的工具以及样式和格式设置要求。</span><span class="sxs-lookup"><span data-stu-id="a77ce-121">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="a77ce-122">请使用“问题和提取请求”模板来帮助文档在各版本之间保持一致性。</span><span class="sxs-lookup"><span data-stu-id="a77ce-122">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="a77ce-123">许可证</span><span class="sxs-lookup"><span data-stu-id="a77ce-123">Licenses</span></span>

<span data-ttu-id="a77ce-124">此项目有两个许可证文件。</span><span class="sxs-lookup"><span data-stu-id="a77ce-124">There are two license files for this project.</span></span>
<span data-ttu-id="a77ce-125">MIT 许可证适用于包含在此存储库中的代码。</span><span class="sxs-lookup"><span data-stu-id="a77ce-125">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="a77ce-126">Creative Commons 许可证适用于文档。</span><span class="sxs-lookup"><span data-stu-id="a77ce-126">The Creative Commons license applies to the documentation.</span></span>
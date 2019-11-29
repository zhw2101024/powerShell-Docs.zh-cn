---
ms.openlocfilehash: 034d75a84e39cb0cf88a272ca58b5ccc229c5d9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540460"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="b3799-101">Microsoft 开放源代码行为准则</span><span class="sxs-lookup"><span data-stu-id="b3799-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="b3799-102">此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="b3799-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="b3799-103">有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)，或如果有任何其他问题或意见，请与 [opencode@microsoft.com ](mailto:opencode@microsoft.com) 联系。</span><span class="sxs-lookup"><span data-stu-id="b3799-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="b3799-106">生成状态</span><span class="sxs-lookup"><span data-stu-id="b3799-106">Build Status</span></span>

| <span data-ttu-id="b3799-107">活动分支</span><span class="sxs-lookup"><span data-stu-id="b3799-107">Live Branch</span></span> | <span data-ttu-id="b3799-108">临时分支</span><span class="sxs-lookup"><span data-stu-id="b3799-108">Staging Branch</span></span> |
|:------------|:---------------|
| <span data-ttu-id="b3799-109">[![live-badge][]][live-badge]</span><span class="sxs-lookup"><span data-stu-id="b3799-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="b3799-110">[![staging-badge][]][staging-badge]</span><span class="sxs-lookup"><span data-stu-id="b3799-110">[![staging-badge][]][staging-badge]</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="b3799-111">PowerShell 文档</span><span class="sxs-lookup"><span data-stu-id="b3799-111">PowerShell Documentation</span></span>

<span data-ttu-id="b3799-112">欢迎使用 PowerShell 文档存储库，其中包含官方 PowerShell 文档。</span><span class="sxs-lookup"><span data-stu-id="b3799-112">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="b3799-113">存储库结构</span><span class="sxs-lookup"><span data-stu-id="b3799-113">Repository Structure</span></span>

<span data-ttu-id="b3799-114">此存储库中的以下每个顶级文件夹都包含一个发布到 [Microsoft Docs](https://docs.microsoft.com/powershell) 的 DocSet。</span><span class="sxs-lookup"><span data-stu-id="b3799-114">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="b3799-115">[/reference/](https://docs.microsoft.com/powershell/scripting/) 对应于跨 5.1、6.0 和 7.0 版本的 PowerShell 概念主题和模块参考。</span><span class="sxs-lookup"><span data-stu-id="b3799-115">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 5.1, 6.0, and 7.0.</span></span> <span data-ttu-id="b3799-116">此内容也是 `Get-Help` cmdlet 检索的帮助内容的来源。</span><span class="sxs-lookup"><span data-stu-id="b3799-116">This content is also the source of help content retrieved by the `Get-Help` cmdlet.</span></span>
  - <span data-ttu-id="b3799-117">[docs-conceptual/](https://docs.microsoft.com/powershell) - 此文件夹包含概念文档和以下文档集：</span><span class="sxs-lookup"><span data-stu-id="b3799-117">[docs-conceptual/](https://docs.microsoft.com/powershell) - this folder contains the conceptual documentation and the following docsets:</span></span>
    - <span data-ttu-id="b3799-118">[developer/](https://docs.microsoft.com/powershell/scripting/developer/) 是 PowerShell SDK 文档（从 MSDN 迁移）</span><span class="sxs-lookup"><span data-stu-id="b3799-118">[developer/](https://docs.microsoft.com/powershell/scripting/developer/) is the PowerShell SDK documentation (migrated from MSDN)</span></span>
    - <span data-ttu-id="b3799-119">[dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) 对应于 Desired State Configuration 功能</span><span class="sxs-lookup"><span data-stu-id="b3799-119">[dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) is for the Desired State Configuration feature</span></span>
    - <span data-ttu-id="b3799-120">[gallery/](https://docs.microsoft.com/powershell/scripting/gallery) 对应于 [PowerShell 库](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="b3799-120">[gallery/](https://docs.microsoft.com/powershell/scripting/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
    - <span data-ttu-id="b3799-121">[jea/](https://docs.microsoft.com/powershell/scripting/jea/) 对应于 Just Enough Administration 功能</span><span class="sxs-lookup"><span data-stu-id="b3799-121">[jea/](https://docs.microsoft.com/powershell/scripting/jea/) is for the Just Enough Administration feature</span></span>
    - <span data-ttu-id="b3799-122">[wmf/](https://docs.microsoft.com/powershell/scripting/wmf/overview) 包含 Windows Management Framework 的发行说明，该软件包用于将 PowerShell 的新版本分发到之前版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="b3799-122">[wmf/](https://docs.microsoft.com/powershell/scripting/wmf/overview) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="b3799-123">贡献文档</span><span class="sxs-lookup"><span data-stu-id="b3799-123">Contributing</span></span>

<span data-ttu-id="b3799-124">通过[拉取请求](https://help.github.com/articles/using-pull-requests/)到临时  分支，我们正积极将贡献文档并入此存储库。</span><span class="sxs-lookup"><span data-stu-id="b3799-124">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="b3799-125">请注意在提交拉取请求前，必须签订[文档贡献许可协议](https://cla.microsoft.com/)，以确保社区成员可免费使用你的文档。</span><span class="sxs-lookup"><span data-stu-id="b3799-125">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="b3799-126">若要详细了解如何参与，请阅读[参与者指南](https://docs.microsoft.com/contribute/powershell/powershell-contribute)。</span><span class="sxs-lookup"><span data-stu-id="b3799-126">For more information on contributing, read our [contributor's guide](https://docs.microsoft.com/contribute/powershell/powershell-contribute).</span></span> <span data-ttu-id="b3799-127">参与者指南详细介绍了如何参与撰写文档、推荐的工具以及样式和格式设置要求。</span><span class="sxs-lookup"><span data-stu-id="b3799-127">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span> <span data-ttu-id="b3799-128">请使用“问题和提取请求”模板来帮助文档在各版本之间保持一致性。</span><span class="sxs-lookup"><span data-stu-id="b3799-128">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="b3799-129">许可证</span><span class="sxs-lookup"><span data-stu-id="b3799-129">Licenses</span></span>

<span data-ttu-id="b3799-130">此项目有两个许可证文件。</span><span class="sxs-lookup"><span data-stu-id="b3799-130">There are two license files for this project.</span></span> <span data-ttu-id="b3799-131">MIT 许可证适用于包含在此存储库中的代码。</span><span class="sxs-lookup"><span data-stu-id="b3799-131">The MIT License applies to the code contained in this repo.</span></span> <span data-ttu-id="b3799-132">Creative Commons 许可证适用于文档。</span><span class="sxs-lookup"><span data-stu-id="b3799-132">The Creative Commons license applies to the documentation.</span></span>
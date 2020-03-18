---
ms.date: 06/12/2017
contributor: JKeithB, SydneyhSmith
keywords: 库,powershell,cmdlet,psgallery
description: 面向发行者的指南
title: PowerShell 库发布指南和最佳做法
ms.openlocfilehash: 07271e037100350d3efc7ae63860f42afd22aae7
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278201"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShell 库发布指南和最佳做法

本文介绍了 Microsoft 团队使用的推荐步骤，以确保发布到 PowerShell 库的包将被广泛采用，并根据 PowerShell 库处理清单数据的方式和大量 PowerShell 库用户的反馈来为用户提供高价值包。 按照这些指南发布的包的安装和受信任几率更高，并且更有可能会吸引更多用户。

下面的指南介绍了高质量 PowerShell 库包有哪些关键要素、哪些是最重要的可选清单设置、如何使用初始审阅者的反馈和 [Powershell 脚本分析器](https://aka.ms/psscriptanalyzer)改进代码、如何对模块进行版本控制，以及有关如何使用已共享内容的文档、测试和示例。 本文档的大部分内容遵循有关发布[高质量 DSC 资源模块](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)的指南。

有关将包发布到 PowerShell 库的机制，请参阅[创建和发布包](../how-to/publishing-packages/publishing-a-package.md)。

欢迎随时提供有关这些指南的反馈。 如有任何反馈，请在我们的 [GitHub 文档存储库](https://github.com/powershell/powershell-docs/issues)中记录待解决问题。

## <a name="best-practices-for-publishing-packages"></a>发布包的最佳做法

下面按名义上的优先级顺序列出了 PowerShell 库项用户认为重要的最佳做法。 按照下面这些指南发布包会大大提升它们被其他用户下载和采用的几率。

- 使用 PSScriptAnalyzer
- 添加文档和示例
- 及时响应反馈
- 提供模块（而不是脚本）
- 提供项目网站链接
- 使用兼容 PSEdition 和平台对包进行标记
- 随模块添加测试
- 添加和/或链接到许可条款
- 对代码进行签名
- 遵循 [SemVer](https://semver.org/) 指南进行版本控制
- 使用“常见 PowerShell 库标记”中收录的常见标记
- 使用本地存储库测试发布
- 使用 PowerShellGet 发布

下面的各个部分简要介绍了上述每种最佳做法。

## <a name="use-psscriptanalyzer"></a>使用 PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) 是一款用于处理 PowerShell 代码的免费静态代码分析工具。 PSScriptAnalyzer  可发现 PowerShell 代码中存在的最常见问题，通常还会建议如何解决问题。 此工具易于使用，并将问题分类为“错误”（必须解决的严重问题）、“警告”（需要查看并应解决的问题）和“信息”（值得参阅最佳做法的问题）。 所有发布到 PowerShell 库的包都会使用 PSScriptAnalyzer  进行扫描，任何错误都会向所有者报告，并且必须予以修复。

最佳做法是使用 `-Recurse` 和 `-Severity` 警告运行 `Invoke-ScriptAnalyzer`。

查看结果并确保：

- 已更正或修复文档中的所有错误。
- 已查看并在必要时解决所有警告。

强烈建议从 PowerShell 库下载包的用户运行 **PSScriptAnalyzer**，并评估所有错误和警告。 如果用户看到 PSScriptAnalyzer  报告的错误，他们很有可能会与包所有者进行联系。 如果包有充分理由保留标记为错误的代码，请将相应信息添加到文档中，以免多次回答同一问题。

## <a name="include-documentation-and-examples"></a>添加文档和示例

文档和示例是确保用户可以利用所有已共享代码的最佳方式。

文档是在发布到 PowerShell Gallery 的包中所添加的最实用内容。
用户通常会忽略没有文档的包，因为只能通过阅读代码来了解包的用途和使用方式。 有多篇文章都介绍了如何为 PowerShell 包提供文档，包括：

- [如何编写 Cmdlet 帮助](https://go.microsoft.com/fwlink/?LinkID=123415)中介绍了有关如何提供帮助的指南。
- 创建 cmdlet 帮助，这是最适合任何 PowerShell 脚本、函数或 cmdlet 的方法。
  有关如何创建 cmdlet 帮助的信息，请从[如何编写 Cmdlet 帮助](https://go.microsoft.com/fwlink/?LinkID=123415)入手。
  若要在脚本中添加帮助，请参阅[关于基于评论的帮助](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。
- 许多模块还包括文本格式的文档，如 MarkDown 文件。 当在 Markdown 作为一种广泛使用格式的 GitHub 中有项目网站时，这尤为有用。 最佳做法是使用 [GitHub 式 Markdown](https://help.github.com/categories/writing-on-github/)。

示例可以向用户展示如何使用包。 许多开发者都表示，他们在查看文档之前会先查看示例，了解如何使用某项。 最适合的示例不仅展示了基本用法，还展示了模拟实际用例，同时对代码进行了详细注释。 发布到 PowerShell 库的模块的示例应位于模块根下的 Examples 文件夹中。

`Examples\RegistryResource` 文件夹下的 [PSDscResource 模块](https://www.powershellgallery.com/packages/PSDscResources)中包含优质示例模式。 具体包含四个示例用例，每个文件的顶部都简要说明了要演示的内容。

## <a name="manage-dependencies"></a>管理依赖项

请务必在模块清单中指定你的模块所依赖的模块。 这样，最终用户就不必为安装你的模块所依赖的正确版本模块而担心了。 若要指定依赖模块，应使用模块清单中的“必需模块”字段。 这会在导入你的模块之前，将列出的所有模块都加载到全局环境中，除非它们已加载。 例如，一些模块可能已由其他模块加载。 也可以使用 RequiredVersion  字段（而不是 ModuleVersion  字段）指定要加载的特定版本。 使用 ModuleVersion  会加载最新版本（在已指定最低版本的情况下）。 如果不使用 RequiredVersion  字段指定特定版本，请务必监视必需模块的版本更新。 特别重要的是，要注意任何可能会影响用户的模块体验的中断性变更。

```powershell
Example: RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})

Example: RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})
```

## <a name="respond-to-feedback"></a>及时反馈响应

及时响应反馈的包所有者会受到社区的高度重视。 请务必及时响应提供建设性反馈的用户，因为他们对包非常感兴趣并尝试帮助改进包。

PowerShell 库支持以下两种反馈方法：

- 联系人所有者：这样，用户可以向包所有者发送电子邮件。 作为包所有者，请务必监视用于 PowerShell 库包的电子邮件地址，并及时响应所提出的问题。 这种方法有一个缺点，就是只有用户和所有者才能看到通信，因此所有者可能需要多次回答同一问题。
- 评论：包网页的底部有“评论”  字段。 此系统的优点是，其他用户可以看到评论和响应，这样就减少了必须回答每个问题的次数。 强烈建议包所有者关注对每个包发表的评论。 若要详细了解如何执行此操作，请参阅[通过社交媒体或发表评论提供反馈](../how-to/working-with-packages/social-media-feedback.md)。

建设性地响应反馈的所有者将受到社区的重视。 使用报表中的机会来请求详细信息。 如果需要，请提供一种解决方法，或确定更新是否解决了问题。

如果在这些信道中发现了任何不当行为，可以使用 PowerShell 库的“报告滥用行为”功能来联系库管理员。

## <a name="modules-versus-scripts"></a>模块与脚本

与其他用户共享脚本非常棒，可以为其他用户提供有关如何解决可能遇到的问题的示例。 问题在于，PowerShell 库中的脚本为单个文件，不含单独的文档、示例和测试。

PowerShell 模块采用文件夹结构，可以随包添加多个文件夹和文件。 使用模块结构，可以添加我们列为最佳做法的其他包，包括 cmdlet 帮助、文档、示例和测试。 最大缺点是模块内的脚本必须作为函数进行公开和使用。 若要了解如何创建模块，请参阅[编写 Windows PowerShell 模块](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。

在某些情况下，脚本可以提升用户体验，特别是在使用 DSC 配置时。 适用于 DSC 配置的最佳做法是，将配置作为脚本发布，并随附包含文档、示例和测试的模块。 该脚本使用 `RequiredModules = @(Name of the Module)` 列出附带的模块。 这种方法可用于任何脚本。

遵循其他最佳做法的独立脚本可为其他用户带来真正的价值。 向 PowerShell 库发布脚本时，强烈建议提供基于评论的文档和项目网站链接。

## <a name="provide-a-link-to-a-project-site"></a>提供项目网站链接

发行者可以在项目网站上直接与 PowerShell 库包的用户进行交互。 用户更倾向于提供项目网站链接的包，因为这样可以更轻松地获取有关包的信息。 PowerShell 库中的许多包在 GitHub 中进行开发，而其他包则由具有专属网站的组织提供。 其中每个网站都可被视为项目网站。

可以在清单的 PSData 部分中添加 ProjectURI，从而添加链接，如下所示：

```
  # A URL to the main website for this project.
  ProjectUri = 'https://github.com/powershell/powershell'
```

提供 ProjectURI 时，PowerShell 库在包网页的左侧添加项目网站链接。

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>使用兼容 PSEdition 和平台对包进行标记

使用以下标记可向用户演示适用于其环境的包：

- PSEdition_Desktop：与 Windows PowerShell 兼容的包
- PSEdition_Core：与 PowerShell Core 兼容的包
- Windows：与 Windows 操作系统兼容的包
- Linux：与 Linux 操作系统兼容的包
- MacOS：与 Mac 操作系统兼容的包

使用兼容平台标记包之后，该包将包含在搜索结果左窗格上的“库”搜索筛选器中。 如果在 GitHub 上托管包，则在标记包时，还可以充分利用 [PowerShell 库兼容性护盾](https://img.shields.io/powershellgallery/p/:packageName.svg)
![兼容性护盾](media/publishing-guidelines/CosmosDB.svg)。

## <a name="include-tests"></a>添加测试

添加包含开放源代码的测试对于用户来说很重要，因为这样可以让用户相信所验证的内容，并展示代码的工作原理。 此外，如果用户修改代码来适应自己的环境，这样做还可以确保用户不会破坏原始功能。

强烈建议编写测试，以利用专为 PowerShell 设计的 Pester 测试框架。 可从 [GitHub](https://github.com/Pester/Pester) 中的 [PowerShell 库](https://www.powershellgallery.com/packages/Pester/)获取 Pester，Windows 10、Windows Server 2016、WMF 5.0 和 WMF 5.1 也随附 Pester。

[GitHub 中的 Pester 项目网站](https://github.com/Pester/Pester)收录了有关如何编写 Pester 测试的实用文档，从入门到最佳做法，无所不包。

[优质资源模块文档](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)强调了测试覆盖率目标，建议的单元测试代码覆盖率为 70%。

## <a name="include-andor-link-to-license-terms"></a>添加和/或链接到许可条款

发布到 PowerShell 库的所有包都必须指定许可条款，或同意受“附件 A”  下[使用条款](https://www.powershellgallery.com/policies/Terms)中许可证的约束。指定不同许可条款的最佳方法是在 PSData  中使用 LicenseURI  ，从而提供许可条款链接。 有关详细信息，请参阅[包清单和库 UI](package-manifest-affecting-ui.md)。

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>对代码进行签名

代码签名不仅可以让用户对包发行者寄予最大的信任，并能确保用户获取的代码副本与发行者发布的完全一样。 若要详细了解代码签名的一般概念，请参阅[代码签名简介](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))。
PowerShell 支持通过以下两种主要方法来验证代码签名：

- 对脚本文件进行签名
- 对模块进行目录签名

对 PowerShell 文件进行签名是一种由来已久的方法，可确保在执行的代码是由可靠的源生成，并且尚未经过修改。 [关于签名](/powershell/module/microsoft.powershell.core/about/about_signing)一文详细介绍了如何对 PowerShell 脚本文件进行签名。 总而言之，可以向 PowerShell 在加载脚本时验证的任何 `.PS1` 文件添加签名。 可以使用[执行策略](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdlet 来约束 PowerShell，以确保使用已签名脚本。

对模块进行目录签名是 PowerShell 版本 5.1 中新增的功能。 [目录 Cmdlet](/powershell/scripting/wmf/5.1/catalog-cmdlets) 一文中介绍了如何对模块进行签名。 总而言之，对模块进行目录签名是通过创建目录文件（其中包含模块中每个文件的哈希值），再对此文件进行签名完成的。

PowerShellGet  `Publish-Module`、`Install-Module` 和 `Update-Module` cmdlet 将检查签名，以确保签名有效，然后确认每个包的哈希值是否与目录中的值一致。 `Save-Module` 不验证签名。 如果在系统中安装了旧版模块，`Install-Module` 将确认新版本的签名颁发机构是否与之前安装的版本一致。 如果未对包进行目录签名，`Install-Module` 和 `Update-Module` 将对 `.PSD1` 文件使用签名。 目录签名可与签名脚本文件结合使用，但不会替换它。 PowerShell 不会在模块加载时验证目录签名。

## <a name="follow-semver-guidelines-for-versioning"></a>遵循 SemVer 指南进行版本控制

[SemVer](https://semver.org/) 是一项公共约定，说明了如何生成并更改版本，以便可以轻松解读更改。 清单数据中必须包含的包的版本。

- 版本应为三个用句点隔开的数字块，如 `0.1.1` 或 `4.11.192`。
- 以 `0` 开头的版本表明包尚无法用于生产，当 0 为唯一使用的数字时，第一个数字只应以 `0` 开头。
- 第一个数字中的更改（例如，从 `1.9.9999` 更改为 `2.0.0`）表明为主要和重大版本更改。
- 第二个数字块中的更改（例如，从 `1.1` 更改为 `1.2`）表明为功能级更改，如将新的 cmdlet 添加到模块。
- 第三个数字块中的更改表明为非重大更改，如新参数、更新后的示例或新测试。
- 列出版本时，PowerShell 会将版本作为字符串进行排序，因此 `1.01.0` 将被视为大于 `1.001.0`。

PowerShell 的创建时间先于 SemVer 发布时间，因此它支持大多数但非所有 SemVer 元素，具体而言：

- 它不支持在版本号中使用预发布字符串。 如果发行者希望在提供版本 `1.0.0` 之后提供新的主要版本的预览版本，这就非常有用。 今后发布的 PowerShell 库和 PowerShellGet  cmdlet 将支持这样做。
- PowerShell 和 PowerShell 库允许使用包含 1、2 和 4 段的版本字符串。 许多早期模块并未遵循这些指南，并且 Microsoft 产品版本在第 4 个数字块中包含生成信息（例如，`5.1.14393.1066`）。 从版本控制的角度来看，这些差异将被忽略。

## <a name="test-using-a-local-repository"></a>使用本地存储库进行测试

PowerShell 库的设计目标不是成为用于测试发布过程的目标。 测试发布到 PowerShell 库的端到端过程，其最佳方法是自行设置并使用本地存储库。 这可以通过多种方式实现，包括：

- 使用 GitHub 中的 [PS 专用库项目](https://github.com/PowerShell/PSPrivateGallery)设置本地 PowerShell 库实例。 此预览项目有助于设置可控制并用于测试的 PowerShell 库实例。
- 设置[内部 Nuget 存储库](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/)。
  需要执行更多工作才能完成此设置，但具有以下优点：验证更多的要求，特别是验证 API 密钥的使用以及发布时目标中是否存在依赖关系。
- 将文件共享设置为“存储库”  测试。 此设置很容易完成，但由于是文件共享，因此不会发生如上所示的验证。 这种情况下，一个潜在的优点是文件共享不会检查必需的 API 密钥，因此可以使用发布到 PowerShell 库时所用的密钥。

采用这些解决方案中的任何一种，使用 `Register-PSRepository` 定义新的存储库  （在 `Publish-Module` 的 `-Repository` 参数中会用到该存储库）。

有关测试发布的另外一点：在运营团队的帮助下才能删除发布到 PowerShell 库的包，该团队会确认没有任何内容依赖于要发布的包。 考虑到该原因，我们不支持将 PowerShell 库作为测试目标，并将与进行此操作的任何发布者联系。

## <a name="use-powershellget-to-publish"></a>使用 PowerShellGet 发布

在使用 PowerShell 库时，强烈建议发布者使用 `Publish-Module` 和 `Publish-Script`。 创建 PowerShellGet  的目的是，让你无需记住有关从中安装和发布到 PowerShell 库的重要详细信息。 有时，发布者会选择跳过 PowerShellGet  并使用 NuGet  客户端或 PackageManagement  cmdlet，而不是 Publish-Module`Publish-Module`。 这会使很多详细信息轻易被漏掉，进而导致各种支持请求。

如果由于某种原因而无法使用 `Publish-Module` 或 `Publish-Script`，请告知我们。
在 PowerShellGet  GitHub 存储库中发布一个问题，并提供导致你选择 NuGet  或 PackageManagement  的详细信息。

## <a name="recommended-workflow"></a>建议的工作流

我们已总结出适用于在 PowerShell 库中发布的包的最成功方法，如下所述：

- 在开放源代码项目网站中进行初始开发。 PowerShell 团队使用 GitHub。
- 使用审阅者的反馈和 [Powershell 脚本分析器](https://aka.ms/psscriptanalyzer)，让代码处于稳定状态。
- 添加文档，告知其他人如何使用项。
- 使用本地存储库测试发布操作。
- 将稳定版或 Alpha 版本发布到 PowerShell 库中，同时确保添加文档和项目网站链接。
- 收集反馈并循环访问项目网站中的代码，再将稳定更新发布到 PowerShell 库中。
- 在项目和模块中添加示例和 Pester 测试。
- 决定是否要对包进行代码签名。
- 如果认为项目可用于生产环境，请将 `1.0.0` 版本发布到 PowerShell 库中。
- 继续收集反馈，并根据用户输入循环访问代码。

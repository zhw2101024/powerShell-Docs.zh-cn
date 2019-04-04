---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
description: 面向发行者的指南
title: PowerShell 库发布指南和最佳做法
ms.openlocfilehash: 1cd0140cc208949e13d23331b23a58ffc374430b
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623902"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a><span data-ttu-id="1cedb-104">PowerShell 库发布指南和最佳做法</span><span class="sxs-lookup"><span data-stu-id="1cedb-104">PowerShellGallery Publishing Guidelines and Best Practices</span></span>

<span data-ttu-id="1cedb-105">本主题介绍了 Microsoft 团队使用的推荐步骤，以确保发布到 PowerShell 库的包将被广泛采用，并根据 PowerShell 库处理清单数据的方式和大量 PowerShell 库用户的反馈来为用户提供高价值包。</span><span class="sxs-lookup"><span data-stu-id="1cedb-105">This topic describes recommended steps used by Microsoft teams to ensure the packages published to the PowerShell Gallery will be widely adopted and provide high value to users, based on how the PowerShell Gallery handles manifest data and on feedback from large numbers of PowerShell Gallery users.</span></span>
<span data-ttu-id="1cedb-106">按照这些指南发布的包的安装和受信任几率更高，并且更有可能会吸引更多用户。</span><span class="sxs-lookup"><span data-stu-id="1cedb-106">Packages that are published following these guidelines will be more likely to be installed, trusted, and attract more users.</span></span>

<span data-ttu-id="1cedb-107">下面的指南介绍了高质量 PowerShell 库包有哪些关键要素、哪些是最重要的可选清单设置、如何使用初始审阅者的反馈和 [Powershell 脚本分析器](https://aka.ms/psscriptanalyzer)改进代码、如何对模块进行版本控制，以及有关如何使用已共享内容的文档、测试和示例。</span><span class="sxs-lookup"><span data-stu-id="1cedb-107">Included below are guidelines for what makes a good PowerShell Gallery package, what optional Manifest settings are most important, improving your code with feedback from initial reviewers and [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer), versioning your module, documentation, tests & examples for how to use what you have shared.</span></span>
<span data-ttu-id="1cedb-108">本文档的大部分内容遵循有关发布[高质量 DSC 资源模块](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)的指南。</span><span class="sxs-lookup"><span data-stu-id="1cedb-108">Much of this documentation follows the guidelines for publishing [High Quality DSC Resource Modules](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).</span></span>

<span data-ttu-id="1cedb-109">有关将包发布到 PowerShell 库的机制，请参阅[创建和发布包](/powershell/gallery/how-to/publishing-packages/publishing-a-package)。</span><span class="sxs-lookup"><span data-stu-id="1cedb-109">For the mechanics of publishing a package to the PowerShell Gallery, see [Creating and Publishing a Package](/powershell/gallery/how-to/publishing-packages/publishing-a-package).</span></span>

<span data-ttu-id="1cedb-110">欢迎随时提供有关这些指南的反馈。</span><span class="sxs-lookup"><span data-stu-id="1cedb-110">Feedback on these guidelines is welcomed.</span></span> <span data-ttu-id="1cedb-111">如有任何反馈，请在我们的 [Github 文档存储库](https://github.com/powershell/powershell-docs/issues)中记录待解决问题。</span><span class="sxs-lookup"><span data-stu-id="1cedb-111">If you do have feedback, please open issues in our [Github documentation repository](https://github.com/powershell/powershell-docs/issues).</span></span>

## <a name="best-practices-for-publishing-packages"></a><span data-ttu-id="1cedb-112">发布包的最佳做法</span><span class="sxs-lookup"><span data-stu-id="1cedb-112">Best practices for publishing packages</span></span>

<span data-ttu-id="1cedb-113">下面按名义上的优先级顺序列出了 PowerShell 库项用户认为重要的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="1cedb-113">The following best practices are what the users of PowerShell Gallery items say is important, and are listed in nominal priority order.</span></span>
<span data-ttu-id="1cedb-114">按照下面这些指南发布包会大大提升它们被其他用户下载和采用的几率。</span><span class="sxs-lookup"><span data-stu-id="1cedb-114">Packages that follow these guidelines are far more likely to be downloaded and adopted by others.</span></span>

- <span data-ttu-id="1cedb-115">使用 PSScriptAnalyzer</span><span class="sxs-lookup"><span data-stu-id="1cedb-115">Use PSScriptAnalyzer</span></span>
- <span data-ttu-id="1cedb-116">添加文档和示例</span><span class="sxs-lookup"><span data-stu-id="1cedb-116">Include documentation and examples</span></span>
- <span data-ttu-id="1cedb-117">及时响应反馈</span><span class="sxs-lookup"><span data-stu-id="1cedb-117">Be responsive to feedback</span></span>
- <span data-ttu-id="1cedb-118">提供模块（而不是脚本）</span><span class="sxs-lookup"><span data-stu-id="1cedb-118">Provide modules rather than scripts</span></span>
- <span data-ttu-id="1cedb-119">提供项目网站链接</span><span class="sxs-lookup"><span data-stu-id="1cedb-119">Provide links to a project site</span></span>
- <span data-ttu-id="1cedb-120">使用兼容 PSEdition 和平台对包进行标记</span><span class="sxs-lookup"><span data-stu-id="1cedb-120">Tag your package with the compatible PSEdition(s) and platforms</span></span>
- <span data-ttu-id="1cedb-121">随模块添加测试</span><span class="sxs-lookup"><span data-stu-id="1cedb-121">Include tests with your modules</span></span>
- <span data-ttu-id="1cedb-122">添加和/或链接到许可条款</span><span class="sxs-lookup"><span data-stu-id="1cedb-122">Include and/or link to license terms</span></span>
- <span data-ttu-id="1cedb-123">对代码进行签名</span><span class="sxs-lookup"><span data-stu-id="1cedb-123">Sign your code</span></span>
- <span data-ttu-id="1cedb-124">遵循 [SemVer](http://semver.org/) 指南进行版本控制</span><span class="sxs-lookup"><span data-stu-id="1cedb-124">Follow [SemVer](http://semver.org/) guidelines for versioning</span></span>
- <span data-ttu-id="1cedb-125">使用“常见 PowerShell 库标记”中收录的常见标记</span><span class="sxs-lookup"><span data-stu-id="1cedb-125">Use common tags, as documented in Common PowerShell Gallery tags</span></span>
- <span data-ttu-id="1cedb-126">使用本地存储库测试发布</span><span class="sxs-lookup"><span data-stu-id="1cedb-126">Test publishing using a local repository</span></span>
- <span data-ttu-id="1cedb-127">使用 PowerShellGet 发布</span><span class="sxs-lookup"><span data-stu-id="1cedb-127">Use PowerShellGet to publish</span></span>

<span data-ttu-id="1cedb-128">下面的各个部分简要介绍了上述每种最佳做法。</span><span class="sxs-lookup"><span data-stu-id="1cedb-128">Each of these is covered briefly in the sections below.</span></span>

## <a name="use-psscriptanalyzer"></a><span data-ttu-id="1cedb-129">使用 PSScriptAnalyzer</span><span class="sxs-lookup"><span data-stu-id="1cedb-129">Use PSScriptAnalyzer</span></span>

<span data-ttu-id="1cedb-130">[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) 是一款用于处理 PowerShell 代码的免费静态代码分析工具。</span><span class="sxs-lookup"><span data-stu-id="1cedb-130">[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) is a free static code analysis tool that works on PowerShell code.</span></span>
<span data-ttu-id="1cedb-131">PSScriptAnalyzer 可发现 PowerShell 代码中存在的最常见问题，通常还会建议如何解决问题。</span><span class="sxs-lookup"><span data-stu-id="1cedb-131">PSScriptAnalyzer will identify the most common issues seen in PowerShell code, and often a recommendation for how to fix the issue.</span></span>
<span data-ttu-id="1cedb-132">此工具易于使用，并将问题分类为“错误”（必须解决的严重问题）、“警告”（需要查看并应解决的问题）和“信息”（值得参阅最佳做法的问题）。</span><span class="sxs-lookup"><span data-stu-id="1cedb-132">The tool is easy to use, and categorizes the issues as Errors (severe, must be addressed), Warning (need to be reviewed & should be addressed), and Information (worth checking out for best practices).</span></span>
<span data-ttu-id="1cedb-133">所有发布到 PowerShell 库的包都会使用 PSScriptAnalyzer 进行扫描，任何错误都会向所有者报告，并且必须予以修复。</span><span class="sxs-lookup"><span data-stu-id="1cedb-133">All packages published to the PowerShell Gallery will be scanned using PSScriptAnalyzer, and any errors will be reported back to the owner and must be addressed.</span></span>

<span data-ttu-id="1cedb-134">最佳做法是使用 `-Recurse` 和 `-Severity` 警告运行 `Invoke-ScriptAnalyzer`。</span><span class="sxs-lookup"><span data-stu-id="1cedb-134">The best practice is to run `Invoke-ScriptAnalyzer` with `-Recurse` and `-Severity` Warning.</span></span>

<span data-ttu-id="1cedb-135">查看结果并确保：</span><span class="sxs-lookup"><span data-stu-id="1cedb-135">Review the results, and ensure that:</span></span>

- <span data-ttu-id="1cedb-136">已更正或修复文档中的所有错误</span><span class="sxs-lookup"><span data-stu-id="1cedb-136">All Errors are corrected or addressed in your documentation</span></span>
- <span data-ttu-id="1cedb-137">已查看并在必要时解决所有警告</span><span class="sxs-lookup"><span data-stu-id="1cedb-137">All Warnings are reviewed, and addressed where applicable</span></span>

<span data-ttu-id="1cedb-138">强烈建议从 PowerShell 库获取包的用户运行 PSScriptAnalyzer，并评估所有错误和警告。</span><span class="sxs-lookup"><span data-stu-id="1cedb-138">Users who acquire packages from the PowerShell Gallery are strongly encouraged to run PSScriptAnalyzer and evaluate all Errors and Warnings.</span></span>
<span data-ttu-id="1cedb-139">如果用户看到 PSScriptAnalyzer 报告的错误，他们很有可能会与包所有者进行联系。</span><span class="sxs-lookup"><span data-stu-id="1cedb-139">Users are very likely to contact package owners if they see that there is an error reported by PSScriptAnalyzer.</span></span>
<span data-ttu-id="1cedb-140">如果包有充分理由保留标记为错误的代码，请将相应信息添加到文档中，以免多次回答同一问题。</span><span class="sxs-lookup"><span data-stu-id="1cedb-140">If there is a compelling reason for your package to keep code that is flagged as an error, add that information to your documentation to avoid having to answer the same question many times.</span></span>

## <a name="include-documentation-and-examples"></a><span data-ttu-id="1cedb-141">添加文档和示例</span><span class="sxs-lookup"><span data-stu-id="1cedb-141">Include documentation and examples</span></span>

<span data-ttu-id="1cedb-142">文档和示例是确保用户可以利用所有已共享代码的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="1cedb-142">Documentation and examples are the best way to ensure users can take advantage of any shared code.</span></span>

<span data-ttu-id="1cedb-143">文档是在发布到 PowerShell Gallery 的包中所添加的最实用内容。</span><span class="sxs-lookup"><span data-stu-id="1cedb-143">Documentation is the most helpful thing to include in packages published to the PowerShell Gallery.</span></span>
<span data-ttu-id="1cedb-144">用户通常会忽略没有文档的包，因为只能通过阅读代码来了解包的用途和使用方式。</span><span class="sxs-lookup"><span data-stu-id="1cedb-144">Users will generally bypass packages without documentation, as the alternative is to read the code to understand what the package is and how to use it.</span></span>
<span data-ttu-id="1cedb-145">有多篇文章都介绍了如何为 PowerShell 包提供文档，包括：</span><span class="sxs-lookup"><span data-stu-id="1cedb-145">There are several articles available about how to provide documentation with PowerShell packages, including:</span></span>

- <span data-ttu-id="1cedb-146">[如何编写 Cmdlet 帮助](https://go.microsoft.com/fwlink/?LinkID=123415)中介绍了有关如何提供帮助的指南</span><span class="sxs-lookup"><span data-stu-id="1cedb-146">Guidelines for providing help are in [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)</span></span>
- <span data-ttu-id="1cedb-147">创建 cmdlet 帮助，这是最适合任何 PowerShell 脚本、函数或 cmdlet 的方法。</span><span class="sxs-lookup"><span data-stu-id="1cedb-147">Creating cmdlet help, which is the best approach for any PowerShell script, function, or cmdlet.</span></span>
  <span data-ttu-id="1cedb-148">有关如何创建 cmdlet 帮助的信息，请从[如何编写 Cmdlet 帮助](https://go.microsoft.com/fwlink/?LinkID=123415)入手。</span><span class="sxs-lookup"><span data-stu-id="1cedb-148">For information about how to create cmdlet help, start with [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415).</span></span>
  <span data-ttu-id="1cedb-149">若要在脚本中添加帮助，请参阅[关于基于评论的帮助](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="1cedb-149">To add help within a script, see [About Comment Based Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>
- <span data-ttu-id="1cedb-150">许多模块还包括文本格式的文档，如 MarkDown 文件。</span><span class="sxs-lookup"><span data-stu-id="1cedb-150">Many modules also include documentation in text format, such as MarkDown files.</span></span>
  <span data-ttu-id="1cedb-151">当在 Markdown 作为一种广泛使用格式的 Github 中有项目网站时，这尤为有用。</span><span class="sxs-lookup"><span data-stu-id="1cedb-151">This can be particularly helpful when there is a project site in Github, where Markdown is a heavily used format.</span></span>
  <span data-ttu-id="1cedb-152">最佳做法是使用 [Github 式 Markdown](https://help.github.com/categories/writing-on-github/)</span><span class="sxs-lookup"><span data-stu-id="1cedb-152">The best practice is to use [Github-flavored Markdown](https://help.github.com/categories/writing-on-github/)</span></span>

<span data-ttu-id="1cedb-153">示例可以向用户展示如何使用包。</span><span class="sxs-lookup"><span data-stu-id="1cedb-153">Examples show users how the package is intended to be used.</span></span>
<span data-ttu-id="1cedb-154">许多开发者都表示，他们在查看文档之前会先查看示例，了解如何使用某项。</span><span class="sxs-lookup"><span data-stu-id="1cedb-154">Many developers will say that they look at examples before documentation to understand how to use something.</span></span>
<span data-ttu-id="1cedb-155">最适合的示例不仅展示了基本用法，还展示了模拟实际用例，同时对代码进行了详细注释。</span><span class="sxs-lookup"><span data-stu-id="1cedb-155">The best type of examples show basic use, plus a simulated realistic use case, and the code is well-commented.</span></span>
<span data-ttu-id="1cedb-156">发布到 PowerShell 库的模块的示例应位于模块根下的 Examples 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="1cedb-156">Examples for modules published to the PowerShell Gallery should be in an Examples folder under the module root.</span></span>

<span data-ttu-id="1cedb-157">Examples\RegistryResource 文件夹下的 [PSDscResource 模块](https://www.powershellgallery.com/packages/PSDscResources)中包含优质示例模式。</span><span class="sxs-lookup"><span data-stu-id="1cedb-157">A good pattern for examples can be found in the [PSDscResource module](https://www.powershellgallery.com/packages/PSDscResources) under the Examples\RegistryResource folder.</span></span>
<span data-ttu-id="1cedb-158">具体包含四个示例用例，每个文件的顶部都简要说明了要演示的内容。</span><span class="sxs-lookup"><span data-stu-id="1cedb-158">There are four sample use cases with a brief description at the top of each file that documents what is being demonstrated.</span></span>

## <a name="respond-to-feedback"></a><span data-ttu-id="1cedb-159">及时反馈响应</span><span class="sxs-lookup"><span data-stu-id="1cedb-159">Respond to feedback</span></span>

<span data-ttu-id="1cedb-160">及时响应反馈的包所有者会受到社区的高度重视。</span><span class="sxs-lookup"><span data-stu-id="1cedb-160">Package owners who respond properly to feedback are highly valued by the community.</span></span>
<span data-ttu-id="1cedb-161">请务必及时响应提供建设性反馈的用户，因为他们对包非常感兴趣并尝试帮助改进包。</span><span class="sxs-lookup"><span data-stu-id="1cedb-161">Users who provide constructive feedback are important to respond to, as they are interested enough in the package to try to help improve it.</span></span>

<span data-ttu-id="1cedb-162">PowerShell 库支持以下两种反馈方法：</span><span class="sxs-lookup"><span data-stu-id="1cedb-162">There are two feedback methods available in the PowerShell Gallery:</span></span>

- <span data-ttu-id="1cedb-163">联系人所有者：这样，用户可以向包所有者发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="1cedb-163">Contact Owner: This allows a user to send an email to the package owner(s).</span></span> <span data-ttu-id="1cedb-164">作为包所有者，请务必监视用于 PowerShell 库包的电子邮件地址，并及时响应所提出的问题。</span><span class="sxs-lookup"><span data-stu-id="1cedb-164">As an package owner, is important to monitor the email address used with the PowerShell Gallery packages, and respond to issues that are raised.</span></span> <span data-ttu-id="1cedb-165">这种方法有一个缺点，就是只有用户和所有者才能看到通信，因此所有者可能需要多次回答同一问题。</span><span class="sxs-lookup"><span data-stu-id="1cedb-165">The one disadvantage to this method is that only the user and owner will ever see the communication, so the owner may have to answer the same question many times.</span></span>
- <span data-ttu-id="1cedb-166">评论：包网页的底部有“评论”字段。</span><span class="sxs-lookup"><span data-stu-id="1cedb-166">Comments: At the bottom of the package page is a Comment field.</span></span>
  <span data-ttu-id="1cedb-167">此系统的优点是，其他用户可以看到评论和响应，这样就减少了必须回答每个问题的次数。</span><span class="sxs-lookup"><span data-stu-id="1cedb-167">The advantage to this system is that other users can see the comments and responses, which reduces the number of times any single question must be answered.</span></span>
  <span data-ttu-id="1cedb-168">强烈建议包所有者关注对每个包发表的评论。</span><span class="sxs-lookup"><span data-stu-id="1cedb-168">As a package owner, it is strongly recommended that you Follow the comments made for each package.</span></span>
<span data-ttu-id="1cedb-169">若要详细了解如何执行此操作，请参阅[通过社交媒体或发表评论提供反馈](../how-to/working-with-packages/social-media-feedback.md)。</span><span class="sxs-lookup"><span data-stu-id="1cedb-169">See [Providing Feedback via Social Media or Comments](../how-to/working-with-packages/social-media-feedback.md) for details on how to do that.</span></span>

<span data-ttu-id="1cedb-170">建设性地响应反馈的所有者将受到社区的重视。</span><span class="sxs-lookup"><span data-stu-id="1cedb-170">Owners who respond to feedback constructively are appreciated by the community.</span></span>
<span data-ttu-id="1cedb-171">可以利用此机会，在报告中请求获取所需的详细信息、提供解决方法或确定更新能否解决问题。</span><span class="sxs-lookup"><span data-stu-id="1cedb-171">Use the opportunity in the report to request more information if needed, provide a workaround, or identify if an update fixes a problem.</span></span>

<span data-ttu-id="1cedb-172">如果在这些信道中发现了任何不当行为，可以使用 PowerShell 库的“报告滥用行为”功能来联系库管理员。</span><span class="sxs-lookup"><span data-stu-id="1cedb-172">If there is inappropriate behavior observed from either of these communication channels, use the Report Abuse feature of the PowerShell Gallery to contact the Gallery Administrators.</span></span>

## <a name="modules-versus-scripts"></a><span data-ttu-id="1cedb-173">模块与脚本</span><span class="sxs-lookup"><span data-stu-id="1cedb-173">Modules Versus Scripts</span></span>

<span data-ttu-id="1cedb-174">与其他用户共享脚本非常棒，可以为其他用户提供有关如何解决可能遇到的问题的示例。</span><span class="sxs-lookup"><span data-stu-id="1cedb-174">Sharing a script with other users is great, and provides others with examples of how to solve problems they may have.</span></span>
<span data-ttu-id="1cedb-175">问题在于，PowerShell 库中的脚本为单个文件，不含单独的文档、示例和测试。</span><span class="sxs-lookup"><span data-stu-id="1cedb-175">The issue is that scripts in the PowerShell Gallery are single files without separate documentation, examples, and tests.</span></span>

<span data-ttu-id="1cedb-176">PowerShell 模块采用文件夹结构，可以随包添加多个文件夹和文件。</span><span class="sxs-lookup"><span data-stu-id="1cedb-176">PowerShell Modules have a folder structure that allows multiple folders and files to be included with the package.</span></span>
<span data-ttu-id="1cedb-177">使用模块结构，可以添加我们列为最佳做法的其他包，包括 cmdlet 帮助、文档、示例和测试。</span><span class="sxs-lookup"><span data-stu-id="1cedb-177">The module structure enables including the other packages we list as best practices: cmdlet help, documentation, examples, and tests.</span></span>
<span data-ttu-id="1cedb-178">最大缺点是模块内的脚本必须作为函数进行公开和使用。</span><span class="sxs-lookup"><span data-stu-id="1cedb-178">The biggest disadvantage is that a script inside a module must be exposed and used as a function.</span></span>
<span data-ttu-id="1cedb-179">若要了解如何创建模块，请参阅[编写 Windows PowerShell 模块](http://go.microsoft.com/fwlink/?LinkId=144916)。</span><span class="sxs-lookup"><span data-stu-id="1cedb-179">For information on how to create a module, see [Writing a Windows PowerShell Module](http://go.microsoft.com/fwlink/?LinkId=144916).</span></span>

<span data-ttu-id="1cedb-180">在某些情况下，脚本可以提升用户体验，特别是在使用 DSC 配置时。</span><span class="sxs-lookup"><span data-stu-id="1cedb-180">There are situations where a script provides a better experience for the user, particularly with DSC configurations.</span></span>
<span data-ttu-id="1cedb-181">适用于 DSC 配置的最佳做法是，将配置作为脚本发布，并随附包含文档、示例和测试的模块。</span><span class="sxs-lookup"><span data-stu-id="1cedb-181">The best practice for DSC configurations is to publish the configuration as a script with an accompanying module that contains the docs, examples, and tests.</span></span>
<span data-ttu-id="1cedb-182">脚本使用 RequiredModules = @(模块名称) 列出随附模块。</span><span class="sxs-lookup"><span data-stu-id="1cedb-182">The script lists the accompanying module using RequiredModules = @(Name of the Module).</span></span>
<span data-ttu-id="1cedb-183">这种方法可用于任何脚本。</span><span class="sxs-lookup"><span data-stu-id="1cedb-183">This approach can be used with any script.</span></span>

<span data-ttu-id="1cedb-184">遵循其他最佳做法的独立脚本可为其他用户带来真正的价值。</span><span class="sxs-lookup"><span data-stu-id="1cedb-184">Standalone scripts that follow the other best practices provide real value to other users.</span></span>
<span data-ttu-id="1cedb-185">向 PowerShell 库发布脚本时，强烈建议提供基于评论的文档和项目网站链接。</span><span class="sxs-lookup"><span data-stu-id="1cedb-185">Providing comment-based documentation and a link to a Project Site are highly recommended when publishing a script to the PowerShell Gallery.</span></span>

## <a name="provide-a-link-to-a-project-site"></a><span data-ttu-id="1cedb-186">提供项目网站链接</span><span class="sxs-lookup"><span data-stu-id="1cedb-186">Provide a link to a project site</span></span>

<span data-ttu-id="1cedb-187">发行者可以在项目网站上直接与 PowerShell 库包的用户进行交互。</span><span class="sxs-lookup"><span data-stu-id="1cedb-187">A Project Site is where a publisher can interact directly with the users of their PowerShell Gallery packages.</span></span>
<span data-ttu-id="1cedb-188">用户更倾向于提供项目网站链接的包，因为这样可以更轻松地获取有关包的信息。</span><span class="sxs-lookup"><span data-stu-id="1cedb-188">Users prefer packages that provide this, as it allows them to get information about the package more easily.</span></span>
<span data-ttu-id="1cedb-189">PowerShell 库中的许多包在 GitHub 中进行开发，而其他包则由具有专属网站的组织提供。</span><span class="sxs-lookup"><span data-stu-id="1cedb-189">Many packages in the PowerShell Gallery are developed in GitHub, others are provided by organizations with a dedicated web presence.</span></span>
<span data-ttu-id="1cedb-190">其中每个网站都可被视为项目网站。</span><span class="sxs-lookup"><span data-stu-id="1cedb-190">Each of these can be considered a project site.</span></span>

<span data-ttu-id="1cedb-191">可以在清单的 PSData 部分中添加 ProjectURI，从而添加链接，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1cedb-191">Adding a link is done by including ProjectURI in the PSData section of the manifest as follows:</span></span>

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

<span data-ttu-id="1cedb-192">提供 ProjectURI 时，PowerShell 库在包网页的左侧添加项目网站链接。</span><span class="sxs-lookup"><span data-stu-id="1cedb-192">When a ProjectURI is provided, the PowerShell Gallery will include a link to the Project Site on the left side of the package page.</span></span>

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a><span data-ttu-id="1cedb-193">使用兼容 PSEdition 和平台对包进行标记</span><span class="sxs-lookup"><span data-stu-id="1cedb-193">Tag your package with the compatible PSEdition(s) and platforms</span></span>

<span data-ttu-id="1cedb-194">使用以下标记可向用户演示适用于其环境的包：</span><span class="sxs-lookup"><span data-stu-id="1cedb-194">Use the following tags to demonstrate to users which packages will work well with their environment:</span></span>

- <span data-ttu-id="1cedb-195">PSEdition_Desktop：与 Windows PowerShell 兼容的包</span><span class="sxs-lookup"><span data-stu-id="1cedb-195">PSEdition_Desktop : Packages that are compatible with Windows PowerShell</span></span>
- <span data-ttu-id="1cedb-196">PSEdition_Core：与 PowerShell Core 兼容的包</span><span class="sxs-lookup"><span data-stu-id="1cedb-196">PSEdition_Core : Packages that are compatible with PowerShell Core</span></span>
- <span data-ttu-id="1cedb-197">Windows：与 Windows 操作系统兼容的包</span><span class="sxs-lookup"><span data-stu-id="1cedb-197">Windows : Packages that are compatible with the Windows Operating System</span></span>
- <span data-ttu-id="1cedb-198">Linux：与 Linux 操作系统兼容的包</span><span class="sxs-lookup"><span data-stu-id="1cedb-198">Linux : Packages that are compatible with Linux Operating Systems</span></span>
- <span data-ttu-id="1cedb-199">MacOS：与 Mac 操作系统兼容的包</span><span class="sxs-lookup"><span data-stu-id="1cedb-199">MacOS : Packages that are compatible with the Mac Operating System</span></span>

<span data-ttu-id="1cedb-200">使用兼容平台标记包之后，该包将包含在搜索结果左窗格上的“库”搜索筛选器中。</span><span class="sxs-lookup"><span data-stu-id="1cedb-200">By tagging your package with the compatible platform(s) it will be included in the Gallery search filters on the left pane of the search results.</span></span> <span data-ttu-id="1cedb-201">如果在 GitHub 上托管包，则在标记包时，还可以充分利用 [PowerShell 库兼容性护盾](https://img.shields.io/powershellgallery/p/:packageName.svg) 
![兼容性护盾](https://img.shields.io/powershellgallery/p/CosmosDB.svg)。</span><span class="sxs-lookup"><span data-stu-id="1cedb-201">If you host your package on GitHub, when you tag your package, you can also take advantage of our [PowerShell Gallery compability shields](https://img.shields.io/powershellgallery/p/:packageName.svg) 
![compatibility shield](https://img.shields.io/powershellgallery/p/CosmosDB.svg).</span></span>  

## <a name="include-tests"></a><span data-ttu-id="1cedb-202">添加测试</span><span class="sxs-lookup"><span data-stu-id="1cedb-202">Include tests</span></span>

<span data-ttu-id="1cedb-203">添加包含开放源代码的测试对于用户来说很重要，因为这样可以让用户相信所验证的内容，并展示代码的工作原理。</span><span class="sxs-lookup"><span data-stu-id="1cedb-203">Including tests with open-source code is important to users, as it gives them assurance about what you validate, and provides information on how your code works.</span></span> <span data-ttu-id="1cedb-204">此外，如果用户修改代码来适应自己的环境，这样做还可以确保用户不会破坏原始功能。</span><span class="sxs-lookup"><span data-stu-id="1cedb-204">It also allows users to ensure they do not break your original functionality if they modify your code to fit their environment.</span></span>

<span data-ttu-id="1cedb-205">强烈建议编写测试，以利用专为 PowerShell 设计的 Pester 测试框架。</span><span class="sxs-lookup"><span data-stu-id="1cedb-205">It is strongly recommended that tests be written to take advantage of the Pester test framework, which has been designed specifically for PowerShell.</span></span>
<span data-ttu-id="1cedb-206">可从 [GitHub](https://github.com/Pester/Pester) 中的 [PowerShell 库](https://www.powershellgallery.com/packages/Pester/)获取 Pester，Windows 10、Windows Server 2016、WMF 5.0 和 WMF 5.1 也随附 Pester。</span><span class="sxs-lookup"><span data-stu-id="1cedb-206">Pester is available in [GitHub](https://github.com/Pester/Pester), the [PowerShell Gallery](https://www.powershellgallery.com/packages/Pester/), and ships in Windows 10, Windows Server 2016, WMF 5.0 and WMF 5.1.</span></span>

<span data-ttu-id="1cedb-207">[GitHub 中的 Pester 项目网站](https://github.com/Pester/Pester)收录了有关如何编写 Pester 测试的实用文档，从入门到最佳做法，无所不包。</span><span class="sxs-lookup"><span data-stu-id="1cedb-207">The [Pester project site in GitHub](https://github.com/Pester/Pester) includes good documentation on writing Pester tests, from getting started to best practices.</span></span>

<span data-ttu-id="1cedb-208">[优质资源模块文档](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)强调了测试覆盖率目标，建议的单元测试代码覆盖率为 70%。</span><span class="sxs-lookup"><span data-stu-id="1cedb-208">The targets for test coverage are called out in the [High Quality Resource Module documentation](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), with 70% unit test code coverage recommended.</span></span>

## <a name="include-andor-link-to-license-terms"></a><span data-ttu-id="1cedb-209">添加和/或链接到许可条款</span><span class="sxs-lookup"><span data-stu-id="1cedb-209">Include and/or link to license terms</span></span>

<span data-ttu-id="1cedb-210">发布到 PowerShell 库的所有包都必须指定许可条款，或同意受“附件 A”下[使用条款](https://www.powershellgallery.com/policies/Terms)中许可证的约束。</span><span class="sxs-lookup"><span data-stu-id="1cedb-210">All packages published to the PowerShell Gallery must specify the license terms, or be bound by the license included in the [Terms of Use](https://www.powershellgallery.com/policies/Terms) under "Exhibit A".</span></span>
<span data-ttu-id="1cedb-211">指定不同许可条款的最佳方法是在 PSData 中使用 LicenseURI，从而提供许可条款链接。</span><span class="sxs-lookup"><span data-stu-id="1cedb-211">The best approach to specifying a different license is to provide a link to the license using the LicenseURI in PSData.</span></span>
<span data-ttu-id="1cedb-212">有关示例，可以参阅“建议清单字段”主题。</span><span class="sxs-lookup"><span data-stu-id="1cedb-212">You can find an example in the Recommended Manifest Fields topic.</span></span>

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a><span data-ttu-id="1cedb-213">对代码进行签名</span><span class="sxs-lookup"><span data-stu-id="1cedb-213">Sign your code</span></span>

<span data-ttu-id="1cedb-214">代码签名不仅可以让用户对包发行者寄予最大的信任，并能确保用户获取的代码副本与发行者发布的完全一样。</span><span class="sxs-lookup"><span data-stu-id="1cedb-214">Code signing provides users with the highest level of assurance for who published the package, and that the copy of the code they acquire is exactly what the publisher released.</span></span>
<span data-ttu-id="1cedb-215">若要详细了解代码签名的一般概念，请参阅[代码签名简介](http://go.microsoft.com/fwlink/?LinkId=106296)。</span><span class="sxs-lookup"><span data-stu-id="1cedb-215">To learn more about code signing generally, see [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=106296).</span></span>
<span data-ttu-id="1cedb-216">PowerShell 支持通过以下两种主要方法来验证代码签名：</span><span class="sxs-lookup"><span data-stu-id="1cedb-216">PowerShell supports validation of code signing through two primary approaches:</span></span>

- <span data-ttu-id="1cedb-217">对脚本文件进行签名</span><span class="sxs-lookup"><span data-stu-id="1cedb-217">Signing script files</span></span>
- <span data-ttu-id="1cedb-218">对模块进行目录签名</span><span class="sxs-lookup"><span data-stu-id="1cedb-218">Catalog signing a module</span></span>

<span data-ttu-id="1cedb-219">对 PowerShell 文件进行签名是一种由来已久的方法，可确保在执行的代码是由可靠的源生成，并且尚未经过修改。</span><span class="sxs-lookup"><span data-stu-id="1cedb-219">Signing PowerShell files is a well-established approach to ensuring that the code being executed was produced by a reliable source, and has not been modified.</span></span>
<span data-ttu-id="1cedb-220">[关于签名](/powershell/module/microsoft.powershell.core/about/about_signing)主题详细介绍了如何对 PowerShell 脚本文件进行签名。</span><span class="sxs-lookup"><span data-stu-id="1cedb-220">Details on how to sign PowerShell script files is covered in the [About Signing](/powershell/module/microsoft.powershell.core/about/about_signing) topic.</span></span>
<span data-ttu-id="1cedb-221">总而言之，可以向 PowerShell 在加载脚本时验证的任何 .PS1 文件添加签名。</span><span class="sxs-lookup"><span data-stu-id="1cedb-221">In overview, a signature can be added to any .PS1 file that PowerShell validates when the script is loaded.</span></span>
<span data-ttu-id="1cedb-222">可以使用[执行策略](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdlet 来约束 PowerShell，以确保使用已签名脚本。</span><span class="sxs-lookup"><span data-stu-id="1cedb-222">PowerShell can be constrained using the [Execution Policy](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdlets to ensure use of signed scripts.</span></span>

<span data-ttu-id="1cedb-223">对模块进行目录签名是 PowerShell 版本 5.1 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="1cedb-223">Catalog signing modules is a feature added to PowerShell in version 5.1.</span></span>
<span data-ttu-id="1cedb-224">[目录 Cmdlet](/powershell/wmf/5.1/catalog-cmdlets) 主题中介绍了如何对模块进行签名。</span><span class="sxs-lookup"><span data-stu-id="1cedb-224">How to sign a module is covered in the [Catalog Cmdlets](/powershell/wmf/5.1/catalog-cmdlets) topic.</span></span>
<span data-ttu-id="1cedb-225">总而言之，对模块进行目录签名是通过创建目录文件（其中包含模块中每个文件的哈希值），再对此文件进行签名完成的。</span><span class="sxs-lookup"><span data-stu-id="1cedb-225">In overview, catalog signing is done by creating a catalog file, which contains a hash value for every file in the module, and then signing that file.</span></span>
<span data-ttu-id="1cedb-226">PowerShellGet publish-module、install-module、save-module 和 update-module cmdlet 将检查签名，以确保签名有效，然后确认每个包的哈希值是否与目录中的值一致。</span><span class="sxs-lookup"><span data-stu-id="1cedb-226">The PowerShellGet publish-module, install-module, save-module, and update-module cmdlets will check the signature to ensure it is valid, then confirm that the hash value for each package matches what is in the catalog.</span></span>
<span data-ttu-id="1cedb-227">如果在系统中安装了旧版模块，install-module 将确认新版本的签名颁发机构是否与之前安装的版本一致。</span><span class="sxs-lookup"><span data-stu-id="1cedb-227">If a previous version of the module is installed on the system, install-module will confirm that the signing authority for the new version matches what was previously installed.</span></span>
<span data-ttu-id="1cedb-228">目录签名可脚本文件签名结合使用，但不会替换它。</span><span class="sxs-lookup"><span data-stu-id="1cedb-228">Catalog signing works with, but does not replace signing script files.</span></span> <span data-ttu-id="1cedb-229">PowerShell 不会在模块加载时验证目录签名。</span><span class="sxs-lookup"><span data-stu-id="1cedb-229">PowerShell does not validate catalog signatures at module load time.</span></span>

## <a name="follow-semver-guidelines-for-versioning"></a><span data-ttu-id="1cedb-230">遵循 SemVer 指南进行版本控制</span><span class="sxs-lookup"><span data-stu-id="1cedb-230">Follow SemVer guidelines for versioning</span></span>

<span data-ttu-id="1cedb-231">[SemVer](http://semver.org/) 是一项公共约定，说明了如何生成并更改版本，以便可以轻松解读更改。</span><span class="sxs-lookup"><span data-stu-id="1cedb-231">[SemVer](http://semver.org/) is a public convention that describes how to structure and change a version to allow easy interpretation of changes.</span></span>
<span data-ttu-id="1cedb-232">清单数据中必须包含的包的版本。</span><span class="sxs-lookup"><span data-stu-id="1cedb-232">The version for your package must be included in the manifest data.</span></span>

- <span data-ttu-id="1cedb-233">版本应为 3 个用句点隔开的数字块，如 0.1.1 或 4.11.192</span><span class="sxs-lookup"><span data-stu-id="1cedb-233">The version should be structured as 3 numeric blocks separated by periods, as in 0.1.1 or 4.11.192</span></span>
- <span data-ttu-id="1cedb-234">以“0”开头的版本表明包尚无法用于生产，当 0 为唯一使用的数字时，第一个数字只应以“0”开头</span><span class="sxs-lookup"><span data-stu-id="1cedb-234">Versions starting with "0" indicate that the package is not yet production ready, and the first number should only begin with "0" if that is the only number used</span></span>
- <span data-ttu-id="1cedb-235">第一个数字块中的更改（例如，从 1.9.9999 更改为 2.0.0）表明为主要和重大版本更改</span><span class="sxs-lookup"><span data-stu-id="1cedb-235">Changes in the first number (1.9.9999 to 2.0.0) indicate major and breaking changes between the versions</span></span>
- <span data-ttu-id="1cedb-236">第二个数字的变化（例如，从 1.1 变成 1.2）表示功能级变更，如将新的 cmdlet 添加到模块中</span><span class="sxs-lookup"><span data-stu-id="1cedb-236">Changes to the second number (1.1 to 1.2) indicate feature-level changes, such as adding new cmdlets to a module</span></span>
- <span data-ttu-id="1cedb-237">第三个数字块中的更改表明为非重大更改，如新参数、更新后的示例或新测试</span><span class="sxs-lookup"><span data-stu-id="1cedb-237">Changes to the third number indicate non-breaking changes, such as new parameters, updated samples, or new tests</span></span>
- <span data-ttu-id="1cedb-238">列出版本时，PowerShell 会将版本作为字符串进行排序，因此 1.01.0 将被视为大于 1.001.0</span><span class="sxs-lookup"><span data-stu-id="1cedb-238">When listing versions, PowerShell will sort the versions as strings, so 1.01.0 will be treated as greater than 1.001.0</span></span>

<span data-ttu-id="1cedb-239">PowerShell 的创建时间先于 SemVer 发布时间，因此它支持大多数但非所有 SemVer 元素，具体而言：</span><span class="sxs-lookup"><span data-stu-id="1cedb-239">PowerShell was created before SemVer was published, so it provides support for most but not all elements of SemVer, specifically:</span></span>

- <span data-ttu-id="1cedb-240">它不支持在版本号中使用预发布字符串。</span><span class="sxs-lookup"><span data-stu-id="1cedb-240">It does not support prerelease strings in version numbers.</span></span> <span data-ttu-id="1cedb-241">如果发行者希望在提供版本 1.0.0 之后提供新的主要版本的预览版本，这就非常有用。</span><span class="sxs-lookup"><span data-stu-id="1cedb-241">This is useful when a publisher wishes to deliver a preview release of a new major version after providing a version 1.0.0.</span></span> <span data-ttu-id="1cedb-242">今后发布的 PowerShell 库和 PowerShellGet cmdlet 将支持这样做。</span><span class="sxs-lookup"><span data-stu-id="1cedb-242">This will be supported in a future release of the PowerShell Gallery and PowerShellGet cmdlets.</span></span>
- <span data-ttu-id="1cedb-243">PowerShell 和 PowerShell 库允许使用包含 1、2 和 4 段的版本字符串。</span><span class="sxs-lookup"><span data-stu-id="1cedb-243">PowerShell and the PowerShell Gallery allow version strings with 1, 2, and 4 segments.</span></span> <span data-ttu-id="1cedb-244">许多早期模块并未遵循这些指南，并且 Microsoft 产品版本在第 4 个数字块中包含生成信息（例如，5.1.14393.1066）。</span><span class="sxs-lookup"><span data-stu-id="1cedb-244">Many early modules did not follow the guidelines, and product releases from Microsoft include build information as a 4th block of numbers (for example 5.1.14393.1066).</span></span> <span data-ttu-id="1cedb-245">从版本控制的角度来看，这些差异将被忽略。</span><span class="sxs-lookup"><span data-stu-id="1cedb-245">From a versioning standpoint, these differences are ignored.</span></span>

## <a name="test-using-a-local-repository"></a><span data-ttu-id="1cedb-246">使用本地存储库进行测试</span><span class="sxs-lookup"><span data-stu-id="1cedb-246">Test using a local repository</span></span>

<span data-ttu-id="1cedb-247">PowerShell 库的设计目标不是成为用于测试发布过程的目标。</span><span class="sxs-lookup"><span data-stu-id="1cedb-247">The PowerShell Gallery is not designed to be a target for testing the publishing process.</span></span>
<span data-ttu-id="1cedb-248">测试发布到 PowerShell 库的端到端过程，其最佳方法是自行设置并使用本地存储库。</span><span class="sxs-lookup"><span data-stu-id="1cedb-248">The best way to test out the end-to-end process of publishing to the PowerShell Gallery is to set up and use your own local repository.</span></span>
<span data-ttu-id="1cedb-249">这可以通过多种方式实现，包括：</span><span class="sxs-lookup"><span data-stu-id="1cedb-249">This can be done in a few ways, including:</span></span>

- <span data-ttu-id="1cedb-250">使用 Github 中的 [PS 专用库项目](https://github.com/PowerShell/PSPrivateGallery)设置本地 PowerShell 库实例。</span><span class="sxs-lookup"><span data-stu-id="1cedb-250">Set up a local PowerShell Gallery instance, using the [PS Private Gallery project](https://github.com/PowerShell/PSPrivateGallery) in Github.</span></span> <span data-ttu-id="1cedb-251">此预览项目有助于设置可控制并用于测试的 PowerShell 库实例。</span><span class="sxs-lookup"><span data-stu-id="1cedb-251">This preview project will help you set up an instance of the PowerShell Gallery that you can control, and use for your tests.</span></span>
- <span data-ttu-id="1cedb-252">设置[内部 Nuget 存储库](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/)。</span><span class="sxs-lookup"><span data-stu-id="1cedb-252">Set up an [internal Nuget repository](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/).</span></span> <span data-ttu-id="1cedb-253">需要执行更多工作才能完成此设置，但具有以下优点：验证更多的要求，特别是验证 API 密钥的使用以及发布时目标中是否存在依赖关系。</span><span class="sxs-lookup"><span data-stu-id="1cedb-253">This will require more work to set up, but will have the advantage of validating a few more of the requirements, notably validating use of an API key, and whether or not dependencies are present in the target when you publish.</span></span>
- <span data-ttu-id="1cedb-254">将文件共享设置为“存储库”测试。</span><span class="sxs-lookup"><span data-stu-id="1cedb-254">Set up a file share as the test “repository”.</span></span> <span data-ttu-id="1cedb-255">此设置很容易完成，但由于是文件共享，因此不会发生如上所示的验证。</span><span class="sxs-lookup"><span data-stu-id="1cedb-255">This is easy to set up, but since it is a file share, the validations noted above will not take place.</span></span> <span data-ttu-id="1cedb-256">这种情况下，一个潜在的优点是文件共享不会检查必需的 API 密钥，因此可以使用发布到 PowerShell 库时所用的密钥。</span><span class="sxs-lookup"><span data-stu-id="1cedb-256">One potential advantage in this case is that the file share does not check the (required) API key, so you can use the same key you would to publish to the PowerShell Gallery.</span></span>

<span data-ttu-id="1cedb-257">对于其中任一解决方案，使用 Register-PSRepository 定义一个新“存储库”，用于发布模块的“-Repository”属性。</span><span class="sxs-lookup"><span data-stu-id="1cedb-257">With any of these solutions, use Register-PSRepository to define a new "repository", which you use in the -Repository property for Publish-Module.</span></span>

<span data-ttu-id="1cedb-258">有关测试发布的另外一点：在运营团队的帮助下才能删除发布到 PowerShell 库的包，该团队会确认没有任何内容依赖于要发布的包。</span><span class="sxs-lookup"><span data-stu-id="1cedb-258">One additional point about test publishing: any package you publish to the PowerShell Gallery cannot be deleted without help from the operations team, who will confirm that nothing is dependent upon the package you wish to publish.</span></span>
<span data-ttu-id="1cedb-259">考虑到该原因，我们不支持将 PowerShell 库作为测试目标，并将与进行此操作的任何发布者联系。</span><span class="sxs-lookup"><span data-stu-id="1cedb-259">For that reason, we do not support the PowerShell Gallery as a testing target, and will contact any publisher who does so.</span></span>

## <a name="use-powershellget-to-publish"></a><span data-ttu-id="1cedb-260">使用 PowerShellGet 发布</span><span class="sxs-lookup"><span data-stu-id="1cedb-260">Use PowerShellGet to publish</span></span>

<span data-ttu-id="1cedb-261">在使用 PowerShell 库时，强烈建议发布者使用 Publish-Module 和 Publish-Script cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1cedb-261">It is strongly recommended that publishers use the Publish-Module and Publish-Script cmdlets when working with the PowerShell Gallery.</span></span>
<span data-ttu-id="1cedb-262">创建 PowerShellGet 的目的是，让你无需记住有关从中安装和发布到 PowerShell 库的重要详细信息。</span><span class="sxs-lookup"><span data-stu-id="1cedb-262">PowerShellGet has been created to help you avoid remembering important details about installing from and publishing to the PowerShell Gallery.</span></span>
<span data-ttu-id="1cedb-263">有时，发布者会选择跳过 PowerShellGet 并使用 NuGet 客户端或 PackageManagement cmdlet，而不是 Publish-Module。</span><span class="sxs-lookup"><span data-stu-id="1cedb-263">On occasion, publishers have chosen to skip PowerShellGet and use the NuGet client, or PackageManagement cmdlets, instead of Publish-Module.</span></span>
<span data-ttu-id="1cedb-264">这会使很多详细信息轻易被漏掉，进而导致各种支持请求。</span><span class="sxs-lookup"><span data-stu-id="1cedb-264">There are a number of details that are easily missed, which results in a variety of support requests.</span></span>

<span data-ttu-id="1cedb-265">如果某种原因致使你无法使用 Publish-Module 或 Publish-Script，请告知我们。</span><span class="sxs-lookup"><span data-stu-id="1cedb-265">If there is a reason that you cannot use Publish-Module or Publish-Script, please let us know.</span></span>
<span data-ttu-id="1cedb-266">在 PowerShellGet GitHub 存储库中发布一个问题，并提供导致你选择 NuGet 或 PackageManagement 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1cedb-266">File an issue in the PowerShellGet GitHub repo, and provide the details that cause you to choose NuGet or PackageManagement.</span></span>

## <a name="recommended-workflow"></a><span data-ttu-id="1cedb-267">建议的工作流</span><span class="sxs-lookup"><span data-stu-id="1cedb-267">Recommended workflow</span></span>

<span data-ttu-id="1cedb-268">我们已总结出适用于在 PowerShell 库中发布的包的最成功方法，如下所述：</span><span class="sxs-lookup"><span data-stu-id="1cedb-268">The most successful approach we have found for packages published to the PowerShell Gallery is this:</span></span>

- <span data-ttu-id="1cedb-269">在开放源代码项目网站中进行初始开发。</span><span class="sxs-lookup"><span data-stu-id="1cedb-269">Do initial development in a an open-source project site.</span></span> <span data-ttu-id="1cedb-270">PowerShell 团队使用 Github。</span><span class="sxs-lookup"><span data-stu-id="1cedb-270">The PowerShell Team uses Github.</span></span>
- <span data-ttu-id="1cedb-271">使用审阅者的反馈和 [Powershell 脚本分析器](https://aka.ms/psscriptanalyzer)，让代码处于稳定状态</span><span class="sxs-lookup"><span data-stu-id="1cedb-271">Use feedback from reviewers and [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer) to get the code to stable state</span></span>
- <span data-ttu-id="1cedb-272">添加文档，告知其他人如何使用项</span><span class="sxs-lookup"><span data-stu-id="1cedb-272">Include documentation, so others know how to use your work</span></span>
- <span data-ttu-id="1cedb-273">使用本地存储库测试发布操作。</span><span class="sxs-lookup"><span data-stu-id="1cedb-273">Test out the publishing action using a local repository.</span></span>
- <span data-ttu-id="1cedb-274">将稳定版或 Alpha 版本发布到 PowerShell 库中，同时确保添加文档和项目网站链接</span><span class="sxs-lookup"><span data-stu-id="1cedb-274">Publish a stable or Alpha release to the PowerShell Gallery, making sure to include the documentation and link to your project site</span></span>
- <span data-ttu-id="1cedb-275">收集反馈并循环访问项目网站中的代码，再将稳定更新发布到 PowerShell 库中</span><span class="sxs-lookup"><span data-stu-id="1cedb-275">Gather feedback and iterate on the code in your project site, then publish stable updates to the PowerShell Gallery</span></span>
- <span data-ttu-id="1cedb-276">在项目和模块中添加示例和 Pester 测试</span><span class="sxs-lookup"><span data-stu-id="1cedb-276">Add examples and Pester tests in your project and your module</span></span>
- <span data-ttu-id="1cedb-277">决定是否要对包进行代码签名</span><span class="sxs-lookup"><span data-stu-id="1cedb-277">Decide if you want to code sign your package</span></span>
- <span data-ttu-id="1cedb-278">如果认为项目可用于生产环境，请将 1.0.0 版本发布到 PowerShell 库中</span><span class="sxs-lookup"><span data-stu-id="1cedb-278">When you feel the project is ready to use in a production environment, publish a 1.0.0 version to the PowerShell Gallery</span></span>
- <span data-ttu-id="1cedb-279">继续收集反馈，并根据用户输入循环访问代码</span><span class="sxs-lookup"><span data-stu-id="1cedb-279">Continue to gather feedback and iterate on your code based on user input</span></span>

---
title: 如何提交拉取请求
description: 本文介绍如何向 PowerShell-Docs 存储库提交拉取请求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 2600049b06da5ad4869b6ff335f00bc40c2d1c22
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060232"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="c752e-103">如何提交拉取请求</span><span class="sxs-lookup"><span data-stu-id="c752e-103">How to submit pull requests</span></span>

<span data-ttu-id="c752e-104">若要更改内容，请从你的分支提交拉取请求 (PR)。</span><span class="sxs-lookup"><span data-stu-id="c752e-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="c752e-105">拉取请求必须先经过审核，才能将其合并。</span><span class="sxs-lookup"><span data-stu-id="c752e-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="c752e-106">请先查看[编辑清单](editorial-checklist.md)，然后再提交拉取请求，以获得最佳结果。</span><span class="sxs-lookup"><span data-stu-id="c752e-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="c752e-107">面向正确的分支</span><span class="sxs-lookup"><span data-stu-id="c752e-107">Target the correct branch</span></span>

<span data-ttu-id="c752e-108">所有拉取请求均应面向 `staging` 分支。</span><span class="sxs-lookup"><span data-stu-id="c752e-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="c752e-109">任何情况下都不应将更改提交到 `live` 分支。</span><span class="sxs-lookup"><span data-stu-id="c752e-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="c752e-110">`staging` 分支中的更改会合并到 `live`，重写对 `live` 所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="c752e-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="c752e-111">若要提交的更改仅适用于尚未发布的 PowerShell 版本，请查找该版本的发布分支。</span><span class="sxs-lookup"><span data-stu-id="c752e-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="c752e-112">你的 PR 应面向此发布分支。</span><span class="sxs-lookup"><span data-stu-id="c752e-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="c752e-113">发布分支的名称模式如下所示：`release-<version>`。</span><span class="sxs-lookup"><span data-stu-id="c752e-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="c752e-114">使拉取请求过程更易于所有人使用</span><span class="sxs-lookup"><span data-stu-id="c752e-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="c752e-115">PR 越简单明确，就能越快地对其进行审核和合并。</span><span class="sxs-lookup"><span data-stu-id="c752e-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="c752e-116">避免分支更新大量文件或包含无关更改</span><span class="sxs-lookup"><span data-stu-id="c752e-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="c752e-117">避免创建包含无关更改的 PR。</span><span class="sxs-lookup"><span data-stu-id="c752e-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="c752e-118">将对现有文章的次要更新与新文章或主要重写区分开来。</span><span class="sxs-lookup"><span data-stu-id="c752e-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="c752e-119">在单独的工作分支中处理这些更改。</span><span class="sxs-lookup"><span data-stu-id="c752e-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="c752e-120">批量更改会创建包含大量已更改文件的 PR。</span><span class="sxs-lookup"><span data-stu-id="c752e-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="c752e-121">将 PR 限制为最多 50 个已更改的文件。</span><span class="sxs-lookup"><span data-stu-id="c752e-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="c752e-122">大型 PR 难以审阅，并且更容易包含错误。</span><span class="sxs-lookup"><span data-stu-id="c752e-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="c752e-123">重命名或删除文件</span><span class="sxs-lookup"><span data-stu-id="c752e-123">Renaming or deleting files</span></span>

<span data-ttu-id="c752e-124">若要重命名或删除文件，则必须存在一个与此 PR 关联的问题。</span><span class="sxs-lookup"><span data-stu-id="c752e-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="c752e-125">该问题必须探讨重命名或删除文件的必要性。</span><span class="sxs-lookup"><span data-stu-id="c752e-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="c752e-126">避免将内容添加或更改与文件重命名和删除混淆。</span><span class="sxs-lookup"><span data-stu-id="c752e-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="c752e-127">已重命名或删除的任何文件都必须添加到主重定向文件中。</span><span class="sxs-lookup"><span data-stu-id="c752e-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="c752e-128">如有可能，还应更新链接到已重命名内容或删除内容的任何文件。</span><span class="sxs-lookup"><span data-stu-id="c752e-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="c752e-129">其中包括任何 TOC 文件。</span><span class="sxs-lookup"><span data-stu-id="c752e-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="c752e-130">文档 PR 验证服务</span><span class="sxs-lookup"><span data-stu-id="c752e-130">Docs PR validation service</span></span>

<span data-ttu-id="c752e-131">文档 PR 验证服务是一个 GitHub 应用，用于对 PR 中的文件运行验证规则。</span><span class="sxs-lookup"><span data-stu-id="c752e-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="c752e-132">必须解决此验证服务报告的任何错误或警报（请查看例外情况）。</span><span class="sxs-lookup"><span data-stu-id="c752e-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="c752e-133">可忽略以下警告：</span><span class="sxs-lookup"><span data-stu-id="c752e-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="c752e-134">你将看到以下行为：</span><span class="sxs-lookup"><span data-stu-id="c752e-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="c752e-135">提交 PR。</span><span class="sxs-lookup"><span data-stu-id="c752e-135">You submit a PR.</span></span>
1. <span data-ttu-id="c752e-136">指示 PR 状态的 GitHub 备注将显示以下状态：存储库已启用“检查”。</span><span class="sxs-lookup"><span data-stu-id="c752e-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repo.</span></span> <span data-ttu-id="c752e-137">请注意，在此示例中启用了两个检查，即“提交验证”和“OpenPublishing.Build”：</span><span class="sxs-lookup"><span data-stu-id="c752e-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![一些检查失败](media/pull-requests/validation-failed.png)

   <span data-ttu-id="c752e-139">即使提交验证失败，生成也可以过关。</span><span class="sxs-lookup"><span data-stu-id="c752e-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="c752e-140">有关更多信息，请单击“详细信息”  。</span><span class="sxs-lookup"><span data-stu-id="c752e-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="c752e-141">“详细信息”页将显示所有已失败的验证检查，并包含关于如何解决问题的信息。</span><span class="sxs-lookup"><span data-stu-id="c752e-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="c752e-142">验证成功后，会将以下注释会添加到 PR：</span><span class="sxs-lookup"><span data-stu-id="c752e-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![生成验证](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="c752e-144">若你是外部（非 Microsoft 员工）参与者，则无权访问详细的生成报告或预览链接。</span><span class="sxs-lookup"><span data-stu-id="c752e-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="c752e-145">PowerShell-Docs 团队成员审核 PR 后，可能会要求你做出更改或解决验证报告标记的问题。</span><span class="sxs-lookup"><span data-stu-id="c752e-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="c752e-146">PowerShell-Docs 团队可帮助你明确如何解决这些问题，以及未来的提交如何避免这些问题。</span><span class="sxs-lookup"><span data-stu-id="c752e-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c752e-147">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c752e-147">Next steps</span></span>

[<span data-ttu-id="c752e-148">PowerShell-Docs 风格指南</span><span class="sxs-lookup"><span data-stu-id="c752e-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="c752e-149">其他资源</span><span class="sxs-lookup"><span data-stu-id="c752e-149">Additional resources</span></span>

[<span data-ttu-id="c752e-150">如何管理拉取请求</span><span class="sxs-lookup"><span data-stu-id="c752e-150">How we manage pull requests</span></span>](managing-pull-requests.md)

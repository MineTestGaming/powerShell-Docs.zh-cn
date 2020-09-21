---
title: 如何管理拉取请求
description: 本文介绍 PowerShell-Docs 团队如何管理拉取请求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: af5280e91aa3744b6172dc3555df6989cb0ce1a2
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158167"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="5e50c-103">管理拉取请求</span><span class="sxs-lookup"><span data-stu-id="5e50c-103">Managing pull requests</span></span>

<span data-ttu-id="5e50c-104">本文说明了如何管理 PowerShell-Docs 存储库中的拉取请求。</span><span class="sxs-lookup"><span data-stu-id="5e50c-104">This article documents how we manage pull requests in the PowerShell-Docs repository.</span></span> <span data-ttu-id="5e50c-105">本文旨在为 PowerShell-Docs 团队成员提供帮助。</span><span class="sxs-lookup"><span data-stu-id="5e50c-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="5e50c-106">在此处发布本文，以便为公共参与者提供流程透明性。</span><span class="sxs-lookup"><span data-stu-id="5e50c-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="5e50c-107">最佳做法</span><span class="sxs-lookup"><span data-stu-id="5e50c-107">Best practices</span></span>

- <span data-ttu-id="5e50c-108">提交 PR 的人员不应在不进行同级评审的情况下合并 PR。</span><span class="sxs-lookup"><span data-stu-id="5e50c-108">The person submitting the PR should not merge the PR without a peer review.</span></span>
- <span data-ttu-id="5e50c-109">提交 PR 后分配同级审阅者。</span><span class="sxs-lookup"><span data-stu-id="5e50c-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="5e50c-110">早期分配可让审阅者使用编辑备注更快地做出响应。</span><span class="sxs-lookup"><span data-stu-id="5e50c-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="5e50c-111">使用注释来描述更改的性质或所请求的评审的类型。</span><span class="sxs-lookup"><span data-stu-id="5e50c-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="5e50c-112">请确保 @mention 审阅者。</span><span class="sxs-lookup"><span data-stu-id="5e50c-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="5e50c-113">例如，如果更改很小，并且不需要完整的技术评审，请在注释中对此进行说明。</span><span class="sxs-lookup"><span data-stu-id="5e50c-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="5e50c-114">PR 流程步骤</span><span class="sxs-lookup"><span data-stu-id="5e50c-114">PR Process steps</span></span>

1. <span data-ttu-id="5e50c-115">作者：创建 PR</span><span class="sxs-lookup"><span data-stu-id="5e50c-115">Writer: Create PR</span></span>
   - <span data-ttu-id="5e50c-116">链接 PR 解决的所有问题</span><span class="sxs-lookup"><span data-stu-id="5e50c-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="5e50c-117">使用 GitHub 的 [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) 功能关闭问题</span><span class="sxs-lookup"><span data-stu-id="5e50c-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="5e50c-118">作者：分配同级审阅者</span><span class="sxs-lookup"><span data-stu-id="5e50c-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="5e50c-119">审阅者：校对和注释（如有必要）</span><span class="sxs-lookup"><span data-stu-id="5e50c-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="5e50c-120">作者：合并评审反馈</span><span class="sxs-lookup"><span data-stu-id="5e50c-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="5e50c-121">两者：评审预览渲染</span><span class="sxs-lookup"><span data-stu-id="5e50c-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="5e50c-122">两者：评审验证报告 - 修复警告和错误</span><span class="sxs-lookup"><span data-stu-id="5e50c-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="5e50c-123">作者：添加注销注释（包括 Acrolinx 信息）</span><span class="sxs-lookup"><span data-stu-id="5e50c-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="5e50c-124">审阅者：标记评审“已批准”</span><span class="sxs-lookup"><span data-stu-id="5e50c-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="5e50c-125">存储库管理员：合并 PR（请参阅下面的条件）</span><span class="sxs-lookup"><span data-stu-id="5e50c-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="5e50c-126">内容审阅者清单</span><span class="sxs-lookup"><span data-stu-id="5e50c-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="5e50c-127">有关更全面的列表，请参阅[编辑清单](editorial-checklist.md)。</span><span class="sxs-lookup"><span data-stu-id="5e50c-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="5e50c-128">校对语法、风格、简洁性、技术准确性</span><span class="sxs-lookup"><span data-stu-id="5e50c-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="5e50c-129">确保示例仍适用于目标版本</span><span class="sxs-lookup"><span data-stu-id="5e50c-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="5e50c-130">检查预览渲染</span><span class="sxs-lookup"><span data-stu-id="5e50c-130">Check Preview rendering</span></span>
- <span data-ttu-id="5e50c-131">检查元数据 - ms.date，删除 ms.assetid，确保必填字段</span><span class="sxs-lookup"><span data-stu-id="5e50c-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="5e50c-132">验证 markdown 正确性</span><span class="sxs-lookup"><span data-stu-id="5e50c-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="5e50c-133">请参阅风格指南以设置特定内容的格式</span><span class="sxs-lookup"><span data-stu-id="5e50c-133">See style guide for formatting specific content</span></span>
- <span data-ttu-id="5e50c-134">按如下所示重新组织示例：</span><span class="sxs-lookup"><span data-stu-id="5e50c-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="5e50c-135">介绍语句</span><span class="sxs-lookup"><span data-stu-id="5e50c-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="5e50c-136">代码和输出</span><span class="sxs-lookup"><span data-stu-id="5e50c-136">Code and output</span></span>
  - <span data-ttu-id="5e50c-137">代码的详细说明（如有必要）</span><span class="sxs-lookup"><span data-stu-id="5e50c-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="5e50c-138">检查超链接的准确性</span><span class="sxs-lookup"><span data-stu-id="5e50c-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="5e50c-139">替换或删除 TechNet/MSDN 链接</span><span class="sxs-lookup"><span data-stu-id="5e50c-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="5e50c-140">确保重定向到目标的最小数量</span><span class="sxs-lookup"><span data-stu-id="5e50c-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="5e50c-141">确保 HTTPS</span><span class="sxs-lookup"><span data-stu-id="5e50c-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="5e50c-142">更正链接类型</span><span class="sxs-lookup"><span data-stu-id="5e50c-142">Correct link type</span></span>
    - <span data-ttu-id="5e50c-143">本地文件的文件链接</span><span class="sxs-lookup"><span data-stu-id="5e50c-143">File links for local files</span></span>
    - <span data-ttu-id="5e50c-144">docset 之外的文件的 URL 链接</span><span class="sxs-lookup"><span data-stu-id="5e50c-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="5e50c-145">从 URL 中删除区域设置</span><span class="sxs-lookup"><span data-stu-id="5e50c-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="5e50c-146">简化指向 `docs.microsoft.com` 的 URL</span><span class="sxs-lookup"><span data-stu-id="5e50c-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="5e50c-147">分支合并进程</span><span class="sxs-lookup"><span data-stu-id="5e50c-147">Branch Merge Process</span></span>

<span data-ttu-id="5e50c-148">Staging 分支是应合并到 live 分支中的唯一分支。</span><span class="sxs-lookup"><span data-stu-id="5e50c-148">The staging branch is the only branch that should ever be merged into live.</span></span> <span data-ttu-id="5e50c-149">应压缩来自短期（工作）分支的合并。</span><span class="sxs-lookup"><span data-stu-id="5e50c-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="5e50c-150">*合并自/到*</span><span class="sxs-lookup"><span data-stu-id="5e50c-150">*Merge from/to*</span></span>  | <span data-ttu-id="5e50c-151">*发布分支*</span><span class="sxs-lookup"><span data-stu-id="5e50c-151">*release-branch*</span></span> | <span data-ttu-id="5e50c-152">*staging*</span><span class="sxs-lookup"><span data-stu-id="5e50c-152">*staging*</span></span>        | <span data-ttu-id="5e50c-153">*live*</span><span class="sxs-lookup"><span data-stu-id="5e50c-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="5e50c-154">*工作分支*</span><span class="sxs-lookup"><span data-stu-id="5e50c-154">*working-branch*</span></span> | <span data-ttu-id="5e50c-155">压缩并合并</span><span class="sxs-lookup"><span data-stu-id="5e50c-155">squash and merge</span></span> | <span data-ttu-id="5e50c-156">压缩并合并</span><span class="sxs-lookup"><span data-stu-id="5e50c-156">squash and merge</span></span> | <span data-ttu-id="5e50c-157">不允许</span><span class="sxs-lookup"><span data-stu-id="5e50c-157">Not allowed</span></span> |
| <span data-ttu-id="5e50c-158">*发布分支*</span><span class="sxs-lookup"><span data-stu-id="5e50c-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="5e50c-159">merge</span><span class="sxs-lookup"><span data-stu-id="5e50c-159">merge</span></span>            | <span data-ttu-id="5e50c-160">不允许</span><span class="sxs-lookup"><span data-stu-id="5e50c-160">Not allowed</span></span> |
| <span data-ttu-id="5e50c-161">*staging*</span><span class="sxs-lookup"><span data-stu-id="5e50c-161">*staging*</span></span>        | <span data-ttu-id="5e50c-162">变基</span><span class="sxs-lookup"><span data-stu-id="5e50c-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="5e50c-163">merge</span><span class="sxs-lookup"><span data-stu-id="5e50c-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="5e50c-164">PR 合并器清单</span><span class="sxs-lookup"><span data-stu-id="5e50c-164">PR Merger checklist</span></span>

- <span data-ttu-id="5e50c-165">内容评审完成</span><span class="sxs-lookup"><span data-stu-id="5e50c-165">Content review complete</span></span>
- <span data-ttu-id="5e50c-166">更正更改的目标分支</span><span class="sxs-lookup"><span data-stu-id="5e50c-166">Correct target branch for the change</span></span>
- <span data-ttu-id="5e50c-167">无合并冲突</span><span class="sxs-lookup"><span data-stu-id="5e50c-167">No merge conflicts</span></span>
- <span data-ttu-id="5e50c-168">所有验证和生成步骤均通过</span><span class="sxs-lookup"><span data-stu-id="5e50c-168">All validation and build step pass</span></span>
  - <span data-ttu-id="5e50c-169">应修复警告和建议（请参阅[说明](#notes)以了解异常情况）</span><span class="sxs-lookup"><span data-stu-id="5e50c-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="5e50c-170">无断开的链接</span><span class="sxs-lookup"><span data-stu-id="5e50c-170">No broken links</span></span>
- <span data-ttu-id="5e50c-171">根据表合并</span><span class="sxs-lookup"><span data-stu-id="5e50c-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="5e50c-172">说明</span><span class="sxs-lookup"><span data-stu-id="5e50c-172">Notes</span></span>

<span data-ttu-id="5e50c-173">可忽略以下警告：</span><span class="sxs-lookup"><span data-stu-id="5e50c-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="5e50c-174">合并 PR 时，将更改目标分支的标头。</span><span class="sxs-lookup"><span data-stu-id="5e50c-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="5e50c-175">基于前一标头的任何打开的 PR 现已过时。</span><span class="sxs-lookup"><span data-stu-id="5e50c-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="5e50c-176">可以使用管理员权限合并过时的 PR 以覆盖 GitHub 中的合并警告。</span><span class="sxs-lookup"><span data-stu-id="5e50c-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="5e50c-177">如果之前合并的 PR 未涉及到相同的文件，则可以放心地执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5e50c-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="5e50c-178">但是，单击“更新分支”按钮是最安全的选项  。</span><span class="sxs-lookup"><span data-stu-id="5e50c-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="5e50c-179">你可能有未解决但需要修复的冲突。</span><span class="sxs-lookup"><span data-stu-id="5e50c-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="5e50c-180">发布到 Live</span><span class="sxs-lookup"><span data-stu-id="5e50c-180">Publishing to Live</span></span>

<span data-ttu-id="5e50c-181">需要定期将 `staging` 分支中累积的更改发布到实时网站。</span><span class="sxs-lookup"><span data-stu-id="5e50c-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span> <span data-ttu-id="5e50c-182">这需要将 `staging` 分支合并到 `live` 分支中。</span><span class="sxs-lookup"><span data-stu-id="5e50c-182">This require merging the `staging` branch into the `live` branch.</span></span>

- <span data-ttu-id="5e50c-183">`staging` 分支应合并到 `live` 中，至少每周一次。</span><span class="sxs-lookup"><span data-stu-id="5e50c-183">The `staging` branch should be merged to `live` at least once per week.</span></span>
- <span data-ttu-id="5e50c-184">做出任何重大更改后，应将 `staging` 分支合并到 `live` 中。</span><span class="sxs-lookup"><span data-stu-id="5e50c-184">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="5e50c-185">50 个或更多文件的更改</span><span class="sxs-lookup"><span data-stu-id="5e50c-185">Changes to 50 or more files</span></span>
  - <span data-ttu-id="5e50c-186">合并发布分支后</span><span class="sxs-lookup"><span data-stu-id="5e50c-186">After merging a release branch</span></span>
  - <span data-ttu-id="5e50c-187">存储库或 docset 配置的更改（docfx.json、OPS 配置、生成脚本等）</span><span class="sxs-lookup"><span data-stu-id="5e50c-187">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="5e50c-188">重定向文件的更改</span><span class="sxs-lookup"><span data-stu-id="5e50c-188">Changes to the redirection file</span></span>
  - <span data-ttu-id="5e50c-189">TOC 的更改</span><span class="sxs-lookup"><span data-stu-id="5e50c-189">Changes to the TOC</span></span>
  - <span data-ttu-id="5e50c-190">合并“项目”分支后（内容重新组织、批量更新等）</span><span class="sxs-lookup"><span data-stu-id="5e50c-190">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>

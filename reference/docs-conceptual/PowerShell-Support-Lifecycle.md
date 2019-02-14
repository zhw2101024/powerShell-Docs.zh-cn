---
title: PowerShell Core 支持生命周期
description: 用于管理 PowerShell Core 支持的策略
ms.date: 08/06/2018
ms.openlocfilehash: cb1daf953b11ffba8f39bcc05a8b122350c497eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677506"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="3e97e-103">PowerShell Core 支持生命周期</span><span class="sxs-lookup"><span data-stu-id="3e97e-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="3e97e-104">PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。</span><span class="sxs-lookup"><span data-stu-id="3e97e-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="3e97e-105">因此，PowerShell Core 未包含在 Windows 7/8.1/10 或 Windows Server 许可协议。</span><span class="sxs-lookup"><span data-stu-id="3e97e-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="3e97e-106">但是，PowerShell Core 受传统 Microsoft 支持协议支持，此类协议包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。</span><span class="sxs-lookup"><span data-stu-id="3e97e-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="3e97e-107">还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。</span><span class="sxs-lookup"><span data-stu-id="3e97e-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="3e97e-108">我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。</span><span class="sxs-lookup"><span data-stu-id="3e97e-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="3e97e-109">此外，可能会发现社区的其他成员的帮助在常规[Microsoft 社区][]或 Microsoft [PowerShell 技术社区][]。</span><span class="sxs-lookup"><span data-stu-id="3e97e-109">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="3e97e-110">我们不能确保社区将解决或及时地解决遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="3e97e-110">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="3e97e-111">如果问题需要立即解决，应使用传统的付费支持选项。</span><span class="sxs-lookup"><span data-stu-id="3e97e-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="3e97e-112">PowerShell Core 生命周期</span><span class="sxs-lookup"><span data-stu-id="3e97e-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="3e97e-113">PowerShell Core 采用 [Microsoft 新式声明周期策略][modern]。</span><span class="sxs-lookup"><span data-stu-id="3e97e-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="3e97e-114">此支持生命周期旨在使客户随时知悉最新版本。</span><span class="sxs-lookup"><span data-stu-id="3e97e-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="3e97e-115">PowerShell Core 的版本 6.x 分支将会更新一次大约每六个月 (示例：6.0、 6.1、 6.2 等。)</span><span class="sxs-lookup"><span data-stu-id="3e97e-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e97e-116">必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="3e97e-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="3e97e-117">例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，你将需要按年 1 月 1，2019 若要维持支持更新到 PowerShell Core 6.1。</span><span class="sxs-lookup"><span data-stu-id="3e97e-117">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命周期][lifecycle-chart]

<span data-ttu-id="3e97e-119">新式生命周期策略还要求，Microsoft 为客户提供 12 个月通知之前不再使用的产品 (即，PowerShell Core) 的支持。</span><span class="sxs-lookup"><span data-stu-id="3e97e-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="3e97e-120">最终，我们希望 PowerShell Core 采取"长期服务"的方法。</span><span class="sxs-lookup"><span data-stu-id="3e97e-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="3e97e-121">在此维护服务方法时，我们将需要仅维护和安全更新即可获取有关 6.x 特定分支/版本上支持。</span><span class="sxs-lookup"><span data-stu-id="3e97e-121">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="3e97e-122">支持平台</span><span class="sxs-lookup"><span data-stu-id="3e97e-122">Supported platforms</span></span>

<span data-ttu-id="3e97e-123">下表以查看哪种平台使用的 PowerShell Core 的版本已正式支持。</span><span class="sxs-lookup"><span data-stu-id="3e97e-123">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="3e97e-124">我们社区也为某些平台提供包，但这些平台不受正式支持。</span><span class="sxs-lookup"><span data-stu-id="3e97e-124">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="3e97e-125">这些包在表中标记为 `Community`。</span><span class="sxs-lookup"><span data-stu-id="3e97e-125">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="3e97e-126">列为 `Experimental` 的平台不受正式支持，但可用于实验和反馈。</span><span class="sxs-lookup"><span data-stu-id="3e97e-126">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="3e97e-127">6.0</span><span class="sxs-lookup"><span data-stu-id="3e97e-127">6.0</span></span>         | <span data-ttu-id="3e97e-128">6.1</span><span class="sxs-lookup"><span data-stu-id="3e97e-128">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="3e97e-129">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="3e97e-129">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="3e97e-130">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-130">Supported</span></span>   | <span data-ttu-id="3e97e-131">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-131">Supported</span></span>   |
| <span data-ttu-id="3e97e-132">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="3e97e-132">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="3e97e-133">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-133">Supported</span></span>   | <span data-ttu-id="3e97e-134">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-134">Supported</span></span>   |
| <span data-ttu-id="3e97e-135">[Windows Server 半年频道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="3e97e-135">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="3e97e-136">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-136">Supported</span></span>   | <span data-ttu-id="3e97e-137">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-137">Supported</span></span>   |
| <span data-ttu-id="3e97e-138">Ubuntu 14.04 和 16.04</span><span class="sxs-lookup"><span data-stu-id="3e97e-138">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="3e97e-139">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-139">Supported</span></span>   | <span data-ttu-id="3e97e-140">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-140">Supported</span></span>   |
| <span data-ttu-id="3e97e-141">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3e97e-141">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="3e97e-142">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-142">Supported</span></span>   |
| <span data-ttu-id="3e97e-143">Ubuntu 18.10（使用 Snap 包）</span><span class="sxs-lookup"><span data-stu-id="3e97e-143">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="3e97e-144">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-144">Community</span></span>   |
| <span data-ttu-id="3e97e-145">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3e97e-145">Debian 9</span></span>                                          | <span data-ttu-id="3e97e-146">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-146">Supported</span></span>   | <span data-ttu-id="3e97e-147">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-147">Supported</span></span>   |
| <span data-ttu-id="3e97e-148">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3e97e-148">CentOS 7</span></span>                                          | <span data-ttu-id="3e97e-149">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-149">Supported</span></span>   | <span data-ttu-id="3e97e-150">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-150">Supported</span></span>   |
| <span data-ttu-id="3e97e-151">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="3e97e-151">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="3e97e-152">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-152">Supported</span></span>   | <span data-ttu-id="3e97e-153">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-153">Supported</span></span>   |
| <span data-ttu-id="3e97e-154">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3e97e-154">openSUSE 42.3</span></span>                                     | <span data-ttu-id="3e97e-155">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-155">Supported</span></span>   | <span data-ttu-id="3e97e-156">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-156">Supported</span></span>   |
| <span data-ttu-id="3e97e-157">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3e97e-157">Fedora 28</span></span>                                         |             | <span data-ttu-id="3e97e-158">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-158">Supported</span></span>   |
| <span data-ttu-id="3e97e-159">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="3e97e-159">macOS 10.12+</span></span>                                      | <span data-ttu-id="3e97e-160">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-160">Supported</span></span>   | <span data-ttu-id="3e97e-161">支持</span><span class="sxs-lookup"><span data-stu-id="3e97e-161">Supported</span></span>   |
| <span data-ttu-id="3e97e-162">Arch</span><span class="sxs-lookup"><span data-stu-id="3e97e-162">Arch</span></span>                                              | <span data-ttu-id="3e97e-163">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-163">Community</span></span>   | <span data-ttu-id="3e97e-164">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-164">Community</span></span>   |
| <span data-ttu-id="3e97e-165">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3e97e-165">Raspbian</span></span>                                          | <span data-ttu-id="3e97e-166">实验</span><span class="sxs-lookup"><span data-stu-id="3e97e-166">Experimental</span></span>| <span data-ttu-id="3e97e-167">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-167">Community</span></span>   |
| <span data-ttu-id="3e97e-168">Kali</span><span class="sxs-lookup"><span data-stu-id="3e97e-168">Kali</span></span>                                              | <span data-ttu-id="3e97e-169">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-169">Community</span></span>   | <span data-ttu-id="3e97e-170">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-170">Community</span></span>   |
| <span data-ttu-id="3e97e-171">AppImage（可在多个 Linux 平台上运行）</span><span class="sxs-lookup"><span data-stu-id="3e97e-171">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="3e97e-172">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-172">Community</span></span>   | <span data-ttu-id="3e97e-173">社区</span><span class="sxs-lookup"><span data-stu-id="3e97e-173">Community</span></span>   |
| [<span data-ttu-id="3e97e-174">Snap 包</span><span class="sxs-lookup"><span data-stu-id="3e97e-174">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="3e97e-175">查看注释</span><span class="sxs-lookup"><span data-stu-id="3e97e-175">See note</span></span>    | <span data-ttu-id="3e97e-176">查看注释</span><span class="sxs-lookup"><span data-stu-id="3e97e-176">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="3e97e-177">将试验 Snap 包一段时间。</span><span class="sxs-lookup"><span data-stu-id="3e97e-177">Snap packages will be experimental for a period.</span></span>
> <span data-ttu-id="3e97e-178">在我们确信 Snap 不会引入新的支持问题后，将支持你当前运行此包的分发。</span><span class="sxs-lookup"><span data-stu-id="3e97e-178">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="3e97e-179">PowerShell 版本生命周期结束</span><span class="sxs-lookup"><span data-stu-id="3e97e-179">PowerShell release end of life</span></span>

<span data-ttu-id="3e97e-180">基于[生命周期的 PowerShell Core](#lifecycle-of-powershell-core)下, 表列出了当将不再支持各种版本的日期。</span><span class="sxs-lookup"><span data-stu-id="3e97e-180">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="3e97e-181">版本</span><span class="sxs-lookup"><span data-stu-id="3e97e-181">Version</span></span> | <span data-ttu-id="3e97e-182">生命周期结束</span><span class="sxs-lookup"><span data-stu-id="3e97e-182">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="3e97e-183">6.0</span><span class="sxs-lookup"><span data-stu-id="3e97e-183">6.0</span></span>     | <span data-ttu-id="3e97e-184">2019 年 2 月 13日日</span><span class="sxs-lookup"><span data-stu-id="3e97e-184">February 13, 2019</span></span>             |
| <span data-ttu-id="3e97e-185">6.1</span><span class="sxs-lookup"><span data-stu-id="3e97e-185">6.1</span></span>     | <span data-ttu-id="3e97e-186">6.2 版本后 6 个月</span><span class="sxs-lookup"><span data-stu-id="3e97e-186">6 Months after 6.2 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="3e97e-187">不支持的平台</span><span class="sxs-lookup"><span data-stu-id="3e97e-187">Platforms, which are out of support</span></span>

<span data-ttu-id="3e97e-188">当平台版本达到生命周期结束时定义的平台所有者时，PowerShell Core 还将停止支持该平台版本。</span><span class="sxs-lookup"><span data-stu-id="3e97e-188">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="3e97e-189">以前发布的包对需要访问的客户仍可用，但将不再提供任何种类的正式支持和更新。</span><span class="sxs-lookup"><span data-stu-id="3e97e-189">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="3e97e-190">因此，分发所有者已结束的以下版本的支持和不受支持。</span><span class="sxs-lookup"><span data-stu-id="3e97e-190">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="3e97e-191">操作系统</span><span class="sxs-lookup"><span data-stu-id="3e97e-191">OS</span></span>       | <span data-ttu-id="3e97e-192">版本</span><span class="sxs-lookup"><span data-stu-id="3e97e-192">Version</span></span> | <span data-ttu-id="3e97e-193">生命周期终止</span><span class="sxs-lookup"><span data-stu-id="3e97e-193">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="3e97e-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="3e97e-194">Fedora</span></span>   | <span data-ttu-id="3e97e-195">24</span><span class="sxs-lookup"><span data-stu-id="3e97e-195">24</span></span>      | [<span data-ttu-id="3e97e-196">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-196">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="3e97e-197">Fedora</span><span class="sxs-lookup"><span data-stu-id="3e97e-197">Fedora</span></span>   | <span data-ttu-id="3e97e-198">25</span><span class="sxs-lookup"><span data-stu-id="3e97e-198">25</span></span>      | [<span data-ttu-id="3e97e-199">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-199">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="3e97e-200">Fedora</span><span class="sxs-lookup"><span data-stu-id="3e97e-200">Fedora</span></span>   | <span data-ttu-id="3e97e-201">26</span><span class="sxs-lookup"><span data-stu-id="3e97e-201">26</span></span>      | [<span data-ttu-id="3e97e-202">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-202">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="3e97e-203">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="3e97e-203">openSUSE</span></span> | <span data-ttu-id="3e97e-204">42.1</span><span class="sxs-lookup"><span data-stu-id="3e97e-204">42.1</span></span>    | [<span data-ttu-id="3e97e-205">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-205">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="3e97e-206">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="3e97e-206">openSUSE</span></span> | <span data-ttu-id="3e97e-207">42.2</span><span class="sxs-lookup"><span data-stu-id="3e97e-207">42.2</span></span>    | [<span data-ttu-id="3e97e-208">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-208">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="3e97e-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3e97e-209">Ubuntu</span></span>   | <span data-ttu-id="3e97e-210">16.10</span><span class="sxs-lookup"><span data-stu-id="3e97e-210">16.10</span></span>   | [<span data-ttu-id="3e97e-211">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-211">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="3e97e-212">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3e97e-212">Ubuntu</span></span>   | <span data-ttu-id="3e97e-213">17.04</span><span class="sxs-lookup"><span data-stu-id="3e97e-213">17.04</span></span>   | [<span data-ttu-id="3e97e-214">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-214">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="3e97e-215">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3e97e-215">Ubuntu</span></span>   | <span data-ttu-id="3e97e-216">17.10</span><span class="sxs-lookup"><span data-stu-id="3e97e-216">17.10</span></span>   | [<span data-ttu-id="3e97e-217">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-217">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="3e97e-218">Debian</span><span class="sxs-lookup"><span data-stu-id="3e97e-218">Debian</span></span>   | <span data-ttu-id="3e97e-219">8</span><span class="sxs-lookup"><span data-stu-id="3e97e-219">8</span></span>       | [<span data-ttu-id="3e97e-220">2018 年 6 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-220">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="3e97e-221">Fedora</span><span class="sxs-lookup"><span data-stu-id="3e97e-221">Fedora</span></span>   | <span data-ttu-id="3e97e-222">27</span><span class="sxs-lookup"><span data-stu-id="3e97e-222">27</span></span>      | [<span data-ttu-id="3e97e-223">2018 年 11 月</span><span class="sxs-lookup"><span data-stu-id="3e97e-223">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |

## <a name="notes-on-licensing"></a><span data-ttu-id="3e97e-224">有关许可的说明</span><span class="sxs-lookup"><span data-stu-id="3e97e-224">Notes on licensing</span></span>

<span data-ttu-id="3e97e-225">PowerShell Core 在 [MIT 许可][] 下发布。</span><span class="sxs-lookup"><span data-stu-id="3e97e-225">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="3e97e-226">根据此许可证，而无需付费的支持协议，用户仅限于[社区支持][]。</span><span class="sxs-lookup"><span data-stu-id="3e97e-226">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="3e97e-227">对于社区支持，Microsoft 无法保证及时作出响应或进行修复。</span><span class="sxs-lookup"><span data-stu-id="3e97e-227">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="3e97e-228">Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="3e97e-228">Windows PowerShell Module</span></span>

<span data-ttu-id="3e97e-229">支持 PowerShell Core 不包括产品模块，除非这些模块显式支持 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="3e97e-229">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="3e97e-230">例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。</span><span class="sxs-lookup"><span data-stu-id="3e97e-230">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="3e97e-231">但是，不显式支持 PowerShell Core 的模块在某些情况下可能兼容。</span><span class="sxs-lookup"><span data-stu-id="3e97e-231">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="3e97e-232">通过安装[ `WindowsPSModulePath` ][]模块，可以添加 Windows PowerShell`PSModulePath`到 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="3e97e-232">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="3e97e-233">首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：</span><span class="sxs-lookup"><span data-stu-id="3e97e-233">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="3e97e-234">安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="3e97e-234">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[顶级]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[社区支持]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft 社区]: https://answers.microsoft.com/
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell 技术社区]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[辅助支持]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 许可]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/

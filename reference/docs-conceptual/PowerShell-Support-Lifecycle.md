---
title: PowerShell Core 支持生命周期
description: 用于管理 PowerShell Core 支持的策略
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086950"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="d77ef-103">PowerShell Core 支持生命周期</span><span class="sxs-lookup"><span data-stu-id="d77ef-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="d77ef-104">PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。</span><span class="sxs-lookup"><span data-stu-id="d77ef-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="d77ef-105">因此，PowerShell Core 不包括在 Windows 7/8.1/10 或 Windows Server 许可协议中。</span><span class="sxs-lookup"><span data-stu-id="d77ef-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="d77ef-106">但是，PowerShell Core 受传统 Microsoft 支持协议支持，此类协议包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。</span><span class="sxs-lookup"><span data-stu-id="d77ef-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="d77ef-107">还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。</span><span class="sxs-lookup"><span data-stu-id="d77ef-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="d77ef-108">社区支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-108">Community Support</span></span>

<span data-ttu-id="d77ef-109">我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。</span><span class="sxs-lookup"><span data-stu-id="d77ef-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="d77ef-110">此外，还可以获取来自常规 [Microsoft 社区][]或 Microsoft [PowerShell 技术社区][] 的其他成员的帮助。</span><span class="sxs-lookup"><span data-stu-id="d77ef-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="d77ef-111">我们不能确保社区能够及时解决问题。</span><span class="sxs-lookup"><span data-stu-id="d77ef-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="d77ef-112">如果问题需要立即解决，应使用传统的付费支持选项。</span><span class="sxs-lookup"><span data-stu-id="d77ef-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="d77ef-113">PowerShell Core 生命周期</span><span class="sxs-lookup"><span data-stu-id="d77ef-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="d77ef-114">PowerShell Core 采用 [Microsoft 新式声明周期策略][modern]。</span><span class="sxs-lookup"><span data-stu-id="d77ef-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="d77ef-115">此支持生命周期旨在使客户随时知悉最新版本。</span><span class="sxs-lookup"><span data-stu-id="d77ef-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="d77ef-116">PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。</span><span class="sxs-lookup"><span data-stu-id="d77ef-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d77ef-117">必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="d77ef-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="d77ef-118">例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="d77ef-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d77ef-119">必须在每个新修补程序版本发布后的 30 天之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="d77ef-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="d77ef-120">例如，如果正在运行 PowerShell Core 6.1，并且 6.1.3 发布于 2019 年 2 月 19 日，则应在发布后的 30 天之内（即，在 2019 年 3 月 21 日前）更新到 PowerShell Core 6.1.3，更新后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="d77ef-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="d77ef-121">如果发现需要任何修补程序，则将在下一次累积更新中发布修补程序。</span><span class="sxs-lookup"><span data-stu-id="d77ef-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

![PowerShell Core 分支生命周期][lifecycle-chart]

<span data-ttu-id="d77ef-123">新式生命周期策略还要求，在中止对某产品（即 PowerShell Core）提供支持前的 12 个月内，Microsoft 需向客户持续提供通知。</span><span class="sxs-lookup"><span data-stu-id="d77ef-123">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="d77ef-124">最终，我们希望 PowerShell Core 采取“长期服务”方法。</span><span class="sxs-lookup"><span data-stu-id="d77ef-124">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="d77ef-125">在此服务方法中，只需服务和安全更新即可获取有关 6.x 特定分支/版本的支持。</span><span class="sxs-lookup"><span data-stu-id="d77ef-125">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="d77ef-126">支持平台</span><span class="sxs-lookup"><span data-stu-id="d77ef-126">Supported platforms</span></span>

<span data-ttu-id="d77ef-127">请参阅下表，了解所用 PowerShell Core 版本正式支持哪些平台。</span><span class="sxs-lookup"><span data-stu-id="d77ef-127">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="d77ef-128">我们社区也为某些平台提供包，但这些平台不受正式支持。</span><span class="sxs-lookup"><span data-stu-id="d77ef-128">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="d77ef-129">这些包在表中标记为 `Community`。</span><span class="sxs-lookup"><span data-stu-id="d77ef-129">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="d77ef-130">列为 `Experimental` 的平台不受正式支持，但可用于实验和反馈。</span><span class="sxs-lookup"><span data-stu-id="d77ef-130">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="d77ef-131">6.1</span><span class="sxs-lookup"><span data-stu-id="d77ef-131">6.1</span></span>         | <span data-ttu-id="d77ef-132">6.2</span><span class="sxs-lookup"><span data-stu-id="d77ef-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="d77ef-133">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="d77ef-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="d77ef-134">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-134">Supported</span></span>   | <span data-ttu-id="d77ef-135">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-135">Supported</span></span>   |
| <span data-ttu-id="d77ef-136">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="d77ef-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="d77ef-137">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-137">Supported</span></span>   | <span data-ttu-id="d77ef-138">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-138">Supported</span></span>   |
| <span data-ttu-id="d77ef-139">[Windows Server 半年频道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="d77ef-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="d77ef-140">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-140">Supported</span></span>   | <span data-ttu-id="d77ef-141">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-141">Supported</span></span>   |
| <span data-ttu-id="d77ef-142">Ubuntu 16.04 和 18.04</span><span class="sxs-lookup"><span data-stu-id="d77ef-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="d77ef-143">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-143">Supported</span></span>   | <span data-ttu-id="d77ef-144">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-144">Supported</span></span>   |
| <span data-ttu-id="d77ef-145">Ubuntu 18.10（使用 Snap 包）</span><span class="sxs-lookup"><span data-stu-id="d77ef-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="d77ef-146">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-146">Community</span></span>   | <span data-ttu-id="d77ef-147">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-147">Community</span></span>   |
| <span data-ttu-id="d77ef-148">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d77ef-148">Debian 9</span></span>                                          | <span data-ttu-id="d77ef-149">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-149">Supported</span></span>   | <span data-ttu-id="d77ef-150">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-150">Supported</span></span>   |
| <span data-ttu-id="d77ef-151">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d77ef-151">CentOS 7</span></span>                                          | <span data-ttu-id="d77ef-152">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-152">Supported</span></span>   | <span data-ttu-id="d77ef-153">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-153">Supported</span></span>   |
| <span data-ttu-id="d77ef-154">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d77ef-154">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="d77ef-155">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-155">Supported</span></span>   | <span data-ttu-id="d77ef-156">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-156">Supported</span></span>   |
| <span data-ttu-id="d77ef-157">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d77ef-157">openSUSE 42.3</span></span>                                     | <span data-ttu-id="d77ef-158">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-158">Supported</span></span>   | <span data-ttu-id="d77ef-159">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-159">Supported</span></span>   |
| <span data-ttu-id="d77ef-160">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d77ef-160">Fedora 28</span></span>                                         | <span data-ttu-id="d77ef-161">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-161">Supported</span></span>   | <span data-ttu-id="d77ef-162">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-162">Supported</span></span>   |
| <span data-ttu-id="d77ef-163">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="d77ef-163">macOS 10.12+</span></span>                                      | <span data-ttu-id="d77ef-164">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-164">Supported</span></span>   | <span data-ttu-id="d77ef-165">支持</span><span class="sxs-lookup"><span data-stu-id="d77ef-165">Supported</span></span>   |
| <span data-ttu-id="d77ef-166">Arch</span><span class="sxs-lookup"><span data-stu-id="d77ef-166">Arch</span></span>                                              | <span data-ttu-id="d77ef-167">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-167">Community</span></span>   | <span data-ttu-id="d77ef-168">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-168">Community</span></span>   |
| <span data-ttu-id="d77ef-169">Raspbian</span><span class="sxs-lookup"><span data-stu-id="d77ef-169">Raspbian</span></span>                                          | <span data-ttu-id="d77ef-170">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-170">Community</span></span>   | <span data-ttu-id="d77ef-171">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-171">Community</span></span>   |
| <span data-ttu-id="d77ef-172">Kali</span><span class="sxs-lookup"><span data-stu-id="d77ef-172">Kali</span></span>                                              | <span data-ttu-id="d77ef-173">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-173">Community</span></span>   | <span data-ttu-id="d77ef-174">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-174">Community</span></span>   |
| <span data-ttu-id="d77ef-175">AppImage（可在多个 Linux 平台上运行）</span><span class="sxs-lookup"><span data-stu-id="d77ef-175">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="d77ef-176">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-176">Community</span></span>   | <span data-ttu-id="d77ef-177">社区</span><span class="sxs-lookup"><span data-stu-id="d77ef-177">Community</span></span>   |
| [<span data-ttu-id="d77ef-178">Snap 包</span><span class="sxs-lookup"><span data-stu-id="d77ef-178">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="d77ef-179">查看注释</span><span class="sxs-lookup"><span data-stu-id="d77ef-179">See note</span></span>    | <span data-ttu-id="d77ef-180">查看注释</span><span class="sxs-lookup"><span data-stu-id="d77ef-180">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="d77ef-181">Snap 包的受支持方式与用于运行包的分发一样。</span><span class="sxs-lookup"><span data-stu-id="d77ef-181">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="d77ef-182">PowerShell 版本生命周期结束</span><span class="sxs-lookup"><span data-stu-id="d77ef-182">PowerShell release end of life</span></span>

<span data-ttu-id="d77ef-183">根据 [PowerShell Core 生命周期](#lifecycle-of-powershell-core)，下表列出了停止支持各版本的日期。</span><span class="sxs-lookup"><span data-stu-id="d77ef-183">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="d77ef-184">版本</span><span class="sxs-lookup"><span data-stu-id="d77ef-184">Version</span></span> | <span data-ttu-id="d77ef-185">生命周期结束</span><span class="sxs-lookup"><span data-stu-id="d77ef-185">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="d77ef-186">6.0</span><span class="sxs-lookup"><span data-stu-id="d77ef-186">6.0</span></span>     | <span data-ttu-id="d77ef-187">2019 年 2 月 13 日</span><span class="sxs-lookup"><span data-stu-id="d77ef-187">February 13, 2019</span></span>             |
| <span data-ttu-id="d77ef-188">6.1</span><span class="sxs-lookup"><span data-stu-id="d77ef-188">6.1</span></span>     | <span data-ttu-id="d77ef-189">2019 年 9 月 28 日</span><span class="sxs-lookup"><span data-stu-id="d77ef-189">September 28, 2019</span></span>            |
| <span data-ttu-id="d77ef-190">6.2</span><span class="sxs-lookup"><span data-stu-id="d77ef-190">6.2</span></span>     | <span data-ttu-id="d77ef-191">6.3 发布后的 6 个月后</span><span class="sxs-lookup"><span data-stu-id="d77ef-191">6 months after 6.3 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="d77ef-192">不受支持的平台</span><span class="sxs-lookup"><span data-stu-id="d77ef-192">Platforms, which are out of support</span></span>

<span data-ttu-id="d77ef-193">如果某个平台版本已到达平台所有者定义的生命周期终止日期，PowerShell Core 也会停止支持相应平台版本。</span><span class="sxs-lookup"><span data-stu-id="d77ef-193">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="d77ef-194">以前发布的包对需要访问的客户仍可用，但将不再提供任何种类的正式支持和更新。</span><span class="sxs-lookup"><span data-stu-id="d77ef-194">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="d77ef-195">因此，分发所有者不再支持以下版本。</span><span class="sxs-lookup"><span data-stu-id="d77ef-195">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="d77ef-196">操作系统</span><span class="sxs-lookup"><span data-stu-id="d77ef-196">OS</span></span>       | <span data-ttu-id="d77ef-197">版本</span><span class="sxs-lookup"><span data-stu-id="d77ef-197">Version</span></span> | <span data-ttu-id="d77ef-198">生命周期终止</span><span class="sxs-lookup"><span data-stu-id="d77ef-198">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="d77ef-199">Fedora</span><span class="sxs-lookup"><span data-stu-id="d77ef-199">Fedora</span></span>   | <span data-ttu-id="d77ef-200">24</span><span class="sxs-lookup"><span data-stu-id="d77ef-200">24</span></span>      | [<span data-ttu-id="d77ef-201">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-201">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="d77ef-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="d77ef-202">Fedora</span></span>   | <span data-ttu-id="d77ef-203">25</span><span class="sxs-lookup"><span data-stu-id="d77ef-203">25</span></span>      | [<span data-ttu-id="d77ef-204">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-204">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="d77ef-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="d77ef-205">Fedora</span></span>   | <span data-ttu-id="d77ef-206">26</span><span class="sxs-lookup"><span data-stu-id="d77ef-206">26</span></span>      | [<span data-ttu-id="d77ef-207">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-207">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="d77ef-208">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="d77ef-208">openSUSE</span></span> | <span data-ttu-id="d77ef-209">42.1</span><span class="sxs-lookup"><span data-stu-id="d77ef-209">42.1</span></span>    | [<span data-ttu-id="d77ef-210">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-210">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="d77ef-211">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="d77ef-211">openSUSE</span></span> | <span data-ttu-id="d77ef-212">42.2</span><span class="sxs-lookup"><span data-stu-id="d77ef-212">42.2</span></span>    | [<span data-ttu-id="d77ef-213">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-213">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="d77ef-214">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d77ef-214">Ubuntu</span></span>   | <span data-ttu-id="d77ef-215">16.10</span><span class="sxs-lookup"><span data-stu-id="d77ef-215">16.10</span></span>   | [<span data-ttu-id="d77ef-216">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-216">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="d77ef-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d77ef-217">Ubuntu</span></span>   | <span data-ttu-id="d77ef-218">17.04</span><span class="sxs-lookup"><span data-stu-id="d77ef-218">17.04</span></span>   | [<span data-ttu-id="d77ef-219">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-219">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="d77ef-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d77ef-220">Ubuntu</span></span>   | <span data-ttu-id="d77ef-221">17.10</span><span class="sxs-lookup"><span data-stu-id="d77ef-221">17.10</span></span>   | [<span data-ttu-id="d77ef-222">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-222">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="d77ef-223">Debian</span><span class="sxs-lookup"><span data-stu-id="d77ef-223">Debian</span></span>   | <span data-ttu-id="d77ef-224">8</span><span class="sxs-lookup"><span data-stu-id="d77ef-224">8</span></span>       | [<span data-ttu-id="d77ef-225">2018 年 6 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-225">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="d77ef-226">Fedora</span><span class="sxs-lookup"><span data-stu-id="d77ef-226">Fedora</span></span>   | <span data-ttu-id="d77ef-227">27</span><span class="sxs-lookup"><span data-stu-id="d77ef-227">27</span></span>      | [<span data-ttu-id="d77ef-228">2018 年 11 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-228">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="d77ef-229">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d77ef-229">Ubuntu</span></span>   | <span data-ttu-id="d77ef-230">14.04</span><span class="sxs-lookup"><span data-stu-id="d77ef-230">14.04</span></span>   | [<span data-ttu-id="d77ef-231">2019 年 4 月</span><span class="sxs-lookup"><span data-stu-id="d77ef-231">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="d77ef-232">有关许可的说明</span><span class="sxs-lookup"><span data-stu-id="d77ef-232">Notes on licensing</span></span>

<span data-ttu-id="d77ef-233">PowerShell Core 在 [MIT 许可][] 下发布。</span><span class="sxs-lookup"><span data-stu-id="d77ef-233">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="d77ef-234">根据此许可规定，如果没有付费支持协议，那么用户只能获得[社区支持][]。</span><span class="sxs-lookup"><span data-stu-id="d77ef-234">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="d77ef-235">对于社区支持，Microsoft 无法保证及时作出响应或进行修复。</span><span class="sxs-lookup"><span data-stu-id="d77ef-235">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="d77ef-236">Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="d77ef-236">Windows PowerShell Module</span></span>

<span data-ttu-id="d77ef-237">对 PowerShell Core 的支持不包括产品模块，除非那些模块显式支持 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="d77ef-237">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="d77ef-238">例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。</span><span class="sxs-lookup"><span data-stu-id="d77ef-238">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="d77ef-239">但是，不显式支持 PowerShell Core 的模块在某些情况下可能兼容。</span><span class="sxs-lookup"><span data-stu-id="d77ef-239">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="d77ef-240">通过安装 [`WindowsPSModulePath`][] 模块，可以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="d77ef-240">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="d77ef-241">首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：</span><span class="sxs-lookup"><span data-stu-id="d77ef-241">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="d77ef-242">安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="d77ef-242">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="d77ef-243">实验性功能</span><span class="sxs-lookup"><span data-stu-id="d77ef-243">Experimental features</span></span>

<span data-ttu-id="d77ef-244">[实验性功能][]只能获得[社区支持](#community-support)。</span><span class="sxs-lookup"><span data-stu-id="d77ef-244">[Experimental features][] are limited to [community support](#community-support).</span></span>

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
[实验性功能]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures

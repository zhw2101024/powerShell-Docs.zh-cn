---
title: PowerShell Core 支持生命周期
description: 用于管理 PowerShell Core 支持的策略
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587153"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="d739c-103">PowerShell Core 支持生命周期</span><span class="sxs-lookup"><span data-stu-id="d739c-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="d739c-104">PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。</span><span class="sxs-lookup"><span data-stu-id="d739c-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="d739c-105">因此，PowerShell Core 不包括在 Windows 7/8.1/10 或 Windows Server 许可协议中。</span><span class="sxs-lookup"><span data-stu-id="d739c-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="d739c-106">但是，PowerShell Core 受传统 Microsoft 支持协议支持，此类协议包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。</span><span class="sxs-lookup"><span data-stu-id="d739c-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="d739c-107">还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。</span><span class="sxs-lookup"><span data-stu-id="d739c-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="d739c-108">我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。</span><span class="sxs-lookup"><span data-stu-id="d739c-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="d739c-109">或者，可以从常规 [Microsoft 社区][]或 Microsoft [PowerShell 技术社区][] 的其他成员获取帮助。</span><span class="sxs-lookup"><span data-stu-id="d739c-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="d739c-110">我们不能确保问题能够及时解决。</span><span class="sxs-lookup"><span data-stu-id="d739c-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="d739c-111">如果问题需要立即解决，应使用传统的付费支持选项。</span><span class="sxs-lookup"><span data-stu-id="d739c-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="d739c-112">PowerShell Core 生命周期</span><span class="sxs-lookup"><span data-stu-id="d739c-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="d739c-113">PowerShell Core 采用 [Microsoft 新式声明周期策略][modern]。</span><span class="sxs-lookup"><span data-stu-id="d739c-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="d739c-114">此支持生命周期旨在使客户随时知悉最新版本。</span><span class="sxs-lookup"><span data-stu-id="d739c-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="d739c-115">PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。</span><span class="sxs-lookup"><span data-stu-id="d739c-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d739c-116">必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="d739c-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="d739c-117">例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="d739c-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命周期][lifecycle-chart]

<span data-ttu-id="d739c-119">新式生命周期策略还要求在中止对某产品（例如 PowerShell Core）提供支持前的 12 个月内， Microsoft 需向客户持续提供通知。</span><span class="sxs-lookup"><span data-stu-id="d739c-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="d739c-120">最终，我们希望 PowerShell Core 采取“长期服务”方法，从而只需服务和安全更新即可获取有关 6.x 特定分支/版本的支持。</span><span class="sxs-lookup"><span data-stu-id="d739c-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="d739c-121">支持平台</span><span class="sxs-lookup"><span data-stu-id="d739c-121">Supported platforms</span></span>

<span data-ttu-id="d739c-122">请参阅下表，了解所用 PowerShell Core 版本正式支持哪些平台。</span><span class="sxs-lookup"><span data-stu-id="d739c-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="d739c-123">我们社区也为某些平台提供包，但这些平台不受正式支持。</span><span class="sxs-lookup"><span data-stu-id="d739c-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="d739c-124">这些包在表中标记为 `Community`。</span><span class="sxs-lookup"><span data-stu-id="d739c-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="d739c-125">列为 `Experimental` 的平台不受正式支持，但可用于实验和反馈。</span><span class="sxs-lookup"><span data-stu-id="d739c-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="d739c-126">6.0</span><span class="sxs-lookup"><span data-stu-id="d739c-126">6.0</span></span>         | <span data-ttu-id="d739c-127">6.1</span><span class="sxs-lookup"><span data-stu-id="d739c-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="d739c-128">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="d739c-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="d739c-129">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-129">Supported</span></span>   | <span data-ttu-id="d739c-130">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-130">Supported</span></span>   |
| <span data-ttu-id="d739c-131">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="d739c-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="d739c-132">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-132">Supported</span></span>   | <span data-ttu-id="d739c-133">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-133">Supported</span></span>   |
| <span data-ttu-id="d739c-134">[Windows Server 半年频道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="d739c-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="d739c-135">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-135">Supported</span></span>   | <span data-ttu-id="d739c-136">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-136">Supported</span></span>   |
| <span data-ttu-id="d739c-137">Ubuntu 14.04 和 16.04</span><span class="sxs-lookup"><span data-stu-id="d739c-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="d739c-138">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-138">Supported</span></span>   | <span data-ttu-id="d739c-139">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-139">Supported</span></span>   |
| <span data-ttu-id="d739c-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d739c-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="d739c-141">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-141">Supported</span></span>   |
| <span data-ttu-id="d739c-142">Ubuntu 18.10（使用 Snap 包）</span><span class="sxs-lookup"><span data-stu-id="d739c-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="d739c-143">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-143">Community</span></span>   |
| <span data-ttu-id="d739c-144">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="d739c-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="d739c-145">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-145">Supported</span></span>   | <span data-ttu-id="d739c-146">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-146">Supported</span></span>   |
| <span data-ttu-id="d739c-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d739c-147">CentOS 7</span></span>                                          | <span data-ttu-id="d739c-148">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-148">Supported</span></span>   | <span data-ttu-id="d739c-149">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-149">Supported</span></span>   |
| <span data-ttu-id="d739c-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d739c-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="d739c-151">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-151">Supported</span></span>   | <span data-ttu-id="d739c-152">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-152">Supported</span></span>   |
| <span data-ttu-id="d739c-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d739c-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="d739c-154">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-154">Supported</span></span>   | <span data-ttu-id="d739c-155">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-155">Supported</span></span>   |
| <span data-ttu-id="d739c-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="d739c-156">Fedora 27</span></span>                                         | <span data-ttu-id="d739c-157">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-157">Supported</span></span>   | <span data-ttu-id="d739c-158">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-158">Supported</span></span>   |
| <span data-ttu-id="d739c-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d739c-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="d739c-160">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-160">Supported</span></span>   |
| <span data-ttu-id="d739c-161">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="d739c-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="d739c-162">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-162">Supported</span></span>   | <span data-ttu-id="d739c-163">支持</span><span class="sxs-lookup"><span data-stu-id="d739c-163">Supported</span></span>   |
| <span data-ttu-id="d739c-164">Arch</span><span class="sxs-lookup"><span data-stu-id="d739c-164">Arch</span></span>                                              | <span data-ttu-id="d739c-165">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-165">Community</span></span>   | <span data-ttu-id="d739c-166">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-166">Community</span></span>   |
| <span data-ttu-id="d739c-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="d739c-167">Raspbian</span></span>                                          | <span data-ttu-id="d739c-168">实验</span><span class="sxs-lookup"><span data-stu-id="d739c-168">Experimental</span></span>| <span data-ttu-id="d739c-169">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-169">Community</span></span>   |
| <span data-ttu-id="d739c-170">Kali</span><span class="sxs-lookup"><span data-stu-id="d739c-170">Kali</span></span>                                              | <span data-ttu-id="d739c-171">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-171">Community</span></span>   | <span data-ttu-id="d739c-172">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-172">Community</span></span>   |
| <span data-ttu-id="d739c-173">AppImage（可在多个 Linux 平台上运行）</span><span class="sxs-lookup"><span data-stu-id="d739c-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="d739c-174">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-174">Community</span></span>   | <span data-ttu-id="d739c-175">社区</span><span class="sxs-lookup"><span data-stu-id="d739c-175">Community</span></span>   |
| [<span data-ttu-id="d739c-176">Snap 包</span><span class="sxs-lookup"><span data-stu-id="d739c-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="d739c-177">查看注释</span><span class="sxs-lookup"><span data-stu-id="d739c-177">See note</span></span>    | <span data-ttu-id="d739c-178">查看注释</span><span class="sxs-lookup"><span data-stu-id="d739c-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="d739c-179">将试验 Snap 包一段时间。</span><span class="sxs-lookup"><span data-stu-id="d739c-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="d739c-180">在我们确信 Snap 不会引入新的支持问题后，将支持你当前运行此包的分发。</span><span class="sxs-lookup"><span data-stu-id="d739c-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="d739c-181">不受支持的平台</span><span class="sxs-lookup"><span data-stu-id="d739c-181">Platform which are out of support</span></span>

<span data-ttu-id="d739c-182">如果平台版本达到平台所有者定义的生命周期终止，PowerShell Core 也会不再支持相应平台版本。</span><span class="sxs-lookup"><span data-stu-id="d739c-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="d739c-183">以前发布的包对需要访问的客户仍可用，但将不再提供任何种类的正式支持和更新。</span><span class="sxs-lookup"><span data-stu-id="d739c-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="d739c-184">因此，分发所有者不再支持以下版本，它们不受支持。</span><span class="sxs-lookup"><span data-stu-id="d739c-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="d739c-185">操作系统</span><span class="sxs-lookup"><span data-stu-id="d739c-185">OS</span></span>       | <span data-ttu-id="d739c-186">版本</span><span class="sxs-lookup"><span data-stu-id="d739c-186">Version</span></span> | <span data-ttu-id="d739c-187">生命周期终止</span><span class="sxs-lookup"><span data-stu-id="d739c-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="d739c-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="d739c-188">Fedora</span></span>   | <span data-ttu-id="d739c-189">24</span><span class="sxs-lookup"><span data-stu-id="d739c-189">24</span></span>      | [<span data-ttu-id="d739c-190">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="d739c-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="d739c-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="d739c-191">Fedora</span></span>   | <span data-ttu-id="d739c-192">25</span><span class="sxs-lookup"><span data-stu-id="d739c-192">25</span></span>      | [<span data-ttu-id="d739c-193">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="d739c-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="d739c-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="d739c-194">Fedora</span></span>   | <span data-ttu-id="d739c-195">26</span><span class="sxs-lookup"><span data-stu-id="d739c-195">26</span></span>      | [<span data-ttu-id="d739c-196">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="d739c-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="d739c-197">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="d739c-197">openSUSE</span></span> | <span data-ttu-id="d739c-198">42.1</span><span class="sxs-lookup"><span data-stu-id="d739c-198">42.1</span></span>    | [<span data-ttu-id="d739c-199">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="d739c-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="d739c-200">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="d739c-200">openSUSE</span></span> | <span data-ttu-id="d739c-201">42.2</span><span class="sxs-lookup"><span data-stu-id="d739c-201">42.2</span></span>    | [<span data-ttu-id="d739c-202">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="d739c-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="d739c-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d739c-203">Ubuntu</span></span>   | <span data-ttu-id="d739c-204">16.10</span><span class="sxs-lookup"><span data-stu-id="d739c-204">16.10</span></span>   | [<span data-ttu-id="d739c-205">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="d739c-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="d739c-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d739c-206">Ubuntu</span></span>   | <span data-ttu-id="d739c-207">17.04</span><span class="sxs-lookup"><span data-stu-id="d739c-207">17.04</span></span>   | [<span data-ttu-id="d739c-208">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="d739c-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="d739c-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d739c-209">Ubuntu</span></span>   | <span data-ttu-id="d739c-210">17.10</span><span class="sxs-lookup"><span data-stu-id="d739c-210">17.10</span></span>   | [<span data-ttu-id="d739c-211">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="d739c-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="d739c-212">有关许可的说明</span><span class="sxs-lookup"><span data-stu-id="d739c-212">Notes on licensing</span></span>

<span data-ttu-id="d739c-213">PowerShell Core 在 [MIT 许可][] 下发布。</span><span class="sxs-lookup"><span data-stu-id="d739c-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="d739c-214">根据此许可规定，如果缺失付费支持协议，则用户仅限于获取[社区支持][]。</span><span class="sxs-lookup"><span data-stu-id="d739c-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="d739c-215">对于社区支持，Microsoft 无法保证及时作出响应或进行修复。</span><span class="sxs-lookup"><span data-stu-id="d739c-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="d739c-216">Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="d739c-216">Windows PowerShell Module</span></span>

<span data-ttu-id="d739c-217">对 PowerShell Core 的支持不扩展到其他产品模块，除非那些产品模块显式支持 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="d739c-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="d739c-218">例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。</span><span class="sxs-lookup"><span data-stu-id="d739c-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="d739c-219">但是，不显式支持 PowerShell Core 的模块在某些情况下可能兼容。</span><span class="sxs-lookup"><span data-stu-id="d739c-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="d739c-220">通过安装 [`WindowsPSModulePath`][] 模块，可以将 Windows PowerShell `PSModulePath` 追加到 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="d739c-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="d739c-221">首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：</span><span class="sxs-lookup"><span data-stu-id="d739c-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="d739c-222">安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="d739c-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

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

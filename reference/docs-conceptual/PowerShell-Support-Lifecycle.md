---
title: PowerShell Core 支持生命周期
description: 用于管理 PowerShell Core 支持的策略
ms.date: 08/06/2018
ms.openlocfilehash: 57804df830da01bee0f48acc374658b025a46b85
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022236"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="06c0d-103">PowerShell Core 支持生命周期</span><span class="sxs-lookup"><span data-stu-id="06c0d-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="06c0d-104">PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。</span><span class="sxs-lookup"><span data-stu-id="06c0d-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span> <span data-ttu-id="06c0d-105">因此，PowerShell Core 不包括在 Windows 7/8.1/10 或 Windows Server 许可协议中。</span><span class="sxs-lookup"><span data-stu-id="06c0d-105">So, PowerShell Core isn't included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="06c0d-106">不过，PowerShell Core 受传统 Microsoft 支持协议支持，包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。</span><span class="sxs-lookup"><span data-stu-id="06c0d-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="06c0d-107">还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。</span><span class="sxs-lookup"><span data-stu-id="06c0d-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="06c0d-108">社区支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-108">Community Support</span></span>

<span data-ttu-id="06c0d-109">我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。</span><span class="sxs-lookup"><span data-stu-id="06c0d-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="06c0d-110">此外，你还可以从 Microsoft [PowerShell 技术社区][]或 [PowerShell][pshub] 中心页的社区部分列出的任何论坛中获得社区其他成员的帮助。</span><span class="sxs-lookup"><span data-stu-id="06c0d-110">Also, you may find help from other members of the community in the Microsoft [PowerShell Tech Community][] or any of the forums listed in the community section of [PowerShell][pshub] hub page.</span></span> <span data-ttu-id="06c0d-111">我们不能确保社区能够及时解决问题。</span><span class="sxs-lookup"><span data-stu-id="06c0d-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span> <span data-ttu-id="06c0d-112">如果问题需要立即解决，应使用传统的付费支持选项。</span><span class="sxs-lookup"><span data-stu-id="06c0d-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="06c0d-113">PowerShell Core 生命周期</span><span class="sxs-lookup"><span data-stu-id="06c0d-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="06c0d-114">PowerShell Core 即将采用 [Microsoft 新式生命周期策略][modern]。</span><span class="sxs-lookup"><span data-stu-id="06c0d-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span> <span data-ttu-id="06c0d-115">此支持生命周期旨在使客户随时知悉最新版本。</span><span class="sxs-lookup"><span data-stu-id="06c0d-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="06c0d-116">PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。</span><span class="sxs-lookup"><span data-stu-id="06c0d-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06c0d-117">必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="06c0d-118">例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06c0d-119">必须在每个新修补程序版本发布后的 30 天之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="06c0d-120">例如，若要运行 PowerShell Core 6.1，且 6.1.3 已于 2019 年 2 月 19 日发布，应在发布后的 30 天之内（即 2019 年 3 月 21 日前）更新到 PowerShell Core 6.1.3，更新后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-120">For example, If you're running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span> <span data-ttu-id="06c0d-121">如果发现需要任何修补程序，则将在下一次累积更新中发布修补程序。</span><span class="sxs-lookup"><span data-stu-id="06c0d-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="06c0d-122">新式生命周期策略还要求，在中止对某产品（即 PowerShell Core）提供支持前的 12 个月内，Microsoft 需向客户持续提供通知。</span><span class="sxs-lookup"><span data-stu-id="06c0d-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="06c0d-123">最终，我们预计 PowerShell Core 将采用长期服务方法。</span><span class="sxs-lookup"><span data-stu-id="06c0d-123">Eventually, we expect PowerShell Core will adopt the long-term servicing approach.</span></span> <span data-ttu-id="06c0d-124">在此服务方法中，只需服务和安全更新即可获取有关 6.x 特定分支/版本的支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="06c0d-125">支持的平台</span><span class="sxs-lookup"><span data-stu-id="06c0d-125">Supported platforms</span></span>

<span data-ttu-id="06c0d-126">若要确认你的 PowerShell Core 平台和版本是否受到官方支持，请参阅下表。</span><span class="sxs-lookup"><span data-stu-id="06c0d-126">To confirm if your platform and version of PowerShell Core are officially supported, see the following table.</span></span>

<span data-ttu-id="06c0d-127">我们的社区也为一些平台提供了包，但它们不受官方支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-127">Our community has also contributed packages for some platforms, but they aren't officially supported.</span></span> <span data-ttu-id="06c0d-128">这些包在表中标记为 `Community`。</span><span class="sxs-lookup"><span data-stu-id="06c0d-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="06c0d-129">列为 `Experimental` 的平台不受官方支持，但可用于实验和反馈。</span><span class="sxs-lookup"><span data-stu-id="06c0d-129">Platforms listed as `Experimental` aren't officially supported, but are available for experimentation and feedback.</span></span>

| <span data-ttu-id="06c0d-130">平台</span><span class="sxs-lookup"><span data-stu-id="06c0d-130">Platform</span></span>                                          |      <span data-ttu-id="06c0d-131">6.2</span><span class="sxs-lookup"><span data-stu-id="06c0d-131">6.2</span></span>      |    <span data-ttu-id="06c0d-132">7.0</span><span class="sxs-lookup"><span data-stu-id="06c0d-132">7.0</span></span>    |
|---------------------------------------------------|:-------------:|:---------:|
| <span data-ttu-id="06c0d-133">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="06c0d-133">Windows 7, 8.1, and 10</span></span>                            |   <span data-ttu-id="06c0d-134">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-134">Supported</span></span>   | <span data-ttu-id="06c0d-135">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-135">Supported</span></span> |
| <span data-ttu-id="06c0d-136">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="06c0d-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             |   <span data-ttu-id="06c0d-137">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-137">Supported</span></span>   | <span data-ttu-id="06c0d-138">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-138">Supported</span></span> |
| <span data-ttu-id="06c0d-139">[Windows Server 半年频道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="06c0d-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> |   <span data-ttu-id="06c0d-140">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-140">Supported</span></span>   | <span data-ttu-id="06c0d-141">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-141">Supported</span></span> |
| <span data-ttu-id="06c0d-142">Ubuntu 16.04 和 18.04</span><span class="sxs-lookup"><span data-stu-id="06c0d-142">Ubuntu 16.04 and 18.04</span></span>                            |   <span data-ttu-id="06c0d-143">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-143">Supported</span></span>   | <span data-ttu-id="06c0d-144">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-144">Supported</span></span> |
| <span data-ttu-id="06c0d-145">Ubuntu 18.10（使用 Snap 包）</span><span class="sxs-lookup"><span data-stu-id="06c0d-145">Ubuntu 18.10 (via Snap Package)</span></span>                   |   <span data-ttu-id="06c0d-146">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-146">Community</span></span>   | <span data-ttu-id="06c0d-147">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-147">Community</span></span> |
| <span data-ttu-id="06c0d-148">Ubuntu 19.04（通过 Snap 包）</span><span class="sxs-lookup"><span data-stu-id="06c0d-148">Ubuntu 19.04 (via Snap Package)</span></span>                   |   <span data-ttu-id="06c0d-149">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-149">Community</span></span>   | <span data-ttu-id="06c0d-150">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-150">Community</span></span> |
| <span data-ttu-id="06c0d-151">Debian 9</span><span class="sxs-lookup"><span data-stu-id="06c0d-151">Debian 9</span></span>                                          |   <span data-ttu-id="06c0d-152">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-152">Supported</span></span>   | <span data-ttu-id="06c0d-153">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-153">Supported</span></span> |
| <span data-ttu-id="06c0d-154">Debian 10</span><span class="sxs-lookup"><span data-stu-id="06c0d-154">Debian 10</span></span>                                         | <span data-ttu-id="06c0d-155">不支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-155">Not Supported</span></span> | <span data-ttu-id="06c0d-156">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-156">Supported</span></span> |
| <span data-ttu-id="06c0d-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="06c0d-157">CentOS 7</span></span>                                          |   <span data-ttu-id="06c0d-158">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-158">Supported</span></span>   | <span data-ttu-id="06c0d-159">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-159">Supported</span></span> |
| <span data-ttu-id="06c0d-160">CentOS 8</span><span class="sxs-lookup"><span data-stu-id="06c0d-160">CentOS 8</span></span>                                          | <span data-ttu-id="06c0d-161">不支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-161">Not Supported</span></span> | <span data-ttu-id="06c0d-162">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-162">Supported</span></span> |
| <span data-ttu-id="06c0d-163">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="06c0d-163">Red Hat Enterprise Linux 7</span></span>                        |   <span data-ttu-id="06c0d-164">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-164">Supported</span></span>   | <span data-ttu-id="06c0d-165">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-165">Supported</span></span> |
| <span data-ttu-id="06c0d-166">Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="06c0d-166">Red Hat Enterprise Linux 8</span></span>                        | <span data-ttu-id="06c0d-167">不支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-167">Not Supported</span></span> | <span data-ttu-id="06c0d-168">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-168">Supported</span></span> |
| <span data-ttu-id="06c0d-169">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="06c0d-169">openSUSE 42.3</span></span>                                     |   <span data-ttu-id="06c0d-170">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-170">Supported</span></span>   | <span data-ttu-id="06c0d-171">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-171">Supported</span></span> |
| <span data-ttu-id="06c0d-172">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="06c0d-172">Fedora 28</span></span>                                         |   <span data-ttu-id="06c0d-173">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-173">Supported</span></span>   | <span data-ttu-id="06c0d-174">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-174">Supported</span></span> |
| <span data-ttu-id="06c0d-175">Fedora 29、Fedora 30</span><span class="sxs-lookup"><span data-stu-id="06c0d-175">Fedora 29, 30</span></span>                                     | <span data-ttu-id="06c0d-176">不支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-176">Not Supported</span></span> | <span data-ttu-id="06c0d-177">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-177">Supported</span></span> |
| <span data-ttu-id="06c0d-178">Alpine 3.8</span><span class="sxs-lookup"><span data-stu-id="06c0d-178">Alpine 3.8</span></span>                                        |   <span data-ttu-id="06c0d-179">请参阅备注</span><span class="sxs-lookup"><span data-stu-id="06c0d-179">See Note</span></span>    | <span data-ttu-id="06c0d-180">请参阅备注</span><span class="sxs-lookup"><span data-stu-id="06c0d-180">See Note</span></span>  |
| <span data-ttu-id="06c0d-181">Alpine 3.9 和 Alpine 3.10</span><span class="sxs-lookup"><span data-stu-id="06c0d-181">Alpine 3.9 and 3.10</span></span>                               | <span data-ttu-id="06c0d-182">不支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-182">Not Supported</span></span> | <span data-ttu-id="06c0d-183">请参阅备注</span><span class="sxs-lookup"><span data-stu-id="06c0d-183">See Note</span></span>  |
| <span data-ttu-id="06c0d-184">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="06c0d-184">macOS 10.12+</span></span>                                      |   <span data-ttu-id="06c0d-185">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-185">Supported</span></span>   | <span data-ttu-id="06c0d-186">支持</span><span class="sxs-lookup"><span data-stu-id="06c0d-186">Supported</span></span> |
| <span data-ttu-id="06c0d-187">Arch</span><span class="sxs-lookup"><span data-stu-id="06c0d-187">Arch</span></span>                                              |   <span data-ttu-id="06c0d-188">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-188">Community</span></span>   | <span data-ttu-id="06c0d-189">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-189">Community</span></span> |
| <span data-ttu-id="06c0d-190">Raspbian</span><span class="sxs-lookup"><span data-stu-id="06c0d-190">Raspbian</span></span>                                          |   <span data-ttu-id="06c0d-191">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-191">Community</span></span>   | <span data-ttu-id="06c0d-192">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-192">Community</span></span> |
| <span data-ttu-id="06c0d-193">Kali</span><span class="sxs-lookup"><span data-stu-id="06c0d-193">Kali</span></span>                                              |   <span data-ttu-id="06c0d-194">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-194">Community</span></span>   | <span data-ttu-id="06c0d-195">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-195">Community</span></span> |
| <span data-ttu-id="06c0d-196">AppImage（可在多个 Linux 平台上运行）</span><span class="sxs-lookup"><span data-stu-id="06c0d-196">AppImage (works on multiple Linux platforms)</span></span>      |   <span data-ttu-id="06c0d-197">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-197">Community</span></span>   | <span data-ttu-id="06c0d-198">社区</span><span class="sxs-lookup"><span data-stu-id="06c0d-198">Community</span></span> |
| [<span data-ttu-id="06c0d-199">Snap 包</span><span class="sxs-lookup"><span data-stu-id="06c0d-199">Snap Package</span></span>](https://snapcraft.io/powershell)   |   <span data-ttu-id="06c0d-200">查看注释</span><span class="sxs-lookup"><span data-stu-id="06c0d-200">See note</span></span>    | <span data-ttu-id="06c0d-201">查看注释</span><span class="sxs-lookup"><span data-stu-id="06c0d-201">See note</span></span>  |

> [!NOTE]
> <span data-ttu-id="06c0d-202">Snap 包与正在运行此包的发行版受到相同的支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-202">Snap packages are supported the same as the distribution you're running the package on.</span></span>

> [!NOTE]
> <span data-ttu-id="06c0d-203">Alpine 不支持 CIM、PowerShell 远程处理和 DSC。</span><span class="sxs-lookup"><span data-stu-id="06c0d-203">CIM, PowerShell Remoting, and DSC are not supported on Alpine.</span></span>

## <a name="powershell-releases-end-of-life"></a><span data-ttu-id="06c0d-204">PowerShell 版本生命周期终止日期</span><span class="sxs-lookup"><span data-stu-id="06c0d-204">PowerShell releases end-of-life</span></span>

<span data-ttu-id="06c0d-205">根据 [PowerShell Core 生命周期](#lifecycle-of-powershell-core)，下表列出了各个版本不再受支持的日期。</span><span class="sxs-lookup"><span data-stu-id="06c0d-205">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various releases will no longer be supported.</span></span>

| <span data-ttu-id="06c0d-206">版本</span><span class="sxs-lookup"><span data-stu-id="06c0d-206">Version</span></span> | <span data-ttu-id="06c0d-207">生命周期终止日期</span><span class="sxs-lookup"><span data-stu-id="06c0d-207">End-of-life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="06c0d-208">6.0</span><span class="sxs-lookup"><span data-stu-id="06c0d-208">6.0</span></span>     | <span data-ttu-id="06c0d-209">2019 年 2 月 13 日</span><span class="sxs-lookup"><span data-stu-id="06c0d-209">February 13, 2019</span></span>             |
| <span data-ttu-id="06c0d-210">6.1</span><span class="sxs-lookup"><span data-stu-id="06c0d-210">6.1</span></span>     | <span data-ttu-id="06c0d-211">2019 年 9 月 28 日</span><span class="sxs-lookup"><span data-stu-id="06c0d-211">September 28, 2019</span></span>            |
| <span data-ttu-id="06c0d-212">6.2</span><span class="sxs-lookup"><span data-stu-id="06c0d-212">6.2</span></span>     | <span data-ttu-id="06c0d-213">7 发布后的 6 个月后</span><span class="sxs-lookup"><span data-stu-id="06c0d-213">6 months after 7 releases</span></span>     |

## <a name="unsupported-platforms"></a><span data-ttu-id="06c0d-214">不支持的平台</span><span class="sxs-lookup"><span data-stu-id="06c0d-214">Unsupported platforms</span></span>

<span data-ttu-id="06c0d-215">如果某个平台版本已到达平台所有者定义的生命周期终止日期，PowerShell Core 也会停止支持相应平台版本。</span><span class="sxs-lookup"><span data-stu-id="06c0d-215">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span> <span data-ttu-id="06c0d-216">以前发布的包对需要访问的客户仍可用，但将不再提供任何种类的正式支持和更新。</span><span class="sxs-lookup"><span data-stu-id="06c0d-216">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="06c0d-217">因此，发行版所有者不再支持以下版本，它们不受支持。</span><span class="sxs-lookup"><span data-stu-id="06c0d-217">So, the distribution owners ended support for the following versions and aren't supported.</span></span>

| <span data-ttu-id="06c0d-218">平台</span><span class="sxs-lookup"><span data-stu-id="06c0d-218">Platform</span></span> | <span data-ttu-id="06c0d-219">版本</span><span class="sxs-lookup"><span data-stu-id="06c0d-219">Version</span></span> | <span data-ttu-id="06c0d-220">生命周期终止</span><span class="sxs-lookup"><span data-stu-id="06c0d-220">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="06c0d-221">Fedora</span><span class="sxs-lookup"><span data-stu-id="06c0d-221">Fedora</span></span>   | <span data-ttu-id="06c0d-222">24</span><span class="sxs-lookup"><span data-stu-id="06c0d-222">24</span></span>      | [<span data-ttu-id="06c0d-223">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-223">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="06c0d-224">Fedora</span><span class="sxs-lookup"><span data-stu-id="06c0d-224">Fedora</span></span>   | <span data-ttu-id="06c0d-225">25</span><span class="sxs-lookup"><span data-stu-id="06c0d-225">25</span></span>      | [<span data-ttu-id="06c0d-226">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-226">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="06c0d-227">Fedora</span><span class="sxs-lookup"><span data-stu-id="06c0d-227">Fedora</span></span>   | <span data-ttu-id="06c0d-228">26</span><span class="sxs-lookup"><span data-stu-id="06c0d-228">26</span></span>      | [<span data-ttu-id="06c0d-229">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-229">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="06c0d-230">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="06c0d-230">openSUSE</span></span> | <span data-ttu-id="06c0d-231">42.1</span><span class="sxs-lookup"><span data-stu-id="06c0d-231">42.1</span></span>    | [<span data-ttu-id="06c0d-232">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-232">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="06c0d-233">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="06c0d-233">openSUSE</span></span> | <span data-ttu-id="06c0d-234">42.2</span><span class="sxs-lookup"><span data-stu-id="06c0d-234">42.2</span></span>    | [<span data-ttu-id="06c0d-235">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-235">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="06c0d-236">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="06c0d-236">Ubuntu</span></span>   | <span data-ttu-id="06c0d-237">16.10</span><span class="sxs-lookup"><span data-stu-id="06c0d-237">16.10</span></span>   | [<span data-ttu-id="06c0d-238">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-238">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="06c0d-239">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="06c0d-239">Ubuntu</span></span>   | <span data-ttu-id="06c0d-240">17.04</span><span class="sxs-lookup"><span data-stu-id="06c0d-240">17.04</span></span>   | [<span data-ttu-id="06c0d-241">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-241">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="06c0d-242">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="06c0d-242">Ubuntu</span></span>   | <span data-ttu-id="06c0d-243">17.1</span><span class="sxs-lookup"><span data-stu-id="06c0d-243">17.10</span></span>   | [<span data-ttu-id="06c0d-244">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-244">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="06c0d-245">Debian</span><span class="sxs-lookup"><span data-stu-id="06c0d-245">Debian</span></span>   | <span data-ttu-id="06c0d-246">8</span><span class="sxs-lookup"><span data-stu-id="06c0d-246">8</span></span>       | [<span data-ttu-id="06c0d-247">2018 年 6 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-247">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="06c0d-248">Fedora</span><span class="sxs-lookup"><span data-stu-id="06c0d-248">Fedora</span></span>   | <span data-ttu-id="06c0d-249">27</span><span class="sxs-lookup"><span data-stu-id="06c0d-249">27</span></span>      | [<span data-ttu-id="06c0d-250">2018 年 11 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-250">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="06c0d-251">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="06c0d-251">Ubuntu</span></span>   | <span data-ttu-id="06c0d-252">14.04</span><span class="sxs-lookup"><span data-stu-id="06c0d-252">14.04</span></span>   | [<span data-ttu-id="06c0d-253">2019 年 4 月</span><span class="sxs-lookup"><span data-stu-id="06c0d-253">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="06c0d-254">有关许可的说明</span><span class="sxs-lookup"><span data-stu-id="06c0d-254">Notes on licensing</span></span>

<span data-ttu-id="06c0d-255">PowerShell Core 在 [MIT 许可][] 下发布。</span><span class="sxs-lookup"><span data-stu-id="06c0d-255">PowerShell Core is released under the [MIT license][].</span></span> <span data-ttu-id="06c0d-256">根据此许可规定，如果没有付费支持协议，那么用户只能获得[社区支持][]。</span><span class="sxs-lookup"><span data-stu-id="06c0d-256">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span> <span data-ttu-id="06c0d-257">对于社区支持，Microsoft 无法保证及时作出响应或进行修复。</span><span class="sxs-lookup"><span data-stu-id="06c0d-257">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="06c0d-258">Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="06c0d-258">Windows PowerShell Module</span></span>

<span data-ttu-id="06c0d-259">对 PowerShell Core 的支持不包括产品模块，除非这些模块显式支持 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="06c0d-259">Support for PowerShell Core doesn't include product modules, unless those modules explicitly support PowerShell Core.</span></span> <span data-ttu-id="06c0d-260">例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。</span><span class="sxs-lookup"><span data-stu-id="06c0d-260">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="06c0d-261">不过，在某些情况下，不显式支持 PowerShell Core 的模块可能是兼容的。</span><span class="sxs-lookup"><span data-stu-id="06c0d-261">However, modules that don't explicitly support PowerShell Core may be compatible in some cases.</span></span> <span data-ttu-id="06c0d-262">通过安装 [WindowsPSModulePath][] 模块，可以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="06c0d-262">By installing the [WindowsPSModulePath][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="06c0d-263">首先，安装来自 PowerShell 库的 WindowsPSModulePath  模块：</span><span class="sxs-lookup"><span data-stu-id="06c0d-263">First, install the **WindowsPSModulePath** module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="06c0d-264">安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="06c0d-264">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="06c0d-265">实验性功能</span><span class="sxs-lookup"><span data-stu-id="06c0d-265">Experimental features</span></span>

<span data-ttu-id="06c0d-266">[实验性功能][]只能获得[社区支持](#community-support)。</span><span class="sxs-lookup"><span data-stu-id="06c0d-266">[Experimental features][] are limited to [community support](#community-support).</span></span>

[顶级]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[社区支持]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[pshub]: https://docs.microsoft.com/powershell
[PowerShell 技术社区]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[辅助支持]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 许可]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[实验性功能]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures

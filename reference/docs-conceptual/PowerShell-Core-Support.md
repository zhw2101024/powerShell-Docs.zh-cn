# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="899fc-101">PowerShell Core 支持生命周期</span><span class="sxs-lookup"><span data-stu-id="899fc-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="899fc-102">PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。</span><span class="sxs-lookup"><span data-stu-id="899fc-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="899fc-103">因此，PowerShell Core 不包括在 Windows 7/8.1/10 或 Windows Server 许可协议中。</span><span class="sxs-lookup"><span data-stu-id="899fc-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="899fc-104">但是，PowerShell Core 受传统 Microsoft 支持协议支持，此类协议包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。</span><span class="sxs-lookup"><span data-stu-id="899fc-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="899fc-105">还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。</span><span class="sxs-lookup"><span data-stu-id="899fc-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="899fc-106">我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。</span><span class="sxs-lookup"><span data-stu-id="899fc-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="899fc-107">或者，可以从常规 [Microsoft 社区][]或 Microsoft [PowerShell 技术社区][] 的其他成员获取帮助。</span><span class="sxs-lookup"><span data-stu-id="899fc-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="899fc-108">我们不能确保问题能够及时解决。</span><span class="sxs-lookup"><span data-stu-id="899fc-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="899fc-109">如果问题需要立即解决，应使用传统的付费支持选项。</span><span class="sxs-lookup"><span data-stu-id="899fc-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="899fc-110">PowerShell Core 生命周期</span><span class="sxs-lookup"><span data-stu-id="899fc-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="899fc-111">PowerShell Core 采用 [Microsoft 新式声明周期策略][modern]。</span><span class="sxs-lookup"><span data-stu-id="899fc-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="899fc-112">此支持生命周期旨在使客户随时知悉最新版本。</span><span class="sxs-lookup"><span data-stu-id="899fc-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="899fc-113">PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。</span><span class="sxs-lookup"><span data-stu-id="899fc-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="899fc-114">必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="899fc-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="899fc-115">例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="899fc-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命周期][lifecycle-chart]

<span data-ttu-id="899fc-117">新式生命周期策略还要求在中止对某产品（例如 PowerShell Core）提供支持前的 12 个月内， Microsoft 需向客户持续提供通知。</span><span class="sxs-lookup"><span data-stu-id="899fc-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="899fc-118">最终，我们希望 PowerShell Core 采取“长期服务”方法，从而只需服务和安全更新即可获取有关 6.x 特定分支/版本的支持。</span><span class="sxs-lookup"><span data-stu-id="899fc-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="899fc-119">支持平台</span><span class="sxs-lookup"><span data-stu-id="899fc-119">Supported platforms</span></span>

<span data-ttu-id="899fc-120">请参阅下表，了解所用 PowerShell Core 版本正式支持哪些平台。</span><span class="sxs-lookup"><span data-stu-id="899fc-120">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="899fc-121">我们社区也为某些平台提供包，但这些平台不受正式支持。</span><span class="sxs-lookup"><span data-stu-id="899fc-121">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="899fc-122">这些包在表中标记为 `Community`。</span><span class="sxs-lookup"><span data-stu-id="899fc-122">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="899fc-123">列为 `Experimental` 的平台不受正式支持，但可用于实验和反馈。</span><span class="sxs-lookup"><span data-stu-id="899fc-123">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="899fc-124">6.0</span><span class="sxs-lookup"><span data-stu-id="899fc-124">6.0</span></span>         | <span data-ttu-id="899fc-125">6.1</span><span class="sxs-lookup"><span data-stu-id="899fc-125">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="899fc-126">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="899fc-126">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="899fc-127">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-127">Supported</span></span>   | <span data-ttu-id="899fc-128">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-128">Supported</span></span>   |
| <span data-ttu-id="899fc-129">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="899fc-129">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="899fc-130">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-130">Supported</span></span>   | <span data-ttu-id="899fc-131">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-131">Supported</span></span>   |
| <span data-ttu-id="899fc-132">[Windows Server 半年频道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="899fc-132">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="899fc-133">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-133">Supported</span></span>   | <span data-ttu-id="899fc-134">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-134">Supported</span></span>   |
| <span data-ttu-id="899fc-135">Ubuntu 14.04 和 16.04</span><span class="sxs-lookup"><span data-stu-id="899fc-135">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="899fc-136">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-136">Supported</span></span>   | <span data-ttu-id="899fc-137">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-137">Supported</span></span>   |
| <span data-ttu-id="899fc-138">Ubuntu 17.10 和 18.04</span><span class="sxs-lookup"><span data-stu-id="899fc-138">Ubuntu 17.10, and 18.04</span></span>                           |             | <span data-ttu-id="899fc-139">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-139">Supported</span></span>   |
| <span data-ttu-id="899fc-140">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="899fc-140">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="899fc-141">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-141">Supported</span></span>   | <span data-ttu-id="899fc-142">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-142">Supported</span></span>   |
| <span data-ttu-id="899fc-143">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="899fc-143">CentOS 7</span></span>                                          | <span data-ttu-id="899fc-144">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-144">Supported</span></span>   | <span data-ttu-id="899fc-145">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-145">Supported</span></span>   |
| <span data-ttu-id="899fc-146">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="899fc-146">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="899fc-147">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-147">Supported</span></span>   | <span data-ttu-id="899fc-148">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-148">Supported</span></span>   |
| <span data-ttu-id="899fc-149">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="899fc-149">OpenSUSE 42.2</span></span>                                     | <span data-ttu-id="899fc-150">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-150">Supported</span></span>   | <span data-ttu-id="899fc-151">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-151">Supported</span></span>   |
| <span data-ttu-id="899fc-152">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="899fc-152">Fedora 27</span></span>                                         | <span data-ttu-id="899fc-153">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-153">Supported</span></span>   | <span data-ttu-id="899fc-154">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-154">Supported</span></span>   |
| <span data-ttu-id="899fc-155">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="899fc-155">Fedora 28</span></span>                                         |             | <span data-ttu-id="899fc-156">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-156">Supported</span></span>   |
| <span data-ttu-id="899fc-157">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="899fc-157">macOS 10.12+</span></span>                                      | <span data-ttu-id="899fc-158">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-158">Supported</span></span>   | <span data-ttu-id="899fc-159">支持</span><span class="sxs-lookup"><span data-stu-id="899fc-159">Supported</span></span>   |
| <span data-ttu-id="899fc-160">Arch</span><span class="sxs-lookup"><span data-stu-id="899fc-160">Arch</span></span>                                              | <span data-ttu-id="899fc-161">社区</span><span class="sxs-lookup"><span data-stu-id="899fc-161">Community</span></span>   | <span data-ttu-id="899fc-162">社区</span><span class="sxs-lookup"><span data-stu-id="899fc-162">Community</span></span>   |
| <span data-ttu-id="899fc-163">Raspbian</span><span class="sxs-lookup"><span data-stu-id="899fc-163">Raspbian</span></span>                                          | <span data-ttu-id="899fc-164">实验</span><span class="sxs-lookup"><span data-stu-id="899fc-164">Experimental</span></span>| <span data-ttu-id="899fc-165">社区</span><span class="sxs-lookup"><span data-stu-id="899fc-165">Community</span></span>   |
| <span data-ttu-id="899fc-166">Kali</span><span class="sxs-lookup"><span data-stu-id="899fc-166">Kali</span></span>                                              | <span data-ttu-id="899fc-167">社区</span><span class="sxs-lookup"><span data-stu-id="899fc-167">Community</span></span>   | <span data-ttu-id="899fc-168">社区</span><span class="sxs-lookup"><span data-stu-id="899fc-168">Community</span></span>   |
| <span data-ttu-id="899fc-169">AppImage（可在多个 Linux 平台上运行）</span><span class="sxs-lookup"><span data-stu-id="899fc-169">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="899fc-170">社区</span><span class="sxs-lookup"><span data-stu-id="899fc-170">Community</span></span>   | <span data-ttu-id="899fc-171">社区</span><span class="sxs-lookup"><span data-stu-id="899fc-171">Community</span></span>   |

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="899fc-172">不受支持的平台</span><span class="sxs-lookup"><span data-stu-id="899fc-172">Platform which are out of support</span></span>

<span data-ttu-id="899fc-173">如果平台版本达到平台所有者定义的生命周期终止，PowerShell Core 也会不再支持相应平台版本。</span><span class="sxs-lookup"><span data-stu-id="899fc-173">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="899fc-174">以前发布的包对需要访问的客户仍可用，但将不再提供任何种类的正式支持和更新。</span><span class="sxs-lookup"><span data-stu-id="899fc-174">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="899fc-175">因此，分发所有者不再支持以下版本，它们不受支持。</span><span class="sxs-lookup"><span data-stu-id="899fc-175">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="899fc-176">操作系统</span><span class="sxs-lookup"><span data-stu-id="899fc-176">OS</span></span>       | <span data-ttu-id="899fc-177">版本</span><span class="sxs-lookup"><span data-stu-id="899fc-177">Version</span></span> | <span data-ttu-id="899fc-178">生命周期终止</span><span class="sxs-lookup"><span data-stu-id="899fc-178">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="899fc-179">Fedora</span><span class="sxs-lookup"><span data-stu-id="899fc-179">Fedora</span></span>   | <span data-ttu-id="899fc-180">26</span><span class="sxs-lookup"><span data-stu-id="899fc-180">26</span></span>      | [<span data-ttu-id="899fc-181">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="899fc-181">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="899fc-182">Fedora</span><span class="sxs-lookup"><span data-stu-id="899fc-182">Fedora</span></span>   | <span data-ttu-id="899fc-183">25</span><span class="sxs-lookup"><span data-stu-id="899fc-183">25</span></span>      | [<span data-ttu-id="899fc-184">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="899fc-184">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="899fc-185">Fedora</span><span class="sxs-lookup"><span data-stu-id="899fc-185">Fedora</span></span>   | <span data-ttu-id="899fc-186">24</span><span class="sxs-lookup"><span data-stu-id="899fc-186">24</span></span>      | [<span data-ttu-id="899fc-187">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="899fc-187">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="899fc-188">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="899fc-188">openSUSE</span></span> | <span data-ttu-id="899fc-189">42.2</span><span class="sxs-lookup"><span data-stu-id="899fc-189">42.2</span></span>    | [<span data-ttu-id="899fc-190">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="899fc-190">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="899fc-191">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="899fc-191">openSUSE</span></span> | <span data-ttu-id="899fc-192">42.1</span><span class="sxs-lookup"><span data-stu-id="899fc-192">42.1</span></span>    | [<span data-ttu-id="899fc-193">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="899fc-193">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="899fc-194">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="899fc-194">Ubuntu</span></span>   | <span data-ttu-id="899fc-195">17.04</span><span class="sxs-lookup"><span data-stu-id="899fc-195">17.04</span></span>   | [<span data-ttu-id="899fc-196">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="899fc-196">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="899fc-197">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="899fc-197">Ubuntu</span></span>   | <span data-ttu-id="899fc-198">16.10</span><span class="sxs-lookup"><span data-stu-id="899fc-198">16.10</span></span>   | [<span data-ttu-id="899fc-199">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="899fc-199">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="899fc-200">有关许可的说明</span><span class="sxs-lookup"><span data-stu-id="899fc-200">Notes on licensing</span></span>

<span data-ttu-id="899fc-201">PowerShell Core 在 [MIT 许可][] 下发布。</span><span class="sxs-lookup"><span data-stu-id="899fc-201">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="899fc-202">根据此许可规定，如果缺失付费支持协议，则用户仅限于获取[社区支持][]。</span><span class="sxs-lookup"><span data-stu-id="899fc-202">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="899fc-203">对于社区支持，Microsoft 无法保证及时作出响应或进行修复。</span><span class="sxs-lookup"><span data-stu-id="899fc-203">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="899fc-204">Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="899fc-204">Windows PowerShell Module</span></span>

<span data-ttu-id="899fc-205">对 PowerShell Core 的支持不扩展到其他产品模块，除非那些产品模块显式支持 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="899fc-205">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="899fc-206">例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。</span><span class="sxs-lookup"><span data-stu-id="899fc-206">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="899fc-207">但是，不显式支持 PowerShell Core 的模块在某些情况下可能兼容。</span><span class="sxs-lookup"><span data-stu-id="899fc-207">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="899fc-208">通过安装 [`WindowsPSModulePath`][] 模块，可以将 Windows PowerShell `PSModulePath` 追加到 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="899fc-208">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="899fc-209">首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：</span><span class="sxs-lookup"><span data-stu-id="899fc-209">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="899fc-210">安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="899fc-210">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

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

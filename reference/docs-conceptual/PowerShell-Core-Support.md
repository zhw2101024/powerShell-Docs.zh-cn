# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="7fa91-101">PowerShell Core 支持生命周期</span><span class="sxs-lookup"><span data-stu-id="7fa91-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="7fa91-102">PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。</span><span class="sxs-lookup"><span data-stu-id="7fa91-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="7fa91-103">因此，PowerShell Core 不包括在 Windows 7/8.1/10 或 Windows Server 许可协议中。</span><span class="sxs-lookup"><span data-stu-id="7fa91-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="7fa91-104">但是，PowerShell Core 受传统 Microsoft 支持协议支持，此类协议包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。</span><span class="sxs-lookup"><span data-stu-id="7fa91-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="7fa91-105">还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。</span><span class="sxs-lookup"><span data-stu-id="7fa91-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="7fa91-106">我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。</span><span class="sxs-lookup"><span data-stu-id="7fa91-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="7fa91-107">或者，可以从常规 [Microsoft 社区][]或 Microsoft [PowerShell 技术社区][] 的其他成员获取帮助。</span><span class="sxs-lookup"><span data-stu-id="7fa91-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="7fa91-108">我们不能确保问题能够及时解决。</span><span class="sxs-lookup"><span data-stu-id="7fa91-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="7fa91-109">如果问题需要立即解决，应使用传统的付费支持选项。</span><span class="sxs-lookup"><span data-stu-id="7fa91-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="7fa91-110">PowerShell Core 生命周期</span><span class="sxs-lookup"><span data-stu-id="7fa91-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="7fa91-111">PowerShell Core 采用 [Microsoft 新式声明周期策略][modern]。</span><span class="sxs-lookup"><span data-stu-id="7fa91-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="7fa91-112">此支持生命周期旨在使客户随时知悉最新版本。</span><span class="sxs-lookup"><span data-stu-id="7fa91-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="7fa91-113">PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。</span><span class="sxs-lookup"><span data-stu-id="7fa91-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7fa91-114">必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="7fa91-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="7fa91-115">例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。</span><span class="sxs-lookup"><span data-stu-id="7fa91-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命周期][lifecycle-chart]

<span data-ttu-id="7fa91-117">新式生命周期策略还要求在中止对某产品（例如 PowerShell Core）提供支持前的 12 个月内， Microsoft 需向客户持续提供通知。</span><span class="sxs-lookup"><span data-stu-id="7fa91-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="7fa91-118">最终，我们希望 PowerShell Core 采取“长期服务”方法，从而只需服务和安全更新即可获取有关 6.x 特定分支/版本的支持。</span><span class="sxs-lookup"><span data-stu-id="7fa91-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="7fa91-119">支持平台</span><span class="sxs-lookup"><span data-stu-id="7fa91-119">Supported platforms</span></span>

<span data-ttu-id="7fa91-120">PowerShell Core 在以下平台上受到正式支持：</span><span class="sxs-lookup"><span data-stu-id="7fa91-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="7fa91-121">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="7fa91-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="7fa91-122">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="7fa91-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="7fa91-123">[Windows Server 半年频道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="7fa91-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="7fa91-124">Ubuntu 14.04、16.04 和 17.04</span><span class="sxs-lookup"><span data-stu-id="7fa91-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="7fa91-125">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="7fa91-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="7fa91-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7fa91-126">CentOS 7</span></span>
* <span data-ttu-id="7fa91-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7fa91-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="7fa91-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7fa91-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="7fa91-129">Fedora 27、28</span><span class="sxs-lookup"><span data-stu-id="7fa91-129">Fedora 27, 28</span></span>
* <span data-ttu-id="7fa91-130">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="7fa91-130">macOS 10.12+</span></span>

<span data-ttu-id="7fa91-131">我们社区也为以下平台提供包，但是它们不受正式支持：</span><span class="sxs-lookup"><span data-stu-id="7fa91-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="7fa91-132">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7fa91-132">Arch Linux</span></span>
* <span data-ttu-id="7fa91-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="7fa91-133">Kali Linux</span></span>
* <span data-ttu-id="7fa91-134">AppImage（可在多个 Linux 平台上运行）</span><span class="sxs-lookup"><span data-stu-id="7fa91-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="7fa91-135">有关许可的说明</span><span class="sxs-lookup"><span data-stu-id="7fa91-135">Notes on licensing</span></span>

<span data-ttu-id="7fa91-136">PowerShell Core 在 [MIT 许可][] 下发布。</span><span class="sxs-lookup"><span data-stu-id="7fa91-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="7fa91-137">根据此许可规定，如果缺失付费支持协议，则用户仅限于获取[社区支持][]。</span><span class="sxs-lookup"><span data-stu-id="7fa91-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="7fa91-138">对于社区支持，Microsoft 无法保证及时作出响应或进行修复。</span><span class="sxs-lookup"><span data-stu-id="7fa91-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="7fa91-139">Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="7fa91-139">Windows PowerShell Module</span></span>

<span data-ttu-id="7fa91-140">对 PowerShell Core 的支持不扩展到其他产品模块，除非那些产品模块显式支持 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="7fa91-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="7fa91-141">例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。</span><span class="sxs-lookup"><span data-stu-id="7fa91-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="7fa91-142">但是，不显式支持 PowerShell Core 的模块在某些情况下可能兼容。</span><span class="sxs-lookup"><span data-stu-id="7fa91-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="7fa91-143">通过安装 [`WindowsPSModulePath`][] 模块，可以将 Windows PowerShell `PSModulePath` 追加到 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="7fa91-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="7fa91-144">首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：</span><span class="sxs-lookup"><span data-stu-id="7fa91-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="7fa91-145">安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="7fa91-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

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

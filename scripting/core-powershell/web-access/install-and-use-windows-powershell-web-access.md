---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "安装和使用 Windows PowerShell Web 访问"
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="f9081-103">安装和使用 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="f9081-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="f9081-104">更新时间：2013 年 11 月 5 日</span><span class="sxs-lookup"><span data-stu-id="f9081-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="f9081-105">适用于：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f9081-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="f9081-106">Windows PowerShell® Web 访问在 Windows Server® 2012 中首次引入，充当 Windows PowerShell 网关，提供以远程计算机为目标的基于 Web 的 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="f9081-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="f9081-107">它可让 IT 专业人士在 Web 浏览器中运行来自 Windows PowerShell 控制台的 Windows PowerShell 命令和脚本，无需在客户端设备上安装 Windows PowerShell、远程管理软件或浏览器插件。</span><span class="sxs-lookup"><span data-stu-id="f9081-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="f9081-108">运行基于 web 的 Windows PowerShell 控制台只需要正确配置的 Windows PowerShell Web 访问网关以及支持 JavaScript® 和接受 Cookie 的客户端设备浏览器。</span><span class="sxs-lookup"><span data-stu-id="f9081-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="f9081-109">客户端设备的示例包括便携式计算机、非工作的个人计算机、借来的计算机、平板计算机、Web 展台、不运行基于 Windows 的操作系统的计算机和手机浏览器。</span><span class="sxs-lookup"><span data-stu-id="f9081-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="f9081-110">IT 专业人士可在远程基于 Windows 的服务器上执行重要的管理任务，这些服务器所属的设备配有 Web 浏览器，并可访问 Internet 连接。</span><span class="sxs-lookup"><span data-stu-id="f9081-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="f9081-111">成功安装和配置网关后，用户可通过使用 Web 浏览器访问 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="f9081-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="f9081-112">当用户打开安全的 Windows PowerShell Web 访问网站时，他们可在成功通过身份验证后运行基于 Web 的 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="f9081-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="f9081-113">Windows PowerShell Web 访问安装和配置过程包含三个步骤：</span><span class="sxs-lookup"><span data-stu-id="f9081-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="f9081-114">安装 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="f9081-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="f9081-115">配置网关</span><span class="sxs-lookup"><span data-stu-id="f9081-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="f9081-116">配置允许用户访问基于 Web 的 Windows PowerShell 控制台的授权规则</span><span class="sxs-lookup"><span data-stu-id="f9081-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="f9081-117">安装和配置 Windows PowerShell Web Access 前，我们建议你阅读该完整指南，其中包括有关如何安装、保护和卸载 Windows PowerShell Web 访问的说明。</span><span class="sxs-lookup"><span data-stu-id="f9081-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="f9081-118">[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)主题介绍了用户如何登录基于 Web 的控制台，并涵盖基于 Web 的 Windows PowerShell 控制台与 **powershell.exe** 控制台之间的限制和差异。</span><span class="sxs-lookup"><span data-stu-id="f9081-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="f9081-119">基于 Web 的控制台的最终用户应阅读[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)部分，但无需阅读本指南的其余部分。</span><span class="sxs-lookup"><span data-stu-id="f9081-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="f9081-120">本主题并不提供详尽的 Web Server (IIS) 操作指导；仅描述了配置 Windows PowerShell Web Access 网关所必需的步骤。</span><span class="sxs-lookup"><span data-stu-id="f9081-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="f9081-121">有关配置和保护 IIS 中的网站安全的详细信息，请参阅“另请参阅”部分中的 IIS 文档资源。</span><span class="sxs-lookup"><span data-stu-id="f9081-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="f9081-122">下图显示 Windows PowerShell Web 访问的工作原理。</span><span class="sxs-lookup"><span data-stu-id="f9081-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="f9081-123">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="f9081-123">In this topic:</span></span>

-   [<span data-ttu-id="f9081-124">运行 Windows PowerShell Web 访问的要求</span><span class="sxs-lookup"><span data-stu-id="f9081-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="f9081-125">浏览器和客户端设备支持</span><span class="sxs-lookup"><span data-stu-id="f9081-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="f9081-126">建议（快速）部署</span><span class="sxs-lookup"><span data-stu-id="f9081-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="f9081-127">自定义部署</span><span class="sxs-lookup"><span data-stu-id="f9081-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="f9081-128">配置正版证书</span><span class="sxs-lookup"><span data-stu-id="f9081-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="f9081-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">运行 Windows PowerShell Web 访问的要求</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f9081-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-130">Windows PowerShell Web 访问需要 Web 服务器 (IIS)、.NET Framework 4.5 和 Windows PowerShell 3.0 或 Windows PowerShell 4.0 在你想运行网关的服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="f9081-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="f9081-131">通过使用服务器管理器中的“添加角色和功能向导”或适用于服务器管理器的 Windows PowerShell 部署 cmdlet，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问。</span><span class="sxs-lookup"><span data-stu-id="f9081-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="f9081-132">当你使用服务器管理器或其部署 cmdlet 安装 Windows PowerShell Web 访问时，所需的角色和功能将在安装过程中自动添加。</span><span class="sxs-lookup"><span data-stu-id="f9081-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="f9081-133">Windows PowerShell Web 访问可让远程用户使用 Web 浏览器中的 Windows PowerShell 访问你组织中的计算机。</span><span class="sxs-lookup"><span data-stu-id="f9081-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="f9081-134">虽然 Windows PowerShell Web 访问是便利和功能强大的管理工具，但基于 Web 的访问存在安全风险，应尽可能安全地配置。</span><span class="sxs-lookup"><span data-stu-id="f9081-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="f9081-135">我们建议配置 Windows PowerShell Web 访问网关的管理员使用可用的安全层，它们分别是包括在 Windows PowerShell Web 访问内的基于 cmdlet 的授权规则以及在 Web 服务器 (IIS) 中和第三方应用程序中可用的安全层。</span><span class="sxs-lookup"><span data-stu-id="f9081-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="f9081-136">本文档包括仅建议在测试环境中使用的不安全示例以及建议在安全部署过程中使用的示例。</span><span class="sxs-lookup"><span data-stu-id="f9081-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="f9081-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">浏览器和客户端设备支持</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f9081-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-138">Windows PowerShell Web 访问支持以下 Internet 浏览器。</span><span class="sxs-lookup"><span data-stu-id="f9081-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="f9081-139">虽然移动浏览器未正式受到支持，但许多此类浏览器均可运行基于 Web 的 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="f9081-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="f9081-140">其他接受 Cookies、运行 JavaScript 和 HTTPS 网站的浏览器有望投入使用，但尚未接受正式测试。</span><span class="sxs-lookup"><span data-stu-id="f9081-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="f9081-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">支持的台式计算机浏览器</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="f9081-142">Microsoft Windows® 8.0、9.0、10.0 和 11.0 的 Windows® Internet Explorer®</span><span class="sxs-lookup"><span data-stu-id="f9081-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="f9081-143">Mozilla Firefox(R) 10.0.2</span><span class="sxs-lookup"><span data-stu-id="f9081-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="f9081-144">Windows 的 Google Chrome(TM) 17.0.963.56m</span><span class="sxs-lookup"><span data-stu-id="f9081-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="f9081-145">用于 Windows 的 Apple Safari® 5.1.2</span><span class="sxs-lookup"><span data-stu-id="f9081-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="f9081-146">用于 Mac OS® 的 Apple Safari 5.1.2</span><span class="sxs-lookup"><span data-stu-id="f9081-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="f9081-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">经过最小限度测试的移动设备或浏览器</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="f9081-148">Windows Phone 7 和 7.5</span><span class="sxs-lookup"><span data-stu-id="f9081-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="f9081-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="f9081-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="f9081-150">iPhone 操作系统 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="f9081-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="f9081-151">iPad 2 操作系统 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="f9081-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="f9081-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">浏览器要求</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-153">若要使用 Windows PowerShell Web 访问基于 Web 的控制台，浏览器必须执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="f9081-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="f9081-154">允许 Windows PowerShell Web 访问网关网站中的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="f9081-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="f9081-155">可打开和访问 HTTPS 页面。</span><span class="sxs-lookup"><span data-stu-id="f9081-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="f9081-156">打开和运行使用 JavaScript 的网站。</span><span class="sxs-lookup"><span data-stu-id="f9081-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="f9081-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">建议（快速）部署</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f9081-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-158">通过使用 Windows PowerShell cmdlet 或从服务器管理器中打开的“添加角色和功能向导”，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问网关。</span><span class="sxs-lookup"><span data-stu-id="f9081-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="f9081-159">对于快速安装和配置，使用 Windows PowerShell cmdlet，如本部分中所述。</span><span class="sxs-lookup"><span data-stu-id="f9081-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="f9081-160">步骤 1：安装 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="f9081-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="f9081-161">步骤 2：配置网关</span><span class="sxs-lookup"><span data-stu-id="f9081-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="f9081-162">步骤 3：配置受限的授权规则</span><span class="sxs-lookup"><span data-stu-id="f9081-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="f9081-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：安装 Windows PowerShell Web 访问</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="f9081-164">使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="f9081-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="f9081-165">使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="f9081-166">在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="f9081-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="f9081-167">在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="f9081-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="f9081-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-169">在 Windows PowerShell 3.0 和 4.0 中，在运行作为模块一部分的 cmdlet 之前，无需将 Server Manager cmdlet 模块导入到 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="f9081-170">在你首次运行 cmdlet（模块的一部分）时，模块被自动导入。</span><span class="sxs-lookup"><span data-stu-id="f9081-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="f9081-171">此外，Windows PowerShell cmdlet 不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="f9081-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="f9081-172">键入以下内容，然后按 **Enter**，其中 *computer_name* 代表要安装 Windows PowerShell Web 访问的远程计算机（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="f9081-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="f9081-173">必要时，<span class="code">Restart</span> 参数会自动重新启动目标服务器。</span><span class="sxs-lookup"><span data-stu-id="f9081-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="f9081-174">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "Copy to clipboard.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="f9081-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-176">使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问在默认情况下不会添加 Web 服务器 (IIS) 管理工具。</span><span class="sxs-lookup"><span data-stu-id="f9081-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="f9081-177">如果你想在相同的服务器上安装管理工具并用作 Windows PowerShell Web 访问网关，请将 <span class="code">IncludeManagementTools</span> 参数添加到安装命令（如本步骤所述）。</span><span class="sxs-lookup"><span data-stu-id="f9081-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="f9081-178">如果你通过远程计算机管理 Windows PowerShell Web 访问网站，请安装 IIS 管理器管理单元，方法是在你想通过其管理网关的计算机上安装<a href="http://go.microsoft.com/fwlink/?LinkID=304145">适用于 Windows 8.1 的远程服务器管理工具</a>或<a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">适用于 Windows 8 的远程服务器管理工具</a>。</span><span class="sxs-lookup"><span data-stu-id="f9081-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="f9081-179">若要在离线的 VHD 上安装角色和功能，你必须添加 <span class="code">ComputerName</span> 参数和 <span class="code">VHD</span> 参数。</span><span class="sxs-lookup"><span data-stu-id="f9081-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="f9081-180"><span class="code">ComputerName</span> 参数含有安装 VHD 的服务器的名称，<span class="code">VHD</span> 参数含有 VHD 在指定服务器上的路径。</span><span class="sxs-lookup"><span data-stu-id="f9081-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="f9081-181">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "Copy to clipboard.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="f9081-182">安装完成后，验证 Windows PowerShell Web 访问是否已安装在目标服务器上，方法是在使用提升的用户权限打开的 Windows PowerShell 控制台中，在目标服务器上运行 **Get-WindowsFeature**。</span><span class="sxs-lookup"><span data-stu-id="f9081-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="f9081-183">你还可以验证 Windows PowerShell Web 访问是否已安装在 Server Manager 控制台中，方法是在“所有服务器”页面上选择目标服务器，然后查看所选服务器的“角色和功能”磁贴。</span><span class="sxs-lookup"><span data-stu-id="f9081-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="f9081-184">你还可以查看 Windows PowerShell Web 访问的自述文件。</span><span class="sxs-lookup"><span data-stu-id="f9081-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="f9081-185">安装 Windows PowerShell Web 访问后，系统将提示你查看自述文件，该文件包含网关的基本且必需的设置说明。</span><span class="sxs-lookup"><span data-stu-id="f9081-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="f9081-186">有关这些设置说明，还可以参阅以下部分：[步骤 2：配置网关](#BKMK_step2)。</span><span class="sxs-lookup"><span data-stu-id="f9081-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="f9081-187">自述文件的路径是 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>。</span><span class="sxs-lookup"><span data-stu-id="f9081-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="f9081-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：配置网关</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-189">使用 **Install-PswaWebApplication** cmdlet 可快速配置 Windows PowerShell Web 访问。</span><span class="sxs-lookup"><span data-stu-id="f9081-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="f9081-190">虽然你可将 <span class="code">UseTestCertificate</span> 参数添加到 <span class="code">Install-PswaWebApplication</span> cmdlet，以出于测试目的而安装自签名的 SSL 证书，但这种做法是不安全的；对安全的生产环境而言，应始终使用证书颁发机构 (CA) 签名的有效 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="f9081-191">管理员可通过 IIS 管理器控制台，使用自行选择的已签名证书代替测试证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="f9081-192">你可完成 Windows PowerShell Web 访问 Web 应用程序配置，方法是运行 <span class="code">Install-PswaWebApplication</span> cmdlet，或在 IIS 管理器中执行基于 GUI 的配置步骤。</span><span class="sxs-lookup"><span data-stu-id="f9081-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="f9081-193">默认情况下，cmdlet 在**默认网站**容器中安装 Web 应用程序、**pswa**（及其应用程序池 **pswa_pool**），如 IIS 管理器所示；必要时，你可指示 cmdlet 更改 Web 应用程序的默认网站容器。</span><span class="sxs-lookup"><span data-stu-id="f9081-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="f9081-194">IIS 管理器提供可供 Web 应用程序使用的配置选项，例如更改端口号或安全套接字层 (SSL) 证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="f9081-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全说明 </span></span><span class="sxs-lookup"><span data-stu-id="f9081-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f9081-196">我们强烈推荐管理员配置网关，以使用 CA 已签名的有效证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="f9081-197">使用 Install-PswaWebApplication，配置带有测试证书的 Windows PowerShell Web 访问网关</span><span class="sxs-lookup"><span data-stu-id="f9081-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="f9081-198">使用 Install-PswaWebApplication 和 IIS 管理器，配置带有正版证书的 Windows PowerShell Web 访问网关</span><span class="sxs-lookup"><span data-stu-id="f9081-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="f9081-199">使用 Install-PswaWebApplication，配置带有测试证书的 Windows PowerShell Web 访问网关。</span><span class="sxs-lookup"><span data-stu-id="f9081-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="f9081-200">执行以下操作之一，打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="f9081-201">在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f9081-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="f9081-202">在 Windows **开始**屏幕上，单击**Windows PowerShell**。</span><span class="sxs-lookup"><span data-stu-id="f9081-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="f9081-203">键入以下命令，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f9081-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="f9081-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="f9081-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全说明 </span></span><span class="sxs-lookup"><span data-stu-id="f9081-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-206"><span class="code">UseTestCertificate</span> 参数仅可在专用测试环境中使用。</span><span class="sxs-lookup"><span data-stu-id="f9081-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="f9081-207">对于安全的生产环境，建议使用证书颁发机构已签名的有效证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="f9081-208">通过运行 cmdlet，在 IIS 默认网站容器中安装 Windows PowerShell Web 访问 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f9081-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="f9081-209">Cmdlet 创建在默认网站 (https://&lt;server_name&gt;/pswa) 上运行 Windows PowerShell Web 访问所必需的基础结构。</span><span class="sxs-lookup"><span data-stu-id="f9081-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="f9081-210">若要在不同的网站上安装 web 应用程序，请添加 <span class="code">WebSiteName</span> 参数，以提供网站名称。</span><span class="sxs-lookup"><span data-stu-id="f9081-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="f9081-211">若要更改 Web 应用程序的名称（默认名称是 <span class="code">pswa</span>），请添加 <span class="code">WebApplicationName</span> 参数。</span><span class="sxs-lookup"><span data-stu-id="f9081-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="f9081-212">通过运行 cmdlet，配置以下设置。</span><span class="sxs-lookup"><span data-stu-id="f9081-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="f9081-213">必要时，你可在 IIS 管理器控制台中手动更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="f9081-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="f9081-214">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="f9081-214">Path: /pswa</span></span>

    -   <span data-ttu-id="f9081-215">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="f9081-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="f9081-216">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="f9081-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="f9081-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="f9081-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="f9081-218"><span class="label">示例：</span><span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="f9081-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="f9081-219">在本示例中，Windows PowerShell Web 访问的相关网站是 https://&lt; *server_name*&gt;/myWebApp。</span><span class="sxs-lookup"><span data-stu-id="f9081-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="f9081-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-221">你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="f9081-222">有关详细信息，请参阅<a href="#BKMK_step3">第 3 步：配置受限的授权规则</a>和<a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 访问的授权规则和安全功能</a>。</span><span class="sxs-lookup"><span data-stu-id="f9081-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="f9081-223">使用 Install-PswaWebApplication 和 IIS 管理器，配置带有正版证书的 Windows PowerShell Web 访问网关</span><span class="sxs-lookup"><span data-stu-id="f9081-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="f9081-224">执行以下操作之一，打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="f9081-225">在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f9081-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="f9081-226">在 Windows **开始**屏幕上，单击**Windows PowerShell**。</span><span class="sxs-lookup"><span data-stu-id="f9081-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="f9081-227">键入以下命令，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f9081-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="f9081-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="f9081-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="f9081-229">通过运行 cmdlet，配置以下网关设置。</span><span class="sxs-lookup"><span data-stu-id="f9081-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="f9081-230">必要时，你可在 IIS 管理器控制台中手动更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="f9081-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="f9081-231">你还可以为 <span class="code">Install-pswawebapplication</span> cmdlet 的 <span class="code">WebsiteName</span> 和<span class="code">WebApplicationName</span> 参数指定值。</span><span class="sxs-lookup"><span data-stu-id="f9081-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="f9081-232">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="f9081-232">Path: /pswa</span></span>

    -   <span data-ttu-id="f9081-233">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="f9081-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="f9081-234">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="f9081-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="f9081-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="f9081-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="f9081-236">通过执行以下操作之一，打开 IIS 管理器控制台。</span><span class="sxs-lookup"><span data-stu-id="f9081-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="f9081-237">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="f9081-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="f9081-238">在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。</span><span class="sxs-lookup"><span data-stu-id="f9081-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="f9081-239">在 Windows **开始**屏幕上，单击**服务器管理器**。</span><span class="sxs-lookup"><span data-stu-id="f9081-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="f9081-240">在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。</span><span class="sxs-lookup"><span data-stu-id="f9081-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="f9081-241">展开“网站”文件夹。</span><span class="sxs-lookup"><span data-stu-id="f9081-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="f9081-242">选择你已安装 Windows PowerShell Web 访问的 Web 应用程序的网站。</span><span class="sxs-lookup"><span data-stu-id="f9081-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="f9081-243">在**操作**窗格中，单击**绑定**。</span><span class="sxs-lookup"><span data-stu-id="f9081-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="f9081-244">在**网站绑定**对话框中，单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="f9081-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="f9081-245">在**添加网站绑定**对话框中，在**类型**字段，选择**https**。</span><span class="sxs-lookup"><span data-stu-id="f9081-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="f9081-246">在“SSL 证书”字段中，从下拉菜单中选择你的已签名证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="f9081-247">单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="f9081-247">Click **OK**.</span></span> <span data-ttu-id="f9081-248">有关如何获得证书的详细信息，请参阅本主题中的[在 IIS 管理器中配置 SSL 证书](#BKMK_cert)。</span><span class="sxs-lookup"><span data-stu-id="f9081-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="f9081-249">现可配置 Windows PowerShell Web 访问 Web 应用程序，以便使用已签名的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="f9081-250">你可通过在浏览器窗口中打开 https://&lt;server_name&gt;/pswa 访问 Windows PowerShell Web 访问。</span><span class="sxs-lookup"><span data-stu-id="f9081-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="f9081-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-252">你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="f9081-253">有关详细信息，请参阅<a href="#BKMK_step3">第 3 步：配置受限的授权规则</a>和<a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 访问的授权规则和安全功能</a>。</span><span class="sxs-lookup"><span data-stu-id="f9081-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="f9081-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">第 3 步：配置受限的授权规则</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-255">安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="f9081-256">Windows PowerShell Web 访问的访问控制通过使用下表所述的 Windows PowerShell cmdlet 集进行管理。</span><span class="sxs-lookup"><span data-stu-id="f9081-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="f9081-257">没有相当的 GUI 可用于添加或管理授权规则。</span><span class="sxs-lookup"><span data-stu-id="f9081-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="f9081-258">有关 Windows PowerShell Web 访问 cmdlet 的更多详细信息，请参阅 cmdlet 参考主题 [Windows PowerShell Web 访问 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9081-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="f9081-259">有关 Windows PowerShell Web 访问授权规则和安全性的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9081-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="f9081-260">添加受限的授权规则</span><span class="sxs-lookup"><span data-stu-id="f9081-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="f9081-261">使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="f9081-262">在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="f9081-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="f9081-263">在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="f9081-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="f9081-264"><span class="label">使用会话配置限制用户访问的可选步骤：</span>验证要在规则中使用的会话配置已存在。</span><span class="sxs-lookup"><span data-stu-id="f9081-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="f9081-265">如果尚未创建这些配置，则使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中用于创建会话配置的说明。</span><span class="sxs-lookup"><span data-stu-id="f9081-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="f9081-266">键入以下命令，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f9081-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="f9081-267">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="f9081-268">本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见的脚本和 cmdlet 需求的特定会话配置的权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="f9081-269">在以下示例中，<span class="code">Contoso</span> 域中名为 <span class="code">JSmith</span> 的用户获得访问权限，以管理计算机 <span class="code">Contoso_214</span>，并使用名为 <span class="code">NewAdminsOnly</span> 的会话配置。</span><span class="sxs-lookup"><span data-stu-id="f9081-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="f9081-270">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="f9081-271">确保通过运行 **Get-PswaAuthorizationRule** cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt; 创建了该规则。</span><span class="sxs-lookup"><span data-stu-id="f9081-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="f9081-272">例如，**Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**。</span><span class="sxs-lookup"><span data-stu-id="f9081-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="f9081-273">配置授权规则之后，授权用户便可以登录基于 Web 的控制台并开始使用 Windows PowerShell Web 访问。</span><span class="sxs-lookup"><span data-stu-id="f9081-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="f9081-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">自定义部署</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f9081-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-275">通过使用服务器管理器中的“添加角色和功能向导”，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问网关。</span><span class="sxs-lookup"><span data-stu-id="f9081-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="f9081-276">安装 Windows PowerShell Web 访问之后，可以在 IIS 管理器中自定义网关的配置。</span><span class="sxs-lookup"><span data-stu-id="f9081-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="f9081-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：安装 Windows PowerShell Web 访问</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="f9081-278">若要使用“添加角色和功能向导”安装 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="f9081-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="f9081-279">如果服务器管理器已经打开，则继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="f9081-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="f9081-280">如果服务器管理器尚未打开，请执行以下任一操作打开它。</span><span class="sxs-lookup"><span data-stu-id="f9081-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="f9081-281">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="f9081-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="f9081-282">在 Windows **开始**屏幕上，单击**服务器管理器**。</span><span class="sxs-lookup"><span data-stu-id="f9081-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="f9081-283">在**管理**菜单上，单击**添加角色和功能**。</span><span class="sxs-lookup"><span data-stu-id="f9081-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="f9081-284">在“选择安装类型”页上，选择“基于角色或基于功能的安装”。</span><span class="sxs-lookup"><span data-stu-id="f9081-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="f9081-285">单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f9081-285">Click **Next**.</span></span>

4.  <span data-ttu-id="f9081-286">在“选择目标服务器”页面上，从服务器池中选择一台服务器，或选择脱机 VHD。</span><span class="sxs-lookup"><span data-stu-id="f9081-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="f9081-287">若要将离线的 VHD 选择为你的目标服务器，则先选择安装 VHD 的服务器，然后选择 VHD 文件。</span><span class="sxs-lookup"><span data-stu-id="f9081-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="f9081-288">有关如何将服务器添加到服务器池的详细信息，请参阅服务器管理器帮助。</span><span class="sxs-lookup"><span data-stu-id="f9081-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="f9081-289">选择目标服务器后，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f9081-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="f9081-290">在向导的**选择功能**页面上，展开**Windows PowerShell**，然后选择**Windows PowerShell Web 访问**。</span><span class="sxs-lookup"><span data-stu-id="f9081-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="f9081-291">注意，系统提示你添加所需的功能，例如 .NET Framework 4.5 以及 Web 服务器 (IIS) 的角色服务。</span><span class="sxs-lookup"><span data-stu-id="f9081-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="f9081-292">添加所需的功能并继续操作。</span><span class="sxs-lookup"><span data-stu-id="f9081-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="f9081-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-294">通过使用“添加角色和功能向导”安装 Windows PowerShell Web 访问还将安装 Web 服务器 (IIS)，包括 IIS 管理器管理单元。</span><span class="sxs-lookup"><span data-stu-id="f9081-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="f9081-295">如果你使用“添加角色和功能向导”，则在默认情况下，也安装了管理单元及其他 IIS 管理工具。</span><span class="sxs-lookup"><span data-stu-id="f9081-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="f9081-296">如果你按照以下步骤，使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问，则不会默认添加管理工具。</span><span class="sxs-lookup"><span data-stu-id="f9081-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="f9081-297">在“确认安装选择”页面上，如果 Windows PowerShell Web 访问的功能文件并不存储在你在步骤 4 中所选的目标服务器上，则单击“指定备用的源路径”，并提供功能文件的路径。</span><span class="sxs-lookup"><span data-stu-id="f9081-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="f9081-298">否则，单击**安装**。</span><span class="sxs-lookup"><span data-stu-id="f9081-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="f9081-299">单击“安装”后，“安装进度”页面将显示安装进度、结果以及有关警告、故障或 Windows PowerShell Web 访问所必需的安装后配置步骤的信息。</span><span class="sxs-lookup"><span data-stu-id="f9081-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="f9081-300">安装 Windows PowerShell Web 访问后，系统将提示你查看自述文件，该文件包含网关的基本且必需的设置说明。</span><span class="sxs-lookup"><span data-stu-id="f9081-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="f9081-301">这些说明也包括在本主题中。</span><span class="sxs-lookup"><span data-stu-id="f9081-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="f9081-302">自述文件的路径是 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>。</span><span class="sxs-lookup"><span data-stu-id="f9081-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="f9081-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：配置网关</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-304">本部分中的说明涉及在网站的子目录（而非根目录）中安装 Windows PowerShell Web 访问 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f9081-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="f9081-305">本步骤与 <span class="code">Install-PswaWebApplication</span> cmdlet 执行的基于 GUI 的操作等效。</span><span class="sxs-lookup"><span data-stu-id="f9081-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="f9081-306">本部分还包括有关如何使用 IIS 管理器将 Windows PowerShell Web 访问网关配置为根网站的说明。</span><span class="sxs-lookup"><span data-stu-id="f9081-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="f9081-307">使用 IIS 管理器在现有的网站中配置网关</span><span class="sxs-lookup"><span data-stu-id="f9081-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="f9081-308">使用 IIS 管理器，将网关配置为带有测试证书的根网站</span><span class="sxs-lookup"><span data-stu-id="f9081-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="f9081-309">使用 IIS 管理器在现有的网站中配置网关</span><span class="sxs-lookup"><span data-stu-id="f9081-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="f9081-310">通过执行以下操作之一，打开 IIS 管理器控制台。</span><span class="sxs-lookup"><span data-stu-id="f9081-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="f9081-311">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="f9081-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="f9081-312">在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。</span><span class="sxs-lookup"><span data-stu-id="f9081-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="f9081-313">在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。</span><span class="sxs-lookup"><span data-stu-id="f9081-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="f9081-314">当它在“应用程序”结果中显示时，单击快捷方式。</span><span class="sxs-lookup"><span data-stu-id="f9081-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="f9081-315">为 Windows PowerShell Web 访问创建新的应用程序池。</span><span class="sxs-lookup"><span data-stu-id="f9081-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="f9081-316">在 IIS 管理器树窗格中展开网关服务器的节点，选择“应用程序池”，然后单击“操作”窗格中的“添加应用程序池”。</span><span class="sxs-lookup"><span data-stu-id="f9081-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="f9081-317">为新的应用程序池添加名称 **pswa_pool**，或提供其他名称。</span><span class="sxs-lookup"><span data-stu-id="f9081-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="f9081-318">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="f9081-318">Click **OK**.</span></span>

4.  <span data-ttu-id="f9081-319">在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。</span><span class="sxs-lookup"><span data-stu-id="f9081-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="f9081-320">选择“站点”文件夹。</span><span class="sxs-lookup"><span data-stu-id="f9081-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="f9081-321">右键单击你想添加 Windows PowerShell Web 访问网站的网站（例如，**默认网站**），然后单击**添加应用程序**。</span><span class="sxs-lookup"><span data-stu-id="f9081-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="f9081-322">在“别名”字段中，键入 pswa 或提供其他别名。</span><span class="sxs-lookup"><span data-stu-id="f9081-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="f9081-323">别名变为虚拟目录的名称。</span><span class="sxs-lookup"><span data-stu-id="f9081-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="f9081-324">例如，以下 URL 中的 **pswa** 表示在本步骤中指定的别名：https://&lt;server_name&gt;/pswa。</span><span class="sxs-lookup"><span data-stu-id="f9081-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="f9081-325">在“应用程序池”字段中，选择在步骤 3 中创建的应用程序池。</span><span class="sxs-lookup"><span data-stu-id="f9081-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="f9081-326">在“物理路径”字段中，浏览到应用程序的位置。</span><span class="sxs-lookup"><span data-stu-id="f9081-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="f9081-327">你可使用默认的位置，即 %windir%/Web/PowerShellWebAccess/wwwroot。</span><span class="sxs-lookup"><span data-stu-id="f9081-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="f9081-328">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="f9081-328">Click **OK**.</span></span>

9.  <span data-ttu-id="f9081-329">按照本主题中的过程 [在 IIS 管理器中配置 SSL 证书](#BKMK_cert) 中的步骤执行。</span><span class="sxs-lookup"><span data-stu-id="f9081-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="f9081-330"><span class="label">可选的安全步骤：</span>利用树窗格中所选的网站，双击内容窗格中的“SSL 设置”。</span><span class="sxs-lookup"><span data-stu-id="f9081-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="f9081-331">选择“需要 SSL”，然后在“操作”窗格中，单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="f9081-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="f9081-332">此外，在“SSL 设置”窗格中，你可要求连接到 Windows PowerShell Web 访问网站的用户持有客户端证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="f9081-333">客户端证书可协助验证客户端设备用户的身份。</span><span class="sxs-lookup"><span data-stu-id="f9081-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="f9081-334">有关要求提供客户端证书如何提高 Windows PowerShell Web 访问的安全性的详细信息，请参阅本指南中 [Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9081-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="f9081-335">在客户端设备上打开浏览器会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-335">Open a browser session on a client device.</span></span> <span data-ttu-id="f9081-336">有关受支持的浏览器和设备的详细信息，请参阅本主题中的[浏览器和客户端设备支持](#BKMK_browser)。</span><span class="sxs-lookup"><span data-stu-id="f9081-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="f9081-337">打开新的 Windows PowerShell Web 访问网站 https://&lt; *gateway_server_name*&gt;/pswa。</span><span class="sxs-lookup"><span data-stu-id="f9081-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="f9081-338">浏览器应显示 Windows PowerShell Web 访问控制台登录页面。</span><span class="sxs-lookup"><span data-stu-id="f9081-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="f9081-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-340">你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="f9081-341">在使用提升的用户权限打开的 Windows PowerShell 会话（以管理员身份运行）中，运行以下脚本（其中 *application_pool_name* 表示你在步骤 3 中创建的应用程序池的名称），以便向应用程序池提供授权文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="f9081-342">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="f9081-343">若要查看授权文件的现有访问权限，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="f9081-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="f9081-344">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="f9081-345">使用 IIS 管理器，将网关配置为带有测试证书的根网站</span><span class="sxs-lookup"><span data-stu-id="f9081-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="f9081-346">通过执行以下操作之一，打开 IIS 管理器控制台。</span><span class="sxs-lookup"><span data-stu-id="f9081-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="f9081-347">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="f9081-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="f9081-348">在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。</span><span class="sxs-lookup"><span data-stu-id="f9081-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="f9081-349">在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。</span><span class="sxs-lookup"><span data-stu-id="f9081-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="f9081-350">当它在“应用程序”结果中显示时，单击快捷方式。</span><span class="sxs-lookup"><span data-stu-id="f9081-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="f9081-351">在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。</span><span class="sxs-lookup"><span data-stu-id="f9081-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="f9081-352">选择“站点”文件夹。</span><span class="sxs-lookup"><span data-stu-id="f9081-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="f9081-353">在**操作**窗格中，单击**添加网站**。</span><span class="sxs-lookup"><span data-stu-id="f9081-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="f9081-354">键入网站的名称，例如**Windows PowerShell Web 访问**。</span><span class="sxs-lookup"><span data-stu-id="f9081-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="f9081-355">新网站的应用程序池自动创建。</span><span class="sxs-lookup"><span data-stu-id="f9081-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="f9081-356">若果使用其他应用程序池，请单击“选择”，以选择与新网站相关的应用程序池。</span><span class="sxs-lookup"><span data-stu-id="f9081-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="f9081-357">在**选择应用程序池**对话框中选择备用的应用程序池，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="f9081-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="f9081-358">在“物理路径”文本框中，导航到 %*windir%*/Web/PowerShellWebAccess/wwwroot。</span><span class="sxs-lookup"><span data-stu-id="f9081-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="f9081-359">在**绑定**区域的**类型**字段中，选择**https**。</span><span class="sxs-lookup"><span data-stu-id="f9081-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="f9081-360">向网站分配一个不再被其他网站或应用程序使用的端口号。</span><span class="sxs-lookup"><span data-stu-id="f9081-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="f9081-361">若要定位打开的端口，你可在“命令提示符”窗口中运行 **netstat** 命令。</span><span class="sxs-lookup"><span data-stu-id="f9081-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="f9081-362">默认端口号为 443。</span><span class="sxs-lookup"><span data-stu-id="f9081-362">The default port number is 443.</span></span>

    <span data-ttu-id="f9081-363">如果其他网站已经使用 443，或你有其他更改端口号的安全原因，则更改默认端口。</span><span class="sxs-lookup"><span data-stu-id="f9081-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="f9081-364">如果在你的网关服务器上运行的其他网站使用你所选的端口，当你在“添加网站”对话框中单击“确定”时，将会显示一条警告信息。</span><span class="sxs-lookup"><span data-stu-id="f9081-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="f9081-365">必须使用未使用的端口运行 Windows PowerShell Web 访问。</span><span class="sxs-lookup"><span data-stu-id="f9081-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="f9081-366">此外，如果你的组织有需要，请指定你的组织和用户都接受的主机名称，例如 **www.contoso.com**。</span><span class="sxs-lookup"><span data-stu-id="f9081-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="f9081-367">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="f9081-367">Click **OK**.</span></span>

10. <span data-ttu-id="f9081-368">为提高生产环境的安全性，我们强烈建议提供证书颁发机构已签名的有效证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="f9081-369">你必须提供 SSL 证书，因为用户仅可通过 HTTPS 网站连接到 Windows PowerShell Web 访问。</span><span class="sxs-lookup"><span data-stu-id="f9081-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="f9081-370">有关如何获得证书的详细信息，请参阅本主题中的[在 IIS 管理器中配置 SSL 证书](#BKMK_cert)。</span><span class="sxs-lookup"><span data-stu-id="f9081-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="f9081-371">单击“确定”关闭“添加网站”对话框。</span><span class="sxs-lookup"><span data-stu-id="f9081-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="f9081-372">在使用提升的用户权限打开的 Windows PowerShell 会话（以管理员身份运行）中，运行以下脚本（其中 *application_pool_name* 表示你在步骤 4 中创建的应用程序池的名称），以便向应用程序池提供授权文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="f9081-373">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="f9081-374">若要查看授权文件的现有访问权限，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="f9081-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="f9081-375">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="f9081-376">利用在 IIS 管理器树窗格中选择的新网站，单击“操作”窗格中的“启动”，以启动网站。</span><span class="sxs-lookup"><span data-stu-id="f9081-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="f9081-377">在客户端设备上打开浏览器会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-377">Open a browser session on a client device.</span></span> <span data-ttu-id="f9081-378">有关受支持的浏览器和设备的详细信息，请参阅本文档中的[浏览器和客户端设备支持](#BKMK_browser)。</span><span class="sxs-lookup"><span data-stu-id="f9081-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="f9081-379">打开新的 Windows PowerShell Web 访问网站。</span><span class="sxs-lookup"><span data-stu-id="f9081-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="f9081-380">因为根网站指向 Windows PowerShell Web 访问文件夹，所以当你打开 https://&lt; *gateway_server_name*&gt;时，浏览器应显示 Windows PowerShell Web 访问登录网页。</span><span class="sxs-lookup"><span data-stu-id="f9081-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="f9081-381">你无需向 URL 添加 **/pswa**。</span><span class="sxs-lookup"><span data-stu-id="f9081-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f9081-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="f9081-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f9081-383">你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="f9081-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 3：配置受限的授权规则</span></a></span><span class="sxs-lookup"><span data-stu-id="f9081-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-385">安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="f9081-386">Windows PowerShell Web 访问的访问控制通过使用下表所述的 Windows PowerShell cmdlet 集进行管理。</span><span class="sxs-lookup"><span data-stu-id="f9081-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="f9081-387">没有相当的 GUI 可用于添加或管理授权规则。</span><span class="sxs-lookup"><span data-stu-id="f9081-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="f9081-388">有关 Windows PowerShell Web 访问 cmdlet 的更多详细信息，请参阅 cmdlet 参考主题 [Windows PowerShell Web 访问 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9081-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="f9081-389">有关 Windows PowerShell Web 访问授权规则和安全性的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9081-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="f9081-390">添加受限的授权规则</span><span class="sxs-lookup"><span data-stu-id="f9081-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="f9081-391">使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="f9081-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="f9081-392">在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="f9081-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="f9081-393">在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="f9081-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="f9081-394"><span class="label">使用会话配置限制用户访问的可选步骤：</span>验证要在规则中使用的会话配置已存在。</span><span class="sxs-lookup"><span data-stu-id="f9081-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="f9081-395">如果尚未创建这些配置，则使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中用于创建会话配置的说明。</span><span class="sxs-lookup"><span data-stu-id="f9081-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="f9081-396">键入以下命令，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f9081-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="f9081-397">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="f9081-398">本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见的脚本和 cmdlet 需求的特定会话配置的权限。</span><span class="sxs-lookup"><span data-stu-id="f9081-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="f9081-399">在以下示例中，<span class="code">Contoso</span> 域中名为 <span class="code">JSmith</span> 的用户获得访问权限，以管理计算机 <span class="code">Contoso_214</span>，并使用名为 <span class="code">NewAdminsOnly</span> 的会话配置。</span><span class="sxs-lookup"><span data-stu-id="f9081-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="f9081-400">Copy</span><span class="sxs-lookup"><span data-stu-id="f9081-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="f9081-401">确保通过运行 **Get-PswaAuthorizationRule** cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt; 创建了该规则。</span><span class="sxs-lookup"><span data-stu-id="f9081-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="f9081-402">例如，**Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**。</span><span class="sxs-lookup"><span data-stu-id="f9081-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="f9081-403">配置授权规则之后，授权用户便可以登录基于 Web 的控制台并开始使用 Windows PowerShell Web 访问。</span><span class="sxs-lookup"><span data-stu-id="f9081-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="f9081-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">配置正版证书</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f9081-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-405">对于安全的生产环境，请始终使用证书颁发机构 (CA) 已签名的有效 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="f9081-406">本部分中的过程介绍如何从 CA 获取并应用有效的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="f9081-407">在 IIS 管理器中配置 SSL 证书</span><span class="sxs-lookup"><span data-stu-id="f9081-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="f9081-408">在 IIS 管理器树窗格中，选择已安装 Windows PowerShell Web 访问的服务器。</span><span class="sxs-lookup"><span data-stu-id="f9081-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="f9081-409">在内容窗格中，双击**服务器证书**。</span><span class="sxs-lookup"><span data-stu-id="f9081-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="f9081-410">在“操作”窗格中，执行以下操作之一。</span><span class="sxs-lookup"><span data-stu-id="f9081-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="f9081-411">有关在 IIS 中配置服务器证书的详细信息，请参阅[在 IIS 7 中配置服务器证书](https://technet.microsoft.com/library/cc732230.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9081-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="f9081-412">单击“导入”，以从网络上的位置中导入现有的有效证书。</span><span class="sxs-lookup"><span data-stu-id="f9081-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="f9081-413">单击“创建证书请求”，以请求证书颁发机构颁发的证书，例如 VeriSign(TM)、Thawte 或 GeoTrust(R)。</span><span class="sxs-lookup"><span data-stu-id="f9081-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="f9081-414">证书的公用名必须与申请的主机头相匹配。</span><span class="sxs-lookup"><span data-stu-id="f9081-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="f9081-415">例如，如果客户端浏览器申请 http://www.contoso.com/，则公用名也必须是 http://www.contoso.com/。</span><span class="sxs-lookup"><span data-stu-id="f9081-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="f9081-416">这是向 Windows PowerShell Web 访问网关提供证书的最安全的推荐方案。</span><span class="sxs-lookup"><span data-stu-id="f9081-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="f9081-417">单击“创建自签名的证书”，以创建你可立即使用的证书，必要时稍后再由 CA 签名。</span><span class="sxs-lookup"><span data-stu-id="f9081-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="f9081-418">为自签名的证书指定一个友好名称，例如 **Windows PowerShell Web 访问**。</span><span class="sxs-lookup"><span data-stu-id="f9081-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="f9081-419">此选项被视为不安全的，仅建议在专用测试环境中使用。</span><span class="sxs-lookup"><span data-stu-id="f9081-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="f9081-420">创建或获得证书后，在 IIS 管理器树窗格中选择要应用证书的网站（如默认网站），然后单击“操作”窗格中的“绑定”。</span><span class="sxs-lookup"><span data-stu-id="f9081-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="f9081-421">如果尚未显示，则在“添加网站绑定”对话框中，向网站添加 **https** 绑定。</span><span class="sxs-lookup"><span data-stu-id="f9081-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="f9081-422">如果使用的不是自签名的证书，请从本程序的步骤 3 中指定主机名称。</span><span class="sxs-lookup"><span data-stu-id="f9081-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="f9081-423">如果使用的是自签名的证书，则无需执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="f9081-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="f9081-424">选择要使用或在步骤 3 中创建的证书，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="f9081-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="f9081-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">使用基于 Web 的 Windows PowerShell 控制台</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f9081-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-426">安装 Windows PowerShell Web 访问以及按照本主题所述完成网关配置之后，基于 Web 的 Windows PowerShell 控制台随时可用。</span><span class="sxs-lookup"><span data-stu-id="f9081-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="f9081-427">有关基于 Web 的控制台的入门详细信息，请参阅[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9081-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="f9081-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f9081-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f9081-429">[Internet Information Services (IIS) 7.0 文档](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 帮助](https://technet.microsoft.com/library/cc732664.aspx)
[配置 Web 服务器安全性 (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec 部署资源](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="f9081-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="f9081-430"><span>显示：</span>继承内容受保护</span><span class="sxs-lookup"><span data-stu-id="f9081-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="f9081-431"><span class="stdr-votetitle">此页面是否有所帮助？</span></span><span class="sxs-lookup"><span data-stu-id="f9081-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="f9081-432">是 否</span><span class="sxs-lookup"><span data-stu-id="f9081-432">Yes No</span></span>

<span data-ttu-id="f9081-433">更多反馈？</span><span class="sxs-lookup"><span data-stu-id="f9081-433">Additional feedback?</span></span>

<span data-ttu-id="f9081-434">剩余 <span class="stdr-count"><span class="stdr-charcnt">1500</span> 个字符</span>提交，跳过此部分</span><span class="sxs-lookup"><span data-stu-id="f9081-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="f9081-435"><span class="stdr-thankyou">谢谢！</span></span><span class="sxs-lookup"><span data-stu-id="f9081-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="f9081-436"><span class="stdr-appreciate">我们非常感谢你的反馈意见。</span></span><span class="sxs-lookup"><span data-stu-id="f9081-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="f9081-437">管理个人资料</span><span class="sxs-lookup"><span data-stu-id="f9081-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="f9081-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span>站点反馈</a>站点反馈</span><span class="sxs-lookup"><span data-stu-id="f9081-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="f9081-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="f9081-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="f9081-440">告诉我们你的体验...</span><span class="sxs-lookup"><span data-stu-id="f9081-440">Tell us about your experience...</span></span>

<span data-ttu-id="f9081-441">页面加载速度快吗？</span><span class="sxs-lookup"><span data-stu-id="f9081-441">Did the page load quickly?</span></span>

<span data-ttu-id="f9081-442"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="f9081-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="f9081-443">你喜欢页面设计吗？</span><span class="sxs-lookup"><span data-stu-id="f9081-443">Do you like the page design?</span></span>

<span data-ttu-id="f9081-444"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="f9081-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="f9081-445">告诉我们更多内容</span><span class="sxs-lookup"><span data-stu-id="f9081-445">Tell us more</span></span>

-   [<span data-ttu-id="f9081-446">快讯</span><span class="sxs-lookup"><span data-stu-id="f9081-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="f9081-447">联系我们</span><span class="sxs-lookup"><span data-stu-id="f9081-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="f9081-448">隐私声明</span><span class="sxs-lookup"><span data-stu-id="f9081-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="f9081-449">使用条款</span><span class="sxs-lookup"><span data-stu-id="f9081-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="f9081-450">商标</span><span class="sxs-lookup"><span data-stu-id="f9081-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="f9081-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="f9081-451">© 2016 Microsoft</span></span>

<span data-ttu-id="f9081-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="f9081-452">© 2016 Microsoft</span></span>

<span data-ttu-id="f9081-453">链接到此站点或从中引用的第三方脚本或代码由拥有此类代码的第三方（而非 Microsoft）授权给你。</span><span class="sxs-lookup"><span data-stu-id="f9081-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="f9081-454">请参阅 ASP.NET Ajax CDN 使用条款，网址为 http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="f9081-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />


---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用基于 Web 的 Windows PowerShell 控制台"
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="5359f-103">使用基于 Web 的 Windows PowerShell 控制台</span><span class="sxs-lookup"><span data-stu-id="5359f-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="5359f-104">更新时间：2013年 6 月 24日</span><span class="sxs-lookup"><span data-stu-id="5359f-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="5359f-105">适用于：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5359f-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="5359f-106">Windows PowerShell® Web 访问让 Windows PowerShell® 用户登录到由安全套接字层 (SSL) 确保安全的网站，以使用 Windows PowerShell 会话、cmdlet 和脚本管理远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5359f-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="5359f-107">由于 Windows PowerShell 控制台在 Web 浏览器中运行，因此，它可从各种客户端设备中打开，包括手机、平板电脑、公用计算机展台、便携式计算机或共享或借来的计算机。</span><span class="sxs-lookup"><span data-stu-id="5359f-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="5359f-108">基于 Web 的 Windows PowerShell 控制台以用户在登录过程中指定的远程计算机为目标。</span><span class="sxs-lookup"><span data-stu-id="5359f-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="5359f-109">本主题描述如何登录以及开始使用 Windows PowerShell Web 访问基于 Web 的控制台。</span><span class="sxs-lookup"><span data-stu-id="5359f-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="5359f-110">本主题不描述如何使用 Windows PowerShell 或运行 cmdlet 或脚本。</span><span class="sxs-lookup"><span data-stu-id="5359f-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="5359f-111">有关如何使用 Windows PowerShell 和脚本资源的信息，请参阅本主题结尾的“另请参阅”部分。</span><span class="sxs-lookup"><span data-stu-id="5359f-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="5359f-112">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="5359f-112">In this topic:</span></span>

-   [<span data-ttu-id="5359f-113">支持的浏览器和客户端设备</span><span class="sxs-lookup"><span data-stu-id="5359f-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="5359f-114">登录到 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="5359f-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="5359f-115">注销和超时</span><span class="sxs-lookup"><span data-stu-id="5359f-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="5359f-116">基于 Web 的 Windows PowerShell 控制台的不同之处</span><span class="sxs-lookup"><span data-stu-id="5359f-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="5359f-117">Windows PowerShell Web 访问支持以下 Internet 浏览器。</span><span class="sxs-lookup"><span data-stu-id="5359f-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="5359f-118">虽然移动浏览器未正式受到支持，但许多此类浏览器均可运行基于 Web 的 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="5359f-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="5359f-119">其他接受 Cookies、运行 JavaScript 和 HTTPS 网站的浏览器有望投入使用，但尚未接受正式测试。</span><span class="sxs-lookup"><span data-stu-id="5359f-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="5359f-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">支持的台式计算机浏览器</span></a></span><span class="sxs-lookup"><span data-stu-id="5359f-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="5359f-121">Microsoft Windows® 8.0、9.0、10.0 和 11.0 的 Windows® Internet Explorer®</span><span class="sxs-lookup"><span data-stu-id="5359f-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="5359f-122">Mozilla Firefox(R) 10.0.2</span><span class="sxs-lookup"><span data-stu-id="5359f-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="5359f-123">Windows 的 Google Chrome(TM) 17.0.963.56m</span><span class="sxs-lookup"><span data-stu-id="5359f-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="5359f-124">用于 Windows 的 Apple Safari® 5.1.2</span><span class="sxs-lookup"><span data-stu-id="5359f-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="5359f-125">用于 Mac OS® 的 Apple Safari 5.1.2</span><span class="sxs-lookup"><span data-stu-id="5359f-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="5359f-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">经过最小限度测试的移动设备或浏览器</span></a></span><span class="sxs-lookup"><span data-stu-id="5359f-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="5359f-127">Windows Phone 7 和 7.5</span><span class="sxs-lookup"><span data-stu-id="5359f-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="5359f-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="5359f-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="5359f-129">iPhone 操作系统 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="5359f-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="5359f-130">iPad 2 操作系统 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="5359f-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="5359f-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">浏览器要求</span></a></span><span class="sxs-lookup"><span data-stu-id="5359f-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="5359f-132">若要使用 Windows PowerShell Web 访问基于 Web 的控制台，浏览器必须执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="5359f-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="5359f-133">允许 Windows PowerShell Web 访问网关网站中的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="5359f-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="5359f-134">可打开和访问 HTTPS 页面。</span><span class="sxs-lookup"><span data-stu-id="5359f-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="5359f-135">打开和运行使用 JavaScript 的网站。</span><span class="sxs-lookup"><span data-stu-id="5359f-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="5359f-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">登录到 Windows PowerShell Web 访问</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="5359f-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="5359f-137">Windows PowerShell Web 访问管理员应为你提供一个 URL，该 URL 是贵组织 Windows PowerShell Web 访问网关网站的地址。</span><span class="sxs-lookup"><span data-stu-id="5359f-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="5359f-138">默认情况下，此网址的地址为 https://&lt;server_name&gt;/pswa。</span><span class="sxs-lookup"><span data-stu-id="5359f-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="5359f-139">在登录到 Windows PowerShell Web 访问之前，确保拥有想要管理的远程计算机的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="5359f-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="5359f-140">你必须是远程计算机上的授权用户，并且必须将远程计算机配置为可远程管理。</span><span class="sxs-lookup"><span data-stu-id="5359f-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="5359f-141">有关将计算机配置为可远程管理的详细信息，请参阅[在 Windows PowerShell 中启用和使用远程命令](https://technet.microsoft.com/magazine/ff700227.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5359f-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="5359f-142">将计算机配置为可远程管理的最简单方法是：在使用提升的用户权限打开的 Windows PowerShell 会话中（**以管理员身份运行**），在计算机上运行**Enable-PSRemoting -force** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5359f-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="5359f-143">登录到 Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="5359f-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="5359f-144">在 Internet 浏览器窗口或选项卡中打开 Windows PowerShell Web 访问网站。</span><span class="sxs-lookup"><span data-stu-id="5359f-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="5359f-145">在 Windows PowerShell Web 访问登录页面中，提供你的网络用户名、密码以及你想管理（以及你是其授权用户）的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="5359f-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="5359f-146">如果 Windows PowerShell Web 访问管理员指示你将 URI（而非计算机名称）用于自定义网站或代理服务器，请在“连接类型”字段中选择“连接 URI”，然后提供 URI。</span><span class="sxs-lookup"><span data-stu-id="5359f-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="5359f-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="5359f-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="5359f-148">如果目标计算机在工作组中，则使用以下语法提供用户名并登录到计算机：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;。</span><span class="sxs-lookup"><span data-stu-id="5359f-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="5359f-149">如果目标计算机是网关服务器，则可在“计算机名”<strong></strong>字段中指定“localhost”<strong></strong>。</span><span class="sxs-lookup"><span data-stu-id="5359f-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="5359f-150">如果目标计算机是网关服务器，并且该网关服务器在工作组中，则可在“计算机名”<strong></strong>字段中使用 <strong>localhost</strong>，但不可在“用户名”<strong></strong>字段中使用 localhost\&lt;<em>user_name</em>&gt;。</span><span class="sxs-lookup"><span data-stu-id="5359f-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="5359f-151">必须使用 &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;。</span><span class="sxs-lookup"><span data-stu-id="5359f-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="5359f-152">“可选的连接设置”部分涉及你想要管理的远程计算机的授权要求。</span><span class="sxs-lookup"><span data-stu-id="5359f-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="5359f-153">有关与可选的连接设置等效的参数的详细信息，请参阅 [Enter-PSSession cmdlet 帮助](https://technet.microsoft.com/library/dd315384.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5359f-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="5359f-154">一般情况下，你用于通过 Windows PowerShell Web 访问网关的凭据与你想要管理的远程计算机所识别的凭据是一样的。</span><span class="sxs-lookup"><span data-stu-id="5359f-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="5359f-155">但是，如果你想要使用不同的凭据管理你在步骤 2 中指定的远程计算机，请展开“可选的连接设置”部分，并提供备用凭据。</span><span class="sxs-lookup"><span data-stu-id="5359f-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="5359f-156">否则，请跳到步骤 6。</span><span class="sxs-lookup"><span data-stu-id="5359f-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="5359f-157">如果 Windows PowerShell Web 访问管理员已经为 Windows PowerShell Web 访问用户创建了自定义会话配置，则在“配置名称”字段中键入会话配置名称。</span><span class="sxs-lookup"><span data-stu-id="5359f-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="5359f-158">有关会话配置的详细信息，请参阅 Microsoft 网站上的 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5359f-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="5359f-159">除非 Windows PowerShell Web 访问管理员指示你以其他方式处理，否则将“身份验证类型”设置保持为“默认”。</span><span class="sxs-lookup"><span data-stu-id="5359f-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="5359f-160">单击**登录**。</span><span class="sxs-lookup"><span data-stu-id="5359f-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="5359f-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">注销和超时</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="5359f-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="5359f-162">执行以下任一操作，均可注销基于 Web 的 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="5359f-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="5359f-163">在控制台的右下角单击“注销”。</span><span class="sxs-lookup"><span data-stu-id="5359f-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="5359f-164">（仅限 Windows Server 2012）</span><span class="sxs-lookup"><span data-stu-id="5359f-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="5359f-165">在控制台的右下角单击“保存”或“退出”（仅适用于 Windows Server 2012 R2）。</span><span class="sxs-lookup"><span data-stu-id="5359f-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="5359f-166">单击“保存”将保存并关闭你的 Windows PowerShell Web 访问会话；稍后可以重新连接到该会话。</span><span class="sxs-lookup"><span data-stu-id="5359f-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="5359f-167">再次登录到 Windows PowerShell Web 访问时，Windows PowerShell Web 访问将显示已保存会话的列表；你可以选择并重新连接到某个已保存的会话，也可以启动新的会话。</span><span class="sxs-lookup"><span data-stu-id="5359f-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="5359f-168">允许用户打开的最大会话数（包括已保存的会话和活动会话）由网关管理员配置。</span><span class="sxs-lookup"><span data-stu-id="5359f-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="5359f-169">单击“退出”将直接注销 Windows PowerShell Web 访问会话，而不保存该会话。</span><span class="sxs-lookup"><span data-stu-id="5359f-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="5359f-170">尝试登录，以便在相同的浏览器会话中或在相同浏览器会话的新选项卡中，管理不同的远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5359f-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="5359f-171">（这种情况不适用于运行 Windows Server 2012 R2 的网关服务器；Windows Server 2012 R2 上运行的 Windows PowerShell Web 访问允许在相同浏览器会话的新选项卡中打开多个用户会话。）有关如何在相同计算机上使用多个活动会话的详细信息，请参阅本主题[基于 Web 的控制台的限制](#BKMK_limits)部分中的“同时连接到多台目标计算机”。</span><span class="sxs-lookup"><span data-stu-id="5359f-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="5359f-172">会话停止活动 20 分钟。</span><span class="sxs-lookup"><span data-stu-id="5359f-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="5359f-173">网关管理员可以自定义停止活动超时时间；有关详细信息，请参阅[会话管理](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt)。</span><span class="sxs-lookup"><span data-stu-id="5359f-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="5359f-174">如果你从基于 Web 的控制台中的会话断开连接是由于网络错误或其他计划外关机或故障，而不是因为自己关闭了会话，Windows PowerShell Web 访问会话将继续运行并连接到目标计算机，直到客户端的超时期结束。</span><span class="sxs-lookup"><span data-stu-id="5359f-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="5359f-175">默认情况下，此超时期为 20 分钟，并由网关管理员配置。</span><span class="sxs-lookup"><span data-stu-id="5359f-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="5359f-176">会话在默认的 20 分钟或网关管理员指定的超时期（以时间较短者为准）后断开连接。</span><span class="sxs-lookup"><span data-stu-id="5359f-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="5359f-177">如果网关服务器正在运行 Windows Server 2012 R2，Windows PowerShell Web 访问将允许用户稍后重新连接到已保存的会话，但是，需在网关管理员指定的超时期过后，才能查看或重新连接到已保存的会话。</span><span class="sxs-lookup"><span data-stu-id="5359f-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="5359f-178">关闭浏览器窗口或选项卡。</span><span class="sxs-lookup"><span data-stu-id="5359f-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="5359f-179">关闭正在运行浏览器的客户端设备，或将它从网络中断开。</span><span class="sxs-lookup"><span data-stu-id="5359f-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="5359f-180">在 Web 控制台中运行“退出”命令。</span><span class="sxs-lookup"><span data-stu-id="5359f-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="5359f-181">如果已连接的会话配置为支持 [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) 模式，或处于受限的运行空间中，则此命令不可用。</span><span class="sxs-lookup"><span data-stu-id="5359f-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="5359f-182">如果你想再次登录，则再次打开 Windows PowerShell Web 访问网页，然后执行本主题中[登录到 Windows PowerShell Web 访问](#BKMK_signin)部分的以下步骤，即可登录。</span><span class="sxs-lookup"><span data-stu-id="5359f-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="5359f-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">基于 Web 的 Windows PowerShell 控制台的不同之处</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="5359f-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="5359f-184">在登录到 Windows PowerShell Web 访问之后, 在浏览器窗口或选项卡中将打开一个基于 Web 的 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="5359f-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="5359f-185">因为控制台连接到你在登录过程中指定的远程计算机，所以在控制台中仅可使用那些在远程计算机上可用的 Windows PowerShell cmdlet 或脚本。</span><span class="sxs-lookup"><span data-stu-id="5359f-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="5359f-186">本部分介绍 Windows PowerShell Web 访问控制台存在的限制，以及 Windows PowerShell Web 访问控制台和已安装的 **PowerShell.exe** 控制台之间的差异。</span><span class="sxs-lookup"><span data-stu-id="5359f-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="5359f-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">PowerShell.exe 的功能差异</span></a></span><span class="sxs-lookup"><span data-stu-id="5359f-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="5359f-188">大多数 Windows PowerShell 主机功能都可在 Windows PowerShell Web 访问基于 Web 的控制台中使用，但有些功能则不可用。</span><span class="sxs-lookup"><span data-stu-id="5359f-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="5359f-189"><span class="label">将会显示嵌套的进度。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="5359f-190">Windows PowerShell Web 访问显示 cmdlet 的进度 GUI（报告进度），但仅显示最高层的进度信息。</span><span class="sxs-lookup"><span data-stu-id="5359f-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="5359f-191"><span class="label">输入颜色修改。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="5359f-192">无法更改输入颜色（前景和背景）。</span><span class="sxs-lookup"><span data-stu-id="5359f-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="5359f-193">输出风格、警告、详细和错误信息均可通过运行脚本进行更改。</span><span class="sxs-lookup"><span data-stu-id="5359f-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="5359f-194"><span class="label">PSHostRawUserInterface。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="5359f-195">Windows PowerShell Web 访问通过 Windows PowerShell 远程管理实施，并且使用远程运行空间。</span><span class="sxs-lookup"><span data-stu-id="5359f-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="5359f-196">Windows PowerShell Web 访问在此界面不执行一些方法；例如，任何写入 Windows 控制台的命令。</span><span class="sxs-lookup"><span data-stu-id="5359f-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="5359f-197">**PowerTab** 等命令在 Windows PowerShell Web 访问中不起作用。</span><span class="sxs-lookup"><span data-stu-id="5359f-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="5359f-198"><span class="label">功能键。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="5359f-199">在许多种情况下，Windows PowerShell Web 访问并不支持一些功能键，因为浏览器保留了此类命令。</span><span class="sxs-lookup"><span data-stu-id="5359f-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="5359f-200">不受支持的功能键</span><span class="sxs-lookup"><span data-stu-id="5359f-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="5359f-201">操作</span><span class="sxs-lookup"><span data-stu-id="5359f-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5359f-202">Ctrl+C</span><span class="sxs-lookup"><span data-stu-id="5359f-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="5359f-203">在 Windows PowerShell Web 访问中，浏览器使用 <strong>Ctrl + C</strong> 复制内容。</span><span class="sxs-lookup"><span data-stu-id="5359f-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="5359f-204">控制台提供“取消”<strong></strong>按钮，用户还可使用 <strong>Ctrl+Q</strong> 来取消命令。</span><span class="sxs-lookup"><span data-stu-id="5359f-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-205">Alt-space、e、l</span><span class="sxs-lookup"><span data-stu-id="5359f-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="5359f-206">滚动屏幕缓冲区</span><span class="sxs-lookup"><span data-stu-id="5359f-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-207">Alt+Space、e、f</span><span class="sxs-lookup"><span data-stu-id="5359f-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="5359f-208">搜索屏幕缓冲区中的文本</span><span class="sxs-lookup"><span data-stu-id="5359f-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-209">Alt+Space、e、k</span><span class="sxs-lookup"><span data-stu-id="5359f-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="5359f-210">选择从屏幕缓冲区中复制而来的文本</span><span class="sxs-lookup"><span data-stu-id="5359f-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-211">Alt+Space、e、p</span><span class="sxs-lookup"><span data-stu-id="5359f-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="5359f-212">将剪贴板内容粘贴到 Windows PowerShell 控制台</span><span class="sxs-lookup"><span data-stu-id="5359f-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-213">Alt+Space、c</span><span class="sxs-lookup"><span data-stu-id="5359f-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="5359f-214">关闭 Windows PowerShell 控制台</span><span class="sxs-lookup"><span data-stu-id="5359f-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-215">Ctrl+Break</span><span class="sxs-lookup"><span data-stu-id="5359f-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="5359f-216">强制关闭 Windows PowerShell 窗口</span><span class="sxs-lookup"><span data-stu-id="5359f-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-217">Ctrl+Home</span><span class="sxs-lookup"><span data-stu-id="5359f-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="5359f-218">从当前命令行的开始部分删除</span><span class="sxs-lookup"><span data-stu-id="5359f-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-219">Ctrl+End</span><span class="sxs-lookup"><span data-stu-id="5359f-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="5359f-220">在命令行的末尾结束删除</span><span class="sxs-lookup"><span data-stu-id="5359f-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-221">F1</span><span class="sxs-lookup"><span data-stu-id="5359f-221">F1</span></span></p></td>
<td><p><span data-ttu-id="5359f-222">将光标向命令行的右侧移动一个字符</span><span class="sxs-lookup"><span data-stu-id="5359f-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-223">F2</span><span class="sxs-lookup"><span data-stu-id="5359f-223">F2</span></span></p></td>
<td><p><span data-ttu-id="5359f-224">通过将最后一个命令复制到你键入的字符，创建新的命令</span><span class="sxs-lookup"><span data-stu-id="5359f-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-225">F3</span><span class="sxs-lookup"><span data-stu-id="5359f-225">F3</span></span></p></td>
<td><p><span data-ttu-id="5359f-226">用最后一个命令行中的内容完成命令行</span><span class="sxs-lookup"><span data-stu-id="5359f-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-227">F4</span><span class="sxs-lookup"><span data-stu-id="5359f-227">F4</span></span></p></td>
<td><p><span data-ttu-id="5359f-228">从光标位置删除字符</span><span class="sxs-lookup"><span data-stu-id="5359f-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-229">F5</span><span class="sxs-lookup"><span data-stu-id="5359f-229">F5</span></span></p></td>
<td><p><span data-ttu-id="5359f-230">向后扫描你的命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="5359f-230">Scan backward through your command history.</span></span> <span data-ttu-id="5359f-231">若要访问 Windows PowerShell Web 访问的命令历史记录中的命令，请在基于 Web 的控制台中单击“历史记录”<strong></strong>滚动按钮。</span><span class="sxs-lookup"><span data-stu-id="5359f-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-232">F7</span><span class="sxs-lookup"><span data-stu-id="5359f-232">F7</span></span></p></td>
<td><p><span data-ttu-id="5359f-233">从命令历史记录中交互选择一个命令</span><span class="sxs-lookup"><span data-stu-id="5359f-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-234">F8</span><span class="sxs-lookup"><span data-stu-id="5359f-234">F8</span></span></p></td>
<td><p><span data-ttu-id="5359f-235">扫描与当前文本匹配的历史记录显示命令</span><span class="sxs-lookup"><span data-stu-id="5359f-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-236">F9</span><span class="sxs-lookup"><span data-stu-id="5359f-236">F9</span></span></p></td>
<td><p><span data-ttu-id="5359f-237">运行历史记录中特定编号的命令</span><span class="sxs-lookup"><span data-stu-id="5359f-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-238">Page Up</span><span class="sxs-lookup"><span data-stu-id="5359f-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="5359f-239">运行历史记录中的第一个命令</span><span class="sxs-lookup"><span data-stu-id="5359f-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5359f-240">Page Down</span><span class="sxs-lookup"><span data-stu-id="5359f-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="5359f-241">运行历史记录中的最后一个命令</span><span class="sxs-lookup"><span data-stu-id="5359f-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5359f-242">Alt+F7</span><span class="sxs-lookup"><span data-stu-id="5359f-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="5359f-243">清空命令历史记录列表</span><span class="sxs-lookup"><span data-stu-id="5359f-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="5359f-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Web 控制台限制</span></a></span><span class="sxs-lookup"><span data-stu-id="5359f-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="5359f-245"><span class="label">双跃点。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="5359f-246">如果尝试通过使用 Windows PowerShell Web 访问来创建或运行新的会话，你会遇到双跃点（或从第一个连接到第二台计算机之间的连接）限制。</span><span class="sxs-lookup"><span data-stu-id="5359f-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="5359f-247">Windows PowerShell Web 访问使用远程运行空间，目前，**PowerShell.exe** 不支持建立从远程运行空间到第二台计算机的远程连接。</span><span class="sxs-lookup"><span data-stu-id="5359f-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="5359f-248">例如，如果你尝试使用 **Enter-PSSession** cmdlet 从现有的连接连接到第二台远程计算机，你会遇到各种错误，例如“无法获得网络资源”。</span><span class="sxs-lookup"><span data-stu-id="5359f-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="5359f-249">若要避免双跃点错误，你的管理员应在你组织的网络环境中配置 CredSSP 身份验证。</span><span class="sxs-lookup"><span data-stu-id="5359f-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="5359f-250">有关如何配置 CredSSP 身份验证的详细信息，请参阅 Microsoft 网站上的[适用于第二跃点远程处理的 CredSSP](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5359f-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="5359f-251">当你想要管理第二台远程计算机时，你还可提供显式凭据；隐式凭据不可能接受第二跃点。</span><span class="sxs-lookup"><span data-stu-id="5359f-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="5359f-252">Windows PowerShell Web 访问使用远程 Windows PowerShell 会话并具有与它相同的限制。</span><span class="sxs-lookup"><span data-stu-id="5359f-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="5359f-253">直接调用 Windows 控制台 API 的命令（例如基于控制台的编辑器或基于文本的菜单程序）不可用，因为此类命令不可读取或写入标准的输入、输出和错误管道。</span><span class="sxs-lookup"><span data-stu-id="5359f-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="5359f-254">因此，启用可执行文件（如 **notepad.exe**）或显示 GUI（如 <span class="code">OpenGridView</span> 或 <span class="code">ogv</span>）的命令不可用。</span><span class="sxs-lookup"><span data-stu-id="5359f-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="5359f-255">此操作将影响你的体验；你会觉得好像 Windows PowerShell Web 访问并不响应你的命令。</span><span class="sxs-lookup"><span data-stu-id="5359f-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="5359f-256">Tab 自动补全不适用于带有受限运行空间的会话配置或在 **NoLanguage** 模式下的会话配置。</span><span class="sxs-lookup"><span data-stu-id="5359f-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="5359f-257">虽然管理员可以配置会话以支持选项卡完成，但出于安全考虑，建议不要这样做，因为此操作会向未授权用户披露以下信息。</span><span class="sxs-lookup"><span data-stu-id="5359f-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="5359f-258">内部文件系统路径</span><span class="sxs-lookup"><span data-stu-id="5359f-258">Internal file system paths</span></span>

    -   <span data-ttu-id="5359f-259">内部计算机上的共享文件夹</span><span class="sxs-lookup"><span data-stu-id="5359f-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="5359f-260">运行空间中的变量</span><span class="sxs-lookup"><span data-stu-id="5359f-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="5359f-261">已加载的类型或 .NET Framework 名称空间</span><span class="sxs-lookup"><span data-stu-id="5359f-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="5359f-262">环境变量</span><span class="sxs-lookup"><span data-stu-id="5359f-262">Environment variables</span></span>

-   <span data-ttu-id="5359f-263">登录到 **NoLanguage** 会话配置或 Windows PowerShell Web 访问的受限运行空间的用户不能运行“退出”命令以结束会话。</span><span class="sxs-lookup"><span data-stu-id="5359f-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="5359f-264">若要注销，用户应在控制台页面上单击“注销”。</span><span class="sxs-lookup"><span data-stu-id="5359f-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="5359f-265"><span class="label">同时连接到多台目标计算机。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="5359f-266">如果网关服务器正在运行 Windows Server 2012，Windows PowerShell Web 访问仅允许每个浏览器会话连接一台远程计算机；它不允许用户只登录一次，即使用独立的浏览器选项卡连接到多台远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5359f-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="5359f-267">当你打开新的选项卡或浏览器窗口时，Windows PowerShell Web 访问将提示你断开当前的会话，并启动新的会话，以使你可以连接到新的（或相同的）远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5359f-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="5359f-268">但是，如果不同的远程计算机需要两个或更多独立会话，Internet Explorer 中的某一功能可让你创建新的会话。</span><span class="sxs-lookup"><span data-stu-id="5359f-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="5359f-269">若要在 Internet Explorer 中启动新的浏览器会话，请按下 **ALT**，打开“文件”菜单，然后选择“新建会话”。</span><span class="sxs-lookup"><span data-stu-id="5359f-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="5359f-270">随后在新的会话中打开 Windows PowerShell Web 访问网站，登录即可访问其他远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5359f-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="5359f-271">当 Windows PowerShell Web 访问网关在 Windows Server 2012 R2 上运行时，用户可以在不同的浏览器选项卡中打开与远程计算机之间的多个连接。</span><span class="sxs-lookup"><span data-stu-id="5359f-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="5359f-272">如果想要使用基于 Web 的 Windows PowerShel 控制台打开与远程计算机之间的多个连接，请咨询 Windows PowerShell Web 访问网关管理员，了解网关服务器是否支持此功能。</span><span class="sxs-lookup"><span data-stu-id="5359f-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="5359f-273"><span class="label">持续的 Windows PowerShell 会话 （重新连接）。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="5359f-274">Windows PowerShell Web 访问网关超时后，网关和目标计算机之间的远程连接将关闭。</span><span class="sxs-lookup"><span data-stu-id="5359f-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="5359f-275">这会阻止当前正在运行的任何 cmdlet 或脚本。</span><span class="sxs-lookup"><span data-stu-id="5359f-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="5359f-276">当你执行长时间运行的任务时，建议使用 **-Job** 基础结构，这样就可以启动作业，断开计算机的连接，稍后重新连接，让作业持续进行。</span><span class="sxs-lookup"><span data-stu-id="5359f-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="5359f-277">使用 **-Job** cmdlet 的另一个好处是可以使用 Windows PowerShell Web 访问启动它们，注销并通过运行 Windows PowerShell Web 访问或另一台主机（如 Windows PowerShell® 集成脚本环境 (ISE)）来重新连接它们。</span><span class="sxs-lookup"><span data-stu-id="5359f-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="5359f-278"><span class="label">调整控制台大小。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="5359f-279">可通过以下三种方式调整 **PowerShell.exe** 控制台窗口大小。</span><span class="sxs-lookup"><span data-stu-id="5359f-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="5359f-280">拖动并使用鼠标调整控制台窗口大小</span><span class="sxs-lookup"><span data-stu-id="5359f-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="5359f-281">使用控制台属性的 GUI，更改高度和宽度属性</span><span class="sxs-lookup"><span data-stu-id="5359f-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="5359f-282">使用 cmdlet，更改控制台窗口的高度和宽度</span><span class="sxs-lookup"><span data-stu-id="5359f-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="5359f-283">可按以下方式使用 cmdlet 来配置 Windows PowerShell Web 访问控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="5359f-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="5359f-284">在下例中，用户将 Windows PowerShell Web 访问控制台的宽度更改为**20**。</span><span class="sxs-lookup"><span data-stu-id="5359f-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="5359f-285">Copy</span><span class="sxs-lookup"><span data-stu-id="5359f-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copy to clipboard.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="5359f-286">你可以使用类似的方式更改控制台的高度。</span><span class="sxs-lookup"><span data-stu-id="5359f-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="5359f-287">如要获取自定义控制台视图的其他示例，请参阅 [Windows PowerShell 团队博客](http://blogs.msdn.com/b/powershell/)。</span><span class="sxs-lookup"><span data-stu-id="5359f-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="5359f-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="5359f-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="5359f-289">[Windows PowerShell Cmdlet 参考](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[ Microsoft TechNet 上的 Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet 脚本中心存储库](http://gallery.technet.microsoft.com/scriptcenter)
[脚本中心 - 嗨，脚本专家！](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell 团队博客](http://blogs.msdn.com/b/powershell/)</span><span class="sxs-lookup"><span data-stu-id="5359f-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="5359f-290"><span>显示：</span>继承内容受保护</span><span class="sxs-lookup"><span data-stu-id="5359f-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="5359f-291"><span class="stdr-votetitle">此页面是否有所帮助？</span></span><span class="sxs-lookup"><span data-stu-id="5359f-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="5359f-292">是 否</span><span class="sxs-lookup"><span data-stu-id="5359f-292">Yes No</span></span>

<span data-ttu-id="5359f-293">更多反馈？</span><span class="sxs-lookup"><span data-stu-id="5359f-293">Additional feedback?</span></span>

<span data-ttu-id="5359f-294">剩余 <span class="stdr-count"><span class="stdr-charcnt">1500</span> 个字符</span>提交，跳过此部分</span><span class="sxs-lookup"><span data-stu-id="5359f-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="5359f-295"><span class="stdr-thankyou">谢谢！</span></span><span class="sxs-lookup"><span data-stu-id="5359f-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="5359f-296"><span class="stdr-appreciate">我们非常感谢你的反馈意见。</span></span><span class="sxs-lookup"><span data-stu-id="5359f-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="5359f-297">管理个人资料</span><span class="sxs-lookup"><span data-stu-id="5359f-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="5359f-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span>站点反馈</a>站点反馈</span><span class="sxs-lookup"><span data-stu-id="5359f-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="5359f-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="5359f-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="5359f-300">告诉我们你的体验...</span><span class="sxs-lookup"><span data-stu-id="5359f-300">Tell us about your experience...</span></span>

<span data-ttu-id="5359f-301">页面加载速度快吗？</span><span class="sxs-lookup"><span data-stu-id="5359f-301">Did the page load quickly?</span></span>

<span data-ttu-id="5359f-302"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="5359f-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="5359f-303">你喜欢页面设计吗？</span><span class="sxs-lookup"><span data-stu-id="5359f-303">Do you like the page design?</span></span>

<span data-ttu-id="5359f-304"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="5359f-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="5359f-305">告诉我们更多内容</span><span class="sxs-lookup"><span data-stu-id="5359f-305">Tell us more</span></span>

-   [<span data-ttu-id="5359f-306">快讯</span><span class="sxs-lookup"><span data-stu-id="5359f-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="5359f-307">联系我们</span><span class="sxs-lookup"><span data-stu-id="5359f-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="5359f-308">隐私声明</span><span class="sxs-lookup"><span data-stu-id="5359f-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="5359f-309">使用条款</span><span class="sxs-lookup"><span data-stu-id="5359f-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="5359f-310">商标</span><span class="sxs-lookup"><span data-stu-id="5359f-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="5359f-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="5359f-311">© 2016 Microsoft</span></span>

<span data-ttu-id="5359f-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="5359f-312">© 2016 Microsoft</span></span>

<span data-ttu-id="5359f-313">链接到此站点或从中引用的第三方脚本或代码由拥有此类代码的第三方（而非 Microsoft）授权给你。</span><span class="sxs-lookup"><span data-stu-id="5359f-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="5359f-314">请参阅 ASP.NET Ajax CDN 使用条款，网址为 http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="5359f-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />


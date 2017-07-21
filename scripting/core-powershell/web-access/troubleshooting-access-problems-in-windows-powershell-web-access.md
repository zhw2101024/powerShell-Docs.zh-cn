---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell Web 访问中的访问问题疑难解答"
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="303d0-103">Windows PowerShell Web 访问中的访问问题疑难解答</span><span class="sxs-lookup"><span data-stu-id="303d0-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="303d0-104">更新时间： 2013年 6 月 24日</span><span class="sxs-lookup"><span data-stu-id="303d0-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="303d0-105">适用于：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="303d0-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="303d0-106">下表识别了一些用户使用 Windows PowerShell Web 访问尝试连接到远程计算机时可能遇到的常见问题，其中包括解决这些问题的建议。</span><span class="sxs-lookup"><span data-stu-id="303d0-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="303d0-107">问题</span><span class="sxs-lookup"><span data-stu-id="303d0-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="303d0-108">可能原因和解决方案</span><span class="sxs-lookup"><span data-stu-id="303d0-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="303d0-109">登录失败</span><span class="sxs-lookup"><span data-stu-id="303d0-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="303d0-110">失败可能是由于下列某个原因所至：</span><span class="sxs-lookup"><span data-stu-id="303d0-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="303d0-111">允许用户访问计算机的授权规则或远程计算机上的特定会话配置并不存在。</span><span class="sxs-lookup"><span data-stu-id="303d0-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="303d0-112">Windows PowerShell Web 访问安全是严谨的；必须使用授权规则明确赋予用户访问远程计算机的权限。</span><span class="sxs-lookup"><span data-stu-id="303d0-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="303d0-113">有关创建授权规则的详细信息，请参阅本指南中的 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 访问的授权规则和安全功能</a>。</span><span class="sxs-lookup"><span data-stu-id="303d0-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="303d0-114">用户未获得访问目标计算机的权限。</span><span class="sxs-lookup"><span data-stu-id="303d0-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="303d0-115">这是由访问控制列表 (ACL) 来确定的。</span><span class="sxs-lookup"><span data-stu-id="303d0-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="303d0-116">有关详细信息，请参阅<a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">使用基于 Web 的 Windows PowerShell 控制台</a>中的“登录到 Windows PowerShell Web 访问”或 <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>（Windows PowerShell 团队博客）。</span><span class="sxs-lookup"><span data-stu-id="303d0-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="303d0-117">可能无法在目标计算机上启用 Windows PowerShell 远程管理。</span><span class="sxs-lookup"><span data-stu-id="303d0-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="303d0-118">验证它是否已在用户尝试连接的计算机上启用。</span><span class="sxs-lookup"><span data-stu-id="303d0-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="303d0-119">有关详细信息，请参阅 Windows PowerShell 相关帮助主题中 <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> 的“如何为进行远程处理而配置计算机”。</span><span class="sxs-lookup"><span data-stu-id="303d0-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="303d0-120">当用户尝试在 Internet Explorer 窗口中登录到 Windows PowerShell Web 访问时，会向他们显示“内部服务器错误”<strong></strong>页面或 Internet Explorer 停止响应。</span><span class="sxs-lookup"><span data-stu-id="303d0-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="303d0-121">此问题特定于 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="303d0-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="303d0-122">对于已使用包含中文字符的域名登录的用户或网关服务器名称中包含一个或多个中文字符时会出现此问题。</span><span class="sxs-lookup"><span data-stu-id="303d0-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="303d0-123">若要解决此问题，用户应<a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">安装并运行 Internet Explorer 10</a>，然后执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="303d0-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="303d0-124">将 Internet Explorer“文档模式”<strong></strong>设置更改为“IE10 标准”<strong></strong>。</span><span class="sxs-lookup"><span data-stu-id="303d0-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="303d0-125">按 <strong>F12</strong> 可打开“开发人员工具”控制台。</span><span class="sxs-lookup"><span data-stu-id="303d0-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="303d0-126">在 Internet Explorer 10 中，单击“浏览器模式”<strong></strong>，然后选择“Internet Explorer 10”<strong></strong>。</span><span class="sxs-lookup"><span data-stu-id="303d0-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="303d0-127">单击“文档模式”<strong></strong>，然后单击“IE10 标准”<strong></strong>。</span><span class="sxs-lookup"><span data-stu-id="303d0-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="303d0-128">再次按 <strong>F12</strong> 可关闭“开发人员工具”控制台。</span><span class="sxs-lookup"><span data-stu-id="303d0-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="303d0-129">禁用自动代理配置。</span><span class="sxs-lookup"><span data-stu-id="303d0-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="303d0-130">在 Internet Explorer 10 中，单击“工具”<strong></strong>，然后单击“Internet 选项”<strong></strong>。</span><span class="sxs-lookup"><span data-stu-id="303d0-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="303d0-131">在“Internet 选项”<strong></strong>对话框中的“连接”<strong></strong>选项卡上，单击“LAN 设置”<strong></strong>。</span><span class="sxs-lookup"><span data-stu-id="303d0-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="303d0-132">清除“自动检测设置”<strong></strong>复选框。</span><span class="sxs-lookup"><span data-stu-id="303d0-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="303d0-133">单击“确定”<strong></strong>，然后再次单击“确定”<strong></strong>可关闭“Internet 选项”<strong></strong>对话框。</span><span class="sxs-lookup"><span data-stu-id="303d0-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="303d0-134">无法连接到远程工作组计算机</span><span class="sxs-lookup"><span data-stu-id="303d0-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="303d0-135">如果目标计算机在工作组中，则使用以下语法，提供用户名，并且登录到计算机：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span><span class="sxs-lookup"><span data-stu-id="303d0-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="303d0-136">找不到 Web 服务器 (IIS) 管理工具，即使已安装了角色</span><span class="sxs-lookup"><span data-stu-id="303d0-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="303d0-137">如果你通过使用 <span class="code">Install-WindowsFeature</span> cmdlet 安装了 Windows PowerShell Web 访问，则不会安装管理工具，除非将 <span class="code">IncludeManagementTools</span> 参数添加到该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="303d0-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="303d0-138">例如，参阅<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">安装和使用 Windows PowerShell Web 访问</a>中的“使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问”。</span><span class="sxs-lookup"><span data-stu-id="303d0-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="303d0-139">你可选择在以网关服务器为目标的“添加角色和功能向导”会话中的工具，添加 IIS 管理器控制台及其他你需要的 IIS 管理工具。</span><span class="sxs-lookup"><span data-stu-id="303d0-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="303d0-140">“添加角色和功能向导”可从服务器管理器中打开。</span><span class="sxs-lookup"><span data-stu-id="303d0-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="303d0-141">无法访问 Windows PowerShell Web 访问网站</span><span class="sxs-lookup"><span data-stu-id="303d0-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="303d0-142">如果已在 Internet Explorer 中启用了增强的安全配置 (IE ESC)，你可以将 Windows PowerShell Web 访问网站添加到受信任的站点列表，或禁用 IE ESC。</span><span class="sxs-lookup"><span data-stu-id="303d0-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="303d0-143">你可以在服务器管理器中的“本地服务器”<strong></strong>页面上的“属性”<strong></strong>磁贴中禁用 IE ESC。</span><span class="sxs-lookup"><span data-stu-id="303d0-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="303d0-144">尝试当网关服务器为目标计算机且又位于工作组中时连接，会显示以下错误消息：“出现授权失败。”<strong>请确认是否已获准连接目标计算机。</strong></span><span class="sxs-lookup"><span data-stu-id="303d0-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="303d0-145">当网关服务器也是目标服务器且位于工作组中时，指定下表所示的用户名、计算机名称以及用户组名。</span><span class="sxs-lookup"><span data-stu-id="303d0-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="303d0-146">不要使用点 (.) 自行表示计算机名称。</span><span class="sxs-lookup"><span data-stu-id="303d0-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="303d0-147">方案</span><span class="sxs-lookup"><span data-stu-id="303d0-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="303d0-148">UserName 参数</span><span class="sxs-lookup"><span data-stu-id="303d0-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="303d0-149">UserGroup 参数</span><span class="sxs-lookup"><span data-stu-id="303d0-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="303d0-150">ComputerName 参数</span><span class="sxs-lookup"><span data-stu-id="303d0-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="303d0-151">ComputerGroup 参数</span><span class="sxs-lookup"><span data-stu-id="303d0-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="303d0-152">网关服务器位于域中</span><span class="sxs-lookup"><span data-stu-id="303d0-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="303d0-153">Server_name<em></em>\user_name<em></em>、Localhost\user_name<em></em> 或 .\user_name<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="303d0-154">Server_name<em></em>\user_group<em></em>、Localhost\user_group<em></em> 或 .\user_group<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="303d0-155">网关服务器的完全限定名称或 Localhost</span><span class="sxs-lookup"><span data-stu-id="303d0-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="303d0-156">Server_name<em></em>\computer_group<em></em>、Localhost\computer_group<em></em> 或 .\computer_group<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="303d0-157">网关服务器位于工作组中</span><span class="sxs-lookup"><span data-stu-id="303d0-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="303d0-158">Server_name<em></em>\user_name<em></em>、Localhost\user_name<em></em> 或 .\user_name<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="303d0-159">Server_name<em></em>\user_group<em></em>、Localhost\user_group<em></em> 或 .\user_group<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="303d0-160">服务器名称</span><span class="sxs-lookup"><span data-stu-id="303d0-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="303d0-161">Server_name<em></em>\computer_group<em></em>、Localhost\computer_group<em></em> 或 .\computer_group<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="303d0-162">以目标计算机身份登录到网关服务器，方法是使用以下格式之一的凭据。</span><span class="sxs-lookup"><span data-stu-id="303d0-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="303d0-163">Server_name<em></em>\user_name<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="303d0-164">Localhost\user_name<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="303d0-165">.\user_name<em></em></span><span class="sxs-lookup"><span data-stu-id="303d0-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="303d0-166">在授权规则中显示安全标识符 (SID) 而不是语法 <em>user_name</em>/<em>computer_name</em> </span><span class="sxs-lookup"><span data-stu-id="303d0-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="303d0-167">规则不再有效或 Active Directory 域服务查询失败。</span><span class="sxs-lookup"><span data-stu-id="303d0-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="303d0-168">如果网关服务器曾一时位于工作组中，但后来加入域中，则这种情形下通常授权规则无效。</span><span class="sxs-lookup"><span data-stu-id="303d0-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="303d0-169">无法登录到已在授权规则中指定为带有域的 IPv6 地址的目标计算机。</span><span class="sxs-lookup"><span data-stu-id="303d0-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="303d0-170">授权规则不支持域名形式的 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="303d0-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="303d0-171">若要使用 IPv6 地址指定目标计算机，请在授权规则中使用原始 IPv6 地址（包含冒号）。</span><span class="sxs-lookup"><span data-stu-id="303d0-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="303d0-172">支持域和数值（带有冒号）IPv6 地址作为 Windows PowerShell Web 访问登录页面而非授权规则中的目标计算机名称。</span><span class="sxs-lookup"><span data-stu-id="303d0-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="303d0-173">有关 IPv6 地址的详细信息，请参阅 <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>（IPv6 的工作原理）。</span><span class="sxs-lookup"><span data-stu-id="303d0-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="303d0-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="303d0-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="303d0-175">[Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about\_Remote\_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="303d0-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="303d0-176"><span>显示：</span>继承内容受保护</span><span class="sxs-lookup"><span data-stu-id="303d0-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="303d0-177"><span class="stdr-votetitle">此页面是否有所帮助？</span></span><span class="sxs-lookup"><span data-stu-id="303d0-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="303d0-178">是 否</span><span class="sxs-lookup"><span data-stu-id="303d0-178">Yes No</span></span>

<span data-ttu-id="303d0-179">更多反馈？</span><span class="sxs-lookup"><span data-stu-id="303d0-179">Additional feedback?</span></span>

<span data-ttu-id="303d0-180">剩余 <span class="stdr-count"><span class="stdr-charcnt">1500</span> 个字符</span>提交，跳过此部分</span><span class="sxs-lookup"><span data-stu-id="303d0-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="303d0-181"><span class="stdr-thankyou">谢谢！</span></span><span class="sxs-lookup"><span data-stu-id="303d0-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="303d0-182"><span class="stdr-appreciate">我们非常感谢你的反馈意见。</span></span><span class="sxs-lookup"><span data-stu-id="303d0-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="303d0-183">管理个人资料</span><span class="sxs-lookup"><span data-stu-id="303d0-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="303d0-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span>站点反馈</a>站点反馈</span><span class="sxs-lookup"><span data-stu-id="303d0-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="303d0-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="303d0-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="303d0-186">告诉我们你的体验...</span><span class="sxs-lookup"><span data-stu-id="303d0-186">Tell us about your experience...</span></span>

<span data-ttu-id="303d0-187">页面加载速度快吗？</span><span class="sxs-lookup"><span data-stu-id="303d0-187">Did the page load quickly?</span></span>

<span data-ttu-id="303d0-188"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="303d0-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="303d0-189">你喜欢页面设计吗？</span><span class="sxs-lookup"><span data-stu-id="303d0-189">Do you like the page design?</span></span>

<span data-ttu-id="303d0-190"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="303d0-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="303d0-191">告诉我们更多内容</span><span class="sxs-lookup"><span data-stu-id="303d0-191">Tell us more</span></span>

-   [<span data-ttu-id="303d0-192">快讯</span><span class="sxs-lookup"><span data-stu-id="303d0-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="303d0-193">联系我们</span><span class="sxs-lookup"><span data-stu-id="303d0-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="303d0-194">隐私声明</span><span class="sxs-lookup"><span data-stu-id="303d0-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="303d0-195">使用条款</span><span class="sxs-lookup"><span data-stu-id="303d0-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="303d0-196">商标</span><span class="sxs-lookup"><span data-stu-id="303d0-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="303d0-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="303d0-197">© 2016 Microsoft</span></span>

<span data-ttu-id="303d0-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="303d0-198">© 2016 Microsoft</span></span>

<span data-ttu-id="303d0-199">链接到此站点或从中引用的第三方脚本或代码由拥有此类代码的第三方（而非 Microsoft）授权给你。</span><span class="sxs-lookup"><span data-stu-id="303d0-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="303d0-200">请参阅 ASP.NET Ajax CDN 使用条款，网址为 http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="303d0-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />


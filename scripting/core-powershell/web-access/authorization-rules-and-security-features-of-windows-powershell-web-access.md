---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell Web 访问的授权规则和安全功能"
ms.openlocfilehash: 706830f618173879185f5b84570fdc7782434d59
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a><span data-ttu-id="72abf-103">Windows PowerShell Web 访问的授权规则和安全功能</span><span class="sxs-lookup"><span data-stu-id="72abf-103">Authorization Rules and Security Features of Windows PowerShell Web Access</span></span>

<span data-ttu-id="72abf-104">更新时间： 2013年 6 月 24日</span><span class="sxs-lookup"><span data-stu-id="72abf-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="72abf-105">适用于：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="72abf-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="72abf-106">在 Windows Server® 2012 R2 和 Windows Server® 2012 中的 Windows PowerShell® Web 访问具有受限的安全模型。</span><span class="sxs-lookup"><span data-stu-id="72abf-106">Windows PowerShell® Web Access in Windows Server® 2012 R2 and Windows Server® 2012 has a restrictive security model.</span></span> <span data-ttu-id="72abf-107">必须向用户显式授予访问权限，他们才能登录 Windows PowerShell Web 访问网关和使用基于 Web 的 Windows PowerShell 控制台。</span><span class="sxs-lookup"><span data-stu-id="72abf-107">Users must explicitly be granted access before they can sign in to the Windows PowerShell Web Access gateway and use the web-based Windows PowerShell console.</span></span>

-   [<span data-ttu-id="72abf-108">配置授权规则和站点安全</span><span class="sxs-lookup"><span data-stu-id="72abf-108">Configuring authorization rules and site security</span></span>](#BKMK_auth)

-   [<span data-ttu-id="72abf-109">会话管理</span><span class="sxs-lookup"><span data-stu-id="72abf-109">Session management</span></span>](#BKMK_sesmgmt)


<span data-ttu-id="72abf-110">安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-110">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="72abf-111">Windows PowerShell Web 访问的访问控制通过使用下表所述的 Windows PowerShell cmdlet 集进行管理。</span><span class="sxs-lookup"><span data-stu-id="72abf-111">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="72abf-112">没有相当的 GUI 可用于添加或管理授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-112">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="72abf-113">有关 Windows PowerShell Web 访问 cmdlet 的更多详细信息，请参阅 cmdlet 参考主题 [Windows PowerShell Web 访问 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)。</span><span class="sxs-lookup"><span data-stu-id="72abf-113">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="72abf-114">管理员可以为 Windows PowerShell Web 访问定义 0-n 条身份验证规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-114">Administrators can define 0-*n* authentication rules for Windows PowerShell Web Access.</span></span> <span data-ttu-id="72abf-115">默认的安全性较为严格，而非宽松；零条身份验证规则意味着无用户可访问任何内容。</span><span class="sxs-lookup"><span data-stu-id="72abf-115">The default security is restrictive rather than permissive; zero authentication rules means no users have access to anything.</span></span>

<span data-ttu-id="72abf-116">Windows Server 2012 R2 中的 Add-PswaAuthorizationRule 和 Test-PswaAuthorizationRule 包含一个 Credential 参数，该参数允许你从远程计算机或在活动的 Windows PowerShell Web 访问会话中添加和测试 Windows PowerShell Web 访问授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-116">Add-PswaAuthorizationRule and Test-PswaAuthorizationRule in Windows Server 2012 R2 include a Credential parameter that allows you to add and test Windows PowerShell Web Access authorization rules from a remote computer, or from within an active Windows PowerShell Web Access session.</span></span> <span data-ttu-id="72abf-117">与其他具有 Credential 参数的 Windows PowerShell cmdlet 一样，你可以指定一个 PSCredential 对象作为该参数的值。</span><span class="sxs-lookup"><span data-stu-id="72abf-117">As with other Windows PowerShell cmdlets that have a Credential parameter, you can specify a PSCredential object as the value of the parameter.</span></span> <span data-ttu-id="72abf-118">若要创建一个包含要传递到远程计算机的凭据的 PSCredential 对象，请运行 [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72abf-118">To create a PSCredential object that contains credentials you want to pass to a remote computer, run the [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx) cmdlet.</span></span>

<span data-ttu-id="72abf-119">Windows PowerShell Web 访问身份验证规则是白名单规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-119">Windows PowerShell Web Access authentication rules are whitelist rules.</span></span> <span data-ttu-id="72abf-120">每条规则定义了用户、目标计算机和特定的Windows PowerShell [会话配置](https://technet.microsoft.com/library/dd819508.aspx)（也称作终结点或运行空间）在特定目标计算机上的允许连接。</span><span class="sxs-lookup"><span data-stu-id="72abf-120">Each rule is a definition of an allowed connection between users, target computers, and particular Windows PowerShell [session configurations](https://technet.microsoft.com/library/dd819508.aspx) (also referred to as endpoints or runspaces) on specified target computers.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="72abf-121"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全说明 </span></span><span class="sxs-lookup"><span data-stu-id="72abf-121"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="72abf-122">用户仅需要一条可访问的规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-122">A user needs only one rule to be true to get access.</span></span> <span data-ttu-id="72abf-123">如果用户有权从基于 Web 的控制台访问一台具有所有语言访问权限或仅可访问 Windows PowerShell 远程管理 cmdlet 的计算机，用户可登录（或跳到）其他与第一台目标计算机连接的计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-123">If a user is given access to one computer with either full language access or access only to Windows PowerShell remote management cmdlets, from the web-based console, the user can log on (or hop) to other computers that are connected to the first target computer.</span></span> <span data-ttu-id="72abf-124">配置 Windows PowerShell Web 访问的最安全方法是仅允许用户访问受限制的会话配置（还称为终结点或运行空间），从而可让用户完成他们通常需要远程执行的特定任务。</span><span class="sxs-lookup"><span data-stu-id="72abf-124">The most secure way to configure Windows PowerShell Web Access is to allow users access only to constrained session configurations (also called endpoints or runspaces) that allow them to accomplish specific tasks that they normally need to perform remotely.</span></span></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="72abf-125">名称</span><span class="sxs-lookup"><span data-stu-id="72abf-125">Name</span></span></p></th>
<th><p><span data-ttu-id="72abf-126">说明</span><span class="sxs-lookup"><span data-stu-id="72abf-126">Description</span></span></p></th>
<th><p><span data-ttu-id="72abf-127">参数</span><span class="sxs-lookup"><span data-stu-id="72abf-127">Parameters</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="72abf-128"><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="72abf-128"><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="72abf-129">向 Windows PowerShell Web 访问授权规则集添加新的授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-129">Adds a new authorization rule to the Windows PowerShell Web Access authorization rule set.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="72abf-130">ComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="72abf-130">ComputerGroupName</span></span></p></li>
<li><p><span data-ttu-id="72abf-131">ComputerName</span><span class="sxs-lookup"><span data-stu-id="72abf-131">ComputerName</span></span></p></li>
<li><p><span data-ttu-id="72abf-132">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="72abf-132">ConfigurationName</span></span></p></li>
<li><p><span data-ttu-id="72abf-133">RuleName</span><span class="sxs-lookup"><span data-stu-id="72abf-133">RuleName</span></span></p></li>
<li><p><span data-ttu-id="72abf-134">UserGroupName</span><span class="sxs-lookup"><span data-stu-id="72abf-134">UserGroupName</span></span></p></li>
<li><p><span data-ttu-id="72abf-135">UserName</span><span class="sxs-lookup"><span data-stu-id="72abf-135">UserName</span></span></p></li>
<li><p><span data-ttu-id="72abf-136">凭据（Windows Server 2012 R2 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="72abf-136">Credential (Windows Server 2012 R2 and later)</span></span></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="72abf-137"><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="72abf-137"><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="72abf-138">从 Windows PowerShell Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-138">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="72abf-139">ID</span><span class="sxs-lookup"><span data-stu-id="72abf-139">Id</span></span></p></li>
<li><p><span data-ttu-id="72abf-140">RuleName</span><span class="sxs-lookup"><span data-stu-id="72abf-140">RuleName</span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="72abf-141"><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="72abf-141"><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="72abf-142">返回一组 Windows PowerShell Web 访问的授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-142">Returns a set of Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="72abf-143">当不与参数结合使用时，cmdlet 将返回所有规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-143">When it is used without parameters, the cmdlet returns all rules.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="72abf-144">ID</span><span class="sxs-lookup"><span data-stu-id="72abf-144">Id</span></span></p></li>
<li><p><span data-ttu-id="72abf-145">RuleName</span><span class="sxs-lookup"><span data-stu-id="72abf-145">RuleName</span></span></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="72abf-146"><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="72abf-146"><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="72abf-147">评估授权规则，以确定是否已授权特定的用户、计算机或会话配置访问请求。</span><span class="sxs-lookup"><span data-stu-id="72abf-147">Evaluates authorization rules to determine if a specific user, computer, or session configuration access request is authorized.</span></span> <span data-ttu-id="72abf-148">默认情况下，如果未添加任何参数，则 cmdlet 将评估所有授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-148">By default, if no parameters are added, the cmdlet evaluates all authorization rules.</span></span> <span data-ttu-id="72abf-149">通过添加参数，管理员可指定授权规则或要测试的规则子集。</span><span class="sxs-lookup"><span data-stu-id="72abf-149">By adding parameters, administrators can specify an authorization rule or a subset of rules to test.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="72abf-150">ComputerName</span><span class="sxs-lookup"><span data-stu-id="72abf-150">ComputerName</span></span></p></li>
<li><p><span data-ttu-id="72abf-151">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="72abf-151">ConfigurationName</span></span></p></li>
<li><p><span data-ttu-id="72abf-152">RuleName</span><span class="sxs-lookup"><span data-stu-id="72abf-152">RuleName</span></span></p></li>
<li><p><span data-ttu-id="72abf-153">UserName</span><span class="sxs-lookup"><span data-stu-id="72abf-153">UserName</span></span></p></li>
<li><p><span data-ttu-id="72abf-154">凭据（Windows Server 2012 R2 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="72abf-154">Credential (Windows Server 2012 R2 and later)</span></span></p></li>
</ul></td>
</tr>
</tbody>
</table>

<span data-ttu-id="72abf-155">先前的 cmdlet 创建了一组访问规则，可供授权 Windows PowerShell Web 访问网关上的用户时使用。</span><span class="sxs-lookup"><span data-stu-id="72abf-155">The preceding cmdlets create a set of access rules which are used to authorize a user on the Windows PowerShell Web Access gateway.</span></span> <span data-ttu-id="72abf-156">规则与目标计算机上的访问控制列表 (ACL) 有所不同，它提高了 Web 访问的安全性。</span><span class="sxs-lookup"><span data-stu-id="72abf-156">The rules are different from the access control lists (ACLs) on the destination computer, and provide an additional layer of security for web access.</span></span> <span data-ttu-id="72abf-157">有关安全性的详细信息如以下部分所述。</span><span class="sxs-lookup"><span data-stu-id="72abf-157">More details about security are described in the following section.</span></span>

<span data-ttu-id="72abf-158">如果用户无法通过任一上述的安全层，则会在浏览器窗口中看到一条常规的“拒绝访问”消息。</span><span class="sxs-lookup"><span data-stu-id="72abf-158">If users cannot pass any of the preceding security layers, they receive a generic “access denied” message in their browser windows.</span></span> <span data-ttu-id="72abf-159">虽然有关安全性的详细信息记录在网关服务器上，但是最终用户并不获得有关他们通过多少个安全层或无法在哪个安全层登录或身份验证的信息。</span><span class="sxs-lookup"><span data-stu-id="72abf-159">Although security details are logged on the gateway server, end users are not shown information about how many security layers they passed, or at which layer the sign-in or authentication failure occurred.</span></span>

<span data-ttu-id="72abf-160">有关如何配置授权规则的详细信息，请参阅本主题中的 [配置授权规则](#BKMK_configrules)。</span><span class="sxs-lookup"><span data-stu-id="72abf-160">For more information about configuring authorization rules, see [Configuring authorization rules](#BKMK_configrules) in this topic.</span></span>

<a href="" id="BKMK_sec"></a>
###

<span data-ttu-id="72abf-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">安全</span></a></span><span class="sxs-lookup"><span data-stu-id="72abf-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Security</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-162">Windows PowerShell Web 访问安全模型在基于 Web 控制台的最终用户和目标计算机之间具有四个安全层。</span><span class="sxs-lookup"><span data-stu-id="72abf-162">The Windows PowerShell Web Access security model has four layers between an end user of the web-based console, and a target computer.</span></span> <span data-ttu-id="72abf-163">Windows PowerShell Web 访问管理员可通过其它配置在 IIS 管理器控制台中添加安全层。</span><span class="sxs-lookup"><span data-stu-id="72abf-163">Windows PowerShell Web Access administrators can add security layers through additional configuration in the IIS Manager console.</span></span> <span data-ttu-id="72abf-164">有关如何确保 IIS 管理器控制台中网站的安全的详细信息，请参阅[配置 Web 服务器安全 (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="72abf-164">For more information about securing websites in the IIS Manager console, see [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx).</span></span> <span data-ttu-id="72abf-165">有关 IIS 最佳做法和阻止拒绝服务攻击的详细信息，请参阅[阻止 DoS/拒绝服务攻击的最佳做法](https://technet.microsoft.com/library/cc750213.aspx)。</span><span class="sxs-lookup"><span data-stu-id="72abf-165">For more information about IIS best practices and preventing denial-of-service attacks, see [Best Practices for Preventing DoS/Denial of Service Attacks](https://technet.microsoft.com/library/cc750213.aspx).</span></span> <span data-ttu-id="72abf-166">管理员还可购买和安装其他零售身份验证软件。</span><span class="sxs-lookup"><span data-stu-id="72abf-166">An administrator can also buy and install additional, retail authentication software.</span></span>

<span data-ttu-id="72abf-167">下表描述最终用户与目标计算机之间的四个安全层。</span><span class="sxs-lookup"><span data-stu-id="72abf-167">The following table describes the four layers of security between end users and target computers.</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="72abf-168">顺序</span><span class="sxs-lookup"><span data-stu-id="72abf-168">Order</span></span></p></th>
<th><p><span data-ttu-id="72abf-169">层</span><span class="sxs-lookup"><span data-stu-id="72abf-169">Layer</span></span></p></th>
<th><p><span data-ttu-id="72abf-170">说明</span><span class="sxs-lookup"><span data-stu-id="72abf-170">Description</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="72abf-171">1</span><span class="sxs-lookup"><span data-stu-id="72abf-171">1</span></span></p></td>
<td><p><span data-ttu-id="72abf-172">Web 服务器 (IIS) 安全功能，如客户端证书身份验证</span><span class="sxs-lookup"><span data-stu-id="72abf-172">Web Server (IIS) security features, such as client certificate authentication</span></span></p></td>
<td><p><span data-ttu-id="72abf-173">Windows PowerShell Web 访问用户必须始终提供用户名和密码，以对其在网关上的帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="72abf-173">Windows PowerShell Web Access users must always provide a user name and password to authenticate their accounts on the gateway.</span></span> <span data-ttu-id="72abf-174">但是，Windows PowerShell Web 访问管理员还可打开或关闭可选的客户端证书身份验证（参阅<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">安装和使用 Windows PowerShell Web 访问</a>中的“使用 IIS Manager 在现有网站中配置网关”的步骤 10）。</span><span class="sxs-lookup"><span data-stu-id="72abf-174">However, Windows PowerShell Web Access administrators can also turn optional client certificate authentication on or off (see step 10 of “To use IIS Manager to configure the gateway in an existing website” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>).</span></span> <span data-ttu-id="72abf-175">可选的客户端证书功能要求最终用户除拥有其用户名和密码外，还须持有有效的客户端证书，这是 Web 服务器 (IIS) 配置的一部分。</span><span class="sxs-lookup"><span data-stu-id="72abf-175">The optional client certificate feature requires end users to have a valid client certificate, in addition to their user names and passwords, and is part of Web Server (IIS) configuration.</span></span> <span data-ttu-id="72abf-176">当启用客户端证书层时，Windows PowerShell Web 访问登录页面将提示用户提供有效的证书，然后再评估用户的登录凭据。</span><span class="sxs-lookup"><span data-stu-id="72abf-176">When the client certificate layer is enabled, the Windows PowerShell Web Access sign-in page prompts users to provide valid certificates before their sign-in credentials are evaluated.</span></span> <span data-ttu-id="72abf-177">客户端证书身份验证程序自动检查客户端证书。</span><span class="sxs-lookup"><span data-stu-id="72abf-177">Client certificate authentication automatically checks for the client certificate.</span></span></p>
<p><span data-ttu-id="72abf-178">如果找不到有效的证书，Windows PowerShell Web 访问会通知用户，以便用户提供证书。</span><span class="sxs-lookup"><span data-stu-id="72abf-178">If a valid certificate is not found, Windows PowerShell Web Access informs users, so they can provide the certificate.</span></span> <span data-ttu-id="72abf-179">如果找到有效的证书，Windows PowerShell Web 访问将为用户打开登录页面，以提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="72abf-179">If a valid client certificate is found, Windows PowerShell Web Access opens the sign-in page for users to provide their user names and passwords.</span></span></p>
<p><span data-ttu-id="72abf-180">这是 Web 服务器 (IIS) 提供其他安全设置的示例之一。</span><span class="sxs-lookup"><span data-stu-id="72abf-180">This is one example of additional security settings that are offered by Web Server (IIS).</span></span> <span data-ttu-id="72abf-181">有关其他 IIS 安全功能的详细信息，请参阅<a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">配置 Web 服务器安全性 (IIS 7)</a>。</span><span class="sxs-lookup"><span data-stu-id="72abf-181">For more information about other IIS security features, see <a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">Configure Web Server Security (IIS 7)</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="72abf-182">2</span><span class="sxs-lookup"><span data-stu-id="72abf-182">2</span></span></p></td>
<td><p><span data-ttu-id="72abf-183">Windows PowerShell Web 访问基于表单的网关身份验证</span><span class="sxs-lookup"><span data-stu-id="72abf-183">Windows PowerShell Web Access forms-based gateway authentication</span></span></p></td>
<td><p><span data-ttu-id="72abf-184">Windows PowerShell Web 访问登录页面需要一组凭据（用户名和密码），并向用户提供一个为目标计算机提供其他凭据的选项。</span><span class="sxs-lookup"><span data-stu-id="72abf-184">The Windows PowerShell Web Access sign-in page requires a set of credentials (user name and password) and offers users the option of providing different credentials for the target computer.</span></span> <span data-ttu-id="72abf-185">如果用户不提供备用凭据，则照样可使用连接网关时所用的主要用户名和密码，连接目标计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-185">If the user does not provide alternate credentials, the primary user name and password that are used to connect to the gateway are also used to connect to the target computer.</span></span></p>
<p><span data-ttu-id="72abf-186">在 Windows PowerShell Web 访问网关上对所需的凭据进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="72abf-186">The required credentials are authenticated on the Windows PowerShell Web Access gateway.</span></span> <span data-ttu-id="72abf-187">这些凭据必须是本地 Windows PowerShell Web 访问网关服务器或 Active Directory® 中有效的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="72abf-187">These credentials must be valid user accounts on either the local Windows PowerShell Web Access gateway server, or in Active Directory®.</span></span></p>
<p><span data-ttu-id="72abf-188">用户在网关上通过身份验证后，Windows PowerShell Web 访问将检查授权规则，以验证用户是否有权访问所需的目标计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-188">After a user is authenticated at the gateway, Windows PowerShell Web Access checks authorization rules to verify if the user has access to the requested target computer.</span></span> <span data-ttu-id="72abf-189">成功授权后，用户的凭据传递到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-189">After successful authorization, the user’s credentials are passed along to the target computer.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="72abf-190">3</span><span class="sxs-lookup"><span data-stu-id="72abf-190">3</span></span></p></td>
<td><p><span data-ttu-id="72abf-191">Windows PowerShell Web 访问授权规则</span><span class="sxs-lookup"><span data-stu-id="72abf-191">Windows PowerShell Web Access authorization rules</span></span></p></td>
<td><p><span data-ttu-id="72abf-192">用户在网关上通过身份验证后，Windows PowerShell Web 访问将检查授权规则，以验证用户是否有权访问所需的目标计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-192">After a user is authenticated at the gateway, Windows PowerShell Web Access checks authorization rules to verify if the user has access to the requested target computer.</span></span> <span data-ttu-id="72abf-193">成功授权后，用户的凭据传递到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-193">After successful authorization, the user’s credentials are passed along to the target computer.</span></span></p>
<p><span data-ttu-id="72abf-194">仅当用户通过网关的身份验证之后，以及用户在目标计算机上通过身份验证之前，评估这些规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-194">These rules are evaluated only after a user has been authenticated by the gateway, and before a user can be authenticated on a target computer.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="72abf-195">4</span><span class="sxs-lookup"><span data-stu-id="72abf-195">4</span></span></p></td>
<td><p><span data-ttu-id="72abf-196">目标身份验证和授权规则</span><span class="sxs-lookup"><span data-stu-id="72abf-196">Target authentication and authorization rules</span></span></p></td>
<td><p><span data-ttu-id="72abf-197">Windows PowerShell Web 访问的最后安全层是目标计算机自身的安全配置。</span><span class="sxs-lookup"><span data-stu-id="72abf-197">The final layer of security for Windows PowerShell Web Access is the target computer’s own security configuration.</span></span> <span data-ttu-id="72abf-198">用户必须持有在目标计算机上配置的适当访问权限，并且按照 Windows PowerShell Web 访问授权规则，运行通过 Windows PowerShell Web 访问影响目标计算机的 Windows PowerShell 基于 Web 的控制台。</span><span class="sxs-lookup"><span data-stu-id="72abf-198">Users must have the appropriate access rights configured on the target computer, and also in the Windows PowerShell Web Access authorization rules, to run a Windows PowerShell web-based console that affects a target computer through Windows PowerShell Web Access.</span></span></p>
<p><span data-ttu-id="72abf-199">该层提供相同的安全机制；如果用户尝试通过运行 <strong>Enter-PSSession</strong> 或 <strong>New-PSSession</strong> cmdlet，为 Windows PowerShell 中的目标计算机创建远程 Windows PowerShell 会话，此类机制将评估连接尝试。</span><span class="sxs-lookup"><span data-stu-id="72abf-199">This layer offers the same security mechanisms that would evaluate connection attempts if users tried to create a remote Windows PowerShell session to a target computer from within Windows PowerShell by running the <strong>Enter-PSSession</strong> or <strong>New-PSSession</strong> cmdlets.</span></span></p>
<p><span data-ttu-id="72abf-200">默认情况下，Windows PowerShell Web 访问使用主要用户名和密码，在网关和目标计算机上进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="72abf-200">By default, Windows PowerShell Web Access uses the primary user name and password for authentication on both the gateway and the target computer.</span></span> <span data-ttu-id="72abf-201">在标题为<strong>可选的连接设置</strong>部分，基于 Web 的登录页面为用户提供一个为目标计算机提供其他凭据的选项（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="72abf-201">The web-based sign-in page, in a section titled <strong>Optional connection settings</strong>, offers users the option of providing different credentials for the target computer, if they are required.</span></span> <span data-ttu-id="72abf-202">如果用户不提供备用凭据，则照样可使用连接网关时所用的主要用户名和密码，连接目标计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-202">If the user does not provide alternate credentials, the primary user name and password that are used to connect to the gateway are also used to connect to the target computer.</span></span></p>
<p><span data-ttu-id="72abf-203">授权规则可让用户访问特定的会话配置。</span><span class="sxs-lookup"><span data-stu-id="72abf-203">Authorization rules can be used to allow users access to a particular session configuration.</span></span> <span data-ttu-id="72abf-204">你可以为 Windows PowerShell Web 访问创建受限的运行空间或会话配置，并可让特定用户在登录到 Windows PowerShell Web 访问时仅连接到特定的会话配置。</span><span class="sxs-lookup"><span data-stu-id="72abf-204">You can create restricted runspaces or session configurations for Windows PowerShell Web Access, and allow specific users to connect only to specific session configurations when they sign in to Windows PowerShell Web Access.</span></span> <span data-ttu-id="72abf-205">你可使用访问控制列表 (ACL) 确定哪个用户具有访问特定终结点的权限，并使用本部分中的授权规则进一步限制特定用户组合访问终结点的权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-205">You can use access control lists (ACLs) to determine which users have access to specific endpoints, and further restrict access to the endpoint for a specific set of users by using authorization rules described in this section.</span></span> <span data-ttu-id="72abf-206">有关受限运行空间的详细信息，请参阅 MSDN 上的<a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">受限运行空间</a>。</span><span class="sxs-lookup"><span data-stu-id="72abf-206">For more information about restricted runspaces, see <a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">Constrained Runspaces</a> on MSDN.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="72abf-207">

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">配置授权规则</span></a></span><span class="sxs-lookup"><span data-stu-id="72abf-207">

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configuring authorization rules</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-208">管理员可能想对为了进行 Windows PowerShell 远程管理已在其环境中定义的 Windows PowerShell Web 访问用户执行相同的授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-208">Administrators likely want the same authorization rule for Windows PowerShell Web Access users that is already defined in their environment for Windows PowerShell remote management.</span></span> <span data-ttu-id="72abf-209">本部分中的第一个程序描述如何添加安全授权规则，此类规则可授予一名用户访问权限，以便用户登录并管理一台计算机，以及处于单个会话配置中。</span><span class="sxs-lookup"><span data-stu-id="72abf-209">The first procedure in this section describes how to add a secure authorization rule that grants access to one user, signing in to manage one computer, and within a single session configuration.</span></span> <span data-ttu-id="72abf-210">第二个程序描述如何删除不再需要的授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-210">The second procedure describes how to remove an authorization rule that is no longer needed.</span></span>

<span data-ttu-id="72abf-211">如果你计划使用自定义会话配置以允许特定用户仅在 Windows PowerShell Web 访问的限制运行空间中运行，则创建自定义会话配置，然后再添加参考其的授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-211">If you plan to use custom session configurations to allow specific users to work only within restricted runspaces in Windows PowerShell Web Access, create your custom session configurations before you add authorization rules that refer to them.</span></span> <span data-ttu-id="72abf-212">无法使用 Windows PowerShell Web 访问 cmdlet 创建自定义会话配置。</span><span class="sxs-lookup"><span data-stu-id="72abf-212">You cannot use the Windows PowerShell Web Access cmdlets to create custom session configurations.</span></span> <span data-ttu-id="72abf-213">有关创建自定义会话配置的详细信息，请参阅 MSDN 上的 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="72abf-213">For more information about creating custom session configurations, see [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

<span data-ttu-id="72abf-214">Windows PowerShell Web 访问 cmdlet 支持一个通配符，即星号 ( \* )。</span><span class="sxs-lookup"><span data-stu-id="72abf-214">Windows PowerShell Web Access cmdlets support one wildcard character, an asterisk ( \* ).</span></span> <span data-ttu-id="72abf-215">字符串中的通配符不受支持；根据属性（用户、计算机或会话配置）使用单个星号。</span><span class="sxs-lookup"><span data-stu-id="72abf-215">Wildcard characters within strings are not supported; use a single asterisk per property (users, computers, or session configurations).</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="72abf-216"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="72abf-216"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="72abf-217">有关使用授权规则授予用户访问权限以及帮助确保 Windows PowerShell Web 访问环境安全的更多方式，请参阅本主题中的<a href="#BKMK_others">其他授权规则方案示例</a>。</span><span class="sxs-lookup"><span data-stu-id="72abf-217">For more ways you can use authorization rules to grant access to users and help secure the Windows PowerShell Web Access environment, see <a href="#BKMK_others">Other authorization rule scenario examples</a> in this topic.</span></span></p></td>
</tr>
</tbody>
</table>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="72abf-218">添加受限的授权规则</span><span class="sxs-lookup"><span data-stu-id="72abf-218">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="72abf-219">使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="72abf-219">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="72abf-220">在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="72abf-220">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="72abf-221">在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="72abf-221">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="72abf-222"><span class="label">使用会话配置限制用户访问的可选步骤：</span>验证要在规则中使用的会话配置已存在。</span><span class="sxs-lookup"><span data-stu-id="72abf-222"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="72abf-223">如果尚未创建这些配置，则使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中用于创建会话配置的说明。</span><span class="sxs-lookup"><span data-stu-id="72abf-223">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="72abf-224">键入以下命令，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="72abf-224">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="72abf-225">Copy</span><span class="sxs-lookup"><span data-stu-id="72abf-225">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_1079478f-cd51-4d35-8022-4b532a9d57a4'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="72abf-226">本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见的脚本和 cmdlet 需求的特定会话配置的权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-226">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="72abf-227">在以下示例中，<span class="code">Contoso</span> 域中名为 <span class="code">JSmith</span> 的用户获得访问权限，以管理计算机 <span class="code">Contoso_214</span>，并使用名为 <span class="code">NewAdminsOnly</span> 的会话配置。</span><span class="sxs-lookup"><span data-stu-id="72abf-227">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="72abf-228">Copy</span><span class="sxs-lookup"><span data-stu-id="72abf-228">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4e760377-e401-4ef4-988f-7a0aec1b2a90'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="72abf-229">确保通过运行 **Get-PswaAuthorizationRule** cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt; 创建了该规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-229">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="72abf-230">例如，**Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**。</span><span class="sxs-lookup"><span data-stu-id="72abf-230">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

#### <a name="to-remove-an-authorization-rule"></a><span data-ttu-id="72abf-231">删除授权规则</span><span class="sxs-lookup"><span data-stu-id="72abf-231">To remove an authorization rule</span></span>

1.  <span data-ttu-id="72abf-232">如果尚未打开 Windows PowerShell 会话，请参阅本部分中[添加非受限的授权规则](#BKMK_arar)的步骤 1。</span><span class="sxs-lookup"><span data-stu-id="72abf-232">If a Windows PowerShell session is not already open, see step 1 of [To add a restrictive authorization rule](#BKMK_arar) in this section.</span></span>

2.  <span data-ttu-id="72abf-233">键入以下内容，然后按 **Enter**，其中的*规则 ID* 代表要删除的规则的唯一 ID 号。</span><span class="sxs-lookup"><span data-stu-id="72abf-233">Type the following, and then press **Enter**, where *rule ID* represents the unique ID number of the rule that you want to remove.</span></span>

    [<span data-ttu-id="72abf-234">Copy</span><span class="sxs-lookup"><span data-stu-id="72abf-234">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0daef66d-0ecf-47fb-a8a0-d4dbceb8409d'); "Copy to clipboard.")

        Remove-PswaAuthorizationRule -ID <rule ID>

    <span data-ttu-id="72abf-235">此外，如果你不知道 ID 号，但知道你想要删除的规则的友好名称，则可获取该规则的名称，并通过管道将它传递给 <span class="code">Remove-PswaAuthorizationRule</span> cmdlet，从而删除该规则，如以下示例所示：Get-PswaAuthorizationRule -RuleName &lt;*rule name*&gt; | Remove-PswaAuthorizationRule。</span><span class="sxs-lookup"><span data-stu-id="72abf-235">Alternatively, if you do not know the ID number, but know the friendly name of the rule you want to remove, you can get the name of the rule, and pipe it to the <span class="code">Remove-PswaAuthorizationRule</span> cmdlet to remove the rule, as shown in the following example: Get-PswaAuthorizationRule -RuleName &lt;*rule name*&gt; | Remove-PswaAuthorizationRule.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="72abf-236"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="72abf-236"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="72abf-237">系统不会提示你确认是否要删除特定的授权规则；按下 <strong>Enter</strong>，即可删除该规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-237">You are not prompted to confirm whether you want to delete the specified authorization rule; the rule is deleted when you press <strong>Enter</strong>.</span></span> <span data-ttu-id="72abf-238">在运行 <strong>Remove-PswaAuthorizationRule</strong> cmdlet 之前，确保你想要删除授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-238">Be sure that you want to remove the authorization rule before running the <strong>Remove-PswaAuthorizationRule</strong> cmdlet.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="72abf-239">

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">其他授权规则方案示例</span></a></span><span class="sxs-lookup"><span data-stu-id="72abf-239">

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Other authorization rule scenario examples</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-240">每个 Windows PowerShell 会话都使用会话配置；如果尚未为会话指定任何会话配置，Windows PowerShell 将使用默认的内置 Windows PowerShell 会话配置（被称为 Microsoft.PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="72abf-240">Every Windows PowerShell session uses a session configuration; if one is not specified for a session, Windows PowerShell uses the default, built-in Windows PowerShell session configuration, called Microsoft.PowerShell.</span></span> <span data-ttu-id="72abf-241">默认的会话配置包括计算机上可用的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="72abf-241">The default session configuration includes all cmdlets that are available on a computer.</span></span> <span data-ttu-id="72abf-242">管理员可利用受限的运行空间（有限范围内的其最终用户可执行的 cmdlet 和任务）定义会话配置，从而限制对所有计算机的访问权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-242">Administrators can restrict access to all computers by defining a session configuration with a restricted runspace (a limited range of cmdlets and tasks that their end users could perform).</span></span> <span data-ttu-id="72abf-243">对于有权访问一台具有所有语言访问权限的计算机或仅可访问 Windows PowerShell 远程管理 cmdlet 的用户，可连接到其他与第一台计算机连接的计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-243">A user who is granted access to one computer with either full language access or only the Windows PowerShell remote management cmdlets can connect to other computers that are connected to the first computer.</span></span> <span data-ttu-id="72abf-244">定义受限的运行空间可阻止用户从其获准许的 Windows PowerShell 运行空间访问其他计算机，从而改善你的 Windows PowerShell Web 访问环境的安全性。</span><span class="sxs-lookup"><span data-stu-id="72abf-244">Defining a restricted runspace can prevent users from accessing other computers from their allowed Windows PowerShell runspace, and improves the security of your Windows PowerShell Web Access environment.</span></span> <span data-ttu-id="72abf-245">可（通过使用组策略）将会话配置分配给所有管理员想通过 Windows PowerShell Web 访问进行访问的计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-245">The session configuration can be distributed (by using Group Policy) to all computers that administrators want to make accessible through Windows PowerShell Web Access.</span></span> <span data-ttu-id="72abf-246">有关会话配置的详细信息，请参阅 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。</span><span class="sxs-lookup"><span data-stu-id="72abf-246">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx).</span></span> <span data-ttu-id="72abf-247">以下是本方案的一些示例。</span><span class="sxs-lookup"><span data-stu-id="72abf-247">The following are some examples of this scenario.</span></span>

-   <span data-ttu-id="72abf-248">管理员创建名为 **PswaEndpoint** 的终结点，其中带有受限的运行空间。</span><span class="sxs-lookup"><span data-stu-id="72abf-248">An administrator creates an endpoint, called **PswaEndpoint**, with a restricted runspace.</span></span> <span data-ttu-id="72abf-249">然后管理员创建规则 (**\*,\*,PswaEndpoint**)，并将终结点分配给其他计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-249">Then, the administrator creates a rule, **\*,\*,PswaEndpoint**, and distributes the endpoint to other computers.</span></span> <span data-ttu-id="72abf-250">规则可让所有用户访问所有带有终结点 **PswaEndpoint** 的计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-250">The rule allows all users to access all computers with the endpoint **PswaEndpoint**.</span></span> <span data-ttu-id="72abf-251">如果这只是在规则集中定义的授权规则，则不能访问不带有终结点的计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-251">If this is the only authorization rule defined in the rule set, computers without that endpoint would not be accessible.</span></span>

-   <span data-ttu-id="72abf-252">管理员创建名为 **PswaEndpoint** 的终结点（其中带有受限的运行空间），并希望限制特定用户的访问权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-252">The administrator created an endpoint with a restricted runspace called **PswaEndpoint**,and wants to restrict access to specific users.</span></span> <span data-ttu-id="72abf-253">管理员创建一组名为 **Level1Support** 的用户，并定义以下规则：**Level1Support,\*,PswaEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="72abf-253">The administrator creates a group of users called **Level1Support**, and defines the following rule: **Level1Support,\*,PswaEndpoint**.</span></span> <span data-ttu-id="72abf-254">规则可让 **Level1Support** 组中的用户访问所有带有 **PswaEndpoint** 配置的计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-254">The rule grants any users in the group **Level1Support** access to all computers with the **PswaEndpoint** configuration.</span></span> <span data-ttu-id="72abf-255">类似地，可限制对特定计算机组合的访问权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-255">Similarly, access can be restricted to a specific set of computers.</span></span>

-   <span data-ttu-id="72abf-256">有些管理员为某些用户提供的访问权限要比其他用户多。</span><span class="sxs-lookup"><span data-stu-id="72abf-256">Some administrators provide certain users more access than others.</span></span> <span data-ttu-id="72abf-257">例如，管理员创建两个用户组，分别是 **Admins** 和 **BasicSupport**。</span><span class="sxs-lookup"><span data-stu-id="72abf-257">For example, an administrator creates two user groups, **Admins** and **BasicSupport**.</span></span> <span data-ttu-id="72abf-258">管理员还创建名为 **PswaEndpoint** 的终结点（其中带有受限的运行空间），并定义以下两条规则：**Admins,\*,\*** 和 **BasicSupport,\*,PswaEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="72abf-258">The administrator also creates an endpoint with a restricted runspace called **PswaEndpoint**, and defines the following two rules: **Admins,\*,\*** and **BasicSupport,\*,PswaEndpoint**.</span></span> <span data-ttu-id="72abf-259">第一条规则为**Admin**组中的所有用户提供访问所有计算机的权限，第二条规则为**BasicSupport**组中的所有用户仅提供访问那些带有**PswaEndpoint**的计算机的权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-259">The first rule provides all users in the **Admin** group access to all computers, and the second rule provides all users in the **BasicSupport** group access only to those computers with **PswaEndpoint**.</span></span>

-   <span data-ttu-id="72abf-260">管理员已设置专用测试环境，希望可让所有授权的网络用户通过他们经常访问的网络访问所有计算机，并持有对所有他们经常访问的会话配置的访问权限。</span><span class="sxs-lookup"><span data-stu-id="72abf-260">An administrator has set up a private test environment, and wants to allow all authorized network users access to all computers on the network to which they typically have access, with access to all session configurations to which they typically have access.</span></span> <span data-ttu-id="72abf-261">因为这是专用测试环境，管理员创建了不安全的授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-261">Because this is a private test environment, the administrator creates an authorization rule that is not secure.</span></span> <span data-ttu-id="72abf-262">管理员运行 cmdlet <span class="code">Add-PswaAuthorizationRule \* \* \*</span>，其使用通配符 **\*** 来表示所有用户、所有计算机和所有配置。</span><span class="sxs-lookup"><span data-stu-id="72abf-262">The administrator runs the cmdlet <span class="code">Add-PswaAuthorizationRule \* \* \*</span>, which uses the wildcard character **\*** to represent all users, all computers, and all configurations.</span></span> <span data-ttu-id="72abf-263">此规则与以下项等效：<span class="code">Add-PswaAuthorizationRule -UserName \* -ComputerName \* -ConfigurationName \*</span>。</span><span class="sxs-lookup"><span data-stu-id="72abf-263">This rule is the equivalent of the following: <span class="code">Add-PswaAuthorizationRule -UserName \* -ComputerName \* -ConfigurationName \*</span>.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="72abf-264"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全说明 </span></span><span class="sxs-lookup"><span data-stu-id="72abf-264"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="72abf-265">此规则不建议在安全的环境中使用，它可绕过 Windows PowerShell Web 访问提供的授权规则安全层。</span><span class="sxs-lookup"><span data-stu-id="72abf-265">This rule is not recommended in a secure environment, and bypasses the authorization rule layer of security provided by Windows PowerShell Web Access.</span></span></p></td>
    </tr>
    </tbody>
    </table>

-   <span data-ttu-id="72abf-266">管理员必须允许用户连接到同时包含工作组和域的环境中的目标计算机，其中工作组计算机偶尔用于连接到域中的目标计算机，域中的计算机偶尔用于连接到工作组中的目标计算机。</span><span class="sxs-lookup"><span data-stu-id="72abf-266">An administrator must allow users to connect to target computers in an environment that includes both workgroups and domains, where workgroup computers are occasionally used to connect to target computers in domains, and computers in domains are occasionally used to connect to target computers in workgroups.</span></span> <span data-ttu-id="72abf-267">管理员具有工作组中的网关服务器 *PswaServer*，并且目标计算机 *srv1.contoso.com* 位于域中。</span><span class="sxs-lookup"><span data-stu-id="72abf-267">The administrator has a gateway server, *PswaServer*, in a workgroup; and target computer *srv1.contoso.com* is in a domain.</span></span> <span data-ttu-id="72abf-268">用户 *Chris* 既是工作组网关服务器又是目标计算机上的授权本地用户。</span><span class="sxs-lookup"><span data-stu-id="72abf-268">User *Chris* is an authorized local user on both the workgroup gateway server and the target computer.</span></span> <span data-ttu-id="72abf-269">他在工作组服务器上的用户名为 *chrisLocal*，他在目标计算机上的用户名为 *contoso\\chris*。</span><span class="sxs-lookup"><span data-stu-id="72abf-269">His user name on the workgroup server is *chrisLocal*; and his user name on the target computer is *contoso\\chris*.</span></span> <span data-ttu-id="72abf-270">若要授权 Chris 可访问 srv1.contoso.com，管理员会添加以下规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-270">To authorize access to srv1.contoso.com for Chris, the administrator adds the following rule.</span></span>

    [<span data-ttu-id="72abf-271">Copy</span><span class="sxs-lookup"><span data-stu-id="72abf-271">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_8d183d3d-1c19-44b8-9297-530b0efc7c79'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell

    <span data-ttu-id="72abf-272">上述规则示例会在网关服务器上对 Chris 进行身份验证，然后授权他可以访问 *srv1*。</span><span class="sxs-lookup"><span data-stu-id="72abf-272">The preceding rule example authenticates Chris on the gateway server, and then authorizes his access to *srv1*.</span></span> <span data-ttu-id="72abf-273">在登录页面上，Chris 必须在“**可选连接设置**”区域 (*contoso\\chris*) 中提供第二组凭据。</span><span class="sxs-lookup"><span data-stu-id="72abf-273">On the sign-in page, Chris must provide a second set of credentials in the **Optional connection settings** area (*contoso\\chris*).</span></span> <span data-ttu-id="72abf-274">网关服务器使用一组额外的凭据在目标计算机*srv1.contoso.com*上对其进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="72abf-274">The gateway server uses the additional set of credentials to authenticate him on the target computer, *srv1.contoso.com*.</span></span>

    <span data-ttu-id="72abf-275">在上述情景中，Windows PowerShell Web 访问仅在以下操作已成功且至少一个授权规则允许使用以下操作之后才会建立到目标计算机的成功连接。</span><span class="sxs-lookup"><span data-stu-id="72abf-275">In the preceding scenario, Windows PowerShell Web Access establishes a successful connection to the target computer only after the following have been successful, and allowed by at least one authorization rule.</span></span>

    1.  <span data-ttu-id="72abf-276">工作组网关服务器上的身份验证，方法是向授权规则添加采用 *server_name*\\*user_name* 格式的用户名</span><span class="sxs-lookup"><span data-stu-id="72abf-276">Authentication on the workgroup gateway server by adding a user name in the format *server_name*\\*user_name* to the authorization rule</span></span>

    2.  <span data-ttu-id="72abf-277">目标计算机上的身份验证，方法是使用“可选连接设置”区域的登录页面中提供的备用凭据</span><span class="sxs-lookup"><span data-stu-id="72abf-277">Authentication on the target computer by using alternate credentials provided on the sign-in page, in the **Optional connection settings** area</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="72abf-278"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="72abf-278"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="72abf-279">如果网关和目标计算机位于不同的工作组或域中，则必须在两个工作组计算机之间、两个域之间或工作组和域之间建立信任关系。</span><span class="sxs-lookup"><span data-stu-id="72abf-279">If gateway and target computers are in different workgroups or domains, a trust relationship must be established between the two workgroup computers, the two domains, or between the workgroup and the domain.</span></span> <span data-ttu-id="72abf-280">不能使用 Windows PowerShell Web 访问授权规则 cmdlet 配置此关系。</span><span class="sxs-lookup"><span data-stu-id="72abf-280">This relationship cannot be configured by using Windows PowerShell Web Access authorization rule cmdlets.</span></span> <span data-ttu-id="72abf-281">授权规则不会定义计算机之间的信任关系，它们仅可授权用户连接到特定目标计算机和会话配置。</span><span class="sxs-lookup"><span data-stu-id="72abf-281">Authorization rules do not define a trust relationship between computers; they can only authorize users to connect to specific target computers and session configurations.</span></span> <span data-ttu-id="72abf-282">有关如何配置不同域之间信任关系的详细信息，请参阅<a href="https://technet.microsoft.com/library/cc794775.aspx">创建域和林信任</a>。</span><span class="sxs-lookup"><span data-stu-id="72abf-282">For more information about how to configure a trust relationship between different domains, see <a href="https://technet.microsoft.com/library/cc794775.aspx">Creating Domain and Forest Trusts</a>.</span></span> <span data-ttu-id="72abf-283">有关如何向受信任主机列表中添加工作组计算机的详细信息，请参阅<a href="https://technet.microsoft.com/library/dd759202.aspx">使用服务器管理器进行远程管理</a>。</span><span class="sxs-lookup"><span data-stu-id="72abf-283">For more information about how to add workgroup computers to a trusted hosts list, see <a href="https://technet.microsoft.com/library/dd759202.aspx">Remote Management with Server Manager</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="72abf-284"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">对多个网站使用单一的授权规则集</span></a></span><span class="sxs-lookup"><span data-stu-id="72abf-284"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using a single set of authorization rules for multiple sites</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-285">授权规则存储在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="72abf-285">Authorization rules are stored in an XML file.</span></span> <span data-ttu-id="72abf-286">默认情况下，XML 文件的路径名为 %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml。</span><span class="sxs-lookup"><span data-stu-id="72abf-286">By default, the path name of the XML file is %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml.</span></span>

<span data-ttu-id="72abf-287">授权规则 XML 文件的路径存储在 **powwa.config** 文件中，可在 %windir%\\Web\\PowershellWebAccess\\data 中找到。</span><span class="sxs-lookup"><span data-stu-id="72abf-287">The path to the authorization rules XML file is stored in the **powwa.config** file, which is found in %windir%\\Web\\PowershellWebAccess\\data.</span></span> <span data-ttu-id="72abf-288">管理员可随时将参考路径更改为 **powwa.config** 中的默认路径，以满足首选项或要求。</span><span class="sxs-lookup"><span data-stu-id="72abf-288">The administrator has the flexibility to change the reference to the default path in **powwa.config** to suit preferences or requirements.</span></span> <span data-ttu-id="72abf-289">允许管理员更改文件的位置，可让多个 Windows PowerShell Web 访问网关在需要此类配置的情况下，使用相同的授权规则。</span><span class="sxs-lookup"><span data-stu-id="72abf-289">Allowing the administrator to change the location of the file lets multiple Windows PowerShell Web Access gateways use the same authorization rules, if such a configuration is desired.</span></span>

<a href="" id="BKMK_sesmgmt"></a>

<span data-ttu-id="72abf-290"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">会话管理</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="72abf-290"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Session management</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-291">默认情况下，Windows PowerShell Web 访问限制一名用户一次访问三个会话。</span><span class="sxs-lookup"><span data-stu-id="72abf-291">By default, Windows PowerShell Web Access limits a user to three sessions at one time.</span></span> <span data-ttu-id="72abf-292">你可在 IIS 管理器中编辑 Web 应用程序的 **web.config** 文件，以支持每名用户可访问不同数目的会话。</span><span class="sxs-lookup"><span data-stu-id="72abf-292">You can edit the web application’s **web.config** file in IIS Manager to support a different number of sessions per user.</span></span> <span data-ttu-id="72abf-293">**web.config** 文件的路径是 $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config。</span><span class="sxs-lookup"><span data-stu-id="72abf-293">The path to the **web.config** file is $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config.</span></span>

<span data-ttu-id="72abf-294">默认情况下，如果编辑了任何设置，则配置 Web 服务器 (IIS)，以重新启动应用程序池。</span><span class="sxs-lookup"><span data-stu-id="72abf-294">By default, Web Server (IIS) is configured to restart the application pool if any settings are edited.</span></span> <span data-ttu-id="72abf-295">例如，如果对 **web.config** 文件进行更改，则重新启动应用程序池。</span><span class="sxs-lookup"><span data-stu-id="72abf-295">For example, the application pool is restarted if changes are made to the **web.config** file.</span></span> <span data-ttu-id="72abf-296">因为 Windows PowerShell Web 访问使用内存中的会话状态，所以，当重新启动应用程序池时，登录到 Windows PowerShell Web 访问会话的用户将错过其会话。</span><span class="sxs-lookup"><span data-stu-id="72abf-296">Because Windows PowerShell Web Access uses in-memory session states, users signed in to Windows PowerShell Web Access sessions lose their sessions when the application pool is restarted.</span></span>

###

<span data-ttu-id="72abf-297"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">在登录页上设置默认参数</span></a></span><span class="sxs-lookup"><span data-stu-id="72abf-297"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Setting default parameters on the sign-in page</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-298">如果您的 Windows PowerShell Web 访问网关在 Windows Server 2012 R2 上运行，您可以配置在 Windows PowerShell Web 访问登录页上显示的设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="72abf-298">If your Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, you can configure default values for the settings that are displayed on the Windows PowerShell Web Access sign-in page.</span></span> <span data-ttu-id="72abf-299">可以配置上一段所述的 **web.config** 文件中的值。</span><span class="sxs-lookup"><span data-stu-id="72abf-299">You can configure values in the **web.config** file that is described in the preceding paragraph.</span></span> <span data-ttu-id="72abf-300">登录页设置的默认值位于 web.config 文件的 **appSettings** 部分中；以下是 **appSettings** 部分的示例。</span><span class="sxs-lookup"><span data-stu-id="72abf-300">Default values for the sign-in page settings are found in the **appSettings** section of the web.config file; the following is an example of the **appSettings** section.</span></span> <span data-ttu-id="72abf-301">其中许多设置的有效值与 Windows PowerShell 中 [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet 的相应参数的有效值相同。</span><span class="sxs-lookup"><span data-stu-id="72abf-301">Valid values for many of these settings are the same as those for the corresponding parameters of the [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet in Windows PowerShell.</span></span> <span data-ttu-id="72abf-302">例如，<span class="code">defaultApplicationName</span> 键（如以下代码块中所示）是目标计算机上 **$PSSessionApplicationName** 首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="72abf-302">For example, the <span class="code">defaultApplicationName</span> key, as shown in the following code block, is the value of the **$PSSessionApplicationName** preference variable on the target computer.</span></span>

[<span data-ttu-id="72abf-303">Copy</span><span class="sxs-lookup"><span data-stu-id="72abf-303">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_6ccfd0a1-485a-4ac5-9636-89ebab501bef'); "Copy to clipboard.")

    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>

###

<span data-ttu-id="72abf-304"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">超时和计划外断开连接</span></a></span><span class="sxs-lookup"><span data-stu-id="72abf-304"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Time-outs and unplanned disconnections</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-305">Windows PowerShell Web 访问会话超时。</span><span class="sxs-lookup"><span data-stu-id="72abf-305">Windows PowerShell Web Access sessions time out.</span></span> <span data-ttu-id="72abf-306">在 Windows Server 2012 上运行的 Windows PowerShell Web 访问中，会话停止活动 15 分钟后，系统会向登录的用户发出超时消息。</span><span class="sxs-lookup"><span data-stu-id="72abf-306">In Windows PowerShell Web Access running on Windows Server 2012, A time-out message is displayed to signed-in users after 15 minutes of session inactivity.</span></span> <span data-ttu-id="72abf-307">如果用户在超时信息显示后五分钟内无任何回应，则会话结束，用户被注销。</span><span class="sxs-lookup"><span data-stu-id="72abf-307">If the user does not respond within five minutes after the time-out message is displayed, the session is ended, and the user is signed out.</span></span> <span data-ttu-id="72abf-308">你可以在 IIS 管理器的网站设置中，更改会话的超时时间。</span><span class="sxs-lookup"><span data-stu-id="72abf-308">You can change time-out periods for sessions in the website settings in IIS Manager.</span></span>

<span data-ttu-id="72abf-309">在 Windows Server 2012 R2 上运行的 Windows PowerShell Web 访问中，会话停止活动 20 分钟后，会话默认超时。</span><span class="sxs-lookup"><span data-stu-id="72abf-309">In Windows PowerShell Web Access running on Windows Server 2012 R2, sessions time out, by default, after 20 minutes of inactivity.</span></span> <span data-ttu-id="72abf-310">如果用户从基于 Web 的控制台中的会话断开连接是由于网络错误或其他计划外关机或故障，而不是因为他们自己关闭了会话，Windows PowerShell Web 访问会话将继续运行并连接到目标计算机，直到客户端的超时期结束。</span><span class="sxs-lookup"><span data-stu-id="72abf-310">If users are disconnected from sessions in the web-based console because of network errors or other unplanned shutdowns or failures, and not because they have closed the sessions themselves, the Windows PowerShell Web Access sessions continue to run, connected to target computers, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="72abf-311">会话在默认的 20 分钟或网关管理员指定的超时期（以时间较短者为准）后断开连接。</span><span class="sxs-lookup"><span data-stu-id="72abf-311">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

<span data-ttu-id="72abf-312">如果网关服务器正在运行 Windows Server 2012 R2，Windows PowerShell Web 访问将允许用户稍后重新连接到已保存的会话，但是，如果是网络错误、计划外关机或其他故障导致会话断开连接，用户需在网关管理员指定的超时期过后，才能查看或重新连接到已保存的会话。</span><span class="sxs-lookup"><span data-stu-id="72abf-312">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but when network errors, unplanned shutdowns, or other failures disconnect sessions, users cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

<span data-ttu-id="72abf-313"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="72abf-313"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="72abf-314">[安装和使用 Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Windows PowerShell Web 访问 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)</span><span class="sxs-lookup"><span data-stu-id="72abf-314">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx)</span></span>

<span data-ttu-id="72abf-315"><span>显示：</span>继承内容受保护</span><span class="sxs-lookup"><span data-stu-id="72abf-315"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="72abf-316"><span class="stdr-votetitle">此页面是否有所帮助？</span></span><span class="sxs-lookup"><span data-stu-id="72abf-316"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="72abf-317">是 否</span><span class="sxs-lookup"><span data-stu-id="72abf-317">Yes No</span></span>

<span data-ttu-id="72abf-318">更多反馈？</span><span class="sxs-lookup"><span data-stu-id="72abf-318">Additional feedback?</span></span>

<span data-ttu-id="72abf-319">剩余 <span class="stdr-count"><span class="stdr-charcnt">1500</span> 个字符</span>提交，跳过此部分</span><span class="sxs-lookup"><span data-stu-id="72abf-319"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="72abf-320"><span class="stdr-thankyou">谢谢！</span></span><span class="sxs-lookup"><span data-stu-id="72abf-320"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="72abf-321"><span class="stdr-appreciate">我们非常感谢你的反馈意见。</span></span><span class="sxs-lookup"><span data-stu-id="72abf-321"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="72abf-322">管理个人资料</span><span class="sxs-lookup"><span data-stu-id="72abf-322">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="72abf-323"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span>站点反馈</a>站点反馈</span><span class="sxs-lookup"><span data-stu-id="72abf-323"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="72abf-324"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="72abf-324"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="72abf-325">告诉我们你的体验...</span><span class="sxs-lookup"><span data-stu-id="72abf-325">Tell us about your experience...</span></span>

<span data-ttu-id="72abf-326">页面加载速度快吗？</span><span class="sxs-lookup"><span data-stu-id="72abf-326">Did the page load quickly?</span></span>

<span data-ttu-id="72abf-327"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="72abf-327"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="72abf-328">你喜欢页面设计吗？</span><span class="sxs-lookup"><span data-stu-id="72abf-328">Do you like the page design?</span></span>

<span data-ttu-id="72abf-329"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="72abf-329"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="72abf-330">告诉我们更多内容</span><span class="sxs-lookup"><span data-stu-id="72abf-330">Tell us more</span></span>

-   [<span data-ttu-id="72abf-331">快讯</span><span class="sxs-lookup"><span data-stu-id="72abf-331">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="72abf-332">联系我们</span><span class="sxs-lookup"><span data-stu-id="72abf-332">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="72abf-333">隐私声明</span><span class="sxs-lookup"><span data-stu-id="72abf-333">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="72abf-334">使用条款</span><span class="sxs-lookup"><span data-stu-id="72abf-334">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="72abf-335">商标</span><span class="sxs-lookup"><span data-stu-id="72abf-335">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="72abf-336">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="72abf-336">© 2016 Microsoft</span></span>

<span data-ttu-id="72abf-337">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="72abf-337">© 2016 Microsoft</span></span>

<span data-ttu-id="72abf-338">链接到此站点或从中引用的第三方脚本或代码由拥有此类代码的第三方（而非 Microsoft）授权给你。</span><span class="sxs-lookup"><span data-stu-id="72abf-338">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="72abf-339">请参阅 ASP.NET Ajax CDN 使用条款，网址为 http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="72abf-339">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />


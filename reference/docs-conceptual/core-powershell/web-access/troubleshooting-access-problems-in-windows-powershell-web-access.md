---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Windows PowerShell Web 访问中的访问问题疑难解答
ms.openlocfilehash: ef476d8e386e5380cb2c9dda69180dfce8748bf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="1af37-103">Windows PowerShell Web 访问中的访问问题疑难解答</span><span class="sxs-lookup"><span data-stu-id="1af37-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="1af37-104">更新时间：2013 年 6 月 24 日（修订时间：2017 年 8 月 23 日）</span><span class="sxs-lookup"><span data-stu-id="1af37-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="1af37-105">适用于：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="1af37-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="1af37-106">下列各部分标识了一些使用 Windows PowerShell Web 访问尝试连接到远程计算机时可能遇到的常见问题，其中包括解决这些问题的建议。</span><span class="sxs-lookup"><span data-stu-id="1af37-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="1af37-107">登录失败</span><span class="sxs-lookup"><span data-stu-id="1af37-107">Sign-in failure</span></span>

<span data-ttu-id="1af37-108">失败可能是由于下列某个原因所至：</span><span class="sxs-lookup"><span data-stu-id="1af37-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="1af37-109">允许用户访问计算机的授权规则或远程计算机上的特定会话配置并不存在。</span><span class="sxs-lookup"><span data-stu-id="1af37-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="1af37-110">Windows PowerShell Web 访问安全是严谨的；必须使用授权规则明确赋予用户访问远程计算机的权限。</span><span class="sxs-lookup"><span data-stu-id="1af37-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="1af37-111">有关创建授权规则的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。</span><span class="sxs-lookup"><span data-stu-id="1af37-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="1af37-112">用户未获得访问目标计算机的权限。</span><span class="sxs-lookup"><span data-stu-id="1af37-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="1af37-113">这是由访问控制列表 (ACL) 来确定的。</span><span class="sxs-lookup"><span data-stu-id="1af37-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="1af37-114">有关详细信息，请参阅[登录到 Windows PowerShell Web 访问](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)或 Windows PowerShell 团队博客。</span><span class="sxs-lookup"><span data-stu-id="1af37-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="1af37-115">可能无法在目标计算机上启用 Windows PowerShell 远程管理。</span><span class="sxs-lookup"><span data-stu-id="1af37-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="1af37-116">验证用户尝试连接的计算机上是否已启用远程管理。</span><span class="sxs-lookup"><span data-stu-id="1af37-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="1af37-117">有关详细信息，请参阅 [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)（如何配置计算机进行远程处理）。</span><span class="sxs-lookup"><span data-stu-id="1af37-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="1af37-118">内部服务器错误</span><span class="sxs-lookup"><span data-stu-id="1af37-118">Internal Server Error</span></span>

<span data-ttu-id="1af37-119">用户尝试在 Internet Explorer 窗口中登录到 Windows PowerShell Web 访问时，系统会向他们显示“内部服务器错误”页面或 Internet Explorer 停止响应。</span><span class="sxs-lookup"><span data-stu-id="1af37-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="1af37-120">此问题特定于 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="1af37-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="1af37-121">可能的原因</span><span class="sxs-lookup"><span data-stu-id="1af37-121">Possible cause</span></span>

<span data-ttu-id="1af37-122">对于已使用包含中文字符的域名登录的用户或网关服务器名称中包含一个或多个中文字符时会出现此问题。</span><span class="sxs-lookup"><span data-stu-id="1af37-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="1af37-123">解决方法</span><span class="sxs-lookup"><span data-stu-id="1af37-123">Workaround</span></span>

1. [<span data-ttu-id="1af37-124">安装并运行 Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="1af37-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="1af37-125">将 Internet Explorer“文档模式”设置更改为“IE10 标准”。</span><span class="sxs-lookup"><span data-stu-id="1af37-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="1af37-126">按 F12 打开“开发人员工具”控制台。</span><span class="sxs-lookup"><span data-stu-id="1af37-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="1af37-127">在 Internet Explorer 10 中，单击“浏览器模式”，然后选择“Internet Explorer 10”。</span><span class="sxs-lookup"><span data-stu-id="1af37-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="1af37-128">单击“文档模式”，然后单击“IE10 标准”。</span><span class="sxs-lookup"><span data-stu-id="1af37-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="1af37-129">再次按 **F12** 可关闭“开发人员工具”控制台。</span><span class="sxs-lookup"><span data-stu-id="1af37-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="1af37-130">在 Internet Explorer 10 中禁用自动代理配置。</span><span class="sxs-lookup"><span data-stu-id="1af37-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="1af37-131">单击 **“工具”**，然后单击 **“Internet 选项”**。</span><span class="sxs-lookup"><span data-stu-id="1af37-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="1af37-132">在“Internet 选项”对话框中的“连接”选项卡上，单击“LAN 设置”。</span><span class="sxs-lookup"><span data-stu-id="1af37-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="1af37-133">清除“自动检测设置”复选框。</span><span class="sxs-lookup"><span data-stu-id="1af37-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="1af37-134">单击“确定”，然后再次单击“确定”可关闭“Internet 选项”对话框。</span><span class="sxs-lookup"><span data-stu-id="1af37-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="1af37-135">无法连接到远程工作组计算机</span><span class="sxs-lookup"><span data-stu-id="1af37-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="1af37-136">如果目标计算机在工作组中，则使用以下语法，提供用户名并登录到计算机：`<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="1af37-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="1af37-137">找不到 Web 服务器 (IIS) 管理工具，即使已安装了角色</span><span class="sxs-lookup"><span data-stu-id="1af37-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="1af37-138">如果使用 `Install-WindowsFeature` cmdlet 安装了 Windows PowerShell Web 访问，除非将 `-IncludeManagementTools` 参数添加到 cmdlet，否则不会安装管理工具。</span><span class="sxs-lookup"><span data-stu-id="1af37-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="1af37-139">有关示例，请参阅[使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="1af37-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="1af37-140">可选择在以网关服务器为目标的“添加角色和功能向导”会话中的工具，添加 IIS Manager 控制台及其他所需的 IIS 管理工具。</span><span class="sxs-lookup"><span data-stu-id="1af37-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="1af37-141">“添加角色和功能向导”可从服务器管理器中打开。</span><span class="sxs-lookup"><span data-stu-id="1af37-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="1af37-142">无法访问 Windows PowerShell Web 访问网站</span><span class="sxs-lookup"><span data-stu-id="1af37-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="1af37-143">如果已在 Internet Explorer 中启用了增强的安全配置 (IE ESC)，可将 Windows PowerShell Web 访问网站添加到受信任的站点列表。</span><span class="sxs-lookup"><span data-stu-id="1af37-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="1af37-144">出于安全风险考虑，建议禁用 IE ESC。</span><span class="sxs-lookup"><span data-stu-id="1af37-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="1af37-145">可在服务器管理器中的“本地服务器”页面上的“属性”磁贴中禁用 IE ESC。</span><span class="sxs-lookup"><span data-stu-id="1af37-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="1af37-146">授权失败。</span><span class="sxs-lookup"><span data-stu-id="1af37-146">An authorization failure occurred.</span></span> <span data-ttu-id="1af37-147">请验证你是否被授权连接到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="1af37-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="1af37-148">如果网关服务器为目标计算机且也位于工作组中，尝试连接时，会显示上述错误消息。</span><span class="sxs-lookup"><span data-stu-id="1af37-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="1af37-149">如果网关服务器也是目标计算机且位于工作组中，指定用户名、计算机名称以及用户组名。</span><span class="sxs-lookup"><span data-stu-id="1af37-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="1af37-150">不要使用点 (.) 自行表示计算机名称。</span><span class="sxs-lookup"><span data-stu-id="1af37-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="1af37-151">方案和适当的值</span><span class="sxs-lookup"><span data-stu-id="1af37-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="1af37-152">所有情况</span><span class="sxs-lookup"><span data-stu-id="1af37-152">All cases</span></span>

<span data-ttu-id="1af37-153">参数</span><span class="sxs-lookup"><span data-stu-id="1af37-153">Parameter</span></span> | <span data-ttu-id="1af37-154">值</span><span class="sxs-lookup"><span data-stu-id="1af37-154">Value</span></span>
-- | --
<span data-ttu-id="1af37-155">UserName</span><span class="sxs-lookup"><span data-stu-id="1af37-155">UserName</span></span> | <span data-ttu-id="1af37-156">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="1af37-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="1af37-157">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="1af37-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="1af37-158">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="1af37-158">.\\user\_name</span></span>
<span data-ttu-id="1af37-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="1af37-159">UserGroup</span></span> | <span data-ttu-id="1af37-160">Server\_name\\user\_group</span><span class="sxs-lookup"><span data-stu-id="1af37-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="1af37-161">Localhost\\user\_group</span><span class="sxs-lookup"><span data-stu-id="1af37-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="1af37-162">.\\user\_group</span><span class="sxs-lookup"><span data-stu-id="1af37-162">.\\user\_group</span></span>
<span data-ttu-id="1af37-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="1af37-163">ComputerGroup</span></span> | <span data-ttu-id="1af37-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="1af37-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="1af37-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="1af37-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="1af37-166">.\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="1af37-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="1af37-167">网关服务器位于域中</span><span class="sxs-lookup"><span data-stu-id="1af37-167">Gateway server is in a domain</span></span>

<span data-ttu-id="1af37-168">参数</span><span class="sxs-lookup"><span data-stu-id="1af37-168">Parameter</span></span> | <span data-ttu-id="1af37-169">值</span><span class="sxs-lookup"><span data-stu-id="1af37-169">Value</span></span>
-- | --
<span data-ttu-id="1af37-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="1af37-170">ComputerName</span></span> | <span data-ttu-id="1af37-171">网关服务器的完全限定名称或 Localhost</span><span class="sxs-lookup"><span data-stu-id="1af37-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="1af37-172">网关服务器位于工作组中</span><span class="sxs-lookup"><span data-stu-id="1af37-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="1af37-173">参数</span><span class="sxs-lookup"><span data-stu-id="1af37-173">Parameter</span></span> | <span data-ttu-id="1af37-174">值</span><span class="sxs-lookup"><span data-stu-id="1af37-174">Value</span></span>
-- | --
<span data-ttu-id="1af37-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="1af37-175">ComputerName</span></span> | <span data-ttu-id="1af37-176">服务器名称</span><span class="sxs-lookup"><span data-stu-id="1af37-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="1af37-177">Gateway credentials</span><span class="sxs-lookup"><span data-stu-id="1af37-177">Gateway credentials</span></span>

<span data-ttu-id="1af37-178">以目标计算机身份登录到网关服务器，方法是使用以下格式之一的凭据。</span><span class="sxs-lookup"><span data-stu-id="1af37-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="1af37-179">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="1af37-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="1af37-180">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="1af37-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="1af37-181">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="1af37-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="1af37-182">授权规则中显示安全标识符 (SID)</span><span class="sxs-lookup"><span data-stu-id="1af37-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="1af37-183">在授权规则中显示安全标识符 (SID) 而不是语法 user\_name/computer\_name。</span><span class="sxs-lookup"><span data-stu-id="1af37-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="1af37-184">规则不再有效或 Active Directory 域服务查询失败。</span><span class="sxs-lookup"><span data-stu-id="1af37-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="1af37-185">如果网关服务器曾一时位于工作组中，但后来加入域中，则这种情形下通常授权规则无效</span><span class="sxs-lookup"><span data-stu-id="1af37-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="1af37-186">无法使用规则登录为带有域的 IPv6 地址</span><span class="sxs-lookup"><span data-stu-id="1af37-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="1af37-187">无法登录到已在授权规则中指定为带有域的 IPv6 地址的目标计算机。</span><span class="sxs-lookup"><span data-stu-id="1af37-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="1af37-188">授权规则不支持域名形式的 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="1af37-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="1af37-189">若要使用 IPv6 地址指定目标计算机，请在授权规则中使用原始 IPv6 地址（包含冒号）。</span><span class="sxs-lookup"><span data-stu-id="1af37-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="1af37-190">支持域和数值（带有冒号）IPv6 地址作为 Windows PowerShell Web 访问登录页面而非授权规则中的目标计算机名称。</span><span class="sxs-lookup"><span data-stu-id="1af37-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="1af37-191">有关 IPv6 地址的详细信息，请参阅 [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx)（IPv6 的工作原理）。</span><span class="sxs-lookup"><span data-stu-id="1af37-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="1af37-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1af37-192">See Also</span></span>

- <span data-ttu-id="1af37-193">[Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="1af37-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="1af37-194">[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="1af37-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="1af37-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="1af37-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
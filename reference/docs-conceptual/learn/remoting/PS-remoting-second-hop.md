---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 在 PowerShell 远程处理中形成第二个跃点
ms.openlocfilehash: 567d75009f7d53e9e95e5480b275ec3991cfb9f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417623"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="967f2-103">在 PowerShell 远程处理中形成第二个跃点</span><span class="sxs-lookup"><span data-stu-id="967f2-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="967f2-104">“第二个跃点问题”是指如下所示的情况：</span><span class="sxs-lookup"><span data-stu-id="967f2-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="967f2-105">已登录到 _ServerA_。</span><span class="sxs-lookup"><span data-stu-id="967f2-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="967f2-106">在 _ServerA_ 中，启动远程 PowerShell 会话，以连接到 _ServerB_。</span><span class="sxs-lookup"><span data-stu-id="967f2-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="967f2-107">通过 PowerShell 远程处理会话在 _ServerB_ 上运行的命令尝试访问 _ServerC_ 上的资源。</span><span class="sxs-lookup"><span data-stu-id="967f2-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="967f2-108">已拒绝访问 _ServerC_ 上的资源，因为用于创建 PowerShell 远程处理会话的凭据未从 _ServerB_ 传递到 _ServerC_。</span><span class="sxs-lookup"><span data-stu-id="967f2-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="967f2-109">有几种方法可以解决此问题：</span><span class="sxs-lookup"><span data-stu-id="967f2-109">There are several ways to address this problem.</span></span> <span data-ttu-id="967f2-110">在本主题中，我们将了解第二个跃点问题的几种最受欢迎的解决方案。</span><span class="sxs-lookup"><span data-stu-id="967f2-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="967f2-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="967f2-111">CredSSP</span></span>

<span data-ttu-id="967f2-112">可以使用[凭据安全支持提供程序(CredSSP)](/windows/win32/secauthn/credential-security-support-provider) 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="967f2-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span></span> <span data-ttu-id="967f2-113">CredSSP 会将凭据缓存在远程服务器 (_ServerB_) 上，因此使用它会给你带来凭据被盗攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="967f2-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="967f2-114">如果远程计算机被攻破，攻击者将有权访问用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="967f2-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="967f2-115">默认情况下，CredSSP 在客户端和服务器计算机上都处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="967f2-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="967f2-116">应该仅在最受信任的环境中启用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="967f2-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="967f2-117">例如，连接到域控制器的域管理员，因为域控制器是高度可信任的。</span><span class="sxs-lookup"><span data-stu-id="967f2-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="967f2-118">若要详细了解在使用 CredSSP 进行 PowerShell 远程处理时需要注意的安全问题，请参阅[非蓄意破坏：当心 CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp)。</span><span class="sxs-lookup"><span data-stu-id="967f2-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="967f2-119">有关凭据被盗攻击的详细信息，请参阅[缓解哈希传递 (PtH) 攻击和其他凭据被盗](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。</span><span class="sxs-lookup"><span data-stu-id="967f2-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="967f2-120">有关如何启用和使用 CredSSP 进行 PowerShell 远程处理的示例，请参阅[使用 CredSSP 解决第二个跃点问题](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/)。</span><span class="sxs-lookup"><span data-stu-id="967f2-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="967f2-121">优点</span><span class="sxs-lookup"><span data-stu-id="967f2-121">Pros</span></span>

- <span data-ttu-id="967f2-122">它适用于运行 Windows Server 2008 或更高版本的所有服务器。</span><span class="sxs-lookup"><span data-stu-id="967f2-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="967f2-123">缺点</span><span class="sxs-lookup"><span data-stu-id="967f2-123">Cons</span></span>

- <span data-ttu-id="967f2-124">可能会造成安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="967f2-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="967f2-125">需要客户端和服务器角色的配置。</span><span class="sxs-lookup"><span data-stu-id="967f2-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="967f2-126">Kerberos 委派（非约束）</span><span class="sxs-lookup"><span data-stu-id="967f2-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="967f2-127">还可以使用 Kerberos 非约束委派来形成第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="967f2-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="967f2-128">但是，此方法无法控制使用委派凭据的位置。</span><span class="sxs-lookup"><span data-stu-id="967f2-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="967f2-129">**注意：** 无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户  。</span><span class="sxs-lookup"><span data-stu-id="967f2-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="967f2-130">有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和 [Kerberos 身份验证工具和设置](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="967f2-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="967f2-131">优点</span><span class="sxs-lookup"><span data-stu-id="967f2-131">Pros</span></span>

- <span data-ttu-id="967f2-132">无需特殊编码。</span><span class="sxs-lookup"><span data-stu-id="967f2-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="967f2-133">缺点</span><span class="sxs-lookup"><span data-stu-id="967f2-133">Cons</span></span>

- <span data-ttu-id="967f2-134">不支持 WinRM 的第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="967f2-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="967f2-135">无法控制使用凭据的位置，因此产生安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="967f2-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="967f2-136">Kerberos 约束委派</span><span class="sxs-lookup"><span data-stu-id="967f2-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="967f2-137">可以使用旧的约束委派（而非基于资源的委派）形成第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="967f2-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="967f2-138">“使用任何身份验证协议”选项配置 Kerberos 约束委派以允许协议转换。</span><span class="sxs-lookup"><span data-stu-id="967f2-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="967f2-139">无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户  。</span><span class="sxs-lookup"><span data-stu-id="967f2-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="967f2-140">有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和 [Kerberos 身份验证工具和设置](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="967f2-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="967f2-141">优点</span><span class="sxs-lookup"><span data-stu-id="967f2-141">Pros</span></span>

- <span data-ttu-id="967f2-142">无需特殊编码</span><span class="sxs-lookup"><span data-stu-id="967f2-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="967f2-143">缺点</span><span class="sxs-lookup"><span data-stu-id="967f2-143">Cons</span></span>

- <span data-ttu-id="967f2-144">不支持 WinRM 的第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="967f2-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="967f2-145">必须对远程服务器 (ServerB  ) 的 Active Directory 对象进行配置。</span><span class="sxs-lookup"><span data-stu-id="967f2-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="967f2-146">限于一个域。</span><span class="sxs-lookup"><span data-stu-id="967f2-146">Limited to one domain.</span></span> <span data-ttu-id="967f2-147">不能跨域或林。</span><span class="sxs-lookup"><span data-stu-id="967f2-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="967f2-148">需要权限才能更新对象和服务主体名称 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="967f2-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="967f2-149">基于资源的 Kerberos 约束委派</span><span class="sxs-lookup"><span data-stu-id="967f2-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="967f2-150">通过使用（Windows Server 2012 中引入的）基于资源的 Kerberos 约束委派，在资源驻留的服务器对象上配置凭据委派。</span><span class="sxs-lookup"><span data-stu-id="967f2-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="967f2-151">在上述第二个跃点场景中，配置 _ServerC_ 以指定从何处接受委派凭据。</span><span class="sxs-lookup"><span data-stu-id="967f2-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="967f2-152">**注意：** 无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户  。</span><span class="sxs-lookup"><span data-stu-id="967f2-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="967f2-153">有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和 [Kerberos 身份验证工具和设置](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="967f2-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="967f2-154">优点</span><span class="sxs-lookup"><span data-stu-id="967f2-154">Pros</span></span>

- <span data-ttu-id="967f2-155">不存储凭据。</span><span class="sxs-lookup"><span data-stu-id="967f2-155">Credentials are not stored.</span></span>
- <span data-ttu-id="967f2-156">使用 PowerShell cmdlet 进行配置相对容易 - 无需任何特殊编码。</span><span class="sxs-lookup"><span data-stu-id="967f2-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="967f2-157">无需特殊域访问权限。</span><span class="sxs-lookup"><span data-stu-id="967f2-157">No special domain access is required.</span></span>
- <span data-ttu-id="967f2-158">可跨域和林使用。</span><span class="sxs-lookup"><span data-stu-id="967f2-158">Works across domains and forests.</span></span>
- <span data-ttu-id="967f2-159">PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="967f2-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="967f2-160">缺点</span><span class="sxs-lookup"><span data-stu-id="967f2-160">Cons</span></span>

- <span data-ttu-id="967f2-161">要求 Windows Server 2012 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="967f2-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="967f2-162">不支持 WinRM 的第二个跃点。</span><span class="sxs-lookup"><span data-stu-id="967f2-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="967f2-163">需要权限才能更新对象和服务主体名称 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="967f2-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="967f2-164">示例</span><span class="sxs-lookup"><span data-stu-id="967f2-164">Example</span></span>

<span data-ttu-id="967f2-165">让我们看看 PowerShell 示例，该示例在 ServerC  上配置基于资源的约束委派以允许来自 _ServerB_ 的委派凭据。</span><span class="sxs-lookup"><span data-stu-id="967f2-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="967f2-166">此示例假定所有服务器都运行 Windows Server 2012 或更高版本，并且任一服务器所属的每个域具有至少一个 Windows Server 2012 域控制器。</span><span class="sxs-lookup"><span data-stu-id="967f2-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="967f2-167">在配置约束委派前，必须先添加 `RSAT-AD-PowerShell` 功能以安装 Active Directory PowerShell 模块，然后将该模块导入会话：</span><span class="sxs-lookup"><span data-stu-id="967f2-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="967f2-168">现在多个可用的 cmdlet 具有 **PrincipalsAllowedToDelegateToAccount** 参数：</span><span class="sxs-lookup"><span data-stu-id="967f2-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="967f2-169">**PrincipalsAllowedToDelegateToAccount** 参数可设置 Active Directory 对象属性 **msDS AllowedToActOnBehalfOfOtherIdentity**，其中包含一份访问控制列表 (ACL)，指定了哪些帐户有权向关联帐户委派凭据（在本示例中，该帐户为 _Server_ 的计算机帐户）。</span><span class="sxs-lookup"><span data-stu-id="967f2-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="967f2-170">现在，我们来设置用于表示服务器的变量：</span><span class="sxs-lookup"><span data-stu-id="967f2-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="967f2-171">默认情况下，WinRM（由此还有 PowerShell 远程处理）作为计算机帐户运行。</span><span class="sxs-lookup"><span data-stu-id="967f2-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="967f2-172">可通过查看 `winrm` 服务的 **StartName** 属性看到：</span><span class="sxs-lookup"><span data-stu-id="967f2-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="967f2-173">为了 _ServerC_ 允许来自 _ServerB_ 上的 PowerShell 远程处理会话的委派，我们通过将 _ServerC_ 上的 **PrincipalsAllowedToDelegateToAccount** 参数设为 _ServerB_ 的计算机对象来授予权限：</span><span class="sxs-lookup"><span data-stu-id="967f2-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="967f2-174">Kerberos [密钥分发中心 (KDC)](/windows/win32/secauthn/key-distribution-center) 缓存拒绝访问尝试（负缓存）长达 15 分钟。</span><span class="sxs-lookup"><span data-stu-id="967f2-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="967f2-175">如果 _ServerB_ 先前已尝试访问 _ServerC_，则需要通过调用以下命令清除 _ServerB_ 上的缓存：</span><span class="sxs-lookup"><span data-stu-id="967f2-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="967f2-176">还可以重启计算机，或等待至少 15 分钟，以清除缓存。</span><span class="sxs-lookup"><span data-stu-id="967f2-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="967f2-177">清除缓存之后，可以通过 _ServerB_ 到 _ServerC_成功运行来自 _ServerA_ 的代码：</span><span class="sxs-lookup"><span data-stu-id="967f2-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="967f2-178">在本示例中，`$using` 变量用于使 `$ServerC` 变量对 _ServerB_ 可见。</span><span class="sxs-lookup"><span data-stu-id="967f2-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="967f2-179">有关 `$using` 变量的详细信息，请参阅 [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx)。</span><span class="sxs-lookup"><span data-stu-id="967f2-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="967f2-180">若要允许多个服务器向 _ServerC_ 委派凭据，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为数组：</span><span class="sxs-lookup"><span data-stu-id="967f2-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="967f2-181">如果想要跨域形成第二个跃点，添加 _ServerB_ 所属域的域控制器的完全限定域名 (FQDN)：</span><span class="sxs-lookup"><span data-stu-id="967f2-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="967f2-182">若要删除向 ServerC 委派凭据的功能，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为 `$null`：</span><span class="sxs-lookup"><span data-stu-id="967f2-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="967f2-183">基于资源的 Kerberos 约束委派的相关信息</span><span class="sxs-lookup"><span data-stu-id="967f2-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="967f2-184">Kerberos 身份验证的中的新功能</span><span class="sxs-lookup"><span data-stu-id="967f2-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- <span data-ttu-id="967f2-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 1 部分）</span><span class="sxs-lookup"><span data-stu-id="967f2-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)</span></span>
- <span data-ttu-id="967f2-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 2 部分）</span><span class="sxs-lookup"><span data-stu-id="967f2-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)</span></span>
- <span data-ttu-id="967f2-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper)（了解 Kerberos 约束委派，以使用集成的 Windows 身份验证进行 Azure Active Directory 应用程序代理部署）</span><span class="sxs-lookup"><span data-stu-id="967f2-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper)</span></span>
- <span data-ttu-id="967f2-188">[[MS-ADA2]：Active Directory 架构属性 M2.210 属性 msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span><span class="sxs-lookup"><span data-stu-id="967f2-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span></span>
- <span data-ttu-id="967f2-189">[[MS-SFU]：Kerberos 协议扩展：用户服务和约束委派协议 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span><span class="sxs-lookup"><span data-stu-id="967f2-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span></span>
- [<span data-ttu-id="967f2-190">基于资源的 Kerberos 约束委派</span><span class="sxs-lookup"><span data-stu-id="967f2-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- <span data-ttu-id="967f2-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)（在不使用约束委派的情况下，使用 PrincipalsAllowedToDelegateToAccount 进行远程管理）</span><span class="sxs-lookup"><span data-stu-id="967f2-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="967f2-192">使用 RunAs 的 PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="967f2-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="967f2-193">可以在 _ServerB_ 上创建会话配置并设置其 **RunAsCredential** 参数。</span><span class="sxs-lookup"><span data-stu-id="967f2-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="967f2-194">有关使用 PSSessionConfiguration 和 RunAs 解决第二个跃点问题的信息，请参阅 [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/)（多跃点 PowerShell 远程处理的另一种解决方案）。</span><span class="sxs-lookup"><span data-stu-id="967f2-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="967f2-195">优点</span><span class="sxs-lookup"><span data-stu-id="967f2-195">Pros</span></span>

- <span data-ttu-id="967f2-196">兼容任何运行 WMF 3.0 或更高版本的服务器。</span><span class="sxs-lookup"><span data-stu-id="967f2-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="967f2-197">缺点</span><span class="sxs-lookup"><span data-stu-id="967f2-197">Cons</span></span>

- <span data-ttu-id="967f2-198">需要在每个中间服务器 (_ServerB_) 上配置 **PSSessionConfiguration** 和 **RunAs**。</span><span class="sxs-lookup"><span data-stu-id="967f2-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="967f2-199">使用域 **RunAs** 帐户时要求密码维护</span><span class="sxs-lookup"><span data-stu-id="967f2-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="967f2-200">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="967f2-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="967f2-201">JEA 允许限制管理员在 PowerShell 会话期间可以运行的命令。</span><span class="sxs-lookup"><span data-stu-id="967f2-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="967f2-202">它可用于解决第二个跃点问题。</span><span class="sxs-lookup"><span data-stu-id="967f2-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="967f2-203">有关 JEA 的信息，请参阅 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)。</span><span class="sxs-lookup"><span data-stu-id="967f2-203">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="967f2-204">优点</span><span class="sxs-lookup"><span data-stu-id="967f2-204">Pros</span></span>

- <span data-ttu-id="967f2-205">使用虚拟帐户时无需密码维护。</span><span class="sxs-lookup"><span data-stu-id="967f2-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="967f2-206">缺点</span><span class="sxs-lookup"><span data-stu-id="967f2-206">Cons</span></span>

- <span data-ttu-id="967f2-207">需要 WMF 5.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="967f2-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="967f2-208">需要在每个中间服务器 (_ServerB_) 上进行配置。</span><span class="sxs-lookup"><span data-stu-id="967f2-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="967f2-209">在 Invoke-Command 脚本块内传递凭据</span><span class="sxs-lookup"><span data-stu-id="967f2-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="967f2-210">可以在对 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet 的调用的 **ScriptBlock** 参数内传递凭据。</span><span class="sxs-lookup"><span data-stu-id="967f2-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="967f2-211">优点</span><span class="sxs-lookup"><span data-stu-id="967f2-211">Pros</span></span>

- <span data-ttu-id="967f2-212">无需特殊服务器配置。</span><span class="sxs-lookup"><span data-stu-id="967f2-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="967f2-213">适用于任何运行 WMF 2.0 或更高版本的服务器。</span><span class="sxs-lookup"><span data-stu-id="967f2-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="967f2-214">缺点</span><span class="sxs-lookup"><span data-stu-id="967f2-214">Cons</span></span>

- <span data-ttu-id="967f2-215">需要繁琐的代码技术。</span><span class="sxs-lookup"><span data-stu-id="967f2-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="967f2-216">运行 WMF 2.0 时，需要不同的语法将参数传递到远程会话。</span><span class="sxs-lookup"><span data-stu-id="967f2-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="967f2-217">示例</span><span class="sxs-lookup"><span data-stu-id="967f2-217">Example</span></span>

<span data-ttu-id="967f2-218">以下示例演示了如何在 **Invoke-command** 脚本块中传递凭据：</span><span class="sxs-lookup"><span data-stu-id="967f2-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="967f2-219">另请参阅</span><span class="sxs-lookup"><span data-stu-id="967f2-219">See also</span></span>

[<span data-ttu-id="967f2-220">PowerShell 远程处理安全注意事项</span><span class="sxs-lookup"><span data-stu-id="967f2-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

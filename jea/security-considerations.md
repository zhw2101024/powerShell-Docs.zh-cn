---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea,powershell,安全性"
title: "JEA 安全注意事项"
ms.openlocfilehash: 2dcce34113998a1c31709b6afe6d0a21c991e79d
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2017
---
# <a name="jea-security-considerations"></a><span data-ttu-id="2a473-103">JEA 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="2a473-103">JEA Security Considerations</span></span>

> <span data-ttu-id="2a473-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2a473-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2a473-105">JEA 通过减少计算机上的永久管理员数量来帮助改善安全状况。</span><span class="sxs-lookup"><span data-stu-id="2a473-105">JEA helps you improve your security posture by reducing the number of permanent administrators on your machines.</span></span>
<span data-ttu-id="2a473-106">为此，它创建了一个新的入口点供用户管理系统（PowerShell 会话配置），该入口点在默认情况下紧密锁定，以防误用。</span><span class="sxs-lookup"><span data-stu-id="2a473-106">It does so by creating a new entry point for users to manage the system (a PowerShell session configuration) which is tightly locked down by default to prevent misuse.</span></span>
<span data-ttu-id="2a473-107">对于需要某些（但并非不受限制的）计算机访问权限来执行管理任务的用户，可授予对 JEA 终结点的权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-107">Users who need some, but not unlimited, access to the machine to perform administrative tasks can be granted access to the JEA endpoint.</span></span>
<span data-ttu-id="2a473-108">由于 JEA 允许用户在无需直接拥有管理员权限的情况下运行管理员命令，因此可以将这些用户从高特权安全组删除（使其成为标准用户）。</span><span class="sxs-lookup"><span data-stu-id="2a473-108">Because JEA allows them to run admin commands without directly having admin access, you can then remove those users from highly privileged security groups (make them standard users).</span></span>

<span data-ttu-id="2a473-109">本主题详细介绍了 JEA 安全模型和最佳做法。</span><span class="sxs-lookup"><span data-stu-id="2a473-109">This topic describes the JEA security model and best practices in more detail.</span></span>

## <a name="run-as-account"></a><span data-ttu-id="2a473-110">运行方式帐户</span><span class="sxs-lookup"><span data-stu-id="2a473-110">Run As account</span></span>

<span data-ttu-id="2a473-111">每个 JEA 终结点都有一个指定的“运行方式”帐户，该帐户是执行连接用户的操作所采用的帐户。</span><span class="sxs-lookup"><span data-stu-id="2a473-111">Each JEA endpoint has a designated "run as" account, which is the account under which the connecting user's actions are performed.</span></span>
<span data-ttu-id="2a473-112">此帐户在[会话配置文件](session-configurations.md)中是可配置的，并且你选择的帐户对终结点的安全性意义重大。</span><span class="sxs-lookup"><span data-stu-id="2a473-112">This account is configurable in the [session configuration file](session-configurations.md), and the account you choose has a significant bearing on the security of your endpoint.</span></span>

<span data-ttu-id="2a473-113">**虚拟帐户**是用于配置运行方式帐户的推荐方法。</span><span class="sxs-lookup"><span data-stu-id="2a473-113">**Virtual accounts** are the recommended way of configuring the run as account.</span></span>
<span data-ttu-id="2a473-114">虚拟帐户是临时创建的一次性本地帐户，便于连接用户在 JEA 会话期间使用。</span><span class="sxs-lookup"><span data-stu-id="2a473-114">Virtual accounts are one-time, temporary local accounts that are created for the connecting user to use during the duration of their JEA session.</span></span>
<span data-ttu-id="2a473-115">一旦用户的会话终止，虚拟帐户将废弃，并且不能再被使用。</span><span class="sxs-lookup"><span data-stu-id="2a473-115">As soon as their session is terminated, the virtual account will be destroyed and cannot be used anymore.</span></span>
<span data-ttu-id="2a473-116">连接用户不知道虚拟帐户的凭据，并且无法通过远程桌面或非约束 PowerShell 终结点等其他方式使用虚拟帐户访问系统。</span><span class="sxs-lookup"><span data-stu-id="2a473-116">The connecting user does not know the credentials for the virtual account and cannot use the virtual account to access the system via other means, such as Remote Desktop or an unconstrained PowerShell endpoint.</span></span>

<span data-ttu-id="2a473-117">默认情况下，虚拟帐户属于计算机上的本地管理员组。</span><span class="sxs-lookup"><span data-stu-id="2a473-117">By default, virtual accounts belong to the local administrators group on the machine.</span></span>
<span data-ttu-id="2a473-118">这将授予他们管理系统中所有内容的全部权限，但这些帐户无权管理网络中的资源。</span><span class="sxs-lookup"><span data-stu-id="2a473-118">This gives them full rights to manage anything on the system, but no rights to manage resources on the network.</span></span>
<span data-ttu-id="2a473-119">在与其他计算机进行身份验证时，用户上下文针对本地计算机帐户，而非虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="2a473-119">When authenticating with other machines, the user context will be that of the local computer account, not the virtual account.</span></span>

<span data-ttu-id="2a473-120">域控制器是一种特殊情况，因为不存在本地管理员组的概念。</span><span class="sxs-lookup"><span data-stu-id="2a473-120">Domain controllers are a special case since there is no concept of a local administrators group.</span></span>
<span data-ttu-id="2a473-121">然而，虚拟帐户属于域管理员，可以管理域控制器上的目录服务。</span><span class="sxs-lookup"><span data-stu-id="2a473-121">Instead, virtual accounts belong to Domain Admins instead and can manage the directory services on the domain controller.</span></span>
<span data-ttu-id="2a473-122">域标识仍然限于在实例化 JEA 会话的域控制器上使用，而任何网络访问都将显示为来自域控制器计算机对象。</span><span class="sxs-lookup"><span data-stu-id="2a473-122">The domain identity is still restricted to use on the domain controller where the JEA session was instantiated, and any network access will appear to come from the domain controller computer object instead.</span></span>

<span data-ttu-id="2a473-123">在这两种情况下，还可以显式定义虚拟帐户应属于哪些安全组。</span><span class="sxs-lookup"><span data-stu-id="2a473-123">In both cases, you can also explicitly define which security groups the virtual account should belong to.</span></span>
<span data-ttu-id="2a473-124">当要执行的任务无需本地/域管理员权限便可完成时，这是一个很合适的做法。</span><span class="sxs-lookup"><span data-stu-id="2a473-124">This is a good practice when the task you are performing can be done without local/domain admin privileges.</span></span>
<span data-ttu-id="2a473-125">如果已为管理员定义了安全组，只需向该组授予虚拟帐户成员身份便可授予其所需权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-125">If you already have a security group defined for your admins, you can simply grant the virtual account membership to that group to give it the permissions it needs.</span></span>
<span data-ttu-id="2a473-126">虚拟帐户组成员身份仅限于工作站和成员服务器上的本地安全组，但在域控制器上，它们只能是域安全组的成员。</span><span class="sxs-lookup"><span data-stu-id="2a473-126">Virtual account group membership is limited to local security groups on workstation and member servers, but on a domain controller they can only be members of domain security groups.</span></span>
<span data-ttu-id="2a473-127">为虚拟帐户指定所属的一个或多个安全组后，该账户将不再属于默认组（本地管理员或域管理员）。</span><span class="sxs-lookup"><span data-stu-id="2a473-127">Once you specify one or more security groups for the virtual account to belong to, it will no longer belong to the default groups (local admin or domain admin).</span></span>

<span data-ttu-id="2a473-128">下表总结了虚拟帐户可能的配置选项和生成权限</span><span class="sxs-lookup"><span data-stu-id="2a473-128">The table below summarizes the possible configuration options and resulting permissions for virtual accounts</span></span>

<span data-ttu-id="2a473-129">计算机类型</span><span class="sxs-lookup"><span data-stu-id="2a473-129">Computer type</span></span>                | <span data-ttu-id="2a473-130">虚拟帐户组配置</span><span class="sxs-lookup"><span data-stu-id="2a473-130">Virtual account group configuration</span></span> | <span data-ttu-id="2a473-131">本地用户上下文</span><span class="sxs-lookup"><span data-stu-id="2a473-131">Local user context</span></span>                                      | <span data-ttu-id="2a473-132">网络用户上下文</span><span class="sxs-lookup"><span data-stu-id="2a473-132">Network user context</span></span>
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
<span data-ttu-id="2a473-133">域控制器</span><span class="sxs-lookup"><span data-stu-id="2a473-133">Domain controller</span></span>            | <span data-ttu-id="2a473-134">默认值</span><span class="sxs-lookup"><span data-stu-id="2a473-134">Default</span></span>                             | <span data-ttu-id="2a473-135">域用户，“*DOMAIN*\Domain Admins”的成员</span><span class="sxs-lookup"><span data-stu-id="2a473-135">Domain user, member of '*DOMAIN*\Domain Admins'</span></span>         | <span data-ttu-id="2a473-136">计算机帐户</span><span class="sxs-lookup"><span data-stu-id="2a473-136">Computer account</span></span>
<span data-ttu-id="2a473-137">域控制器</span><span class="sxs-lookup"><span data-stu-id="2a473-137">Domain controller</span></span>            | <span data-ttu-id="2a473-138">域组 A 和域组 B</span><span class="sxs-lookup"><span data-stu-id="2a473-138">Domain groups A and B</span></span>               | <span data-ttu-id="2a473-139">域用户，“*DOMAIN*\A”、“*DOMAIN*\B”的成员</span><span class="sxs-lookup"><span data-stu-id="2a473-139">Domain user, member of '*DOMAIN*\A', '*DOMAIN*\B'</span></span>       | <span data-ttu-id="2a473-140">计算机帐户</span><span class="sxs-lookup"><span data-stu-id="2a473-140">Computer account</span></span>
<span data-ttu-id="2a473-141">成员服务器或工作站</span><span class="sxs-lookup"><span data-stu-id="2a473-141">Member server or workstation</span></span> | <span data-ttu-id="2a473-142">默认值</span><span class="sxs-lookup"><span data-stu-id="2a473-142">Default</span></span>                             | <span data-ttu-id="2a473-143">本地用户、“*BUILTIN*\Administrators”的成员</span><span class="sxs-lookup"><span data-stu-id="2a473-143">Local user, member of '*BUILTIN*\Administrators'</span></span>        | <span data-ttu-id="2a473-144">计算机帐户</span><span class="sxs-lookup"><span data-stu-id="2a473-144">Computer account</span></span>
<span data-ttu-id="2a473-145">成员服务器或工作站</span><span class="sxs-lookup"><span data-stu-id="2a473-145">Member server or workstation</span></span> | <span data-ttu-id="2a473-146">本地组 C 和 D</span><span class="sxs-lookup"><span data-stu-id="2a473-146">Local groups C and D</span></span>                | <span data-ttu-id="2a473-147">本地用户、“*COMPUTER*\C”和“*COMPUTER*\D”的成员</span><span class="sxs-lookup"><span data-stu-id="2a473-147">Local user, member of '*COMPUTER*\C' and '*COMPUTER*\D'</span></span> | <span data-ttu-id="2a473-148">计算机帐户</span><span class="sxs-lookup"><span data-stu-id="2a473-148">Computer account</span></span>

<span data-ttu-id="2a473-149">查看安全审核事件和应用程序事件日志时，将看到每个 JEA 用户会话都有一个唯一的虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="2a473-149">When you look at security audit events and application event logs, you will see that each JEA user session has a unique virtual account.</span></span>
<span data-ttu-id="2a473-150">这有助于将 JEA 终结点中的用户操作追溯到运行该命令的原始用户。</span><span class="sxs-lookup"><span data-stu-id="2a473-150">This helps you track user actions in a JEA endpoint back to the original user who ran the command.</span></span>
<span data-ttu-id="2a473-151">虚拟帐户名称遵循以下格式：“WinRM Virtual Users\\WinRM\_VA\_ACCOUNTNUMBER\_DOMAIN\_sAMAccountName”。例如，当域“Contoso”中的用户“Alice”在 JEA 终结点中重启服务时，与任何服务控制管理器事件关联的用户名将为“WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice”。</span><span class="sxs-lookup"><span data-stu-id="2a473-151">Virtual account names follow the format "WinRM Virtual Users\\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAIN*\_*sAMAccountName*" For example, if user "Alice" in domain "Contoso" restarts a service in a JEA endpoint, the username associated with any service control manager events would be "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice".</span></span>


<span data-ttu-id="2a473-152">**组托管的服务帐户 (gMSA)** 在成员服务器需要对 JEA 会话中的网络资源具有访问权限时十分有用。</span><span class="sxs-lookup"><span data-stu-id="2a473-152">**Group managed service accounts (gMSAs)** are useful when a member server needs to have access to network resources in the JEA session.</span></span>
<span data-ttu-id="2a473-153">这种情况的一个示例用例是 JEA 终结点，它可用于控制对托管在其它计算机上的 REST API 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-153">An example use case for this is a JEA endpoint that is used to control access to a REST API hosted on a different machine.</span></span>
<span data-ttu-id="2a473-154">编写函数对 REST API 执行所需调用很容易，不过若要通过 API 的身份验证，则需要网络标识。</span><span class="sxs-lookup"><span data-stu-id="2a473-154">It is easy to write functions to make the desired invocations on the REST API, but in order to authenticate with the API you need a network identity.</span></span>
<span data-ttu-id="2a473-155">使用组托管服务帐户可实现“第二个跃点”，同时仍控制哪些计算机可使用该帐户。</span><span class="sxs-lookup"><span data-stu-id="2a473-155">Using a group managed service account makes the "second hop" possible while still having control over which computers can use the account.</span></span>
<span data-ttu-id="2a473-156">gMSA 帐户所属的安全组（本地或域）定义 gMSA 的有效权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-156">The effective permissions of the gMSA are defined by the security groups (local or domain) to which the gMSA account belongs.</span></span>

<span data-ttu-id="2a473-157">JEA 终结点配置为使用 gMSA 帐户时，所有 JEA 用户的操作将显示来自同一个组托管服务帐户。</span><span class="sxs-lookup"><span data-stu-id="2a473-157">When a JEA endpoint is configured to use a gMSA account, the actions of all JEA users will appear to come from the same group managed service account.</span></span>
<span data-ttu-id="2a473-158">将操作追溯到特定用户的唯一方法是标识 PowerShell 会话脚本中运行的命令集。</span><span class="sxs-lookup"><span data-stu-id="2a473-158">The only way you can trace actions back to a specific user is to identify the set of commands run in a PowerShell session transcript.</span></span>

<span data-ttu-id="2a473-159">在未指定运行方式帐户，并希望 PowerShell 使用连接用户的凭据在远程服务器上运行命令时使用传递凭据。</span><span class="sxs-lookup"><span data-stu-id="2a473-159">**Pass-thru credentials** are used when you do not specify a run as account and want PowerShell to use the connecting user's credential to run commands on the remote server.</span></span>
<span data-ttu-id="2a473-160">*不*推荐 JEA 使用此配置，因为该配置要求向连接用户授予特权管理组的直接访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-160">This configuration is *not* recommended for JEA as it would require you to grant the connecting user direct access to privileged management groups.</span></span>
<span data-ttu-id="2a473-161">如果连接用户已有管理员权限，他们可以完全避免 JEA，并通过其他非约束方式管理系统。</span><span class="sxs-lookup"><span data-stu-id="2a473-161">If the connecting user already has admin privileges, they can avoid JEA altogether and manage the system via other, unconstrained means.</span></span>
<span data-ttu-id="2a473-162">有关详细信息，请参阅下节关于如何使 [JEA 不阻止管理员](#jea-does-not-protect-against-admins)的内容。</span><span class="sxs-lookup"><span data-stu-id="2a473-162">See the section below on how [JEA does not protect against admins](#jea-does-not-protect-against-admins) for more information.</span></span>

<span data-ttu-id="2a473-163">**标准运行方式帐户**允许指定整个 PowerShell 会话运行所采用的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="2a473-163">**Standard run as accounts** allow you to specify any user account under which the entire PowerShell session will run.</span></span>
<span data-ttu-id="2a473-164">这有一个重要的区别，因为设置为（通过 `-RunAsCredential` 参数）使用固定运行方式帐户的会话配置并不了解 JEA。</span><span class="sxs-lookup"><span data-stu-id="2a473-164">This is an important distinction, because a session configuration set to use a fixed run as account (with the `-RunAsCredential` parameter) is not JEA-aware.</span></span>
<span data-ttu-id="2a473-165">这意味着角色定义不再按预期正常运行，并且有权访问该终结点的每个用户都会分配相同的角色。</span><span class="sxs-lookup"><span data-stu-id="2a473-165">That means that role definitions no longer function as expected, and every user authorized to access the endpoint will be assigned the same role.</span></span>

<span data-ttu-id="2a473-166">由于将操作追溯到特定用户存在难度并且缺少将用户映射到角色的支持，因此不应该对 JEA 终结点使用 RunAsCredential。</span><span class="sxs-lookup"><span data-stu-id="2a473-166">You should not use a RunAsCredential on a JEA endpoint because of the difficulty in tracing actions back to specific users and the lack of support for mapping users to roles.</span></span>

## <a name="winrm-endpoint-acl"></a><span data-ttu-id="2a473-167">WinRM 终结点 ACL</span><span class="sxs-lookup"><span data-stu-id="2a473-167">WinRM Endpoint ACL</span></span>

<span data-ttu-id="2a473-168">与常规 PowerShell 远程终结点一样，每个 JEA 终结点在 WinRM 配置中都设有单独的访问控制列表 (ACL)，控制哪些用户可以通过 JEA 终结点的身份验证。</span><span class="sxs-lookup"><span data-stu-id="2a473-168">As with regular PowerShell remoting endpoints, each JEA endpoint has a separate access control list (ACL) set in the WinRM configuration that controls who can authenticate with the JEA endpoint.</span></span>
<span data-ttu-id="2a473-169">如果配置错误，受信任的用户可能无法访问 JEA 终结点和/或不受信任的用户可能获得访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-169">If improperly configured, trusted users may not be able to access the JEA endpoint and/or untrusted users may gain access.</span></span>
<span data-ttu-id="2a473-170">但是， WinRM ACL 不影响用户到 JEA 角色的映射。</span><span class="sxs-lookup"><span data-stu-id="2a473-170">The WinRM ACL does not, however, affect the mapping of users to JEA roles.</span></span>
<span data-ttu-id="2a473-171">该映射由系统中注册的会话配置文件中的 *RoleDefinitions* 字段控制。</span><span class="sxs-lookup"><span data-stu-id="2a473-171">That is controlled by the *RoleDefinitions* field in the session configuration file that was registered on the system.</span></span>

<span data-ttu-id="2a473-172">默认情况下，如果使用会话配置文件和一个或多个角色功能注册 JEA 终结点，WinRM ACL 将配置为允许所有用户映射到终结点的一个或多个角色访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-172">By default, when you register a JEA endpoint using a session configuration file and one or more role capabilities, the WinRM ACL will be configured to allow all users mapping to one or more roles access to the endpoint.</span></span>
<span data-ttu-id="2a473-173">例如，使用以下命令配置的 JEA 会话将授予对 CONTOSO\JEA\_Lev1 和 CONTOSO\JEA\_Lev2 的完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-173">For example, a JEA session configured using the following commands will grant full access to *CONTOSO\JEA\_Lev1* and *CONTOSO\JEA\_Lev2*.</span></span>

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

<span data-ttu-id="2a473-174">可以使用 [Get-pssessionconfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 审核用户权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-174">You can audit user permissions with the [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

<span data-ttu-id="2a473-175">若要更改哪些用户具有访问权限，请运行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` 进行交互式提示或运行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` 来更新权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-175">To change which users have access, run either `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` for an interactive prompt or `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` to update the permissions.</span></span>
<span data-ttu-id="2a473-176">用户至少需要调用权限才能访问 JEA 终结点。</span><span class="sxs-lookup"><span data-stu-id="2a473-176">Users need at least *Invoke* rights to access the JEA endpoint.</span></span>

<span data-ttu-id="2a473-177">如果其他用户获得 JEA 终结点的访问权限，但不属于会话配置文件中定义的任何角色，他们将能够启动 JEA 会话，但只有默认 cmdlet 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-177">If additional users are granted access to the JEA endpoint but do not fall into any of the roles defined in the session configuration file, they will be able to start a JEA session but only have access to the default cmdlets.</span></span>
<span data-ttu-id="2a473-178">可以通过运行 `Get-PSSessionCapability` 来审核 JEA 终结点中的用户权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-178">You can audit user permissions in a JEA endpoint by running `Get-PSSessionCapability`.</span></span>
<span data-ttu-id="2a473-179">有关审核用户有权访问 JEA 终结点中的哪些命令的详细信息，请查看[有关 JEA 的审核和报告](audit-and-report.md)。</span><span class="sxs-lookup"><span data-stu-id="2a473-179">Check out the [Auditing and Reporting on JEA](audit-and-report.md) article for more information about auditing which commands a user has access to in a JEA endpoint.</span></span>

## <a name="least-privilege-roles"></a><span data-ttu-id="2a473-180">最小特权角色</span><span class="sxs-lookup"><span data-stu-id="2a473-180">Least privilege roles</span></span>

<span data-ttu-id="2a473-181">设计 JEA 角色时，务必记住后台运行的虚拟或组托管服务帐户通常具有不受限制的访问权限，以管理本地计算机。</span><span class="sxs-lookup"><span data-stu-id="2a473-181">When designing JEA roles, it is important to remember that the virtual or group managed service account running behind the scenes often has unrestricted access to manage the local machine.</span></span>
<span data-ttu-id="2a473-182">JEA 角色功能通过限制可使用该特权运行上下文的命令和应用程序帮助限制使用该帐户的目的。</span><span class="sxs-lookup"><span data-stu-id="2a473-182">JEA role capabilities help restrict what that account can be used for by limiting the commands and applications that can be run using that privileged context.</span></span>
<span data-ttu-id="2a473-183">设计错误的角色可允许运行危险命令，该命令可能允许用户中断 JEA 边界或获得对敏感信息的访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-183">Improperly designed roles can allow dangerous commands to run that may allow a user to break out of the JEA boundaries or obtain access to sensitive information.</span></span>

<span data-ttu-id="2a473-184">例如，考虑以下角色功能事项：</span><span class="sxs-lookup"><span data-stu-id="2a473-184">For example, consider the following role capability entry:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

<span data-ttu-id="2a473-185">此角色功能使用户能够从 Microsoft.PowerShell.Management 模块使用名词“Process”运行任何 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2a473-185">This role capability allows users to run any PowerShell cmdlet with the noun "Process" from the Microsoft.PowerShell.Management module.</span></span>
<span data-ttu-id="2a473-186">用户可能需要访问 `Get-Process` 等 cmdlet，以了解哪些应用程序在系统上运行，以及访问 `Stop-Process` 以终止任何挂起的应用程序。</span><span class="sxs-lookup"><span data-stu-id="2a473-186">Users may need to access cmdlets like `Get-Process` to understand what applications are running on the system and `Stop-Process` to kill any hung applications.</span></span>
<span data-ttu-id="2a473-187">但是，此项还允许访问 `Start-Process`，以用于启动具有完全管理员权限的任意程序。</span><span class="sxs-lookup"><span data-stu-id="2a473-187">However, this entry also allows `Start-Process`, which can be used to start up an arbitrary program with full administrator permissions.</span></span>
<span data-ttu-id="2a473-188">该程序无需安装在系统本地，因此攻击者只需启动文件共享上的一个程序，就可授予连接用户本地管理员权限、运行恶意程序等等。”</span><span class="sxs-lookup"><span data-stu-id="2a473-188">The program doesn't need to be installed locally on the system, so an adversary could simply start a program on a file share that gives the connecting user local admin privileges, runs malware, and more.'</span></span>

<span data-ttu-id="2a473-189">此相同角色功能的更安全版本如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a473-189">A more secure version of this same role capability would look like:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

<span data-ttu-id="2a473-190">避免在角色功能中使用通配符，并确保定期[审计有效用户权限](audit-and-report.md#check-effective-rights-for-a-specific-user)可了解用户有权访问哪些命令。</span><span class="sxs-lookup"><span data-stu-id="2a473-190">Avoid using wildcards in role capabilities, and be sure to [audit effective user permissions](audit-and-report.md#check-effective-rights-for-a-specific-user) regularly to understand which commands a user has access to.</span></span>

## <a name="jea-does-not-protect-against-admins"></a><span data-ttu-id="2a473-191">JEA 不阻止管理员</span><span class="sxs-lookup"><span data-stu-id="2a473-191">JEA does not protect against admins</span></span>

<span data-ttu-id="2a473-192">JEA 核心原则之一是允许非管理员执行某些管理员任务。</span><span class="sxs-lookup"><span data-stu-id="2a473-192">One of the core principles of JEA is that it allows non-admins to perform *some* admin tasks.</span></span>
<span data-ttu-id="2a473-193">JEA 不阻止已经具有管理员权限的用户。</span><span class="sxs-lookup"><span data-stu-id="2a473-193">JEA does not protect against those who already have administrator privileges.</span></span>
<span data-ttu-id="2a473-194">环境中属于“域管理员”、“本地管理员”或其他高特权组的用户，仍能够通过其他方式登录到计算机获得 JEA 的保护。</span><span class="sxs-lookup"><span data-stu-id="2a473-194">Users who belong "domain admins," "local admins," or other highly privileged groups in your environment will still be able to get around JEA's protections by signing into the machine via another means.</span></span>
<span data-ttu-id="2a473-195">例如，他们可以使用 RDP 登录、使用远程 MMC 控制台，或连接到不受约束的 PowerShell 终结点。</span><span class="sxs-lookup"><span data-stu-id="2a473-195">They could, for example, sign in with RDP, use remote MMC consoles, or connect to unconstrained PowerShell endpoints.</span></span>
<span data-ttu-id="2a473-196">系统上的本地管理员还可以修改 JEA 配置以允许其他用户管理系统或更改角色功能，从而扩展其 JEA 会话中用户可以执行的操作范围。</span><span class="sxs-lookup"><span data-stu-id="2a473-196">Local admins on the system can also modify JEA configurations to allow additional users to manage the system or change a role capability to extend the scope of what a user can do in their JEA session.</span></span>
<span data-ttu-id="2a473-197">因此必须要评估 JEA 用户的扩展权限，了解是否可以通过其他方式获得对系统的特许访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-197">It is therefore important to evaluate your JEA users' extended permissions to see if there are other ways they could gain privileged access to the system.</span></span>

<span data-ttu-id="2a473-198">一种常见做法是使用 JEA 进行常规的日常维护，并且获得“及时”特许访问权限解决方案，使用户在紧急情况下能够临时成为本地管理员。</span><span class="sxs-lookup"><span data-stu-id="2a473-198">A common practice is to use JEA for regular day-to-day maintenance and have a "just in time" privileged access management solution allow users to temporarily become local admins in emergency situations.</span></span>
<span data-ttu-id="2a473-199">这有助于确保用户不会成为系统的永久管理员，只有当且仅当他们完成记录这些权限使用情况的工作流时，才能获得这些权限。</span><span class="sxs-lookup"><span data-stu-id="2a473-199">This helps ensure users are not permanent admins on the system, but can get those rights if, and only when, they complete a workflow that documents their use of those permissions.</span></span>


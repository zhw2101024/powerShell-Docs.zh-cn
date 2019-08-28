---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 会话配置
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017728"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="53cc7-103">JEA 会话配置</span><span class="sxs-lookup"><span data-stu-id="53cc7-103">JEA Session Configurations</span></span>

<span data-ttu-id="53cc7-104">JEA 终结点通过在系统上创建和注册 PowerShell 会话配置文件进行注册。</span><span class="sxs-lookup"><span data-stu-id="53cc7-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="53cc7-105">会话配置定义了可使用 JEA 终结点的人员及其有权访问的角色。</span><span class="sxs-lookup"><span data-stu-id="53cc7-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="53cc7-106">它们还定义了一些全局设置，这些设置应用于 JEA 会话中的所有用户。</span><span class="sxs-lookup"><span data-stu-id="53cc7-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="53cc7-107">创建会话配置文件</span><span class="sxs-lookup"><span data-stu-id="53cc7-107">Create a session configuration file</span></span>

<span data-ttu-id="53cc7-108">要注册 JEA 终结点，必须指定该终结点的配置方式。</span><span class="sxs-lookup"><span data-stu-id="53cc7-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="53cc7-109">需要考虑很多选项。</span><span class="sxs-lookup"><span data-stu-id="53cc7-109">There are many options to consider.</span></span> <span data-ttu-id="53cc7-110">最重要的选项是：</span><span class="sxs-lookup"><span data-stu-id="53cc7-110">The most important options are:</span></span>

- <span data-ttu-id="53cc7-111">谁有权访问 JEA 终结点</span><span class="sxs-lookup"><span data-stu-id="53cc7-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="53cc7-112">他们分配到哪些角色</span><span class="sxs-lookup"><span data-stu-id="53cc7-112">Which roles they be assigned</span></span>
- <span data-ttu-id="53cc7-113">JEA 在后台使用哪个标识</span><span class="sxs-lookup"><span data-stu-id="53cc7-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="53cc7-114">JEA 终结点的名称</span><span class="sxs-lookup"><span data-stu-id="53cc7-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="53cc7-115">这些选项是在 PowerShell 数据文件中定义的，该文件被称为 PowerShell 会话配置文件，扩展名为 `.pssc`。</span><span class="sxs-lookup"><span data-stu-id="53cc7-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="53cc7-116">可使用任意文本编辑器编辑会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="53cc7-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="53cc7-117">请运行以下命令，创建一个空白的模板配置文件。</span><span class="sxs-lookup"><span data-stu-id="53cc7-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="53cc7-118">默认情况下，模板文件仅包含最常用的配置选项。</span><span class="sxs-lookup"><span data-stu-id="53cc7-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="53cc7-119">使用 `-Full` 切换，在生成的 PSSC 中包含所有适用设置。</span><span class="sxs-lookup"><span data-stu-id="53cc7-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="53cc7-120">`-SessionType RestrictedRemoteServer` 字段指示 JEA 使用该会话配置进行安全管理。</span><span class="sxs-lookup"><span data-stu-id="53cc7-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="53cc7-121">此类型的会话在 NoLanguage 模式下运行，且只有权访问以下默认命令（和别名）  ：</span><span class="sxs-lookup"><span data-stu-id="53cc7-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="53cc7-122">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="53cc7-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="53cc7-123">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="53cc7-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="53cc7-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="53cc7-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="53cc7-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="53cc7-125">Get-FormatData</span></span>
- <span data-ttu-id="53cc7-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="53cc7-126">Get-Help</span></span>
- <span data-ttu-id="53cc7-127">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="53cc7-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="53cc7-128">Out-Default</span><span class="sxs-lookup"><span data-stu-id="53cc7-128">Out-Default</span></span>
- <span data-ttu-id="53cc7-129">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="53cc7-129">Select-Object (select)</span></span>

<span data-ttu-id="53cc7-130">PowerShell 提供程序均不可用，也不提供任何外部程序（可执行文件或脚本）。</span><span class="sxs-lookup"><span data-stu-id="53cc7-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="53cc7-131">有关语言模式的详细信息，请参阅 [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)。</span><span class="sxs-lookup"><span data-stu-id="53cc7-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="53cc7-132">选择 JEA 标识</span><span class="sxs-lookup"><span data-stu-id="53cc7-132">Choose the JEA identity</span></span>

<span data-ttu-id="53cc7-133">JEA 在后台运行已连接用户的命令时需要使用标识（即帐户）。</span><span class="sxs-lookup"><span data-stu-id="53cc7-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="53cc7-134">由你定义 JEA 在会话配置文件中使用哪个标识。</span><span class="sxs-lookup"><span data-stu-id="53cc7-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="53cc7-135">本地虚拟帐户</span><span class="sxs-lookup"><span data-stu-id="53cc7-135">Local Virtual Account</span></span>

<span data-ttu-id="53cc7-136">如果为 JEA 终结点定义的所有角色均用于管理本地计算机，并且本地管理员帐户足以成功运行命令，则本地虚拟帐户非常有用。</span><span class="sxs-lookup"><span data-stu-id="53cc7-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="53cc7-137">虚拟帐户是特定用户所独有的临时帐户，仅在 PowerShell 会话的持续时间内有效。</span><span class="sxs-lookup"><span data-stu-id="53cc7-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="53cc7-138">在成员服务器或工作站上，虚拟帐户属于本地计算机的管理员组  。</span><span class="sxs-lookup"><span data-stu-id="53cc7-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="53cc7-139">在 Active Directory 域控制器上，虚拟帐户属于域的**域管理员**组。</span><span class="sxs-lookup"><span data-stu-id="53cc7-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="53cc7-140">如果会话配置定义的角色不需要完全管理权限，则可指定将包含虚拟帐户的安全组。</span><span class="sxs-lookup"><span data-stu-id="53cc7-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="53cc7-141">在成员服务器或工作站上，指定的安全组必须是本地组，而不是来自域的组。</span><span class="sxs-lookup"><span data-stu-id="53cc7-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="53cc7-142">指定一个或多个安全组后，不可将虚拟帐户分配给本地或域管理员组。</span><span class="sxs-lookup"><span data-stu-id="53cc7-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="53cc7-143">虚拟帐户在本地服务器安全策略中被临时授予“作为服务登录”的权限。</span><span class="sxs-lookup"><span data-stu-id="53cc7-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="53cc7-144">如果指定的 VirtualAccountGroups 之一已在策略中被授予此权限，则无法对策略添加和删除单个虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="53cc7-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="53cc7-145">对于会仔细审核域控制器安全策略修订的域控制器这类情形，这可能会十分有用。</span><span class="sxs-lookup"><span data-stu-id="53cc7-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="53cc7-146">这仅在具有 2018 年 11 月或更高版本汇总的 Windows Server 2016 和具有 2019 年 1 月或更高版本汇总的 Windows Server 2019 中可用。</span><span class="sxs-lookup"><span data-stu-id="53cc7-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="53cc7-147">组托管服务帐户</span><span class="sxs-lookup"><span data-stu-id="53cc7-147">Group-managed service account</span></span>

<span data-ttu-id="53cc7-148">组托管服务帐户 (GMSA) 是 JEA 用户需要访问文件共享和 Web 服务等网络资源时适合使用的标识。</span><span class="sxs-lookup"><span data-stu-id="53cc7-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="53cc7-149">GMSA 提供域标识，用于对域内任何计算机上的资源进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="53cc7-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="53cc7-150">GMSA 提供的权限由你正在访问的资源而定。</span><span class="sxs-lookup"><span data-stu-id="53cc7-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="53cc7-151">你不具有任何计算机或服务的管理员权限，除非计算机或服务管理员已向 GMSA 显式授予这些权限。</span><span class="sxs-lookup"><span data-stu-id="53cc7-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="53cc7-152">仅在必要时才应使用 GMSA：</span><span class="sxs-lookup"><span data-stu-id="53cc7-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="53cc7-153">使用 GMSA 时，很难追溯到执行操作的用户。</span><span class="sxs-lookup"><span data-stu-id="53cc7-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="53cc7-154">每位用户都共享相同的运行身份标识。</span><span class="sxs-lookup"><span data-stu-id="53cc7-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="53cc7-155">你必须查看 PowerShell 会话脚本和日志，才能将各用户与其操作关联起来。</span><span class="sxs-lookup"><span data-stu-id="53cc7-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="53cc7-156">GMSA 可访问连接用户无需访问的多个网络资源。</span><span class="sxs-lookup"><span data-stu-id="53cc7-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="53cc7-157">请始终尽力限制 JEA 会话中的有效权限以符合最低特权原则。</span><span class="sxs-lookup"><span data-stu-id="53cc7-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="53cc7-158">组托管服务帐户仅适用于使用 PowerShell 5.1 或更高版本且已加入域的计算机。</span><span class="sxs-lookup"><span data-stu-id="53cc7-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="53cc7-159">要详细了解如何保护 JEA 会话，请参阅[安全注意事项](security-considerations.md)一文。</span><span class="sxs-lookup"><span data-stu-id="53cc7-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="53cc7-160">会话脚本</span><span class="sxs-lookup"><span data-stu-id="53cc7-160">Session transcripts</span></span>

<span data-ttu-id="53cc7-161">建议将 JEA 终结点配置为自动记录用户会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="53cc7-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="53cc7-162">通过 PowerShell 会话脚本，可查看连接用户、向其分配的运行方式标识以及该用户运行的命令。</span><span class="sxs-lookup"><span data-stu-id="53cc7-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="53cc7-163">对于需要了解谁执行了特定系统更改的审核团队，这些信息非常有用。</span><span class="sxs-lookup"><span data-stu-id="53cc7-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="53cc7-164">若要在会话配置文件中配置自动脚本，请提供应存储脚本的文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="53cc7-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="53cc7-165">脚本由本地系统帐户写入到文件夹中，该帐户需要目录的读取和写入权限  。</span><span class="sxs-lookup"><span data-stu-id="53cc7-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="53cc7-166">标准用户应无权访问该文件夹。</span><span class="sxs-lookup"><span data-stu-id="53cc7-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="53cc7-167">请限制有权审核脚本的安全管理员的数量。</span><span class="sxs-lookup"><span data-stu-id="53cc7-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="53cc7-168">用户驱动器</span><span class="sxs-lookup"><span data-stu-id="53cc7-168">User drive</span></span>

<span data-ttu-id="53cc7-169">如果连接用户需要将文件复制到 JEA 终结点或从中复制文件，可在会话配置文件中启用用户驱动器。</span><span class="sxs-lookup"><span data-stu-id="53cc7-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="53cc7-170">用户驱动器是映射到各连接用户的唯一文件夹的 **PSDrive**。</span><span class="sxs-lookup"><span data-stu-id="53cc7-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="53cc7-171">此文件夹允许用户将文件复制到系统或从中复制文件，但不提供访问完整文件系统的权限，也不公开 FileSystem 提供程序。</span><span class="sxs-lookup"><span data-stu-id="53cc7-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="53cc7-172">用户驱动器内容在会话之间持续存在，以便应对网络连接可能中断的情况。</span><span class="sxs-lookup"><span data-stu-id="53cc7-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="53cc7-173">默认情况下，用户驱动器允许每个用户存储最多 50 MB 的数据。</span><span class="sxs-lookup"><span data-stu-id="53cc7-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="53cc7-174">可使用“UserDriveMaximumSize”  字段限制用户能使用的数据量。</span><span class="sxs-lookup"><span data-stu-id="53cc7-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="53cc7-175">如果不想持久保留用户驱动器中的数据，可在系统上配置计划任务，每晚自动清理文件夹。</span><span class="sxs-lookup"><span data-stu-id="53cc7-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="53cc7-176">用户驱动器仅适用于 PowerShell 5.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="53cc7-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="53cc7-177">有关 PSDrive 的详细信息，请参阅[管理 PowerShell 驱动器](/powershell/scripting/samples/managing-windows-powershell-drives)。</span><span class="sxs-lookup"><span data-stu-id="53cc7-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="53cc7-178">角色定义</span><span class="sxs-lookup"><span data-stu-id="53cc7-178">Role definitions</span></span>

<span data-ttu-id="53cc7-179">会话配置文件中的角色定义可定义**用户**到**角色**的映射。</span><span class="sxs-lookup"><span data-stu-id="53cc7-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="53cc7-180">注册时，此字段中包含的所有用户或组都将获得 JEA 终结点的权限。</span><span class="sxs-lookup"><span data-stu-id="53cc7-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="53cc7-181">每个用户或组仅可在哈希表中以键的形式内附一次，但可向其分配多个角色。</span><span class="sxs-lookup"><span data-stu-id="53cc7-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="53cc7-182">角色功能名称应为角色功能文件的名称，但不带 `.psrc` 扩展名。</span><span class="sxs-lookup"><span data-stu-id="53cc7-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="53cc7-183">如果某用户属于角色定义中的多个组，则有权访问每个组的角色。</span><span class="sxs-lookup"><span data-stu-id="53cc7-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="53cc7-184">两个角色向同一个 cmdlet 授予访问权限时，向用户授予最宽松的参数集。</span><span class="sxs-lookup"><span data-stu-id="53cc7-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="53cc7-185">在角色定义字段中指定本地用户或组时，请务必使用计算机名称，而不是 localhost 或通配符  。</span><span class="sxs-lookup"><span data-stu-id="53cc7-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="53cc7-186">可通过检查 `$env:COMPUTERNAME` 变量来查看计算机名称。</span><span class="sxs-lookup"><span data-stu-id="53cc7-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="53cc7-187">角色功能搜索顺序</span><span class="sxs-lookup"><span data-stu-id="53cc7-187">Role capability search order</span></span>

<span data-ttu-id="53cc7-188">如上例所示，角色功能由角色功能文件的基名称进行引用。</span><span class="sxs-lookup"><span data-stu-id="53cc7-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="53cc7-189">文件的基名称是不带扩展名的文件名。</span><span class="sxs-lookup"><span data-stu-id="53cc7-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="53cc7-190">如果多个角色功能适用于具有相同名称的系统，则 PowerShell 使用其隐式搜索顺序选择有效的角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="53cc7-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="53cc7-191">JEA 不提供对名称相同的所有角色功能文件的访问权限  。</span><span class="sxs-lookup"><span data-stu-id="53cc7-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="53cc7-192">JEA 使用 `$env:PSModulePath` 环境变量来确定扫描角色功能文件的路径。</span><span class="sxs-lookup"><span data-stu-id="53cc7-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="53cc7-193">在每个路径中，JEA 查找包含“RoleCapabilities”子文件夹的有效 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="53cc7-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="53cc7-194">与导入模块一样，与具有相同名称的自定义角色功能相比，JEA 更倾向于 Windows 随附的角色功能。</span><span class="sxs-lookup"><span data-stu-id="53cc7-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="53cc7-195">对于所有其他命名冲突，优先级由 Windows 枚举目录中文件的顺序决定。</span><span class="sxs-lookup"><span data-stu-id="53cc7-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="53cc7-196">不保证按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="53cc7-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="53cc7-197">找到的匹配所指定名称的第一个角色功能文件用于连接用户。</span><span class="sxs-lookup"><span data-stu-id="53cc7-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="53cc7-198">由于角色功能搜索顺序具有不确定性，由此强烈建议让角色功能具有唯一的文件名  。</span><span class="sxs-lookup"><span data-stu-id="53cc7-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="53cc7-199">条件访问规则</span><span class="sxs-lookup"><span data-stu-id="53cc7-199">Conditional access rules</span></span>

<span data-ttu-id="53cc7-200">RoleDefinitions 字段中包含的所有用户和组都将自动获得访问 JEA 终结点的权限  。</span><span class="sxs-lookup"><span data-stu-id="53cc7-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="53cc7-201">通过条件访问规则，可优化此访问权限并要求用户隶属于其他不会影响其所拥有角色的安全组。</span><span class="sxs-lookup"><span data-stu-id="53cc7-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="53cc7-202">如果要将 JEA 与即时特权访问管理解决方案、智能卡身份验证或其他多重身份验证解决方案进行集成，此规则十分有用。</span><span class="sxs-lookup"><span data-stu-id="53cc7-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="53cc7-203">条件访问规则在会话配置文件的 RequiredGroups 字段中进行定义。</span><span class="sxs-lookup"><span data-stu-id="53cc7-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="53cc7-204">可在此处提供哈希表（选择性嵌套），利用“And”和“Or”键构造规则。</span><span class="sxs-lookup"><span data-stu-id="53cc7-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="53cc7-205">以下是如何使用此字段的一些示例：</span><span class="sxs-lookup"><span data-stu-id="53cc7-205">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="53cc7-206">条件访问规则仅适用于 PowerShell 5.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="53cc7-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="53cc7-207">其他属性</span><span class="sxs-lookup"><span data-stu-id="53cc7-207">Other properties</span></span>

<span data-ttu-id="53cc7-208">会话配置文件还可执行角色功能文件能实现的所有操作，但无法授予连接用户访问不同命令的权限。</span><span class="sxs-lookup"><span data-stu-id="53cc7-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="53cc7-209">如果想要允许所有用户访问特定的 cmdlet、函数或提供程序，可直接在会话配置文件中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="53cc7-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="53cc7-210">有关会话配置文件中受支持属性的完整列表，请运行 `Get-Help New-PSSessionConfigurationFile -Full`。</span><span class="sxs-lookup"><span data-stu-id="53cc7-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="53cc7-211">测试会话配置文件</span><span class="sxs-lookup"><span data-stu-id="53cc7-211">Testing a session configuration file</span></span>

<span data-ttu-id="53cc7-212">可使用 [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet 测试会话配置。</span><span class="sxs-lookup"><span data-stu-id="53cc7-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="53cc7-213">如果已手动编辑 `.pssc` 文件，则建议测试会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="53cc7-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="53cc7-214">测试可确保语法正确无误。</span><span class="sxs-lookup"><span data-stu-id="53cc7-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="53cc7-215">如果会话配置文件没有通过此测试，则不能在系统上注册该文件。</span><span class="sxs-lookup"><span data-stu-id="53cc7-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="53cc7-216">示例会话配置文件</span><span class="sxs-lookup"><span data-stu-id="53cc7-216">Sample session configuration file</span></span>

<span data-ttu-id="53cc7-217">下面的示例演示了如何创建和验证 JEA 的会话配置。</span><span class="sxs-lookup"><span data-stu-id="53cc7-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="53cc7-218">为了简便和易读，角色定义是在 `$roles` 变量中进行创建和存储的。</span><span class="sxs-lookup"><span data-stu-id="53cc7-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="53cc7-219">但并非必须这样做。</span><span class="sxs-lookup"><span data-stu-id="53cc7-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="53cc7-220">更新会话配置文件</span><span class="sxs-lookup"><span data-stu-id="53cc7-220">Updating session configuration files</span></span>

<span data-ttu-id="53cc7-221">要更改 JEA 会话配置的属性（包括用户到角色的映射），必须进行[注销](register-jea.md#unregistering-jea-configurations)。</span><span class="sxs-lookup"><span data-stu-id="53cc7-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="53cc7-222">然后，使用更新后的会话配置文件[重新注册](register-jea.md) JEA 会话配置。</span><span class="sxs-lookup"><span data-stu-id="53cc7-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="53cc7-223">后续步骤</span><span class="sxs-lookup"><span data-stu-id="53cc7-223">Next steps</span></span>

- [<span data-ttu-id="53cc7-224">注册 JEA 配置</span><span class="sxs-lookup"><span data-stu-id="53cc7-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="53cc7-225">创作 JEA 角色</span><span class="sxs-lookup"><span data-stu-id="53cc7-225">Author JEA roles</span></span>](role-capabilities.md)

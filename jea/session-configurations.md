---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea,powershell,安全性"
title: "JEA 会话配置"
ms.openlocfilehash: c475a90a59d91b074f954cfb656b00142444c052
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="jea-session-configurations"></a><span data-ttu-id="d24ec-103">JEA 会话配置</span><span class="sxs-lookup"><span data-stu-id="d24ec-103">JEA Session Configurations</span></span>

> <span data-ttu-id="d24ec-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d24ec-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d24ec-105">JEA 终结点通过在系统上采用特定方式创建和注册 PowerShell 会话配置文件进行注册。</span><span class="sxs-lookup"><span data-stu-id="d24ec-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="d24ec-106">会话配置确定可使用 JEA 终结点的*人员*及其有权访问的角色。</span><span class="sxs-lookup"><span data-stu-id="d24ec-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="d24ec-107">它们还定义一些全局设置，这些设置应用于 JEA 会话中任何角色的用户。</span><span class="sxs-lookup"><span data-stu-id="d24ec-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="d24ec-108">本主题介绍如何创建 PowerShell 会话配置文件和注册 JEA 终结点。</span><span class="sxs-lookup"><span data-stu-id="d24ec-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="d24ec-109">创建会话配置文件</span><span class="sxs-lookup"><span data-stu-id="d24ec-109">Create a session configuration file</span></span>

<span data-ttu-id="d24ec-110">若要注册 JEA 终结点，需要指定该终结点的配置方式。</span><span class="sxs-lookup"><span data-stu-id="d24ec-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="d24ec-111">此处需考虑很多事项：最重要的是谁应具有访问 JEA 终结点的权限，其将分配有哪些角色，JEA 实际将使用哪个标识，以及 JEA 终结点将采用哪个名称。</span><span class="sxs-lookup"><span data-stu-id="d24ec-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="d24ec-112">这些均可在 PowerShell 会话配置文件中定义，该文件是以 .pssc 扩展名结尾的 PowerShell 数据文件。</span><span class="sxs-lookup"><span data-stu-id="d24ec-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="d24ec-113">若要创建 JEA 终结点的主干会话配置文件，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d24ec-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="d24ec-114">默认情况下，主干文件仅包含最常用的配置选项。</span><span class="sxs-lookup"><span data-stu-id="d24ec-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="d24ec-115">使用 `-Full` 切换，在生成的 PSSC 中包含所有适用设置。</span><span class="sxs-lookup"><span data-stu-id="d24ec-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="d24ec-116">可在任意文本编辑器中打开会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="d24ec-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="d24ec-117">`-SessionType RestrictedRemoteServer` 字段指示 JEA 将使用该会话配置进行安全管理。</span><span class="sxs-lookup"><span data-stu-id="d24ec-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="d24ec-118">通过此方式配置的会话将在 [NoLanguage 模式](https://technet.microsoft.com/library/dn433292.aspx)下运行，并且只包含以下 8 个默认命令（和别名）：</span><span class="sxs-lookup"><span data-stu-id="d24ec-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="d24ec-119">Clear-Host (cls, clear)</span><span class="sxs-lookup"><span data-stu-id="d24ec-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="d24ec-120">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="d24ec-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="d24ec-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="d24ec-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="d24ec-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="d24ec-122">Get-FormatData</span></span>
- <span data-ttu-id="d24ec-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="d24ec-123">Get-Help</span></span>
- <span data-ttu-id="d24ec-124">Measure-Object (measure)</span><span class="sxs-lookup"><span data-stu-id="d24ec-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="d24ec-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="d24ec-125">Out-Default</span></span>
- <span data-ttu-id="d24ec-126">Select-Object (select)</span><span class="sxs-lookup"><span data-stu-id="d24ec-126">Select-Object (select)</span></span>

<span data-ttu-id="d24ec-127">PowerShell 提供程序均不可用，也不提供任何外部程序（可执行文件、脚本等）。</span><span class="sxs-lookup"><span data-stu-id="d24ec-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="d24ec-128">以下是要为 JEA 会话配置的其他几个字段。</span><span class="sxs-lookup"><span data-stu-id="d24ec-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="d24ec-129">均在以下各节中有所介绍。</span><span class="sxs-lookup"><span data-stu-id="d24ec-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="d24ec-130">选择 JEA 标识</span><span class="sxs-lookup"><span data-stu-id="d24ec-130">Choose the JEA identity</span></span>

<span data-ttu-id="d24ec-131">JEA 在后台运行已连接用户的命令时需要使用标识（即帐户）。</span><span class="sxs-lookup"><span data-stu-id="d24ec-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="d24ec-132">用户决定 JEA 将在会话配置文件中使用哪个标识。</span><span class="sxs-lookup"><span data-stu-id="d24ec-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="d24ec-133">本地虚拟帐户</span><span class="sxs-lookup"><span data-stu-id="d24ec-133">Local Virtual Account</span></span>

<span data-ttu-id="d24ec-134">如果此 JEA 终结点支持的角色均用于管理本地计算机，并且本地管理员帐户足以成功运行命令，则应将 JEA 配置为使用本地虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="d24ec-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="d24ec-135">虚拟帐户是特定用户所独有的临时帐户，仅在 PowerShell 会话的持续时间内有效。</span><span class="sxs-lookup"><span data-stu-id="d24ec-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="d24ec-136">在成员服务器或工作站上，虚拟帐户属于本地计算机的**管理员**组，并且有权访问大多数系统资源。</span><span class="sxs-lookup"><span data-stu-id="d24ec-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="d24ec-137">在 Active Directory 域控制器上，虚拟帐户属于域的**域管理员**组。</span><span class="sxs-lookup"><span data-stu-id="d24ec-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="d24ec-138">如果会话配置支持的角色不需要此类广泛特权，可选择性地指定将包含虚拟帐户的安全组。</span><span class="sxs-lookup"><span data-stu-id="d24ec-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="d24ec-139">在成员服务器或工作站上，指定的安全组必须是本地组，而不是来自域的组。</span><span class="sxs-lookup"><span data-stu-id="d24ec-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="d24ec-140">指定一个或多个安全组后，虚拟帐户将不再属于本地或域管理员组。</span><span class="sxs-lookup"><span data-stu-id="d24ec-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="d24ec-141">组托管服务帐户</span><span class="sxs-lookup"><span data-stu-id="d24ec-141">Group Managed Service Account</span></span>


<span data-ttu-id="d24ec-142">对于需要 JEA 用户访问其他计算机或 Web 服务等网络资源的应用场景，组托管服务帐户 (gMSA) 是更适合使用的标识。</span><span class="sxs-lookup"><span data-stu-id="d24ec-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="d24ec-143">gMSA 帐户提供域标识，可用于向域中任何计算机上的资源进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d24ec-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="d24ec-144">gMSA 帐户授予你的权限由你当前访问的资源决定。</span><span class="sxs-lookup"><span data-stu-id="d24ec-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="d24ec-145">你在任何计算机或服务上均不会自动拥有管理员权限，除非计算机/服务已显式授予 gMSA 帐户管理员特权。</span><span class="sxs-lookup"><span data-stu-id="d24ec-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="d24ec-146">仅在由于多个原因需要访问网络资源时才应使用 gMSA 帐户：</span><span class="sxs-lookup"><span data-stu-id="d24ec-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="d24ec-147">使用 gMSA 帐户时，更难跟踪用户的操作，因为每个用户均共享相同的运行方式标识。</span><span class="sxs-lookup"><span data-stu-id="d24ec-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="d24ec-148">你需要参考 PowerShell 会话记录和日志，将用户与其操作进行关联。</span><span class="sxs-lookup"><span data-stu-id="d24ec-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="d24ec-149">gMSA 帐户可访问连接用户无需访问的多个网络资源。</span><span class="sxs-lookup"><span data-stu-id="d24ec-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="d24ec-150">请始终尽力限制 JEA 会话中的有效权限以符合最低特权原则。</span><span class="sxs-lookup"><span data-stu-id="d24ec-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="d24ec-151">组托管服务帐户仅适用于 Windows PowerShell 5.1 或更高版本以及已加入域的计算机。</span><span class="sxs-lookup"><span data-stu-id="d24ec-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="d24ec-152">有关以用户身份运行的详细信息</span><span class="sxs-lookup"><span data-stu-id="d24ec-152">More information about run as users</span></span>

<span data-ttu-id="d24ec-153">若要进一步了解运行方式标识及其如何影响 JEA 会话的安全性，可参阅[安全性注意事项](security-considerations.md)文章。</span><span class="sxs-lookup"><span data-stu-id="d24ec-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="d24ec-154">会话脚本</span><span class="sxs-lookup"><span data-stu-id="d24ec-154">Session transcripts</span></span>

<span data-ttu-id="d24ec-155">建议将 JEA 会话配置文件配置为自动记录用户会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="d24ec-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="d24ec-156">通过 PowerShell 会话脚本，可查看连接用户、向其分配的运行方式标识以及该用户运行的命令。</span><span class="sxs-lookup"><span data-stu-id="d24ec-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="d24ec-157">对于需要了解谁执行了特定系统更改的审核团队，这些信息非常有用。</span><span class="sxs-lookup"><span data-stu-id="d24ec-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="d24ec-158">若要在会话配置文件中配置自动脚本，请提供应存储脚本的文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="d24ec-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="d24ec-159">应将指定的文件夹配置为阻止用户修改或删除其中的任何数据。</span><span class="sxs-lookup"><span data-stu-id="d24ec-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="d24ec-160">脚本由本地系统帐户写入到文件夹中，该帐户需要目录的读取和写入权限。</span><span class="sxs-lookup"><span data-stu-id="d24ec-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="d24ec-161">标准用户不得具有文件夹的访问权限，一组数量有限的安全管理员须具有访问权限来进行脚本审核。</span><span class="sxs-lookup"><span data-stu-id="d24ec-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="d24ec-162">用户驱动器</span><span class="sxs-lookup"><span data-stu-id="d24ec-162">User drive</span></span>

<span data-ttu-id="d24ec-163">如果连接用户需要将文件复制到 JEA 终结点或从中复制文件才可运行命令，可在会话配置文件中启用用户驱动器。</span><span class="sxs-lookup"><span data-stu-id="d24ec-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="d24ec-164">用户驱动器是映射到各连接用户的唯一文件夹的 [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives)。</span><span class="sxs-lookup"><span data-stu-id="d24ec-164">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="d24ec-165">此文件夹充当将文件复制到系统/从中复制文件的空间，但不提供访问完整文件系统或公开 FileSystem 提供程序的权限。</span><span class="sxs-lookup"><span data-stu-id="d24ec-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="d24ec-166">用户驱动器内容在会话之间持续存在，以便应对网络连接可能中断的情况。</span><span class="sxs-lookup"><span data-stu-id="d24ec-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="d24ec-167">默认情况下，用户驱动器允许每个用户存储最多 50 MB 的数据。</span><span class="sxs-lookup"><span data-stu-id="d24ec-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="d24ec-168">可使用“UserDriveMaximumSize”字段限制用户能使用的数据量。</span><span class="sxs-lookup"><span data-stu-id="d24ec-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="d24ec-169">如果不想持久保留用户驱动器中的数据，可在系统上配置计划任务，每晚自动清理文件夹。</span><span class="sxs-lookup"><span data-stu-id="d24ec-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="d24ec-170">用户驱动器仅适用于 Windows PowerShell 5.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="d24ec-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="d24ec-171">角色定义</span><span class="sxs-lookup"><span data-stu-id="d24ec-171">Role definitions</span></span>

<span data-ttu-id="d24ec-172">会话配置文件中的角色定义可定义*用户*到*角色*的映射。</span><span class="sxs-lookup"><span data-stu-id="d24ec-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="d24ec-173">注册时，此字段中包含的所有用户或组都将获得到 JEA 终结点的权限。</span><span class="sxs-lookup"><span data-stu-id="d24ec-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="d24ec-174">每个用户或组仅可在哈希表中以键的形式内附一次，但可向其分配多个角色。</span><span class="sxs-lookup"><span data-stu-id="d24ec-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="d24ec-175">角色功能名称应为角色功能文件的名称，但不带 .psrc 扩展名。</span><span class="sxs-lookup"><span data-stu-id="d24ec-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="d24ec-176">如果某用户属于角色定义中的多个组，则其将获得访问每个组角色的权限。</span><span class="sxs-lookup"><span data-stu-id="d24ec-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="d24ec-177">如果两个角色向同一个 cmdlet 授予访问权限，则将向用户授予最宽松的参数集。</span><span class="sxs-lookup"><span data-stu-id="d24ec-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="d24ec-178">在角色定义字段中指定本地用户或组时，请务必在反斜杠前面添加计算机名称（而不是 *localhost* 或 *.*）。</span><span class="sxs-lookup"><span data-stu-id="d24ec-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="d24ec-179">可通过检查 `$env:computername` 变量来查看计算机名称。</span><span class="sxs-lookup"><span data-stu-id="d24ec-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="d24ec-180">角色功能搜索顺序</span><span class="sxs-lookup"><span data-stu-id="d24ec-180">Role capability search order</span></span>
<span data-ttu-id="d24ec-181">如上例所示，角色功能由角色功能文件的平面名称（不含扩展名的文件名）进行引用。</span><span class="sxs-lookup"><span data-stu-id="d24ec-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="d24ec-182">如果多个角色功能适用于带相同平面名称的系统，PowerShell 将使用隐式搜索顺序选择有效的角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="d24ec-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="d24ec-183">它将**仅**向部分带同一名称的角色功能文件授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="d24ec-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="d24ec-184">JEA 使用 `$env:PSModulePath` 环境变量来确定扫描角色功能文件的路径。</span><span class="sxs-lookup"><span data-stu-id="d24ec-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="d24ec-185">在每个路径中，JEA 将查找包含“RoleCapabilities”子文件夹的有效 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="d24ec-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="d24ec-186">与导入模块一样，与具有相同名称的自定义角色功能相比，JEA 更倾向于 Windows 随附的角色功能。</span><span class="sxs-lookup"><span data-stu-id="d24ec-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="d24ec-187">对于所有其他命名冲突，优先级由 Windows 枚举目录中文件的顺序（不保证按字母顺序排序）决定。</span><span class="sxs-lookup"><span data-stu-id="d24ec-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="d24ec-188">找到的匹配所需名称的第一个角色功能文件将用于连接用户。</span><span class="sxs-lookup"><span data-stu-id="d24ec-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="d24ec-189">当两个或多个角色功能共享同一名称时，角色功能搜索顺序是不确定的，因此**强烈建议**确保角色功能在计算机上具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="d24ec-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="d24ec-190">条件访问规则</span><span class="sxs-lookup"><span data-stu-id="d24ec-190">Conditional access rules</span></span>

<span data-ttu-id="d24ec-191">RoleDefinitions 字段中包含的所有用户和组都将自动获得访问 JEA 终结点的权限。</span><span class="sxs-lookup"><span data-stu-id="d24ec-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="d24ec-192">通过条件访问规则，可优化此访问权限并要求用户隶属于其他不会影响其所拥有角色的安全组。</span><span class="sxs-lookup"><span data-stu-id="d24ec-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="d24ec-193">如果想要将 JEA 与“及时”特权访问管理解决方案、智能卡身份验证或其他多重身份验证解决方案进行集成，则此规则十分有用。</span><span class="sxs-lookup"><span data-stu-id="d24ec-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="d24ec-194">条件访问规则在会话配置文件的 RequiredGroups 字段中进行定义。</span><span class="sxs-lookup"><span data-stu-id="d24ec-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="d24ec-195">可在此处提供哈希表（选择性嵌套），利用“And”和“Or”键构造规则。</span><span class="sxs-lookup"><span data-stu-id="d24ec-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="d24ec-196">以下是如何使用此字段的一些示例：</span><span class="sxs-lookup"><span data-stu-id="d24ec-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="d24ec-197">条件访问规则仅适用于 Windows PowerShell 5.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="d24ec-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="d24ec-198">其他属性</span><span class="sxs-lookup"><span data-stu-id="d24ec-198">Other properties</span></span>
<span data-ttu-id="d24ec-199">会话配置文件还可执行角色功能文件能实现的所有操作，但无法授予连接用户访问不同命令的权限。</span><span class="sxs-lookup"><span data-stu-id="d24ec-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="d24ec-200">如果想要允许所有用户访问特定的 cmdlet、函数或提供程序，可直接在会话配置文件中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d24ec-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="d24ec-201">有关会话配置文件中受支持属性的完整列表，请运行 `Get-Help New-PSSessionConfigurationFile -Full`。</span><span class="sxs-lookup"><span data-stu-id="d24ec-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="d24ec-202">测试会话配置文件</span><span class="sxs-lookup"><span data-stu-id="d24ec-202">Testing a session configuration file</span></span>

<span data-ttu-id="d24ec-203">可使用 [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet 测试会话配置。</span><span class="sxs-lookup"><span data-stu-id="d24ec-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="d24ec-204">如果已使用文本编辑器手动编辑 pssc 文件时，强烈建议测试会话配置文件以确保语法正确。</span><span class="sxs-lookup"><span data-stu-id="d24ec-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="d24ec-205">如果会话配置文件未通过此测试，它将无法在系统上成功注册。</span><span class="sxs-lookup"><span data-stu-id="d24ec-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="d24ec-206">示例会话配置文件</span><span class="sxs-lookup"><span data-stu-id="d24ec-206">Sample session configuration file</span></span>

<span data-ttu-id="d24ec-207">下面的完整示例演示了如何创建和验证 JEA 的会话配置。</span><span class="sxs-lookup"><span data-stu-id="d24ec-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="d24ec-208">请注意，为了简便和易读，在 `$roles` 变量中创建和存储角色定义。</span><span class="sxs-lookup"><span data-stu-id="d24ec-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="d24ec-209">但并非必须这样做。</span><span class="sxs-lookup"><span data-stu-id="d24ec-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="d24ec-210">更新会话配置文件</span><span class="sxs-lookup"><span data-stu-id="d24ec-210">Updating session configuration files</span></span>

<span data-ttu-id="d24ec-211">如果需要更改 JEA 会话配置的属性（包括用户到角色的映射），需要[注销](register-jea.md#unregistering-jea-configurations)和[重新注册](register-jea.md) JEA 会话配置。</span><span class="sxs-lookup"><span data-stu-id="d24ec-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="d24ec-212">重新注册 JEA 会话配置时，使用包含所需更改的更新后的 PowerShell 会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="d24ec-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d24ec-213">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d24ec-213">Next steps</span></span>

- [<span data-ttu-id="d24ec-214">注册 JEA 配置</span><span class="sxs-lookup"><span data-stu-id="d24ec-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="d24ec-215">创作 JEA 角色</span><span class="sxs-lookup"><span data-stu-id="d24ec-215">Author JEA roles</span></span>](role-capabilities.md)


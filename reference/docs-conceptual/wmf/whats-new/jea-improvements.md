---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 对 Just Enough Administration (JEA) 的改进
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147597"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="1c88c-103">对 Just Enough Administration (JEA) 的改进</span><span class="sxs-lookup"><span data-stu-id="1c88c-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="1c88c-104">Just Enough Administration 是 WMF 5.0 中的新功能，可通过 PowerShell 远程处理实现基于角色的管理。</span><span class="sxs-lookup"><span data-stu-id="1c88c-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="1c88c-105">通过允许非管理员以管理员身份运行特定的命令、脚本和可执行文件，它扩展了现有受约束的终结点基础结构。</span><span class="sxs-lookup"><span data-stu-id="1c88c-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="1c88c-106">这使你可以减少环境中的完全权限管理员数量并提高安全性。</span><span class="sxs-lookup"><span data-stu-id="1c88c-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="1c88c-107">指向/来自 JEA 终结点的受约束的文件副本</span><span class="sxs-lookup"><span data-stu-id="1c88c-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="1c88c-108">现可将文件远程复制到 JEA 终结点或远程复制其中的文件，并确信连接用户不能复制你系统上的任意  文件。</span><span class="sxs-lookup"><span data-stu-id="1c88c-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="1c88c-109">这可通过配置 PSSC 文件为连接用户安装用户驱动器来实现。</span><span class="sxs-lookup"><span data-stu-id="1c88c-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="1c88c-110">用户驱动器是新的 PSDrive，是每个连接用户特有的并跨会话保持。</span><span class="sxs-lookup"><span data-stu-id="1c88c-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="1c88c-111">当 `Copy-Item` 用于将文件复制到 JEA 会话或从中复制时，其被限制为仅允许访问用户驱动器。</span><span class="sxs-lookup"><span data-stu-id="1c88c-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="1c88c-112">将文件复制到任何其他 PSDrive 的尝试会失败。</span><span class="sxs-lookup"><span data-stu-id="1c88c-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="1c88c-113">若要在 JEA 会话配置文件中设置用户驱动器，请使用以下新字段：</span><span class="sxs-lookup"><span data-stu-id="1c88c-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="1c88c-114">将在 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER` 处创建支持用户驱动器的文件夹</span><span class="sxs-lookup"><span data-stu-id="1c88c-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="1c88c-115">若要利用用户驱动器，并将文件复制到配置为公开用户驱动器的 JEA 终结点或从中复制文件，请使用 `Copy-Item` 上的 `-ToSession` 和 `-FromSession` 参数。</span><span class="sxs-lookup"><span data-stu-id="1c88c-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="1c88c-116">随后可编写自定义函数以处理用户驱动器中存储的数据，并将其提供“角色功能”文件中的用户。</span><span class="sxs-lookup"><span data-stu-id="1c88c-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="1c88c-117">支持组托管服务帐户</span><span class="sxs-lookup"><span data-stu-id="1c88c-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="1c88c-118">在某些情况下，用户需在 JEA 会话中执行的任务可能需要访问本地计算机以外的资源 。</span><span class="sxs-lookup"><span data-stu-id="1c88c-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="1c88c-119">当 JEA 会话配置为使用虚拟帐户时，任何接触此类资源的尝试都将来自本地计算机的 ID，而非虚拟帐户或已连接用户。</span><span class="sxs-lookup"><span data-stu-id="1c88c-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="1c88c-120">TP5 现已开始支持在[组托管服务帐户](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\))上下文中运行 JEA，从而大大简化了使用域标识来访问网络资源的过程。</span><span class="sxs-lookup"><span data-stu-id="1c88c-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="1c88c-121">若要将 JEA 会话配置为在 gMSA 帐户下运行，请在 PSSC 文件中使用以下新密钥：</span><span class="sxs-lookup"><span data-stu-id="1c88c-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="1c88c-122">组托管服务帐户不会隔离虚拟帐户或限制其范围。</span><span class="sxs-lookup"><span data-stu-id="1c88c-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="1c88c-123">每个连接用户都将共享同一 gMSA 标识，这一标识可能拥有整个企业范围内的权限。</span><span class="sxs-lookup"><span data-stu-id="1c88c-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="1c88c-124">选择使用 gMSA 时请格外小心；若可能，请始终优先使用限于本地计算机的虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="1c88c-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="1c88c-125">条件访问策略</span><span class="sxs-lookup"><span data-stu-id="1c88c-125">Conditional access policies</span></span>

<span data-ttu-id="1c88c-126">JEA 可很好地限制用户在连接到系统进行管理时可执行的操作；但如果你还想限制用户可使用 JEA 的*时间*，该如何操作？</span><span class="sxs-lookup"><span data-stu-id="1c88c-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="1c88c-127">我们已向会话配置文件 (.pssc) 添加了配置选项，使你能够指定用户为建立 JEA 会话而必须归属的安全组。</span><span class="sxs-lookup"><span data-stu-id="1c88c-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="1c88c-128">如果你的环境中有实时 (JIT) 系统且希望你的用户在访问高权限 JEA 终结点前提升其权限，那么这将特别有用。</span><span class="sxs-lookup"><span data-stu-id="1c88c-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="1c88c-129">通过 PSSC 文件中的新 *RequiredGroups* 字段，你可指定用于确定用户是否可连接到 JEA 的逻辑。</span><span class="sxs-lookup"><span data-stu-id="1c88c-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="1c88c-130">它包括指定使用“And”和“Or”密钥来构造规则的哈希表（可选择嵌套）。</span><span class="sxs-lookup"><span data-stu-id="1c88c-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="1c88c-131">以下是如何使用此字段的一些示例：</span><span class="sxs-lookup"><span data-stu-id="1c88c-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="1c88c-132">已修复：Windows Server 2008 R2 现支持虚拟帐户</span><span class="sxs-lookup"><span data-stu-id="1c88c-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="1c88c-133">在 WMF 5.1 中，现可在 Windows Server 2008 R2 上使用虚拟帐户，从而跨 Windows Server 2008 R2 - 2016 实现一致的配置和功能。</span><span class="sxs-lookup"><span data-stu-id="1c88c-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="1c88c-134">在 Windows 7 上使用 JEA 时，虚拟帐户仍不受支持。</span><span class="sxs-lookup"><span data-stu-id="1c88c-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>
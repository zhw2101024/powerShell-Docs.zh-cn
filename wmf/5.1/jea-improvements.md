---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
contributor: ryanpu
title: "对 Just Enough Administration (JEA) 的改进"
ms.openlocfilehash: 2811b4deb3f4fca513791c7389ee5f9f877dbfe8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="54291-103">对 Just Enough Administration (JEA) 的改进</span><span class="sxs-lookup"><span data-stu-id="54291-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="54291-104">指向/来自 JEA 终结点的受约束的文件副本</span><span class="sxs-lookup"><span data-stu-id="54291-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="54291-105">现可将文件远程复制到 JEA 终结点或远程复制其中的文件，并确信连接用户不能复制你系统上的*任意*文件。</span><span class="sxs-lookup"><span data-stu-id="54291-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="54291-106">这可通过配置 PSSC 文件为连接用户安装用户驱动器来实现。</span><span class="sxs-lookup"><span data-stu-id="54291-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="54291-107">用户驱动器是新的 PSDrive，是每个连接用户特有的并跨会话保持。</span><span class="sxs-lookup"><span data-stu-id="54291-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="54291-108">当复制项用于将文件复制到 JEA 会话或从中复制时，其被限制为仅允许访问用户驱动器。</span><span class="sxs-lookup"><span data-stu-id="54291-108">When Copy-Item is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="54291-109">将文件复制到任何其他 PSDrive 的尝试会失败。</span><span class="sxs-lookup"><span data-stu-id="54291-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="54291-110">若要在 JEA 会话配置文件中设置用户驱动器，请使用以下新字段：</span><span class="sxs-lookup"><span data-stu-id="54291-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="54291-111">将在 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER` 处创建支持用户驱动器的文件夹</span><span class="sxs-lookup"><span data-stu-id="54291-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="54291-112">若要利用用户驱动器，并将文件复制到配置为公开用户驱动器的 JEA 终结点或从中复制文件，请使用复制项上的 `-ToSession` 和 `-FromSession` 参数。</span><span class="sxs-lookup"><span data-stu-id="54291-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on Copy-Item.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="54291-113">随后可编写自定义函数以处理用户驱动器中存储的数据，并将其提供“角色功能”文件中的用户。</span><span class="sxs-lookup"><span data-stu-id="54291-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="54291-114">支持组托管服务帐户</span><span class="sxs-lookup"><span data-stu-id="54291-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="54291-115">在某些情况下，用户需在 JEA 会话中执行的任务可能需要访问本地计算机以外的资源 。</span><span class="sxs-lookup"><span data-stu-id="54291-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="54291-116">当 JEA 会话配置为使用虚拟帐户时，任何接触此类资源的尝试都将来自本地计算机的 ID，而非虚拟帐户或已连接用户。</span><span class="sxs-lookup"><span data-stu-id="54291-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="54291-117">在 TP5 中，我们启用了对在 [组托管服务帐户](https://technet.microsoft.com/zh-cn/library/jj128431(v=ws.11\).aspx) 的上下文中运行 JEA 的支持，从而大幅简化了使用域标识来访问网络资源的操作。</span><span class="sxs-lookup"><span data-stu-id="54291-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="54291-118">若要将 JEA 会话配置为在 gMSA 帐户下运行，请在 PSSC 文件中使用以下新密钥：</span><span class="sxs-lookup"><span data-stu-id="54291-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> <span data-ttu-id="54291-119">**注意：**组托管服务帐户不会隔离虚拟帐户或限制其范围。</span><span class="sxs-lookup"><span data-stu-id="54291-119">**Note:** Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="54291-120">每个连接用户都将共享同一 gMSA 标识，这一标识可能拥有整个企业范围内的权限。</span><span class="sxs-lookup"><span data-stu-id="54291-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="54291-121">选择使用 gMSA 时请格外小心；若可能，请始终优先使用限于本地计算机的虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="54291-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="54291-122">条件访问策略</span><span class="sxs-lookup"><span data-stu-id="54291-122">Conditional access policies</span></span>

<span data-ttu-id="54291-123">JEA 可很好地限制用户在连接到系统进行管理时可执行的操作；但如果你还想限制用户可使用 JEA 的*时间*，该如何操作？</span><span class="sxs-lookup"><span data-stu-id="54291-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="54291-124">我们已向会话配置文件 (.pssc) 添加了配置选项，使你能够指定用户为建立 JEA 会话而必须归属的安全组。</span><span class="sxs-lookup"><span data-stu-id="54291-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="54291-125">如果你的环境中有实时 (JIT) 系统且希望你的用户在访问高权限 JEA 终结点前提升其权限，那么这将非常有用。</span><span class="sxs-lookup"><span data-stu-id="54291-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="54291-126">通过 PSSC 文件中的新 *RequiredGroups* 字段，你可指定用于确定用户是否可连接到 JEA 的逻辑。</span><span class="sxs-lookup"><span data-stu-id="54291-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="54291-127">它包括指定使用“And”和“Or”密钥来构造规则的哈希表（可选择嵌套）。</span><span class="sxs-lookup"><span data-stu-id="54291-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="54291-128">以下是如何使用此字段的一些示例：</span><span class="sxs-lookup"><span data-stu-id="54291-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="54291-129">已修复：Windows Server 2008 R2 现支持虚拟帐户</span><span class="sxs-lookup"><span data-stu-id="54291-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>
<span data-ttu-id="54291-130">在 WMF 5.1 中，现可在 Windows Server 2008 R2 上使用虚拟帐户，从而跨 Windows Server 2008 R2 - 2016 实现一致的配置和功能。</span><span class="sxs-lookup"><span data-stu-id="54291-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="54291-131">在 Windows 7 上使用 JEA 时，虚拟帐户仍不受支持。</span><span class="sxs-lookup"><span data-stu-id="54291-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>


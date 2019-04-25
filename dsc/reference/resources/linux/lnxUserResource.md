---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxUser 资源
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077647"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="58152-103">适用于 Linux 的 DSC nxUser 资源</span><span class="sxs-lookup"><span data-stu-id="58152-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="58152-104">PowerShell Desired State Configuration (DSC) 中的 nxUser 资源提供了在 Linux 节点上管理本地用户的机制。</span><span class="sxs-lookup"><span data-stu-id="58152-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="58152-105">语法</span><span class="sxs-lookup"><span data-stu-id="58152-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="58152-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="58152-106">Properties</span></span>

|  <span data-ttu-id="58152-107">属性</span><span class="sxs-lookup"><span data-stu-id="58152-107">Property</span></span> |  <span data-ttu-id="58152-108">指示要确保其特定状态的帐户名。</span><span class="sxs-lookup"><span data-stu-id="58152-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="58152-109">UserName</span><span class="sxs-lookup"><span data-stu-id="58152-109">UserName</span></span>| <span data-ttu-id="58152-110">指定你想确保其中文件或目录状态的位置。</span><span class="sxs-lookup"><span data-stu-id="58152-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="58152-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="58152-111">Ensure</span></span>| <span data-ttu-id="58152-112">指定帐户是否存在。</span><span class="sxs-lookup"><span data-stu-id="58152-112">Specifies whether the account exists.</span></span> <span data-ttu-id="58152-113">将此属性设置为“Present”以确保该帐户存在，将其设置为“Absent”以确保该帐户不存在。</span><span class="sxs-lookup"><span data-stu-id="58152-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="58152-114">FullName</span><span class="sxs-lookup"><span data-stu-id="58152-114">FullName</span></span>| <span data-ttu-id="58152-115">包含用于用户帐户的完整名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="58152-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="58152-116">说明</span><span class="sxs-lookup"><span data-stu-id="58152-116">Description</span></span>| <span data-ttu-id="58152-117">用户帐户的说明。</span><span class="sxs-lookup"><span data-stu-id="58152-117">The description for the user account.</span></span>|
| <span data-ttu-id="58152-118">密码</span><span class="sxs-lookup"><span data-stu-id="58152-118">Password</span></span>| <span data-ttu-id="58152-119">适用于 Linux 计算机的形式的用户密码哈希。</span><span class="sxs-lookup"><span data-stu-id="58152-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="58152-120">通常情况下，这是加盐的 SHA-256 或 SHA-512 哈希。</span><span class="sxs-lookup"><span data-stu-id="58152-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="58152-121">在 Debian 和 Ubuntu Linux 上，可以使用 mkpasswd 命令生成此值。</span><span class="sxs-lookup"><span data-stu-id="58152-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="58152-122">对于其他 Linux 发行版本，可以使用 Python 加密库的加密方法生成此哈希。</span><span class="sxs-lookup"><span data-stu-id="58152-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="58152-123">禁用</span><span class="sxs-lookup"><span data-stu-id="58152-123">Disabled</span></span>| <span data-ttu-id="58152-124">指示帐户是否已启用。</span><span class="sxs-lookup"><span data-stu-id="58152-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="58152-125">将此属性设置为 **$true** 以确已禁用保此帐户，将其设置为 **$false** 以确保已启用此帐户。</span><span class="sxs-lookup"><span data-stu-id="58152-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="58152-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="58152-126">PasswordChangeRequired</span></span>| <span data-ttu-id="58152-127">指示用户是否可以更改密码。</span><span class="sxs-lookup"><span data-stu-id="58152-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="58152-128">将此属性设置为 **$true** 以确保用户无法更改密码，将其设置为 **$false** 以允许用户更改密码。</span><span class="sxs-lookup"><span data-stu-id="58152-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="58152-129">默认值为 **$false**。</span><span class="sxs-lookup"><span data-stu-id="58152-129">The default value is **$false**.</span></span> <span data-ttu-id="58152-130">仅当创建以前不存在的用户帐户时，才会计算此属性。</span><span class="sxs-lookup"><span data-stu-id="58152-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="58152-131">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="58152-131">HomeDirectory</span></span>| <span data-ttu-id="58152-132">用户的主目录</span><span class="sxs-lookup"><span data-stu-id="58152-132">The home directory for the user.</span></span>|
| <span data-ttu-id="58152-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="58152-133">GroupID</span></span>| <span data-ttu-id="58152-134">用户的主要组 ID</span><span class="sxs-lookup"><span data-stu-id="58152-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="58152-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="58152-135">DependsOn</span></span> | <span data-ttu-id="58152-136">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="58152-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="58152-137">例如，如果你想要首先运行 ID 为“ResourceName”、类型为“ResourceType”的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="58152-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="58152-138">示例</span><span class="sxs-lookup"><span data-stu-id="58152-138">Example</span></span>

<span data-ttu-id="58152-139">以下示例可确保用户“monuser”存在且为组“DBusers”的成员。</span><span class="sxs-lookup"><span data-stu-id="58152-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```
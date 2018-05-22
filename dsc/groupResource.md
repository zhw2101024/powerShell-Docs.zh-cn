---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Group 资源
ms.openlocfilehash: 68e0840eaeb116b92260ca697acd5796460a2909
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-group-resource"></a><span data-ttu-id="42622-103">DSC Group 资源</span><span class="sxs-lookup"><span data-stu-id="42622-103">DSC Group Resource</span></span>

> <span data-ttu-id="42622-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="42622-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="42622-105">Windows PowerShell Desired State Configuration (DSC) 中的 Group 资源提供了管理目标节点上的本地组的机制。</span><span class="sxs-lookup"><span data-stu-id="42622-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="42622-106">语法</span><span class="sxs-lookup"><span data-stu-id="42622-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="42622-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="42622-107">Properties</span></span>

|  <span data-ttu-id="42622-108">属性</span><span class="sxs-lookup"><span data-stu-id="42622-108">Property</span></span>  |  <span data-ttu-id="42622-109">说明</span><span class="sxs-lookup"><span data-stu-id="42622-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="42622-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="42622-110">GroupName</span></span>| <span data-ttu-id="42622-111">要确保其处于特定状态的组的名称。</span><span class="sxs-lookup"><span data-stu-id="42622-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="42622-112">凭据</span><span class="sxs-lookup"><span data-stu-id="42622-112">Credential</span></span>| <span data-ttu-id="42622-113">访问远程资源所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="42622-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="42622-114">**注意**：此帐户必须拥有相应的 Active Directory 权限，才能将所有非本地帐户添加到组中；否则，在目标节点上执行配置时会生成错误。</span><span class="sxs-lookup"><span data-stu-id="42622-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="42622-115">说明</span><span class="sxs-lookup"><span data-stu-id="42622-115">Description</span></span>| <span data-ttu-id="42622-116">组的说明。</span><span class="sxs-lookup"><span data-stu-id="42622-116">The description of the group.</span></span>|
| <span data-ttu-id="42622-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="42622-117">Ensure</span></span>| <span data-ttu-id="42622-118">指示该组是否存在。</span><span class="sxs-lookup"><span data-stu-id="42622-118">Indicates if the group exists.</span></span> <span data-ttu-id="42622-119">将其属性设置为“Absent”可确保组不存在。</span><span class="sxs-lookup"><span data-stu-id="42622-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="42622-120">将其设置为"Present"（默认值）可确保组存在。</span><span class="sxs-lookup"><span data-stu-id="42622-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="42622-121">成员</span><span class="sxs-lookup"><span data-stu-id="42622-121">Members</span></span>| <span data-ttu-id="42622-122">使用此属性将当前的组成员身份替换为指定成员。</span><span class="sxs-lookup"><span data-stu-id="42622-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="42622-123">此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。</span><span class="sxs-lookup"><span data-stu-id="42622-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="42622-124">如果你在配置中设置此属性，请勿使用 **MembersToExclude** 或 **MembersToInclude** 属性。</span><span class="sxs-lookup"><span data-stu-id="42622-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="42622-125">这样会生成错误。</span><span class="sxs-lookup"><span data-stu-id="42622-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="42622-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="42622-126">MembersToExclude</span></span>| <span data-ttu-id="42622-127">使用此属性从现有的组成员身份中删除成员。</span><span class="sxs-lookup"><span data-stu-id="42622-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="42622-128">此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。</span><span class="sxs-lookup"><span data-stu-id="42622-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="42622-129">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="42622-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="42622-130">这样会生成错误。</span><span class="sxs-lookup"><span data-stu-id="42622-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="42622-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="42622-131">MembersToInclude</span></span>| <span data-ttu-id="42622-132">使用此属性将成员添加到组的现有成员资格中。</span><span class="sxs-lookup"><span data-stu-id="42622-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="42622-133">此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。</span><span class="sxs-lookup"><span data-stu-id="42622-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="42622-134">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="42622-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="42622-135">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="42622-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="42622-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="42622-136">DependsOn</span></span> | <span data-ttu-id="42622-137">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="42622-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="42622-138">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 \`DependsOn = "[ResourceType]ResourceName"\`\`。</span><span class="sxs-lookup"><span data-stu-id="42622-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="42622-139">示例 1</span><span class="sxs-lookup"><span data-stu-id="42622-139">Example 1</span></span>

<span data-ttu-id="42622-140">下面的示例展示了如何确保名为“TestGroup”的组不存在。</span><span class="sxs-lookup"><span data-stu-id="42622-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="42622-141">示例 2</span><span class="sxs-lookup"><span data-stu-id="42622-141">Example 2</span></span>

<span data-ttu-id="42622-142">以下示例演示如何将 Active Directory 用户添加到属于多计算机实验室版本（已在其中对本地管理员帐户使用 PSCredential）的本地管理员组。</span><span class="sxs-lookup"><span data-stu-id="42622-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="42622-143">由于这也适用于域管理员帐户（在域提升后），因此需要将这个现有 PSCredential 转换为域友好凭据。</span><span class="sxs-lookup"><span data-stu-id="42622-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="42622-144">然后，便可以将域用户添加到成员服务器上的本地管理员组。</span><span class="sxs-lookup"><span data-stu-id="42622-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="42622-145">示例 3</span><span class="sxs-lookup"><span data-stu-id="42622-145">Example 3</span></span>

<span data-ttu-id="42622-146">下面的示例展示了如何确保服务器 TigerTeamSource.Contoso.Com 上的本地组 TigerTeamAdmins 不包含特定域帐户 Contoso\JerryG。</span><span class="sxs-lookup"><span data-stu-id="42622-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```
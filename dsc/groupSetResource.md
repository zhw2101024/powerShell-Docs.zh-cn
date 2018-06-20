---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
description: 提供了管理目标节点上的本地组的机制。
title: DSC GroupSet 资源
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222347"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="e4c93-104">DSC GroupSet 资源</span><span class="sxs-lookup"><span data-stu-id="e4c93-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="e4c93-105">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4c93-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="e4c93-106">Windows PowerShell Desired State Configuration (DSC) 中的 **GroupSet** 资源提供了管理目标节点上的本地组的机制。</span><span class="sxs-lookup"><span data-stu-id="e4c93-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="e4c93-107">此资源是[复合资源](authoringResourceComposite.md)，它会针对 `GroupName` 参数中指定的每个组调用 [Group 资源](groupResource.md)。</span><span class="sxs-lookup"><span data-stu-id="e4c93-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="e4c93-108">当你要对多个组添加和/或删除相同成员列表、删除多个组或添加具有相同成员列表的多个组时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="e4c93-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="e4c93-109">语法##</span><span class="sxs-lookup"><span data-stu-id="e4c93-109">Syntax##</span></span>
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="e4c93-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="e4c93-110">Properties</span></span>

|  <span data-ttu-id="e4c93-111">属性</span><span class="sxs-lookup"><span data-stu-id="e4c93-111">Property</span></span>  |  <span data-ttu-id="e4c93-112">说明</span><span class="sxs-lookup"><span data-stu-id="e4c93-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="e4c93-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="e4c93-113">GroupName</span></span>| <span data-ttu-id="e4c93-114">要确保其处于特定状态的组的名称。</span><span class="sxs-lookup"><span data-stu-id="e4c93-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="e4c93-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="e4c93-115">MembersToExclude</span></span>| <span data-ttu-id="e4c93-116">使用此属性从现有的组成员身份中删除成员。</span><span class="sxs-lookup"><span data-stu-id="e4c93-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="e4c93-117">此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。</span><span class="sxs-lookup"><span data-stu-id="e4c93-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e4c93-118">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="e4c93-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e4c93-119">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="e4c93-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="e4c93-120">凭据</span><span class="sxs-lookup"><span data-stu-id="e4c93-120">Credential</span></span>| <span data-ttu-id="e4c93-121">访问远程资源所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="e4c93-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="e4c93-122">**注意**：此帐户必须具有相应的 Active Directory 权限才能将所有非将本地帐户添加到组中；否则，将发生错误。</span><span class="sxs-lookup"><span data-stu-id="e4c93-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="e4c93-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="e4c93-123">Ensure</span></span>| <span data-ttu-id="e4c93-124">指示组是否存在。</span><span class="sxs-lookup"><span data-stu-id="e4c93-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="e4c93-125">将此属性设置为“Absent”可确保组不存在。</span><span class="sxs-lookup"><span data-stu-id="e4c93-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="e4c93-126">将它设置为“Present”（默认值）可确保组存在。</span><span class="sxs-lookup"><span data-stu-id="e4c93-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="e4c93-127">成员</span><span class="sxs-lookup"><span data-stu-id="e4c93-127">Members</span></span>| <span data-ttu-id="e4c93-128">使用此属性将当前的组成员身份替换为指定成员。</span><span class="sxs-lookup"><span data-stu-id="e4c93-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="e4c93-129">此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。</span><span class="sxs-lookup"><span data-stu-id="e4c93-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e4c93-130">如果你在配置中设置此属性，请勿使用 **MembersToExclude** 或 **MembersToInclude** 属性。</span><span class="sxs-lookup"><span data-stu-id="e4c93-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="e4c93-131">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="e4c93-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="e4c93-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="e4c93-132">MembersToInclude</span></span>| <span data-ttu-id="e4c93-133">使用此属性将成员添加到组的现有成员资格中。</span><span class="sxs-lookup"><span data-stu-id="e4c93-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="e4c93-134">此属性的值是一组形式为 *Domain*\\*UserName* 的字符串。</span><span class="sxs-lookup"><span data-stu-id="e4c93-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e4c93-135">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="e4c93-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e4c93-136">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="e4c93-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="e4c93-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e4c93-137">DependsOn</span></span> | <span data-ttu-id="e4c93-138">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="e4c93-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e4c93-139">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 \`DependsOn = "[ResourceType]ResourceName"\`\`。</span><span class="sxs-lookup"><span data-stu-id="e4c93-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="e4c93-140">示例 1</span><span class="sxs-lookup"><span data-stu-id="e4c93-140">Example 1</span></span>

<span data-ttu-id="e4c93-141">下面的示例演示如何确保名为“myGroup”和“myOtherGroup”的两个组存在。</span><span class="sxs-lookup"><span data-stu-id="e4c93-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

><span data-ttu-id="e4c93-142">**注意：** 为简单起见，此示例使用纯文本凭据。</span><span class="sxs-lookup"><span data-stu-id="e4c93-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="e4c93-143">有关如何在配置 MOF 文件中加密凭据的信息，请参阅[保护 MOF 文件](secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="e4c93-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>
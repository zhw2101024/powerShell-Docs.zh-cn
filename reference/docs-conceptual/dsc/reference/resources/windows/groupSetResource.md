---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
description: 提供了管理目标节点上的本地组的机制。
title: DSC GroupSet 资源
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953174"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="26656-104">DSC GroupSet 资源</span><span class="sxs-lookup"><span data-stu-id="26656-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="26656-105">适用于：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="26656-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="26656-106">Windows PowerShell Desired State Configuration (DSC) 中的 **GroupSet** 资源提供了管理目标节点上的本地组的机制。</span><span class="sxs-lookup"><span data-stu-id="26656-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="26656-107">此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 `GroupName` 参数中指定的每个组调用 [Group 资源](groupResource.md)。</span><span class="sxs-lookup"><span data-stu-id="26656-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="26656-108">当你要对多个组添加和/或删除相同成员列表、删除多个组或添加具有相同成员列表的多个组时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="26656-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="26656-109">语法</span><span class="sxs-lookup"><span data-stu-id="26656-109">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="26656-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="26656-110">Properties</span></span>

|<span data-ttu-id="26656-111">属性</span><span class="sxs-lookup"><span data-stu-id="26656-111">Property</span></span> |<span data-ttu-id="26656-112">说明</span><span class="sxs-lookup"><span data-stu-id="26656-112">Description</span></span> |
|---|---|
|<span data-ttu-id="26656-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="26656-113">GroupName</span></span> |<span data-ttu-id="26656-114">要确保其处于特定状态的组的名称。</span><span class="sxs-lookup"><span data-stu-id="26656-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="26656-115">成员</span><span class="sxs-lookup"><span data-stu-id="26656-115">Members</span></span> |<span data-ttu-id="26656-116">使用此属性将当前的组成员身份替换为指定成员。</span><span class="sxs-lookup"><span data-stu-id="26656-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="26656-117">此属性的值是一组形式为 `Domain\UserName` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="26656-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="26656-118">如果你在配置中设置此属性，请勿使用 **MembersToExclude** 或 **MembersToInclude** 属性。</span><span class="sxs-lookup"><span data-stu-id="26656-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="26656-119">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="26656-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="26656-120">说明</span><span class="sxs-lookup"><span data-stu-id="26656-120">Description</span></span> |<span data-ttu-id="26656-121">组的说明。</span><span class="sxs-lookup"><span data-stu-id="26656-121">The description of the group.</span></span> |
|<span data-ttu-id="26656-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="26656-122">MembersToInclude</span></span> |<span data-ttu-id="26656-123">使用此属性将成员添加到组的现有成员资格中。</span><span class="sxs-lookup"><span data-stu-id="26656-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="26656-124">此属性的值是一组形式为 `Domain\UserName` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="26656-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="26656-125">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="26656-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="26656-126">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="26656-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="26656-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="26656-127">MembersToExclude</span></span> |<span data-ttu-id="26656-128">使用此属性从现有的组成员身份中删除成员。</span><span class="sxs-lookup"><span data-stu-id="26656-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="26656-129">此属性的值是一组形式为 `Domain\UserName` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="26656-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="26656-130">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="26656-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="26656-131">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="26656-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="26656-132">凭据</span><span class="sxs-lookup"><span data-stu-id="26656-132">Credential</span></span> |<span data-ttu-id="26656-133">访问远程资源所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="26656-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="26656-134">此帐户必须具有相应的 Active Directory 权限才能将所有非将本地帐户添加到组中；否则，将发生错误。</span><span class="sxs-lookup"><span data-stu-id="26656-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="26656-135">公共属性</span><span class="sxs-lookup"><span data-stu-id="26656-135">Common properties</span></span>

|<span data-ttu-id="26656-136">属性</span><span class="sxs-lookup"><span data-stu-id="26656-136">Property</span></span> |<span data-ttu-id="26656-137">说明</span><span class="sxs-lookup"><span data-stu-id="26656-137">Description</span></span> |
|---|---|
|<span data-ttu-id="26656-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="26656-138">DependsOn</span></span> |<span data-ttu-id="26656-139">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="26656-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="26656-140">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="26656-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="26656-141">Ensure</span><span class="sxs-lookup"><span data-stu-id="26656-141">Ensure</span></span> |<span data-ttu-id="26656-142">指示组是否存在。</span><span class="sxs-lookup"><span data-stu-id="26656-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="26656-143">将此属性设置为 **Absent** 可确保组不存在。</span><span class="sxs-lookup"><span data-stu-id="26656-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="26656-144">将其设置为 **Present** 可确保组存在。</span><span class="sxs-lookup"><span data-stu-id="26656-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="26656-145">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="26656-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="26656-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="26656-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="26656-147">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="26656-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="26656-148">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="26656-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="26656-149">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="26656-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="26656-150">示例 1：确保组存在</span><span class="sxs-lookup"><span data-stu-id="26656-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="26656-151">下面的示例演示如何确保名为“myGroup”和“myOtherGroup”的两个组存在。</span><span class="sxs-lookup"><span data-stu-id="26656-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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

> [!NOTE]
> <span data-ttu-id="26656-152">为简单起见，此示例使用纯文本凭据。</span><span class="sxs-lookup"><span data-stu-id="26656-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="26656-153">有关如何在配置 MOF 文件中加密凭据的信息，请参阅[保护 MOF 文件](../../../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="26656-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
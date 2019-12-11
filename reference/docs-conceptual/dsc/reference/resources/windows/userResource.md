---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC User 资源
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953004"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="c5339-103">DSC User 资源</span><span class="sxs-lookup"><span data-stu-id="c5339-103">DSC User Resource</span></span>

> <span data-ttu-id="c5339-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c5339-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="c5339-105">Windows PowerShell Desired State Configuration (DSC) 中的 **User** 资源提供在目标节点上管理用户帐户的机制。</span><span class="sxs-lookup"><span data-stu-id="c5339-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5339-106">语法</span><span class="sxs-lookup"><span data-stu-id="c5339-106">Syntax</span></span>

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c5339-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="c5339-107">Properties</span></span>

|<span data-ttu-id="c5339-108">属性</span><span class="sxs-lookup"><span data-stu-id="c5339-108">Property</span></span> |<span data-ttu-id="c5339-109">说明</span><span class="sxs-lookup"><span data-stu-id="c5339-109">Description</span></span> |
|---|---|
|<span data-ttu-id="c5339-110">UserName</span><span class="sxs-lookup"><span data-stu-id="c5339-110">UserName</span></span> |<span data-ttu-id="c5339-111">指示要确保其特定状态的帐户名。</span><span class="sxs-lookup"><span data-stu-id="c5339-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="c5339-112">说明</span><span class="sxs-lookup"><span data-stu-id="c5339-112">Description</span></span> |<span data-ttu-id="c5339-113">指示要用于用户帐户的说明。</span><span class="sxs-lookup"><span data-stu-id="c5339-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="c5339-114">禁用</span><span class="sxs-lookup"><span data-stu-id="c5339-114">Disabled</span></span> |<span data-ttu-id="c5339-115">指示帐户是否已启用。</span><span class="sxs-lookup"><span data-stu-id="c5339-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="c5339-116">将此属性设置为 `$true` 可确保已禁用保此帐户，将其设置为 `$false` 可确保已启用此帐户。</span><span class="sxs-lookup"><span data-stu-id="c5339-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="c5339-117">FullName</span><span class="sxs-lookup"><span data-stu-id="c5339-117">FullName</span></span> |<span data-ttu-id="c5339-118">表示包含要用于用户帐户的完整名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="c5339-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="c5339-119">密码</span><span class="sxs-lookup"><span data-stu-id="c5339-119">Password</span></span> |<span data-ttu-id="c5339-120">指示要用于此帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="c5339-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="c5339-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="c5339-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="c5339-122">指示用户是否可以更改密码。</span><span class="sxs-lookup"><span data-stu-id="c5339-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="c5339-123">将此属性设置为 `$true` 可确保用户无法更改密码，将其设置为 `$false` 可允许用户更改密码。</span><span class="sxs-lookup"><span data-stu-id="c5339-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="c5339-124">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="c5339-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="c5339-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="c5339-125">PasswordChangeRequired</span></span> |<span data-ttu-id="c5339-126">指定用户下次登录时是否必须更改密码。</span><span class="sxs-lookup"><span data-stu-id="c5339-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="c5339-127">要使用户必须更改密码，请将此属性设置为 `$true`。</span><span class="sxs-lookup"><span data-stu-id="c5339-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="c5339-128">默认值为 `$true`。</span><span class="sxs-lookup"><span data-stu-id="c5339-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="c5339-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="c5339-129">PasswordNeverExpires</span></span> |<span data-ttu-id="c5339-130">指示密码是否会过期。</span><span class="sxs-lookup"><span data-stu-id="c5339-130">Indicates if the password will expire.</span></span> <span data-ttu-id="c5339-131">若要确保此帐户的密码永不过期，请将此属性设置为 `$true`。</span><span class="sxs-lookup"><span data-stu-id="c5339-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="c5339-132">如果密码将过期，请将其设置为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="c5339-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="c5339-133">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="c5339-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c5339-134">公共属性</span><span class="sxs-lookup"><span data-stu-id="c5339-134">Common properties</span></span>

|<span data-ttu-id="c5339-135">属性</span><span class="sxs-lookup"><span data-stu-id="c5339-135">Property</span></span> |<span data-ttu-id="c5339-136">说明</span><span class="sxs-lookup"><span data-stu-id="c5339-136">Description</span></span> |
|---|---|
|<span data-ttu-id="c5339-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c5339-137">DependsOn</span></span> |<span data-ttu-id="c5339-138">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="c5339-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c5339-139">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="c5339-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c5339-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="c5339-140">Ensure</span></span> |<span data-ttu-id="c5339-141">指示帐户是否存在。</span><span class="sxs-lookup"><span data-stu-id="c5339-141">Indicates if the account exists.</span></span> <span data-ttu-id="c5339-142">将此属性设置为 **Present** 可确保帐户存在，将其设置为 **Absent** 可确保帐户不存在。</span><span class="sxs-lookup"><span data-stu-id="c5339-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="c5339-143">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="c5339-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="c5339-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c5339-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="c5339-145">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="c5339-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c5339-146">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="c5339-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c5339-147">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="c5339-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="c5339-148">示例</span><span class="sxs-lookup"><span data-stu-id="c5339-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```
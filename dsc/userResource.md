---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC User 资源
ms.openlocfilehash: f2660933aec43967e3f4082a983ef328a5b93851
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189646"
---
#<a name="dsc-user-resource"></a><span data-ttu-id="6427d-103">DSC 用户资源#</span><span class="sxs-lookup"><span data-stu-id="6427d-103">DSC User Resource#</span></span>


><span data-ttu-id="6427d-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6427d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="6427d-105">Windows PowerShell Desired State Configuration (DSC) 中的 __User__ 资源提供在目标节点上管理用户帐户的机制。</span><span class="sxs-lookup"><span data-stu-id="6427d-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="6427d-106">语法##</span><span class="sxs-lookup"><span data-stu-id="6427d-106">Syntax##</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="6427d-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="6427d-107">Properties</span></span>
|  <span data-ttu-id="6427d-108">属性</span><span class="sxs-lookup"><span data-stu-id="6427d-108">Property</span></span>  |  <span data-ttu-id="6427d-109">说明</span><span class="sxs-lookup"><span data-stu-id="6427d-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="6427d-110">UserName</span><span class="sxs-lookup"><span data-stu-id="6427d-110">UserName</span></span>| <span data-ttu-id="6427d-111">指示要确保其特定状态的帐户名。</span><span class="sxs-lookup"><span data-stu-id="6427d-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="6427d-112">说明</span><span class="sxs-lookup"><span data-stu-id="6427d-112">Description</span></span>| <span data-ttu-id="6427d-113">指示要用于用户帐户的说明。</span><span class="sxs-lookup"><span data-stu-id="6427d-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="6427d-114">禁用</span><span class="sxs-lookup"><span data-stu-id="6427d-114">Disabled</span></span>| <span data-ttu-id="6427d-115">指示帐户是否已启用。</span><span class="sxs-lookup"><span data-stu-id="6427d-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="6427d-116">将此属性设置为 __$true__ 以确已禁用保此帐户，将其设置为 __$false__ 以确保已启用此帐户。</span><span class="sxs-lookup"><span data-stu-id="6427d-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>|
| <span data-ttu-id="6427d-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="6427d-117">Ensure</span></span>| <span data-ttu-id="6427d-118">指示帐户是否存在。</span><span class="sxs-lookup"><span data-stu-id="6427d-118">Indicates if the account exists.</span></span> <span data-ttu-id="6427d-119">将此属性设置为“Present”以确保该帐户存在，将其设置为“Absent”以确保该帐户不存在。</span><span class="sxs-lookup"><span data-stu-id="6427d-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="6427d-120">FullName</span><span class="sxs-lookup"><span data-stu-id="6427d-120">FullName</span></span>| <span data-ttu-id="6427d-121">表示包含要用于用户帐户的完整名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="6427d-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="6427d-122">密码</span><span class="sxs-lookup"><span data-stu-id="6427d-122">Password</span></span>| <span data-ttu-id="6427d-123">指示要用于此帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="6427d-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="6427d-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="6427d-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="6427d-125">指示用户是否可以更改密码。</span><span class="sxs-lookup"><span data-stu-id="6427d-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="6427d-126">将此属性设置为 __$true__ 以确保用户无法更改密码，将其设置为 __$false__ 以允许用户更改密码。</span><span class="sxs-lookup"><span data-stu-id="6427d-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="6427d-127">默认值为 __$false__。</span><span class="sxs-lookup"><span data-stu-id="6427d-127">The default value is __$false__.</span></span>|
| <span data-ttu-id="6427d-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="6427d-128">PasswordChangeRequired</span></span>| <span data-ttu-id="6427d-129">指定用户下次登录时是否必须更改密码。</span><span class="sxs-lookup"><span data-stu-id="6427d-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="6427d-130">要使用户必须更改密码，请将此属性设置为 __$true__。</span><span class="sxs-lookup"><span data-stu-id="6427d-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="6427d-131">默认值为 __$true__。</span><span class="sxs-lookup"><span data-stu-id="6427d-131">The default value is __$true__.</span></span>|
| <span data-ttu-id="6427d-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="6427d-132">PasswordNeverExpires</span></span>| <span data-ttu-id="6427d-133">指示密码是否会过期。</span><span class="sxs-lookup"><span data-stu-id="6427d-133">Indicates if the password will expire.</span></span> <span data-ttu-id="6427d-134">将此属性设置为 __$true__ 以确保此帐户的密码永不过期，将其设置为 __$false__ 则密码会过期。</span><span class="sxs-lookup"><span data-stu-id="6427d-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="6427d-135">默认值为 __$false__。</span><span class="sxs-lookup"><span data-stu-id="6427d-135">The default value is __$false__.</span></span>|
| <span data-ttu-id="6427d-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6427d-136">DependsOn</span></span> | <span data-ttu-id="6427d-137">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="6427d-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6427d-138">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="6427d-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="6427d-139">示例</span><span class="sxs-lookup"><span data-stu-id="6427d-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```
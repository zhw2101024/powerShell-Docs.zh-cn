---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Service 资源
ms.openlocfilehash: 3e2db8999ab1db2964f88e1ee14c6ad6e641c5e3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-service-resource"></a><span data-ttu-id="941e9-103">DSC Service 资源</span><span class="sxs-lookup"><span data-stu-id="941e9-103">DSC Service Resource</span></span>

> <span data-ttu-id="941e9-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="941e9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="941e9-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Service** 资源提供了在目标节点上管理服务的机制。</span><span class="sxs-lookup"><span data-stu-id="941e9-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="941e9-106">语法</span><span class="sxs-lookup"><span data-stu-id="941e9-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="941e9-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="941e9-107">Properties</span></span>

|  <span data-ttu-id="941e9-108">属性</span><span class="sxs-lookup"><span data-stu-id="941e9-108">Property</span></span>  |  <span data-ttu-id="941e9-109">说明</span><span class="sxs-lookup"><span data-stu-id="941e9-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="941e9-110">名称</span><span class="sxs-lookup"><span data-stu-id="941e9-110">Name</span></span>| <span data-ttu-id="941e9-111">指示服务名称。</span><span class="sxs-lookup"><span data-stu-id="941e9-111">Indicates the service name.</span></span> <span data-ttu-id="941e9-112">请注意，有时它与显示名称不同。</span><span class="sxs-lookup"><span data-stu-id="941e9-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="941e9-113">你可以使用 Get-Service cmdlet 获取服务及其当前状态的列表。</span><span class="sxs-lookup"><span data-stu-id="941e9-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="941e9-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="941e9-114">BuiltInAccount</span></span>| <span data-ttu-id="941e9-115">指示要用于服务的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="941e9-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="941e9-116">允许用于此属性的值有：**LocalService**、**LocalSystem** 和 **NetworkService**。</span><span class="sxs-lookup"><span data-stu-id="941e9-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="941e9-117">凭据</span><span class="sxs-lookup"><span data-stu-id="941e9-117">Credential</span></span>| <span data-ttu-id="941e9-118">指示服务将在其下运行的帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="941e9-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="941e9-119">此属性与 __BuiltinAccount__ 属性不能一起使用。</span><span class="sxs-lookup"><span data-stu-id="941e9-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="941e9-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="941e9-120">DependsOn</span></span>| <span data-ttu-id="941e9-121">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="941e9-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="941e9-122">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="941e9-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="941e9-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="941e9-123">StartupType</span></span>| <span data-ttu-id="941e9-124">设置服务的启动类型。</span><span class="sxs-lookup"><span data-stu-id="941e9-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="941e9-125">允许用于此属性的值有：**Automatic**、**Disabled** 和 **Manual**。</span><span class="sxs-lookup"><span data-stu-id="941e9-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="941e9-126">State</span><span class="sxs-lookup"><span data-stu-id="941e9-126">State</span></span>| <span data-ttu-id="941e9-127">指示你想要确保服务所处的状态。</span><span class="sxs-lookup"><span data-stu-id="941e9-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="941e9-128">说明</span><span class="sxs-lookup"><span data-stu-id="941e9-128">Description</span></span> | <span data-ttu-id="941e9-129">指示目标服务的说明。</span><span class="sxs-lookup"><span data-stu-id="941e9-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="941e9-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="941e9-130">DisplayName</span></span> | <span data-ttu-id="941e9-131">指示目标服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="941e9-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="941e9-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="941e9-132">Ensure</span></span> | <span data-ttu-id="941e9-133">指示目标服务是否在系统中存在。</span><span class="sxs-lookup"><span data-stu-id="941e9-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="941e9-134">将此属性设置为 **Absent** 可确保目标服务不存在。</span><span class="sxs-lookup"><span data-stu-id="941e9-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="941e9-135">将它设置为 **Present**（默认值）可确保目标服务存在。</span><span class="sxs-lookup"><span data-stu-id="941e9-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="941e9-136">路径</span><span class="sxs-lookup"><span data-stu-id="941e9-136">Path</span></span> | <span data-ttu-id="941e9-137">指示新服务的二进制文件的路径。</span><span class="sxs-lookup"><span data-stu-id="941e9-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="941e9-138">示例</span><span class="sxs-lookup"><span data-stu-id="941e9-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
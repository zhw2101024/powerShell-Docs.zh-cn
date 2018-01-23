---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC ServiceSet 资源"
ms.openlocfilehash: 9556a1d513c3819a36c1161e3b35388ca1eb66f9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="9683d-103">DSC ServiceSet 资源</span><span class="sxs-lookup"><span data-stu-id="9683d-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="9683d-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9683d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="9683d-105">Windows PowerShell Desired State Configuration (DSC) 中的 **ServiceSet** 资源提供了在目标节点上管理服务的机制。</span><span class="sxs-lookup"><span data-stu-id="9683d-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="9683d-106">此资源是[复合资源](authoringResourceComposite.md)，它会针对 `Name` 属性中指定的每个服务调用 [Service 资源](serviceResource.md)。</span><span class="sxs-lookup"><span data-stu-id="9683d-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="9683d-107">要将一些服务配置为相同状态时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="9683d-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="9683d-108">语法</span><span class="sxs-lookup"><span data-stu-id="9683d-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="9683d-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="9683d-109">Properties</span></span>

|  <span data-ttu-id="9683d-110">属性</span><span class="sxs-lookup"><span data-stu-id="9683d-110">Property</span></span>  |  <span data-ttu-id="9683d-111">说明</span><span class="sxs-lookup"><span data-stu-id="9683d-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="9683d-112">名称</span><span class="sxs-lookup"><span data-stu-id="9683d-112">Name</span></span>| <span data-ttu-id="9683d-113">指示服务名称。</span><span class="sxs-lookup"><span data-stu-id="9683d-113">Indicates the service names.</span></span> <span data-ttu-id="9683d-114">请注意，有时它与显示名称不同。</span><span class="sxs-lookup"><span data-stu-id="9683d-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="9683d-115">你可以使用 [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet 获取服务及其当前状态的列表。</span><span class="sxs-lookup"><span data-stu-id="9683d-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="9683d-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="9683d-116">StartupType</span></span>| <span data-ttu-id="9683d-117">设置服务的启动类型。</span><span class="sxs-lookup"><span data-stu-id="9683d-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="9683d-118">允许用于此属性的值有：**Automatic**、**Disabled** 和 **Manual**。</span><span class="sxs-lookup"><span data-stu-id="9683d-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|  
| <span data-ttu-id="9683d-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="9683d-119">BuiltInAccount</span></span>| <span data-ttu-id="9683d-120">指示要用于服务的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="9683d-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="9683d-121">允许用于此属性的值有：**LocalService**、**LocalSystem** 和 **NetworkService**。</span><span class="sxs-lookup"><span data-stu-id="9683d-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="9683d-122">State</span><span class="sxs-lookup"><span data-stu-id="9683d-122">State</span></span>| <span data-ttu-id="9683d-123">指示你要确保服务所处的状态：**Stopped** 或 **Running**。</span><span class="sxs-lookup"><span data-stu-id="9683d-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>| 
| <span data-ttu-id="9683d-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="9683d-124">Ensure</span></span>| <span data-ttu-id="9683d-125">指示服务是否在系统中存在。</span><span class="sxs-lookup"><span data-stu-id="9683d-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="9683d-126">将此属性设置为 **Absent** 可确保服务不存在。</span><span class="sxs-lookup"><span data-stu-id="9683d-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="9683d-127">将它设置为 **Present**（默认值）可确保目标服务存在。</span><span class="sxs-lookup"><span data-stu-id="9683d-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="9683d-128">凭据</span><span class="sxs-lookup"><span data-stu-id="9683d-128">Credential</span></span>| <span data-ttu-id="9683d-129">指示服务资源将在其下运行的帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="9683d-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="9683d-130">此属性与 **BuiltinAccount** 属性不能一起使用。</span><span class="sxs-lookup"><span data-stu-id="9683d-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>| 
| <span data-ttu-id="9683d-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9683d-131">DependsOn</span></span>| <span data-ttu-id="9683d-132">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="9683d-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9683d-133">例如，如果你想要首先运行 ID 为 *ResourceName*、类型为 *ResourceType* 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="9683d-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 



## <a name="example"></a><span data-ttu-id="9683d-134">示例</span><span class="sxs-lookup"><span data-stu-id="9683d-134">Example</span></span>

<span data-ttu-id="9683d-135">以下配置启动“Windows 音频”和“远程桌面服务”服务。</span><span class="sxs-lookup"><span data-stu-id="9683d-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```


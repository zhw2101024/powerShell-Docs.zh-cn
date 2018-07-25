---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxGroup 资源
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093596"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="4b64d-103">适用于 Linux 的 DSC nxGroup 资源</span><span class="sxs-lookup"><span data-stu-id="4b64d-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="4b64d-104">PowerShell Desired State Configuration (DSC) 中的 **nxGroup** 资源提供了在 Linux 节点上管理本地组的机制。</span><span class="sxs-lookup"><span data-stu-id="4b64d-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b64d-105">语法</span><span class="sxs-lookup"><span data-stu-id="4b64d-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="4b64d-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="4b64d-106">Properties</span></span>

|  <span data-ttu-id="4b64d-107">属性</span><span class="sxs-lookup"><span data-stu-id="4b64d-107">Property</span></span> |  <span data-ttu-id="4b64d-108">说明</span><span class="sxs-lookup"><span data-stu-id="4b64d-108">Description</span></span> |
|---|---|
| <span data-ttu-id="4b64d-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="4b64d-109">GroupName</span></span>| <span data-ttu-id="4b64d-110">指定要确保其特定状态的组的名称。</span><span class="sxs-lookup"><span data-stu-id="4b64d-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="4b64d-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="4b64d-111">Ensure</span></span>| <span data-ttu-id="4b64d-112">确定是否检查组是否存在。</span><span class="sxs-lookup"><span data-stu-id="4b64d-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="4b64d-113">将此属性设置为“Present”以确保该组存在。</span><span class="sxs-lookup"><span data-stu-id="4b64d-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="4b64d-114">将其设置为“Absent”以确保该组不存在。</span><span class="sxs-lookup"><span data-stu-id="4b64d-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="4b64d-115">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="4b64d-115">The default value is "Present".</span></span>|
| <span data-ttu-id="4b64d-116">成员</span><span class="sxs-lookup"><span data-stu-id="4b64d-116">Members</span></span>| <span data-ttu-id="4b64d-117">指定构成该组的成员。</span><span class="sxs-lookup"><span data-stu-id="4b64d-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="4b64d-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="4b64d-118">MembersToInclude</span></span>| <span data-ttu-id="4b64d-119">指定要确保是该组成员的用户。</span><span class="sxs-lookup"><span data-stu-id="4b64d-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="4b64d-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="4b64d-120">MembersToExclude</span></span>| <span data-ttu-id="4b64d-121">指定要确保不是该组成员的用户。</span><span class="sxs-lookup"><span data-stu-id="4b64d-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="4b64d-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="4b64d-122">PreferredGroupID</span></span>| <span data-ttu-id="4b64d-123">尽量将组 ID 设置为提供的值。</span><span class="sxs-lookup"><span data-stu-id="4b64d-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="4b64d-124">如果组 ID 正在使用中，则使用下一个可用的组 ID。</span><span class="sxs-lookup"><span data-stu-id="4b64d-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="4b64d-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4b64d-125">DependsOn</span></span> | <span data-ttu-id="4b64d-126">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="4b64d-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4b64d-127">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = '[ResourceType]ResourceName'`。</span><span class="sxs-lookup"><span data-stu-id="4b64d-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="4b64d-128">示例</span><span class="sxs-lookup"><span data-stu-id="4b64d-128">Example</span></span>

<span data-ttu-id="4b64d-129">下面的示例确保用户“monuser”存在，且为组“DBusers”的成员。</span><span class="sxs-lookup"><span data-stu-id="4b64d-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```
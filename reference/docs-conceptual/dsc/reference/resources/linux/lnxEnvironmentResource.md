---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux nxEnvironment 资源的 DSC
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953224"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="6ba75-103">适用于 Linux nxEnvironment 资源的 DSC</span><span class="sxs-lookup"><span data-stu-id="6ba75-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="6ba75-104">PowerShell Desired State Configuration (DSC) 中的 nxEnvironment  资源提供了管理 Linux 节点上系统环境变量的机制。</span><span class="sxs-lookup"><span data-stu-id="6ba75-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ba75-105">语法</span><span class="sxs-lookup"><span data-stu-id="6ba75-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="6ba75-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="6ba75-106">Properties</span></span>

|<span data-ttu-id="6ba75-107">属性</span><span class="sxs-lookup"><span data-stu-id="6ba75-107">Property</span></span> |<span data-ttu-id="6ba75-108">说明</span><span class="sxs-lookup"><span data-stu-id="6ba75-108">Description</span></span> |
|---|---|
|<span data-ttu-id="6ba75-109">名称</span><span class="sxs-lookup"><span data-stu-id="6ba75-109">Name</span></span> |<span data-ttu-id="6ba75-110">指示指示你想要确保其特定状态的环境变量的名称。</span><span class="sxs-lookup"><span data-stu-id="6ba75-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="6ba75-111">值</span><span class="sxs-lookup"><span data-stu-id="6ba75-111">Value</span></span> |<span data-ttu-id="6ba75-112">要分配给环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="6ba75-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="6ba75-113">路径</span><span class="sxs-lookup"><span data-stu-id="6ba75-113">Path</span></span> |<span data-ttu-id="6ba75-114">定义正在配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="6ba75-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="6ba75-115">如果变量是 **Path**，则将此属性设置为 `$true`；否则将其设置为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="6ba75-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="6ba75-116">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="6ba75-116">The default is `$false`.</span></span> <span data-ttu-id="6ba75-117">如果正在配置的变量是 **Path**，则通过 **Value** 属性提供的值将被附加到现有值。</span><span class="sxs-lookup"><span data-stu-id="6ba75-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6ba75-118">公共属性</span><span class="sxs-lookup"><span data-stu-id="6ba75-118">Common properties</span></span>

|<span data-ttu-id="6ba75-119">属性</span><span class="sxs-lookup"><span data-stu-id="6ba75-119">Property</span></span> |<span data-ttu-id="6ba75-120">说明</span><span class="sxs-lookup"><span data-stu-id="6ba75-120">Description</span></span> |
|---|---|
|<span data-ttu-id="6ba75-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6ba75-121">DependsOn</span></span> |<span data-ttu-id="6ba75-122">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="6ba75-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6ba75-123">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="6ba75-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6ba75-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="6ba75-124">Ensure</span></span> |<span data-ttu-id="6ba75-125">确定是否要检查变量是否存在。</span><span class="sxs-lookup"><span data-stu-id="6ba75-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="6ba75-126">将此属性设置为 **Present** 可确保变量存在。</span><span class="sxs-lookup"><span data-stu-id="6ba75-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="6ba75-127">将其设置为 **Absent** 可确保变量不存在。</span><span class="sxs-lookup"><span data-stu-id="6ba75-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="6ba75-128">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="6ba75-128">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="6ba75-129">其他信息</span><span class="sxs-lookup"><span data-stu-id="6ba75-129">Additional Information</span></span>

- <span data-ttu-id="6ba75-130">如果 **Path** 不存在，或者设置为 `$false`，则在 `/etc/environment` 中管理环境变量。</span><span class="sxs-lookup"><span data-stu-id="6ba75-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="6ba75-131">你的程序或脚本可能需要配置以获取 `/etc/environment` 文件从而访问托管的环境变量。</span><span class="sxs-lookup"><span data-stu-id="6ba75-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="6ba75-132">如果 **Path** 设置为 `$true`，则在 `/etc/profile.d/DSCenvironment.sh` 文件中管理环境变量。</span><span class="sxs-lookup"><span data-stu-id="6ba75-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="6ba75-133">如果不存在，则将创建此文件。</span><span class="sxs-lookup"><span data-stu-id="6ba75-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="6ba75-134">如果 **Ensure** 设置为 **Absent**，**Path** 设置为 `$true`，则仅从 `/etc/profile.d/DSCenvironment.sh`（而非其他文件）中删除现有环境变量。</span><span class="sxs-lookup"><span data-stu-id="6ba75-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="6ba75-135">示例</span><span class="sxs-lookup"><span data-stu-id="6ba75-135">Example</span></span>

<span data-ttu-id="6ba75-136">以下示例说明如何使用 **nxEnvironment** 资源来确保 **TestEnvironmentVariable** 存在且具有值“Test-Value”。</span><span class="sxs-lookup"><span data-stu-id="6ba75-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="6ba75-137">如果不存在，则将创建 **TestEnvironmentVariable**。</span><span class="sxs-lookup"><span data-stu-id="6ba75-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
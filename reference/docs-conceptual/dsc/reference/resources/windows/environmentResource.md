---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Environment 资源
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954714"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="75989-103">DSC Environment 资源</span><span class="sxs-lookup"><span data-stu-id="75989-103">DSC Environment Resource</span></span>

> <span data-ttu-id="75989-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="75989-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="75989-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Environment** 资源提供了管理系统环境变量的机制。</span><span class="sxs-lookup"><span data-stu-id="75989-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="75989-106">语法</span><span class="sxs-lookup"><span data-stu-id="75989-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="75989-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="75989-107">Properties</span></span>

|<span data-ttu-id="75989-108">属性</span><span class="sxs-lookup"><span data-stu-id="75989-108">Property</span></span> |<span data-ttu-id="75989-109">说明</span><span class="sxs-lookup"><span data-stu-id="75989-109">Description</span></span> |
|---|---|
|<span data-ttu-id="75989-110">名称</span><span class="sxs-lookup"><span data-stu-id="75989-110">Name</span></span> |<span data-ttu-id="75989-111">指示指示你想要确保其特定状态的环境变量的名称。</span><span class="sxs-lookup"><span data-stu-id="75989-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="75989-112">路径</span><span class="sxs-lookup"><span data-stu-id="75989-112">Path</span></span> |<span data-ttu-id="75989-113">定义正在配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="75989-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="75989-114">如果变量是 **Path**，则将此属性设置为 `$true`；否则将其设置为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="75989-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="75989-115">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="75989-115">The default is `$false`.</span></span> <span data-ttu-id="75989-116">如果正在配置的变量是 **Path**，则通过 **Value** 属性提供的值将被附加到现有值。</span><span class="sxs-lookup"><span data-stu-id="75989-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="75989-117">值</span><span class="sxs-lookup"><span data-stu-id="75989-117">Value</span></span> |<span data-ttu-id="75989-118">要分配给环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="75989-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="75989-119">公共属性</span><span class="sxs-lookup"><span data-stu-id="75989-119">Common properties</span></span>

|<span data-ttu-id="75989-120">属性</span><span class="sxs-lookup"><span data-stu-id="75989-120">Property</span></span> |<span data-ttu-id="75989-121">说明</span><span class="sxs-lookup"><span data-stu-id="75989-121">Description</span></span> |
|---|---|
|<span data-ttu-id="75989-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="75989-122">DependsOn</span></span> |<span data-ttu-id="75989-123">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="75989-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="75989-124">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="75989-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="75989-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="75989-125">Ensure</span></span> |<span data-ttu-id="75989-126">指示变量是否存在。</span><span class="sxs-lookup"><span data-stu-id="75989-126">Indicates if a variable exists.</span></span> <span data-ttu-id="75989-127">如果不存在此变量，将此属性设置为 **Present** 以创建环境变量；如果已存在此变量，则确保其值与通过 **Value** 属性提供的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="75989-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="75989-128">如果存在该变量，将其设置为 **Absent** 可将其删除。</span><span class="sxs-lookup"><span data-stu-id="75989-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="75989-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="75989-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="75989-130">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="75989-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="75989-131">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="75989-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="75989-132">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="75989-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="75989-133">示例</span><span class="sxs-lookup"><span data-stu-id="75989-133">Example</span></span>

<span data-ttu-id="75989-134">以下示例可确保 TestEnvironmentVariable 存在且具有值 _TestValue_。</span><span class="sxs-lookup"><span data-stu-id="75989-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="75989-135">如果不存在，则创建它。</span><span class="sxs-lookup"><span data-stu-id="75989-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
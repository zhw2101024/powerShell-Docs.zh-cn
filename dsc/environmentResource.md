---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Environment 资源
ms.openlocfilehash: 023ecf4cc2e3f553770d9c49a94b6e903e560b01
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="0f78f-103">DSC Environment 资源</span><span class="sxs-lookup"><span data-stu-id="0f78f-103">DSC Environment Resource</span></span>

> <span data-ttu-id="0f78f-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0f78f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0f78f-105">Windows PowerShell Desired State Configuration (DSC) 中的 __Environment__ 资源提供了管理系统环境变量的机制。</span><span class="sxs-lookup"><span data-stu-id="0f78f-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f78f-106">语法</span><span class="sxs-lookup"><span data-stu-id="0f78f-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="0f78f-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="0f78f-107">Properties</span></span>

|  <span data-ttu-id="0f78f-108">属性</span><span class="sxs-lookup"><span data-stu-id="0f78f-108">Property</span></span>  |  <span data-ttu-id="0f78f-109">说明</span><span class="sxs-lookup"><span data-stu-id="0f78f-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="0f78f-110">名称</span><span class="sxs-lookup"><span data-stu-id="0f78f-110">Name</span></span>| <span data-ttu-id="0f78f-111">指示指示你想要确保其特定状态的环境变量的名称。</span><span class="sxs-lookup"><span data-stu-id="0f78f-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="0f78f-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="0f78f-112">Ensure</span></span>| <span data-ttu-id="0f78f-113">指示变量是否存在。</span><span class="sxs-lookup"><span data-stu-id="0f78f-113">Indicates if a variable exists.</span></span> <span data-ttu-id="0f78f-114">如果不存在此变量，将此属性设置为 __Present__ 以创建环境变量；如果已存在此变量，则确保其值与通过 __Value__ 属性提供的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="0f78f-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="0f78f-115">如果存在该变量，将其设置为 __Absent__ 可将其删除。</span><span class="sxs-lookup"><span data-stu-id="0f78f-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="0f78f-116">路径</span><span class="sxs-lookup"><span data-stu-id="0f78f-116">Path</span></span>| <span data-ttu-id="0f78f-117">定义正在配置的环境变量。</span><span class="sxs-lookup"><span data-stu-id="0f78f-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="0f78f-118">如果变量是 __Path__，则将此属性设置为 __$true__；否则将其设置为 __$false__。</span><span class="sxs-lookup"><span data-stu-id="0f78f-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="0f78f-119">默认值为 __$false__。</span><span class="sxs-lookup"><span data-stu-id="0f78f-119">The default is __$false__.</span></span> <span data-ttu-id="0f78f-120">如果正在配置的变量是 __Path__，则通过 __Value__ 属性提供的值将被附加到现有值。</span><span class="sxs-lookup"><span data-stu-id="0f78f-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="0f78f-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0f78f-121">DependsOn</span></span> | <span data-ttu-id="0f78f-122">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="0f78f-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0f78f-123">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0f78f-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="0f78f-124">值</span><span class="sxs-lookup"><span data-stu-id="0f78f-124">Value</span></span>| <span data-ttu-id="0f78f-125">要分配给环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="0f78f-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="0f78f-126">示例</span><span class="sxs-lookup"><span data-stu-id="0f78f-126">Example</span></span>

<span data-ttu-id="0f78f-127">以下示例可确保 __TestEnvironmentVariable__ 存在且具有值 __TestValue__。</span><span class="sxs-lookup"><span data-stu-id="0f78f-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="0f78f-128">如果不存在，则创建它。</span><span class="sxs-lookup"><span data-stu-id="0f78f-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
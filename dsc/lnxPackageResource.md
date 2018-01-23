---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "适用于 Linux 的 DSC nxPackage 资源"
ms.openlocfilehash: 41c627ebb39dad535f7acc8fe34739355f7a81b5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="066f3-103">适用于 Linux 的 DSC nxPackage 资源</span><span class="sxs-lookup"><span data-stu-id="066f3-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="066f3-104">PowerShell Desired State Configuration (DSC) 中的 **nxPackage** 资源提供了在 Linux 节点上管理程序包的机制。</span><span class="sxs-lookup"><span data-stu-id="066f3-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="066f3-105">语法</span><span class="sxs-lookup"><span data-stu-id="066f3-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## <a name="properties"></a><span data-ttu-id="066f3-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="066f3-106">Properties</span></span>

|  <span data-ttu-id="066f3-107">属性</span><span class="sxs-lookup"><span data-stu-id="066f3-107">Property</span></span> |  <span data-ttu-id="066f3-108">说明</span><span class="sxs-lookup"><span data-stu-id="066f3-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="066f3-109">名称</span><span class="sxs-lookup"><span data-stu-id="066f3-109">Name</span></span>| <span data-ttu-id="066f3-110">要确保其特定状态的程序包的名称。</span><span class="sxs-lookup"><span data-stu-id="066f3-110">The name of the package for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="066f3-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="066f3-111">Ensure</span></span>| <span data-ttu-id="066f3-112">确定是否检查程序包是否存在。</span><span class="sxs-lookup"><span data-stu-id="066f3-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="066f3-113">将此属性设置为“Present”以确保该程序包存在。</span><span class="sxs-lookup"><span data-stu-id="066f3-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="066f3-114">将其设置为“Absent”以确保该程序包不存在。</span><span class="sxs-lookup"><span data-stu-id="066f3-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="066f3-115">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="066f3-115">The default value is "Present".</span></span>|  
| <span data-ttu-id="066f3-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="066f3-116">PackageManager</span></span>| <span data-ttu-id="066f3-117">支持的值有“yum”、“apt”和“zypper”。</span><span class="sxs-lookup"><span data-stu-id="066f3-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="066f3-118">指定安装程序包时要使用的程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="066f3-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="066f3-119">如果指定了 **FilePath**，则将使用提供的路径安装程序包。</span><span class="sxs-lookup"><span data-stu-id="066f3-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="066f3-120">否则，将使用程序包管理器从预配置的存储库安装程序包。</span><span class="sxs-lookup"><span data-stu-id="066f3-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="066f3-121">如果既不提供 **PackageManager**，也不提供 **FilePath**，则将使用系统默认的程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="066f3-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>| 
| <span data-ttu-id="066f3-122">文件路径</span><span class="sxs-lookup"><span data-stu-id="066f3-122">FilePath</span></span>| <span data-ttu-id="066f3-123">程序包所在的文件路径</span><span class="sxs-lookup"><span data-stu-id="066f3-123">The file path where the package resides</span></span>| 
| <span data-ttu-id="066f3-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="066f3-124">PackageGroup</span></span>| <span data-ttu-id="066f3-125">如果为 **$true**，则 **Name** 应为用于 **PackageManager** 的程序包组的名称。</span><span class="sxs-lookup"><span data-stu-id="066f3-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="066f3-126">提供 **FilePath** 时，**PacakgeGroup** 无效。</span><span class="sxs-lookup"><span data-stu-id="066f3-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>| 
| <span data-ttu-id="066f3-127">参数</span><span class="sxs-lookup"><span data-stu-id="066f3-127">Arguments</span></span>| <span data-ttu-id="066f3-128">将完全按原样传输给程序包的参数字符串。</span><span class="sxs-lookup"><span data-stu-id="066f3-128">A string of arguments that will be passed to the package exactly as provided.</span></span>| 
| <span data-ttu-id="066f3-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="066f3-129">ReturnCode</span></span>| <span data-ttu-id="066f3-130">预期的返回代码。</span><span class="sxs-lookup"><span data-stu-id="066f3-130">The expected return code.</span></span> <span data-ttu-id="066f3-131">如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。</span><span class="sxs-lookup"><span data-stu-id="066f3-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>| 
| <span data-ttu-id="066f3-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="066f3-132">DependsOn</span></span> | <span data-ttu-id="066f3-133">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="066f3-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="066f3-134">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="066f3-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="066f3-135">示例</span><span class="sxs-lookup"><span data-stu-id="066f3-135">Example</span></span>

<span data-ttu-id="066f3-136">以下示例将确保使用“Yum”程序包管理器在 Linux 计算机上安装了名为“httpd”的程序包。</span><span class="sxs-lookup"><span data-stu-id="066f3-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```


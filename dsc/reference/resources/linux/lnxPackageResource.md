---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxPackage 资源
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047145"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="1c0b5-103">适用于 Linux 的 DSC nxPackage 资源</span><span class="sxs-lookup"><span data-stu-id="1c0b5-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="1c0b5-104">PowerShell Desired State Configuration (DSC) 中的 **nxPackage** 资源提供了在 Linux 节点上管理程序包的机制。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c0b5-105">语法</span><span class="sxs-lookup"><span data-stu-id="1c0b5-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="1c0b5-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="1c0b5-106">Properties</span></span>

|  <span data-ttu-id="1c0b5-107">属性</span><span class="sxs-lookup"><span data-stu-id="1c0b5-107">Property</span></span> |  <span data-ttu-id="1c0b5-108">说明</span><span class="sxs-lookup"><span data-stu-id="1c0b5-108">Description</span></span> |
|---|---|
| <span data-ttu-id="1c0b5-109">名称</span><span class="sxs-lookup"><span data-stu-id="1c0b5-109">Name</span></span>| <span data-ttu-id="1c0b5-110">要确保其特定状态的程序包的名称。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="1c0b5-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="1c0b5-111">Ensure</span></span>| <span data-ttu-id="1c0b5-112">确定是否检查程序包是否存在。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="1c0b5-113">将此属性设置为“Present”以确保该程序包存在。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="1c0b5-114">将其设置为“Absent”以确保该程序包不存在。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="1c0b5-115">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-115">The default value is "Present".</span></span>|
| <span data-ttu-id="1c0b5-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="1c0b5-116">PackageManager</span></span>| <span data-ttu-id="1c0b5-117">支持的值有“yum”、“apt”和“zypper”。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="1c0b5-118">指定安装程序包时要使用的程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="1c0b5-119">如果指定了 **FilePath**，则将使用提供的路径安装程序包。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="1c0b5-120">否则，将使用程序包管理器从预配置的存储库安装程序包。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="1c0b5-121">如果既不提供 **PackageManager**，也不提供 **FilePath**，则将使用系统默认的程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="1c0b5-122">文件路径</span><span class="sxs-lookup"><span data-stu-id="1c0b5-122">FilePath</span></span>| <span data-ttu-id="1c0b5-123">程序包所在的文件路径</span><span class="sxs-lookup"><span data-stu-id="1c0b5-123">The file path where the package resides</span></span>|
| <span data-ttu-id="1c0b5-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="1c0b5-124">PackageGroup</span></span>| <span data-ttu-id="1c0b5-125">如果为 **$true**，则 **Name** 应为用于 **PackageManager** 的程序包组的名称。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="1c0b5-126">提供 **FilePath** 时，**PacakgeGroup** 无效。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="1c0b5-127">参数</span><span class="sxs-lookup"><span data-stu-id="1c0b5-127">Arguments</span></span>| <span data-ttu-id="1c0b5-128">将完全按原样传输给程序包的参数字符串。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="1c0b5-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="1c0b5-129">ReturnCode</span></span>| <span data-ttu-id="1c0b5-130">预期的返回代码。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-130">The expected return code.</span></span> <span data-ttu-id="1c0b5-131">如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="1c0b5-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1c0b5-132">DependsOn</span></span> | <span data-ttu-id="1c0b5-133">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1c0b5-134">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="1c0b5-135">示例</span><span class="sxs-lookup"><span data-stu-id="1c0b5-135">Example</span></span>

<span data-ttu-id="1c0b5-136">以下示例将确保使用“Yum”程序包管理器在 Linux 计算机上安装了名为“httpd”的程序包。</span><span class="sxs-lookup"><span data-stu-id="1c0b5-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

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
---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxService 资源
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267773"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="99ee4-103">适用于 Linux 的 DSC nxService 资源</span><span class="sxs-lookup"><span data-stu-id="99ee4-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="99ee4-104">PowerShell Desired State Configuration (DSC) 中的 **nxService** 资源提供了在 Linux 节点上管理服务的机制。</span><span class="sxs-lookup"><span data-stu-id="99ee4-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="99ee4-105">语法</span><span class="sxs-lookup"><span data-stu-id="99ee4-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="99ee4-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="99ee4-106">Properties</span></span>

| <span data-ttu-id="99ee4-107">属性</span><span class="sxs-lookup"><span data-stu-id="99ee4-107">Property</span></span> | <span data-ttu-id="99ee4-108">说明</span><span class="sxs-lookup"><span data-stu-id="99ee4-108">Description</span></span> |
|---|---|
| <span data-ttu-id="99ee4-109">名称</span><span class="sxs-lookup"><span data-stu-id="99ee4-109">Name</span></span>| <span data-ttu-id="99ee4-110">要配置的服务/守护程序的名称。</span><span class="sxs-lookup"><span data-stu-id="99ee4-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="99ee4-111">控制器</span><span class="sxs-lookup"><span data-stu-id="99ee4-111">Controller</span></span>| <span data-ttu-id="99ee4-112">配置服务时使用的服务控制器类型。</span><span class="sxs-lookup"><span data-stu-id="99ee4-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="99ee4-113">启用</span><span class="sxs-lookup"><span data-stu-id="99ee4-113">Enabled</span></span>| <span data-ttu-id="99ee4-114">指示服务是否开机启动。</span><span class="sxs-lookup"><span data-stu-id="99ee4-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="99ee4-115">State</span><span class="sxs-lookup"><span data-stu-id="99ee4-115">State</span></span>| <span data-ttu-id="99ee4-116">指示服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="99ee4-116">Indicates whether the service is running.</span></span> <span data-ttu-id="99ee4-117">将此属性设置为“Stopped”以确保该服务不在运行。</span><span class="sxs-lookup"><span data-stu-id="99ee4-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="99ee4-118">将其设置为“Running”以确保该服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="99ee4-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="99ee4-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="99ee4-119">DependsOn</span></span> | <span data-ttu-id="99ee4-120">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="99ee4-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="99ee4-121">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="99ee4-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="99ee4-122">其他信息</span><span class="sxs-lookup"><span data-stu-id="99ee4-122">Additional Information</span></span>

<span data-ttu-id="99ee4-123">**nxService** 资源不会为不存在的服务创建服务定义或脚本。</span><span class="sxs-lookup"><span data-stu-id="99ee4-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="99ee4-124">你可使用 PowerShell Desired State Configuration **nxFile** 资源管理服务定义文件或脚本是否存在或管理其内容。</span><span class="sxs-lookup"><span data-stu-id="99ee4-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="99ee4-125">示例</span><span class="sxs-lookup"><span data-stu-id="99ee4-125">Example</span></span>

<span data-ttu-id="99ee4-126">下面的示例展示了已向 SystemD 服务控制器注册的“httpd”服务（适用于 Apache HTTP 服务器）的配置。</span><span class="sxs-lookup"><span data-stu-id="99ee4-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
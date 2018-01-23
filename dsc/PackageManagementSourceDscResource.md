---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC PackageManagementSource 资源"
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="3fdd1-103">DSC PackageManagementSource 资源</span><span class="sxs-lookup"><span data-stu-id="3fdd1-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="3fdd1-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3fdd1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3fdd1-105">Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="3fdd1-106">**以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="3fdd1-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="3fdd1-107">此资源需要 http://PowerShellGallery.com 中的 **PackageManagement** 模块。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="3fdd1-108">语法</span><span class="sxs-lookup"><span data-stu-id="3fdd1-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="3fdd1-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="3fdd1-109">Properties</span></span>
|  <span data-ttu-id="3fdd1-110">属性</span><span class="sxs-lookup"><span data-stu-id="3fdd1-110">Property</span></span>  |  <span data-ttu-id="3fdd1-111">说明</span><span class="sxs-lookup"><span data-stu-id="3fdd1-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="3fdd1-112">名称</span><span class="sxs-lookup"><span data-stu-id="3fdd1-112">Name</span></span>| <span data-ttu-id="3fdd1-113">指定要在系统上注册或取消注册的包源名称。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="3fdd1-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="3fdd1-114">Ensure</span></span>| <span data-ttu-id="3fdd1-115">确定是要注册还是要取消注册包源。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="3fdd1-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="3fdd1-116">InstallationPolicy</span></span>| <span data-ttu-id="3fdd1-117">确定是否信任包源。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="3fdd1-118">可取值为“Untrusted”或“Trusted”。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="3fdd1-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="3fdd1-119">ProviderName</span></span>| <span data-ttu-id="3fdd1-120">指定 OneGet 提供程序的名称，借此可以与包源进行互操作。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="3fdd1-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="3fdd1-121">SourceUri</span></span>| <span data-ttu-id="3fdd1-122">指定包源的 URI。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="3fdd1-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="3fdd1-123">SourceCredential</span></span>| <span data-ttu-id="3fdd1-124">提供远程源上程序包的访问权限。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="3fdd1-125">示例</span><span class="sxs-lookup"><span data-stu-id="3fdd1-125">Example</span></span>

<span data-ttu-id="3fdd1-126">此示例使用 **PackageManagementSource** DSC 资源注册 http://nuget.org 包源。</span><span class="sxs-lookup"><span data-stu-id="3fdd1-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```


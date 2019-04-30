---
ms.date: 06/20/2018
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagementSource 资源
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077579"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="42e69-103">DSC PackageManagementSource 资源</span><span class="sxs-lookup"><span data-stu-id="42e69-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="42e69-104">适用于：Windows PowerShell 4.0、Windows PowerShell 5.0 和 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="42e69-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="42e69-105">Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。</span><span class="sxs-lookup"><span data-stu-id="42e69-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="42e69-106">**以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="42e69-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="42e69-107">此资源需要 http://PowerShellGallery.com 中的 PackageManagement 模块。</span><span class="sxs-lookup"><span data-stu-id="42e69-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42e69-108">PackageManagement 模块应至少为版本 1.1.7.0，以下属性信息才正确。</span><span class="sxs-lookup"><span data-stu-id="42e69-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="42e69-109">语法</span><span class="sxs-lookup"><span data-stu-id="42e69-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="42e69-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="42e69-110">Properties</span></span>

|  <span data-ttu-id="42e69-111">属性</span><span class="sxs-lookup"><span data-stu-id="42e69-111">Property</span></span>  |  <span data-ttu-id="42e69-112">说明</span><span class="sxs-lookup"><span data-stu-id="42e69-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="42e69-113">名称</span><span class="sxs-lookup"><span data-stu-id="42e69-113">Name</span></span>| <span data-ttu-id="42e69-114">指定要在系统上注册或取消注册的包源名称。</span><span class="sxs-lookup"><span data-stu-id="42e69-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="42e69-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="42e69-115">ProviderName</span></span>| <span data-ttu-id="42e69-116">指定 OneGet 提供程序的名称，借此可以与包源进行互操作。</span><span class="sxs-lookup"><span data-stu-id="42e69-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="42e69-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="42e69-117">SourceLocation</span></span>| <span data-ttu-id="42e69-118">指定包源的 URI。</span><span class="sxs-lookup"><span data-stu-id="42e69-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="42e69-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="42e69-119">Ensure</span></span>| <span data-ttu-id="42e69-120">确定是要注册还是要取消注册包源。</span><span class="sxs-lookup"><span data-stu-id="42e69-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="42e69-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="42e69-121">InstallationPolicy</span></span>| <span data-ttu-id="42e69-122">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="42e69-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="42e69-123">确定是否信任包的源。</span><span class="sxs-lookup"><span data-stu-id="42e69-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="42e69-124">可取值为：“Untrusted”或“Trusted”。</span><span class="sxs-lookup"><span data-stu-id="42e69-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="42e69-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="42e69-125">SourceCredential</span></span>| <span data-ttu-id="42e69-126">提供远程源上程序包的访问权限。</span><span class="sxs-lookup"><span data-stu-id="42e69-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="42e69-127">示例</span><span class="sxs-lookup"><span data-stu-id="42e69-127">Example</span></span>

<span data-ttu-id="42e69-128">此示例使用 PackageManagementSource DSC 资源注册 http://nuget.org 包源。</span><span class="sxs-lookup"><span data-stu-id="42e69-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```
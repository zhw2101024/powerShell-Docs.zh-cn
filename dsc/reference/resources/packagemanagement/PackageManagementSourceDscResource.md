---
ms.date: 06/20/2018
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagementSource 资源
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047055"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="927ef-103">DSC PackageManagementSource 资源</span><span class="sxs-lookup"><span data-stu-id="927ef-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="927ef-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0 中，Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="927ef-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="927ef-105">Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。</span><span class="sxs-lookup"><span data-stu-id="927ef-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="927ef-106">**以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="927ef-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="927ef-107">此资源需要 http://PowerShellGallery.com 中的 PackageManagement 模块。</span><span class="sxs-lookup"><span data-stu-id="927ef-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="927ef-108">PackageManagement 模块应至少为版本 1.1.7.0，以下属性信息才正确。</span><span class="sxs-lookup"><span data-stu-id="927ef-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="927ef-109">语法</span><span class="sxs-lookup"><span data-stu-id="927ef-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="927ef-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="927ef-110">Properties</span></span>

|  <span data-ttu-id="927ef-111">属性</span><span class="sxs-lookup"><span data-stu-id="927ef-111">Property</span></span>  |  <span data-ttu-id="927ef-112">说明</span><span class="sxs-lookup"><span data-stu-id="927ef-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="927ef-113">名称</span><span class="sxs-lookup"><span data-stu-id="927ef-113">Name</span></span>| <span data-ttu-id="927ef-114">指定要在系统上注册或取消注册的包源名称。</span><span class="sxs-lookup"><span data-stu-id="927ef-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="927ef-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="927ef-115">ProviderName</span></span>| <span data-ttu-id="927ef-116">指定 OneGet 提供程序的名称，借此可以与包源进行互操作。</span><span class="sxs-lookup"><span data-stu-id="927ef-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="927ef-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="927ef-117">SourceLocation</span></span>| <span data-ttu-id="927ef-118">指定包源的 URI。</span><span class="sxs-lookup"><span data-stu-id="927ef-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="927ef-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="927ef-119">Ensure</span></span>| <span data-ttu-id="927ef-120">确定是要注册还是要取消注册包源。</span><span class="sxs-lookup"><span data-stu-id="927ef-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="927ef-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="927ef-121">InstallationPolicy</span></span>| <span data-ttu-id="927ef-122">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="927ef-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="927ef-123">确定是否信任包的源。</span><span class="sxs-lookup"><span data-stu-id="927ef-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="927ef-124">其中之一：、。"不受信任"，"受信任"。</span><span class="sxs-lookup"><span data-stu-id="927ef-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="927ef-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="927ef-125">SourceCredential</span></span>| <span data-ttu-id="927ef-126">提供远程源上程序包的访问权限。</span><span class="sxs-lookup"><span data-stu-id="927ef-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="927ef-127">示例</span><span class="sxs-lookup"><span data-stu-id="927ef-127">Example</span></span>

<span data-ttu-id="927ef-128">此示例使用 PackageManagementSource DSC 资源注册 http://nuget.org 包源。</span><span class="sxs-lookup"><span data-stu-id="927ef-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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
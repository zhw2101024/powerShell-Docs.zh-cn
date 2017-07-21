---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC PackageManagement 资源"
ms.openlocfilehash: a984fbf5db561a696d89b60dde8b92096c6e4924
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="43fb2-103">DSC PackageManagement 资源</span><span class="sxs-lookup"><span data-stu-id="43fb2-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="43fb2-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="43fb2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="43fb2-105">Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagement** 资源提供了一种在目标节点上安装或卸载程序包管理包的机制。</span><span class="sxs-lookup"><span data-stu-id="43fb2-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="43fb2-106">此资源需要 http://PowerShellGallery.com 中的 **PackageManagement** 模块。</span><span class="sxs-lookup"><span data-stu-id="43fb2-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="43fb2-107">语法</span><span class="sxs-lookup"><span data-stu-id="43fb2-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="43fb2-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="43fb2-108">Properties</span></span>
|  <span data-ttu-id="43fb2-109">属性</span><span class="sxs-lookup"><span data-stu-id="43fb2-109">Property</span></span>  |  <span data-ttu-id="43fb2-110">说明</span><span class="sxs-lookup"><span data-stu-id="43fb2-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="43fb2-111">名称</span><span class="sxs-lookup"><span data-stu-id="43fb2-111">Name</span></span>| <span data-ttu-id="43fb2-112">指定要安装或卸载的包名称。</span><span class="sxs-lookup"><span data-stu-id="43fb2-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="43fb2-113">源</span><span class="sxs-lookup"><span data-stu-id="43fb2-113">Source</span></span>| <span data-ttu-id="43fb2-114">指定可以在其中找到包的包源名称。</span><span class="sxs-lookup"><span data-stu-id="43fb2-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="43fb2-115">这可以是 URI，也可以是使用 Register-PackageSource 或 PackageManagementSource DSC 资源注册的源。</span><span class="sxs-lookup"><span data-stu-id="43fb2-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="43fb2-116">也可以使用 DSC 资源 MSFT_PackageManagementSource 注册包源。</span><span class="sxs-lookup"><span data-stu-id="43fb2-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="43fb2-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="43fb2-117">Ensure</span></span>| <span data-ttu-id="43fb2-118">确定是要安装还是要卸载包。</span><span class="sxs-lookup"><span data-stu-id="43fb2-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="43fb2-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="43fb2-119">RequiredVersion</span></span>| <span data-ttu-id="43fb2-120">指定要安装的包的确切版本。</span><span class="sxs-lookup"><span data-stu-id="43fb2-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="43fb2-121">如果不指定这个参数，此 DSC 资源将安装包的最新版本，同时符合 MaximumVersion 参数指定的任何最高版本要求。</span><span class="sxs-lookup"><span data-stu-id="43fb2-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="43fb2-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="43fb2-122">MinimumVersion</span></span>| <span data-ttu-id="43fb2-123">指定要安装的包的最低允许版本。</span><span class="sxs-lookup"><span data-stu-id="43fb2-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="43fb2-124">如果不添加这个参数，此 DSC 资源将安装包的最高版本，同时符合 MaximumVersion 参数指定的任何最高版本要求。</span><span class="sxs-lookup"><span data-stu-id="43fb2-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="43fb2-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="43fb2-125">MaximumVersion</span></span>| <span data-ttu-id="43fb2-126">指定要安装的包的最高允许版本。</span><span class="sxs-lookup"><span data-stu-id="43fb2-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="43fb2-127">如果不指定这个参数，此 DSC 资源将安装包的最高版本。</span><span class="sxs-lookup"><span data-stu-id="43fb2-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="43fb2-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="43fb2-128">SourceCredential</span></span> | <span data-ttu-id="43fb2-129">为指定的包提供程序或源指定有权安装包的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="43fb2-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="43fb2-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="43fb2-130">ProviderName</span></span>| <span data-ttu-id="43fb2-131">指定将用作包搜索限定范围的包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="43fb2-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="43fb2-132">可通过运行 Get-PackageProvider cmdlet 获取包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="43fb2-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="43fb2-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="43fb2-133">AdditionalParameters</span></span>| <span data-ttu-id="43fb2-134">以哈希表的形式传递的提供程序特定参数。</span><span class="sxs-lookup"><span data-stu-id="43fb2-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="43fb2-135">例如，对于 NuGet 提供程序，可以传递 DestinationPath 等附加参数。</span><span class="sxs-lookup"><span data-stu-id="43fb2-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="43fb2-136">附加参数</span><span class="sxs-lookup"><span data-stu-id="43fb2-136">Additional Parameters</span></span>
<span data-ttu-id="43fb2-137">下表列出了 AdditionalParameters 属性的选项。</span><span class="sxs-lookup"><span data-stu-id="43fb2-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="43fb2-138">参数</span><span class="sxs-lookup"><span data-stu-id="43fb2-138">Parameter</span></span>  | <span data-ttu-id="43fb2-139">说明</span><span class="sxs-lookup"><span data-stu-id="43fb2-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="43fb2-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="43fb2-140">DestinationPath</span></span>| <span data-ttu-id="43fb2-141">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="43fb2-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="43fb2-142">指定要在其中安装包的文件位置。</span><span class="sxs-lookup"><span data-stu-id="43fb2-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="43fb2-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="43fb2-143">InstallationPolicy</span></span>| <span data-ttu-id="43fb2-144">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="43fb2-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="43fb2-145">确定是否信任包的源。</span><span class="sxs-lookup"><span data-stu-id="43fb2-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="43fb2-146">可取值为“Untrusted”或“Trusted”。</span><span class="sxs-lookup"><span data-stu-id="43fb2-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="43fb2-147">示例</span><span class="sxs-lookup"><span data-stu-id="43fb2-147">Example</span></span>

<span data-ttu-id="43fb2-148">此示例使用 **PackageManagement** DSC 资源安装 **JQuery** NuGet 包和 **GistProvider** PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="43fb2-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="43fb2-149">此示例先确保已指定相应的包源，然后定义 **JQuery** 和 **GistProvider** 包的预期状态（分别为 NuGet 和 PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="43fb2-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```


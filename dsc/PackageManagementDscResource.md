---
ms.date: 06/20/2018
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagement 资源
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268086"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="8343d-103">DSC PackageManagement 资源</span><span class="sxs-lookup"><span data-stu-id="8343d-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="8343d-104">适用于：Windows PowerShell 4.0、Windows PowerShell 5.0 和 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8343d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="8343d-105">Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagement** 资源提供了一种在目标节点上安装或卸载程序包管理包的机制。</span><span class="sxs-lookup"><span data-stu-id="8343d-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="8343d-106">此资源需要 [http://PowerShellGallery.com](http://PowerShellGallery.com) 中的 PackageManagement 模块。</span><span class="sxs-lookup"><span data-stu-id="8343d-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8343d-107">PackageManagement 模块应至少为版本 1.1.7.0，以下属性信息才正确。</span><span class="sxs-lookup"><span data-stu-id="8343d-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="8343d-108">语法</span><span class="sxs-lookup"><span data-stu-id="8343d-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="8343d-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="8343d-109">Properties</span></span>

| <span data-ttu-id="8343d-110">属性</span><span class="sxs-lookup"><span data-stu-id="8343d-110">Property</span></span> | <span data-ttu-id="8343d-111">说明</span><span class="sxs-lookup"><span data-stu-id="8343d-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8343d-112">名称</span><span class="sxs-lookup"><span data-stu-id="8343d-112">Name</span></span>| <span data-ttu-id="8343d-113">指定要安装或卸载的包名称。</span><span class="sxs-lookup"><span data-stu-id="8343d-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="8343d-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="8343d-114">AdditionalParameters</span></span>| <span data-ttu-id="8343d-115">传递给 `Get-Package -AdditionalArguments` 的参数的提供程序特定哈希表。</span><span class="sxs-lookup"><span data-stu-id="8343d-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="8343d-116">例如，对于 NuGet 提供程序，可以传递 DestinationPath 等附加参数。</span><span class="sxs-lookup"><span data-stu-id="8343d-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="8343d-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="8343d-117">Ensure</span></span>| <span data-ttu-id="8343d-118">确定是要安装还是要卸载包。</span><span class="sxs-lookup"><span data-stu-id="8343d-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="8343d-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="8343d-119">MaximumVersion</span></span>|<span data-ttu-id="8343d-120">指定要查找的包的允许的最高版本。</span><span class="sxs-lookup"><span data-stu-id="8343d-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="8343d-121">如果不添加此参数，资源便会查找最高版本的包。</span><span class="sxs-lookup"><span data-stu-id="8343d-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="8343d-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="8343d-122">MinimumVersion</span></span>|<span data-ttu-id="8343d-123">指定要查找的包的允许的最低版本。</span><span class="sxs-lookup"><span data-stu-id="8343d-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="8343d-124">如果不添加此参数，资源便会查找最高版本的包，同时也是 MaximumVersion 参数指定的最高版本。</span><span class="sxs-lookup"><span data-stu-id="8343d-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="8343d-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="8343d-125">ProviderName</span></span>| <span data-ttu-id="8343d-126">指定将用作包搜索限定范围的包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="8343d-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="8343d-127">可运行 `Get-PackageProvider` cmdlet 来获取包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="8343d-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="8343d-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="8343d-128">RequiredVersion</span></span>| <span data-ttu-id="8343d-129">指定要安装的包的确切版本。</span><span class="sxs-lookup"><span data-stu-id="8343d-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="8343d-130">如果不指定此参数，这个 DSC 资源便会安装最新版本的包，同时也是 MaximumVersion 参数指定的最高版本。</span><span class="sxs-lookup"><span data-stu-id="8343d-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="8343d-131">源</span><span class="sxs-lookup"><span data-stu-id="8343d-131">Source</span></span>| <span data-ttu-id="8343d-132">指定可以在其中找到包的包源名称。</span><span class="sxs-lookup"><span data-stu-id="8343d-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="8343d-133">这可以是 URI，也可以是向 `Register-PackageSource` 或 PackageManagementSource DSC 资源注册的源。</span><span class="sxs-lookup"><span data-stu-id="8343d-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="8343d-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="8343d-134">SourceCredential</span></span> | <span data-ttu-id="8343d-135">为指定的包提供程序或源指定有权安装包的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8343d-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="8343d-136">附加参数</span><span class="sxs-lookup"><span data-stu-id="8343d-136">Additional Parameters</span></span>

<span data-ttu-id="8343d-137">下表列出了 AdditionalParameters 属性的选项。</span><span class="sxs-lookup"><span data-stu-id="8343d-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="8343d-138">参数</span><span class="sxs-lookup"><span data-stu-id="8343d-138">Parameter</span></span> | <span data-ttu-id="8343d-139">说明</span><span class="sxs-lookup"><span data-stu-id="8343d-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8343d-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="8343d-140">DestinationPath</span></span>| <span data-ttu-id="8343d-141">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="8343d-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="8343d-142">指定要在其中安装包的文件位置。</span><span class="sxs-lookup"><span data-stu-id="8343d-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="8343d-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="8343d-143">InstallationPolicy</span></span>| <span data-ttu-id="8343d-144">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="8343d-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="8343d-145">确定是否信任包的源。</span><span class="sxs-lookup"><span data-stu-id="8343d-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="8343d-146">其中之一：`Untrusted`、`Trusted`。</span><span class="sxs-lookup"><span data-stu-id="8343d-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="8343d-147">示例</span><span class="sxs-lookup"><span data-stu-id="8343d-147">Example</span></span>

<span data-ttu-id="8343d-148">此示例使用 **PackageManagement** DSC 资源安装 **JQuery** NuGet 包和 **GistProvider** PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="8343d-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="8343d-149">此示例先确保已指定相应的包源，然后定义 **JQuery** 和 **GistProvider** 包的预期状态（分别为 NuGet 和 PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="8343d-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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
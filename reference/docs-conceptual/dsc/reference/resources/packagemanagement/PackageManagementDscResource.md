---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagement 资源
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953234"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="6412e-103">DSC PackageManagement 资源</span><span class="sxs-lookup"><span data-stu-id="6412e-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="6412e-104">适用于：Windows PowerShell 4.0、Windows PowerShell 5.0 和 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="6412e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="6412e-105">Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagement** 资源提供了一种在目标节点上安装或卸载程序包管理包的机制。</span><span class="sxs-lookup"><span data-stu-id="6412e-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="6412e-106">此资源需要 [http://PowerShellGallery.com](https://PowerShellGallery.com) 中的 PackageManagement  模块。</span><span class="sxs-lookup"><span data-stu-id="6412e-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6412e-107">PackageManagement  模块应至少为版本 1.1.7.0，以下属性信息才正确。</span><span class="sxs-lookup"><span data-stu-id="6412e-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="6412e-108">语法</span><span class="sxs-lookup"><span data-stu-id="6412e-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="6412e-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="6412e-109">Properties</span></span>

|<span data-ttu-id="6412e-110">属性</span><span class="sxs-lookup"><span data-stu-id="6412e-110">Property</span></span> |<span data-ttu-id="6412e-111">说明</span><span class="sxs-lookup"><span data-stu-id="6412e-111">Description</span></span> |
|---|---|
|<span data-ttu-id="6412e-112">名称</span><span class="sxs-lookup"><span data-stu-id="6412e-112">Name</span></span> |<span data-ttu-id="6412e-113">指定要安装或卸载的包名称。</span><span class="sxs-lookup"><span data-stu-id="6412e-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="6412e-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="6412e-114">AdditionalParameters</span></span> |<span data-ttu-id="6412e-115">传递给 `Get-Package -AdditionalArguments` 的参数的提供程序特定哈希表。</span><span class="sxs-lookup"><span data-stu-id="6412e-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="6412e-116">例如，对于 NuGet 提供程序，可以传递 DestinationPath 等附加参数。</span><span class="sxs-lookup"><span data-stu-id="6412e-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="6412e-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6412e-117">MaximumVersion</span></span> |<span data-ttu-id="6412e-118">指定要查找的包的允许的最高版本。</span><span class="sxs-lookup"><span data-stu-id="6412e-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="6412e-119">如果不添加此参数，资源便会查找最高版本的包。</span><span class="sxs-lookup"><span data-stu-id="6412e-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="6412e-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6412e-120">MinimumVersion</span></span> |<span data-ttu-id="6412e-121">指定要查找的包的允许的最低版本。</span><span class="sxs-lookup"><span data-stu-id="6412e-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="6412e-122">如果不添加此参数，资源便会查找最高版本的包，同时也是 MaximumVersion  参数指定的最高版本。</span><span class="sxs-lookup"><span data-stu-id="6412e-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="6412e-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="6412e-123">ProviderName</span></span> |<span data-ttu-id="6412e-124">指定将用作包搜索限定范围的包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="6412e-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="6412e-125">可运行 `Get-PackageProvider` cmdlet 来获取包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="6412e-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="6412e-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6412e-126">RequiredVersion</span></span> |<span data-ttu-id="6412e-127">指定要安装的包的确切版本。</span><span class="sxs-lookup"><span data-stu-id="6412e-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="6412e-128">如果不指定此参数，这个 DSC 资源便会安装最新版本的包，同时也是 MaximumVersion  参数指定的最高版本。</span><span class="sxs-lookup"><span data-stu-id="6412e-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="6412e-129">源</span><span class="sxs-lookup"><span data-stu-id="6412e-129">Source</span></span> |<span data-ttu-id="6412e-130">指定可以在其中找到包的包源名称。</span><span class="sxs-lookup"><span data-stu-id="6412e-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="6412e-131">这可以是 URI，也可以是向 `Register-PackageSource` 或 PackageManagementSource DSC 资源注册的源。</span><span class="sxs-lookup"><span data-stu-id="6412e-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="6412e-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="6412e-132">SourceCredential</span></span> |<span data-ttu-id="6412e-133">为指定的包提供程序或源指定有权安装包的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="6412e-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="6412e-134">附加参数</span><span class="sxs-lookup"><span data-stu-id="6412e-134">Additional Parameters</span></span>

<span data-ttu-id="6412e-135">下表列出了 AdditionalParameters 属性的选项。</span><span class="sxs-lookup"><span data-stu-id="6412e-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="6412e-136">参数</span><span class="sxs-lookup"><span data-stu-id="6412e-136">Parameter</span></span> |<span data-ttu-id="6412e-137">说明</span><span class="sxs-lookup"><span data-stu-id="6412e-137">Description</span></span> |
|---|---|
|<span data-ttu-id="6412e-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="6412e-138">DestinationPath</span></span> |<span data-ttu-id="6412e-139">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6412e-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="6412e-140">指定要在其中安装包的文件位置。</span><span class="sxs-lookup"><span data-stu-id="6412e-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="6412e-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="6412e-141">InstallationPolicy</span></span> |<span data-ttu-id="6412e-142">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6412e-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="6412e-143">确定是否信任包的源。</span><span class="sxs-lookup"><span data-stu-id="6412e-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="6412e-144">可取值为：**Untrusted** 或 **Trusted**。</span><span class="sxs-lookup"><span data-stu-id="6412e-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6412e-145">公共属性</span><span class="sxs-lookup"><span data-stu-id="6412e-145">Common properties</span></span>

|<span data-ttu-id="6412e-146">属性</span><span class="sxs-lookup"><span data-stu-id="6412e-146">Property</span></span> |<span data-ttu-id="6412e-147">说明</span><span class="sxs-lookup"><span data-stu-id="6412e-147">Description</span></span> |
|---|---|
|<span data-ttu-id="6412e-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6412e-148">DependsOn</span></span> |<span data-ttu-id="6412e-149">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="6412e-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6412e-150">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="6412e-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6412e-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="6412e-151">Ensure</span></span> |<span data-ttu-id="6412e-152">确定是要安装还是要卸载包。</span><span class="sxs-lookup"><span data-stu-id="6412e-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="6412e-153">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="6412e-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="6412e-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6412e-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="6412e-155">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="6412e-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="6412e-156">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="6412e-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="6412e-157">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="6412e-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="6412e-158">示例</span><span class="sxs-lookup"><span data-stu-id="6412e-158">Example</span></span>

<span data-ttu-id="6412e-159">此示例使用 **PackageManagement** DSC 资源安装 **JQuery** NuGet 包和 **GistProvider** PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="6412e-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="6412e-160">此示例先确保已指定相应的包源，然后定义 **JQuery** 和 **GistProvider** 包的预期状态（分别为 NuGet 和 PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="6412e-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
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
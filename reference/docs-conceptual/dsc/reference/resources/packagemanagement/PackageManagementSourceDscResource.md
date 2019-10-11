---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagementSource 资源
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954784"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="7e87a-103">DSC PackageManagementSource 资源</span><span class="sxs-lookup"><span data-stu-id="7e87a-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="7e87a-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7e87a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="7e87a-105">Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。</span><span class="sxs-lookup"><span data-stu-id="7e87a-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="7e87a-106">**以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="7e87a-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="7e87a-107">此资源需要 [PowerShell 库](https://PowerShellGallery.com)中的 **PackageManagement** 模块。</span><span class="sxs-lookup"><span data-stu-id="7e87a-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e87a-108">PackageManagement  模块应至少为版本 1.1.7.0，以下属性信息才正确。</span><span class="sxs-lookup"><span data-stu-id="7e87a-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e87a-109">语法</span><span class="sxs-lookup"><span data-stu-id="7e87a-109">Syntax</span></span>

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7e87a-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="7e87a-110">Properties</span></span>

|<span data-ttu-id="7e87a-111">属性</span><span class="sxs-lookup"><span data-stu-id="7e87a-111">Property</span></span> |<span data-ttu-id="7e87a-112">说明</span><span class="sxs-lookup"><span data-stu-id="7e87a-112">Description</span></span> |
|---|---|
|<span data-ttu-id="7e87a-113">名称</span><span class="sxs-lookup"><span data-stu-id="7e87a-113">Name</span></span> |<span data-ttu-id="7e87a-114">指定要在系统上注册或取消注册的包源名称。</span><span class="sxs-lookup"><span data-stu-id="7e87a-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="7e87a-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="7e87a-115">ProviderName</span></span> |<span data-ttu-id="7e87a-116">指定 OneGet 提供程序的名称，借此可以与包源进行互操作。</span><span class="sxs-lookup"><span data-stu-id="7e87a-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="7e87a-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="7e87a-117">SourceLocation</span></span> |<span data-ttu-id="7e87a-118">指定包源的 URI。</span><span class="sxs-lookup"><span data-stu-id="7e87a-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="7e87a-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="7e87a-119">InstallationPolicy</span></span> |<span data-ttu-id="7e87a-120">供提供程序使用，如内置的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="7e87a-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="7e87a-121">确定是否信任包的源。</span><span class="sxs-lookup"><span data-stu-id="7e87a-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="7e87a-122">可取值为：**Untrusted** 或 **Trusted**。</span><span class="sxs-lookup"><span data-stu-id="7e87a-122">One of: **Untrusted** or **Trusted**.</span></span> |
|<span data-ttu-id="7e87a-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="7e87a-123">SourceCredential</span></span> |<span data-ttu-id="7e87a-124">提供远程源上程序包的访问权限。</span><span class="sxs-lookup"><span data-stu-id="7e87a-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7e87a-125">公共属性</span><span class="sxs-lookup"><span data-stu-id="7e87a-125">Common properties</span></span>

|<span data-ttu-id="7e87a-126">属性</span><span class="sxs-lookup"><span data-stu-id="7e87a-126">Property</span></span> |<span data-ttu-id="7e87a-127">说明</span><span class="sxs-lookup"><span data-stu-id="7e87a-127">Description</span></span> |
|---|---|
|<span data-ttu-id="7e87a-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7e87a-128">DependsOn</span></span> |<span data-ttu-id="7e87a-129">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="7e87a-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7e87a-130">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7e87a-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7e87a-131">Ensure</span><span class="sxs-lookup"><span data-stu-id="7e87a-131">Ensure</span></span> |<span data-ttu-id="7e87a-132">确定是要注册还是要取消注册包源。</span><span class="sxs-lookup"><span data-stu-id="7e87a-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="7e87a-133">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="7e87a-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="7e87a-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7e87a-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="7e87a-135">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="7e87a-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7e87a-136">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="7e87a-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7e87a-137">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="7e87a-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="7e87a-138">示例</span><span class="sxs-lookup"><span data-stu-id="7e87a-138">Example</span></span>

<span data-ttu-id="7e87a-139">此示例使用 PackageManagementSource  DSC 资源注册 `https://nuget.org` 包源。</span><span class="sxs-lookup"><span data-stu-id="7e87a-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsFeatureSet 资源
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952954"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="4de53-103">DSC WindowsFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="4de53-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="4de53-104">适用于：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="4de53-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="4de53-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsFeatureSet** 资源提供了确保在目标节点上添加或删除角色和功能的机制。</span><span class="sxs-lookup"><span data-stu-id="4de53-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="4de53-106">此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 **Name** 属性中指定的每个功能调用 [WindowsFeature 资源](windowsfeatureResource.md)。</span><span class="sxs-lookup"><span data-stu-id="4de53-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="4de53-107">要将一些 Windows 功能配置为相同状态时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="4de53-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="4de53-108">语法</span><span class="sxs-lookup"><span data-stu-id="4de53-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="4de53-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="4de53-109">Properties</span></span>

|  <span data-ttu-id="4de53-110">属性</span><span class="sxs-lookup"><span data-stu-id="4de53-110">Property</span></span>  |  <span data-ttu-id="4de53-111">说明</span><span class="sxs-lookup"><span data-stu-id="4de53-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="4de53-112">名称</span><span class="sxs-lookup"><span data-stu-id="4de53-112">Name</span></span> |<span data-ttu-id="4de53-113">要确保添加或删除的角色或功能的名称。</span><span class="sxs-lookup"><span data-stu-id="4de53-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="4de53-114">这与 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet 的 **Name** 属性相同，并非角色或功能的显示名称。</span><span class="sxs-lookup"><span data-stu-id="4de53-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="4de53-115">源</span><span class="sxs-lookup"><span data-stu-id="4de53-115">Source</span></span> |<span data-ttu-id="4de53-116">指示要用于安装的源文件的位置（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="4de53-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="4de53-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="4de53-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="4de53-118">将此属性设置为 `$true` 可包括通过 **Name** 属性指定的功能的所有必需子功能。</span><span class="sxs-lookup"><span data-stu-id="4de53-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="4de53-119">凭据</span><span class="sxs-lookup"><span data-stu-id="4de53-119">Credential</span></span> |<span data-ttu-id="4de53-120">要用于添加或删除角色或功能的凭据。</span><span class="sxs-lookup"><span data-stu-id="4de53-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="4de53-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="4de53-121">LogPath</span></span> |<span data-ttu-id="4de53-122">希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="4de53-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4de53-123">公共属性</span><span class="sxs-lookup"><span data-stu-id="4de53-123">Common properties</span></span>

|<span data-ttu-id="4de53-124">属性</span><span class="sxs-lookup"><span data-stu-id="4de53-124">Property</span></span> |<span data-ttu-id="4de53-125">说明</span><span class="sxs-lookup"><span data-stu-id="4de53-125">Description</span></span> |
|---|---|
|<span data-ttu-id="4de53-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4de53-126">DependsOn</span></span> |<span data-ttu-id="4de53-127">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="4de53-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4de53-128">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="4de53-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4de53-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="4de53-129">Ensure</span></span> |<span data-ttu-id="4de53-130">指示是否添加角色或功能。</span><span class="sxs-lookup"><span data-stu-id="4de53-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="4de53-131">若要确保添加角色或功能，请将此属性设置为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="4de53-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="4de53-132">若要确保删除角色或功能，请将此属性设置为 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="4de53-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="4de53-133">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="4de53-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="4de53-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4de53-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="4de53-135">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="4de53-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4de53-136">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="4de53-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4de53-137">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="4de53-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="4de53-138">示例</span><span class="sxs-lookup"><span data-stu-id="4de53-138">Example</span></span>

<span data-ttu-id="4de53-139">以下配置可确保安装 **Web 服务器** (IIS) 和 **SMTP 服务器**功能，以及各自的所有子功能。</span><span class="sxs-lookup"><span data-stu-id="4de53-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
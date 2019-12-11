---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsFeature 资源。
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954624"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="23c05-103">DSC WindowsFeature 资源。</span><span class="sxs-lookup"><span data-stu-id="23c05-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="23c05-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="23c05-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="23c05-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsFeature** 资源提供了在目标节点上添加或删除角色和功能的机制。</span><span class="sxs-lookup"><span data-stu-id="23c05-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="23c05-106">语法</span><span class="sxs-lookup"><span data-stu-id="23c05-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="23c05-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="23c05-107">Properties</span></span>

|<span data-ttu-id="23c05-108">属性</span><span class="sxs-lookup"><span data-stu-id="23c05-108">Property</span></span> |<span data-ttu-id="23c05-109">说明</span><span class="sxs-lookup"><span data-stu-id="23c05-109">Description</span></span> |
|---|---|
|<span data-ttu-id="23c05-110">名称</span><span class="sxs-lookup"><span data-stu-id="23c05-110">Name</span></span> |<span data-ttu-id="23c05-111">指示想确保添加或删除的角色或功能的名称。</span><span class="sxs-lookup"><span data-stu-id="23c05-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="23c05-112">此参数与来自 [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet 的 **Name** 属性一样，并非该角色或功能的显示名称。</span><span class="sxs-lookup"><span data-stu-id="23c05-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="23c05-113">凭据</span><span class="sxs-lookup"><span data-stu-id="23c05-113">Credential</span></span> |<span data-ttu-id="23c05-114">指示要用于添加或删除角色或功能的凭据。</span><span class="sxs-lookup"><span data-stu-id="23c05-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="23c05-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="23c05-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="23c05-116">将此属性设置为 `$true` 以确保所有必需的子功能的状态为通过 **Name** 属性指定的功能的状态。</span><span class="sxs-lookup"><span data-stu-id="23c05-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="23c05-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="23c05-117">LogPath</span></span> |<span data-ttu-id="23c05-118">指示你希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="23c05-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="23c05-119">源</span><span class="sxs-lookup"><span data-stu-id="23c05-119">Source</span></span> |<span data-ttu-id="23c05-120">指示要用于安装的源文件的位置（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="23c05-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="23c05-121">公共属性</span><span class="sxs-lookup"><span data-stu-id="23c05-121">Common properties</span></span>

|<span data-ttu-id="23c05-122">属性</span><span class="sxs-lookup"><span data-stu-id="23c05-122">Property</span></span> |<span data-ttu-id="23c05-123">说明</span><span class="sxs-lookup"><span data-stu-id="23c05-123">Description</span></span> |
|---|---|
|<span data-ttu-id="23c05-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="23c05-124">DependsOn</span></span> |<span data-ttu-id="23c05-125">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="23c05-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="23c05-126">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="23c05-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="23c05-127">Ensure</span><span class="sxs-lookup"><span data-stu-id="23c05-127">Ensure</span></span> |<span data-ttu-id="23c05-128">指示是否已添加角色或功能。</span><span class="sxs-lookup"><span data-stu-id="23c05-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="23c05-129">若要确保添加角色或功能，请将此属性设置为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="23c05-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="23c05-130">若要确保删除角色或功能，请将此属性设置为 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="23c05-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="23c05-131">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="23c05-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="23c05-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="23c05-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="23c05-133">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="23c05-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="23c05-134">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="23c05-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="23c05-135">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="23c05-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="23c05-136">示例</span><span class="sxs-lookup"><span data-stu-id="23c05-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WindowsFeature 资源。"
ms.openlocfilehash: b4f50cb9ee172600b1811175e9cf67f6a7ed2d55
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2017
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="afd32-103">DSC WindowsFeature 资源。</span><span class="sxs-lookup"><span data-stu-id="afd32-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="afd32-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="afd32-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="afd32-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsFeature** 资源提供了在目标节点上添加或删除角色和功能的机制。</span><span class="sxs-lookup"><span data-stu-id="afd32-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="afd32-106">语法</span><span class="sxs-lookup"><span data-stu-id="afd32-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="afd32-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="afd32-107">Properties</span></span>

|  <span data-ttu-id="afd32-108">属性</span><span class="sxs-lookup"><span data-stu-id="afd32-108">Property</span></span>  |  <span data-ttu-id="afd32-109">说明</span><span class="sxs-lookup"><span data-stu-id="afd32-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="afd32-110">名称</span><span class="sxs-lookup"><span data-stu-id="afd32-110">Name</span></span>| <span data-ttu-id="afd32-111">指示想确保添加或删除的角色或功能的名称。</span><span class="sxs-lookup"><span data-stu-id="afd32-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="afd32-112">此参数与来自 [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet 的 __Name__ 属性一样，并非该角色或功能的显示名称。</span><span class="sxs-lookup"><span data-stu-id="afd32-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>| 
| <span data-ttu-id="afd32-113">凭据</span><span class="sxs-lookup"><span data-stu-id="afd32-113">Credential</span></span>| <span data-ttu-id="afd32-114">指示要用于添加或删除角色或功能的凭据。</span><span class="sxs-lookup"><span data-stu-id="afd32-114">Indicates the credentials to use to add or remove the role or feature.</span></span>| 
| <span data-ttu-id="afd32-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="afd32-115">Ensure</span></span>| <span data-ttu-id="afd32-116">指示是否已添加角色或功能。</span><span class="sxs-lookup"><span data-stu-id="afd32-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="afd32-117">若要确保添加了角色或功能，请将此属性设置为“Present”。若要确保删除了角色或功能，请将此属性设为“Absent”。</span><span class="sxs-lookup"><span data-stu-id="afd32-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="afd32-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="afd32-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="afd32-119">将此属性设置为 __$true__ 以确保所有必需子功能的状态均为你通过 __Name__ 属性指定的功能的状态。</span><span class="sxs-lookup"><span data-stu-id="afd32-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>| 
| <span data-ttu-id="afd32-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="afd32-120">LogPath</span></span>| <span data-ttu-id="afd32-121">指示你希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="afd32-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="afd32-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="afd32-122">DependsOn</span></span>| <span data-ttu-id="afd32-123">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="afd32-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="afd32-124">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="afd32-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="afd32-125">源</span><span class="sxs-lookup"><span data-stu-id="afd32-125">Source</span></span>| <span data-ttu-id="afd32-126">指示要用于安装的源文件的位置（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="afd32-126">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="afd32-127">示例</span><span class="sxs-lookup"><span data-stu-id="afd32-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```


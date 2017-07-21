---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WindowsFeatureSet 资源"
ms.openlocfilehash: 3cdabc36ef35c2bf912ac54393fe40024a8e8bc0
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="b258b-103">DSC WindowsFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="b258b-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="b258b-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b258b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b258b-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsFeatureSet** 资源提供了确保在目标节点上添加或删除角色和功能的机制。</span><span class="sxs-lookup"><span data-stu-id="b258b-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="b258b-106">此资源是[复合资源](authoringResourceComposite.md)，它会针对 `Name` 属性中指定的每个功能调用 [WindowsFeature 资源](windowsfeatureResource.md)。</span><span class="sxs-lookup"><span data-stu-id="b258b-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="b258b-107">要将一些 Windows 功能配置为相同状态时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="b258b-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="b258b-108">语法</span><span class="sxs-lookup"><span data-stu-id="b258b-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]] 
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="b258b-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="b258b-109">Properties</span></span>

|  <span data-ttu-id="b258b-110">属性</span><span class="sxs-lookup"><span data-stu-id="b258b-110">Property</span></span>  |  <span data-ttu-id="b258b-111">说明</span><span class="sxs-lookup"><span data-stu-id="b258b-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="b258b-112">名称</span><span class="sxs-lookup"><span data-stu-id="b258b-112">Name</span></span>| <span data-ttu-id="b258b-113">要确保添加或删除的角色或功能的名称。</span><span class="sxs-lookup"><span data-stu-id="b258b-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="b258b-114">这与 [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet 的 **Name** 属性相同，并非角色或功能的显示名称。</span><span class="sxs-lookup"><span data-stu-id="b258b-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>| 
| <span data-ttu-id="b258b-115">凭据</span><span class="sxs-lookup"><span data-stu-id="b258b-115">Credential</span></span>| <span data-ttu-id="b258b-116">要用于添加或删除角色或功能的凭据。</span><span class="sxs-lookup"><span data-stu-id="b258b-116">The credentials to use to add or remove the roles or features.</span></span>| 
| <span data-ttu-id="b258b-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="b258b-117">Ensure</span></span>| <span data-ttu-id="b258b-118">指示是否添加角色或功能。</span><span class="sxs-lookup"><span data-stu-id="b258b-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="b258b-119">若要确保添加角色或功能，请将此属性设置为“Present”。若要确保删除角色或功能，请将此属性设为“Absent”。</span><span class="sxs-lookup"><span data-stu-id="b258b-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="b258b-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="b258b-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="b258b-121">将此属性设置为 **$true** 可包括通过 **Name** 属性指定的功能的所有所需子功能。</span><span class="sxs-lookup"><span data-stu-id="b258b-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>| 
| <span data-ttu-id="b258b-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="b258b-122">LogPath</span></span>| <span data-ttu-id="b258b-123">希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="b258b-123">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="b258b-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b258b-124">DependsOn</span></span>| <span data-ttu-id="b258b-125">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="b258b-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b258b-126">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="b258b-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="b258b-127">源</span><span class="sxs-lookup"><span data-stu-id="b258b-127">Source</span></span>| <span data-ttu-id="b258b-128">指示要用于安装的源文件的位置（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="b258b-128">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="b258b-129">示例</span><span class="sxs-lookup"><span data-stu-id="b258b-129">Example</span></span>

<span data-ttu-id="b258b-130">以下配置可确保安装 **Web 服务器** (IIS) 和 **SMTP 服务器**功能，以及各自的所有子功能。</span><span class="sxs-lookup"><span data-stu-id="b258b-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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


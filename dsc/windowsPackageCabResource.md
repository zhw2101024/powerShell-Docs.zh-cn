---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC WindowsPackageCab 资源"
ms.openlocfilehash: 1d7c8d9bf45d2eda8734daa8877315d219662c75
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="9eb91-103">DSC WindowsPackageCab 资源</span><span class="sxs-lookup"><span data-stu-id="9eb91-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="9eb91-104">适用于：Windows PowerShell 5.1 及更高版本</span><span class="sxs-lookup"><span data-stu-id="9eb91-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="9eb91-105">Windows PowerShell Desired State Configuration (DSC) 中的 WindowsPackageCab 资源提供了一种机制，用于在目标节点上安装或卸载 Windows Cabinet (.cab) 程序包。</span><span class="sxs-lookup"><span data-stu-id="9eb91-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="9eb91-106">目标节点必须已安装 DISM PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="9eb91-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="9eb91-107">有关信息，请参阅[在 Windows PowerShell 中使用 DISM](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14)。</span><span class="sxs-lookup"><span data-stu-id="9eb91-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span> 


## <a name="syntax"></a><span data-ttu-id="9eb91-108">语法</span><span class="sxs-lookup"><span data-stu-id="9eb91-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="9eb91-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="9eb91-109">Properties</span></span>

|  <span data-ttu-id="9eb91-110">属性</span><span class="sxs-lookup"><span data-stu-id="9eb91-110">Property</span></span>  |  <span data-ttu-id="9eb91-111">说明</span><span class="sxs-lookup"><span data-stu-id="9eb91-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="9eb91-112">名称</span><span class="sxs-lookup"><span data-stu-id="9eb91-112">Name</span></span>| <span data-ttu-id="9eb91-113">指明要确保其处于特定状态的程序包的名称。</span><span class="sxs-lookup"><span data-stu-id="9eb91-113">Indicates the name of the package for you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="9eb91-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="9eb91-114">Ensure</span></span>| <span data-ttu-id="9eb91-115">指示程序包是否已安装。</span><span class="sxs-lookup"><span data-stu-id="9eb91-115">Indicates if the package is installed.</span></span> <span data-ttu-id="9eb91-116">将此属性设置为“Absent”以确保未安装程序包（如果已安装则卸载程序包）。</span><span class="sxs-lookup"><span data-stu-id="9eb91-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="9eb91-117">将其设置为“Present”（默认值）以确保已安装程序包。</span><span class="sxs-lookup"><span data-stu-id="9eb91-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="9eb91-118">路径</span><span class="sxs-lookup"><span data-stu-id="9eb91-118">Path</span></span>| <span data-ttu-id="9eb91-119">指示程序包所在的路径。</span><span class="sxs-lookup"><span data-stu-id="9eb91-119">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="9eb91-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="9eb91-120">LogPath</span></span>| <span data-ttu-id="9eb91-121">指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="9eb91-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="9eb91-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9eb91-122">DependsOn</span></span> | <span data-ttu-id="9eb91-123">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="9eb91-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9eb91-124">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 \`DependsOn = "[ResourceType]ResourceName"\`\`。</span><span class="sxs-lookup"><span data-stu-id="9eb91-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>| 

## <a name="example"></a><span data-ttu-id="9eb91-125">示例</span><span class="sxs-lookup"><span data-stu-id="9eb91-125">Example</span></span>

<span data-ttu-id="9eb91-126">下面的示例配置需要使用输入参数，并确保安装了 `$Name` 参数指定的.cab 文件。</span><span class="sxs-lookup"><span data-stu-id="9eb91-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```


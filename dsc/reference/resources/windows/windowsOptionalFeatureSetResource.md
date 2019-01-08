---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsOptionalFeatureSet 资源
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047150"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="1943b-103">DSC WindowsOptionalFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="1943b-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="1943b-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1943b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1943b-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsOptionalFeatureSet** 资源提供了确保在目标节点上启用可选功能的机制。</span><span class="sxs-lookup"><span data-stu-id="1943b-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="1943b-106">此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 `Name` 属性中指定的每个功能调用 [WindowsOptionalFeature 资源](windowsOptionalFeatureResource.md)。</span><span class="sxs-lookup"><span data-stu-id="1943b-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="1943b-107">要将一些 Windows 可选功能配置为相同状态时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="1943b-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="1943b-108">语法</span><span class="sxs-lookup"><span data-stu-id="1943b-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="1943b-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="1943b-109">Properties</span></span>

|  <span data-ttu-id="1943b-110">属性</span><span class="sxs-lookup"><span data-stu-id="1943b-110">Property</span></span>  |  <span data-ttu-id="1943b-111">说明</span><span class="sxs-lookup"><span data-stu-id="1943b-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="1943b-112">名称</span><span class="sxs-lookup"><span data-stu-id="1943b-112">Name</span></span>| <span data-ttu-id="1943b-113">指示要确保启用或禁用的功能的名称。</span><span class="sxs-lookup"><span data-stu-id="1943b-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="1943b-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="1943b-114">Ensure</span></span>| <span data-ttu-id="1943b-115">指定是否启用功能。</span><span class="sxs-lookup"><span data-stu-id="1943b-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="1943b-116">若要确保启用功能，请将此属性设置为“启用”。若要确保禁用功能，请将此属性设为“禁用”。</span><span class="sxs-lookup"><span data-stu-id="1943b-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="1943b-117">源</span><span class="sxs-lookup"><span data-stu-id="1943b-117">Source</span></span>| <span data-ttu-id="1943b-118">未实现。</span><span class="sxs-lookup"><span data-stu-id="1943b-118">Not implemented.</span></span>|
| <span data-ttu-id="1943b-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="1943b-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="1943b-120">指定 DISM 在搜索源文件以启用功能时是否联系 Windows 更新 (WU)。</span><span class="sxs-lookup"><span data-stu-id="1943b-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="1943b-121">如果为 $true，则 DISM 不联系 WU。</span><span class="sxs-lookup"><span data-stu-id="1943b-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="1943b-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="1943b-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="1943b-123">设置为 **$true** 可在功能禁用时（即，**Ensure** 设置为“Absent”时）删除与之关联的所有文件。</span><span class="sxs-lookup"><span data-stu-id="1943b-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="1943b-124">日志级别</span><span class="sxs-lookup"><span data-stu-id="1943b-124">LogLevel</span></span>| <span data-ttu-id="1943b-125">日志中显示的最大输出级别。</span><span class="sxs-lookup"><span data-stu-id="1943b-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="1943b-126">接受的值包括："ErrorsOnly"（只记录错误）、"ErrorsAndWarning"（错误和警告记录），和"ErrorsAndWarningAndInformation"（错误、 警告和调试信息记录）。</span><span class="sxs-lookup"><span data-stu-id="1943b-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="1943b-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="1943b-127">LogPath</span></span>| <span data-ttu-id="1943b-128">希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="1943b-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="1943b-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1943b-129">DependsOn</span></span>| <span data-ttu-id="1943b-130">指定必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="1943b-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1943b-131">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="1943b-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

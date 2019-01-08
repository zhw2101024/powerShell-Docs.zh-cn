---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsOptionalFeature 资源
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047169"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="f6493-103">DSC WindowsOptionalFeature 资源</span><span class="sxs-lookup"><span data-stu-id="f6493-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="f6493-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f6493-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f6493-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsOptionalFeature** 资源提供了确保在目标节点上启用可选功能的机制。</span><span class="sxs-lookup"><span data-stu-id="f6493-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6493-106">语法</span><span class="sxs-lookup"><span data-stu-id="f6493-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="f6493-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="f6493-107">Properties</span></span>

|  <span data-ttu-id="f6493-108">属性</span><span class="sxs-lookup"><span data-stu-id="f6493-108">Property</span></span>  |  <span data-ttu-id="f6493-109">说明</span><span class="sxs-lookup"><span data-stu-id="f6493-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="f6493-110">名称</span><span class="sxs-lookup"><span data-stu-id="f6493-110">Name</span></span>| <span data-ttu-id="f6493-111">指示要确保启用或禁用的功能的名称。</span><span class="sxs-lookup"><span data-stu-id="f6493-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="f6493-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="f6493-112">Ensure</span></span>| <span data-ttu-id="f6493-113">指定是否启用功能。</span><span class="sxs-lookup"><span data-stu-id="f6493-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="f6493-114">若要确保启用功能，请将此属性设置为“启用”。若要确保禁用功能，请将此属性设为“禁用”。</span><span class="sxs-lookup"><span data-stu-id="f6493-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="f6493-115">源</span><span class="sxs-lookup"><span data-stu-id="f6493-115">Source</span></span>| <span data-ttu-id="f6493-116">未实现。</span><span class="sxs-lookup"><span data-stu-id="f6493-116">Not implemented.</span></span>|
| <span data-ttu-id="f6493-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="f6493-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="f6493-118">指定 DISM 在搜索源文件以启用功能时是否联系 Windows 更新 (WU)。</span><span class="sxs-lookup"><span data-stu-id="f6493-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="f6493-119">如果为 $true，则 DISM 不联系 WU。</span><span class="sxs-lookup"><span data-stu-id="f6493-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="f6493-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="f6493-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="f6493-121">设置为 **$true** 可在功能禁用时（即，**Ensure** 设置为“Absent”时）删除与之关联的所有文件。</span><span class="sxs-lookup"><span data-stu-id="f6493-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="f6493-122">日志级别</span><span class="sxs-lookup"><span data-stu-id="f6493-122">LogLevel</span></span>| <span data-ttu-id="f6493-123">日志中显示的最大输出级别。</span><span class="sxs-lookup"><span data-stu-id="f6493-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="f6493-124">接受的值包括："ErrorsOnly"（只记录错误）、"ErrorsAndWarning"（错误和警告记录），和"ErrorsAndWarningAndInformation"（错误、 警告和调试信息记录）。</span><span class="sxs-lookup"><span data-stu-id="f6493-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="f6493-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="f6493-125">LogPath</span></span>| <span data-ttu-id="f6493-126">希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="f6493-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="f6493-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f6493-127">DependsOn</span></span>| <span data-ttu-id="f6493-128">指定必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="f6493-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f6493-129">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="f6493-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
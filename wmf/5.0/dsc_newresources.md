---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 64a00e041bbeeea117db43116b486e83dfe923b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085824"
---
# <a name="new-built-in-dsc-resources"></a><span data-ttu-id="067fd-102">新的内置 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="067fd-102">New built-in DSC resources</span></span>

<span data-ttu-id="067fd-103">WMF 5.0 RTM 具有 4 个新的 DSC 资源：</span><span class="sxs-lookup"><span data-stu-id="067fd-103">WMF 5.0 RTM has 4 new DSC resources:</span></span>
* <span data-ttu-id="067fd-104">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="067fd-104">WindowsFeatureSet</span></span>
* <span data-ttu-id="067fd-105">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="067fd-105">WindowsOptionalFeatureSet</span></span>
* <span data-ttu-id="067fd-106">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="067fd-106">ServiceSet</span></span>
* <span data-ttu-id="067fd-107">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="067fd-107">ProcessSet</span></span>

<span data-ttu-id="067fd-108">这些资源提供了一种使用单个资源调用配置多个实例的简便方法。</span><span class="sxs-lookup"><span data-stu-id="067fd-108">These resources provide an easy way to configure multiple instances using a single resource call.</span></span>

## <a name="windowsfeatureset"></a><span data-ttu-id="067fd-109">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="067fd-109">WindowsFeatureSet</span></span>

```powershell
# Get the syntax of WindowsFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsFeatureSet -Syntax

WindowsFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [Ensure = [String]]
    [Source = [String]]
    [IncludeAllSubFeature = [Boolean]]
    [Credential = [PSCredential]]
    [LogPath = [String]]
}
```

## <a name="windowsoptionalfeatureset"></a><span data-ttu-id="067fd-110">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="067fd-110">WindowsOptionalFeatureSet</span></span>

```powershell
# Get the syntax of WindowsOptionalFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsOptionalFeatureSet -Syntax

WindowsOptionalFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    Ensure = [String]
    [Source = [String[]]]
    [RemoveFilesOnDisable = [Boolean]]
    [LogPath = [String]]
    [NoWindowsUpdateCheck = [Boolean]]
    [LogLevel = [String]]
}
```

## <a name="serviceset"></a><span data-ttu-id="067fd-111">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="067fd-111">ServiceSet</span></span>

```powershell
# Get the syntax of ServiceSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ServiceSet -Syntax

ServiceSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [StartupType = [String]]
    [BuiltInAccount = [String]]
    [State = [String]]
    [Ensure = [String]]
    [Credential = [PSCredential]]
}
```

## <a name="processset"></a><span data-ttu-id="067fd-112">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="067fd-112">ProcessSet</span></span>

```powershell
# Get the syntax of ProcessSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ProcessSet -Syntax

ProcessSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Path = [String[]]
    [Credential = [PSCredential]]
    [Ensure = [String]]
    [StandardOutputPath = [String]]
    [StandardErrorPath = [String]]
    [StandardInputPath = [String]]
    [WorkingDirectory = [String]]
}
```

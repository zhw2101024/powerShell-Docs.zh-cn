---
ms.date: 06/12/2017
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: 具有兼容的 PowerShell 版本的脚本
ms.openlocfilehash: 386e65295641fb6932c13047246742531aeaec64
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093654"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="3e9b5-103">具有兼容的 PowerShell 版本的脚本</span><span class="sxs-lookup"><span data-stu-id="3e9b5-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="3e9b5-104">从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。</span><span class="sxs-lookup"><span data-stu-id="3e9b5-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="3e9b5-105">**桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="3e9b5-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="3e9b5-106">**核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。</span><span class="sxs-lookup"><span data-stu-id="3e9b5-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="3e9b5-107">正在运行的 PowerShell 版本显示在 $PSVersionTable.的 PSEdition 属性中。</span><span class="sxs-lookup"><span data-stu-id="3e9b5-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="3e9b5-108">脚本编写者可以防止执行脚本，除非它使用 #requires 语句的 PSEdition 参数在 PowerShell 的兼容版本上运行。</span><span class="sxs-lookup"><span data-stu-id="3e9b5-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a #requires statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="3e9b5-109">PowerShell 库用户可以查找特定 PowerShell 版本上受支持的脚本的列表。</span><span class="sxs-lookup"><span data-stu-id="3e9b5-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="3e9b5-110">不带 PSEdition_Desktop 和 PSEditon_Core 的脚本可以在 PowerShell Desktop 版本上运行。</span><span class="sxs-lookup"><span data-stu-id="3e9b5-110">Scripts without PSEdition_Desktop and PSEditon_Core are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core
```

## <a name="more-details"></a><span data-ttu-id="3e9b5-111">详细信息</span><span class="sxs-lookup"><span data-stu-id="3e9b5-111">More details</span></span>

- [<span data-ttu-id="3e9b5-112">PSEditions 模块</span><span class="sxs-lookup"><span data-stu-id="3e9b5-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="3e9b5-113">PowerShell 库的 PSEditions 支持</span><span class="sxs-lookup"><span data-stu-id="3e9b5-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)
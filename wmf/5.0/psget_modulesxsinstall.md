---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 69188738333a853a16e6ea68689ecba5dc632225
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="4a3e8-102">PowerShell 5.0 或更高版本上的并行版本支持</span><span class="sxs-lookup"><span data-stu-id="4a3e8-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="4a3e8-103">现在，在 Windows PowerShell 5.0 或更高版本运行的 Install-Module cmdlet、Update-Module cmdlet 和 Publish-Module cmdlet 中有了对并行 (SxS) 模块版本的支持。</span><span class="sxs-lookup"><span data-stu-id="4a3e8-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="4a3e8-104">此外，我们还将 -RequiredVersion 参数添加到了 Publish-Module cmdlet 中以指定要发布的版本。</span><span class="sxs-lookup"><span data-stu-id="4a3e8-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="4a3e8-105">Path 参数现在支持具有版本文件夹的模块基准路径。</span><span class="sxs-lookup"><span data-stu-id="4a3e8-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="4a3e8-106">**Install-Module 示例：**</span><span class="sxs-lookup"><span data-stu-id="4a3e8-106">**Install-Module examples:**</span></span>
```powershell
PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Type       Repository           Description            
-------    ----                                ----       ----------           -----------            
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```


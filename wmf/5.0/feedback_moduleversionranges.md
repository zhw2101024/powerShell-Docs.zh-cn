---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="67a6d-102">对声明版本范围的模块支持（1.\* 等）</span><span class="sxs-lookup"><span data-stu-id="67a6d-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="67a6d-103">现与 **-MaximumVersion** 结合的 **-MinimumVersion** 让用户能够在特定范围内获取/导入模块。</span><span class="sxs-lookup"><span data-stu-id="67a6d-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="67a6d-104">该参数还支持**。**\*.</span><span class="sxs-lookup"><span data-stu-id="67a6d-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="67a6d-105">以下示例演示其工作原理：</span><span class="sxs-lookup"><span data-stu-id="67a6d-105">The following example shows how it works:</span></span>

<span data-ttu-id="67a6d-106">现在，你可以组合**-MinimumVersion**和**-MaximumVersion**用于导入在特定范围内的模块：</span><span class="sxs-lookup"><span data-stu-id="67a6d-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

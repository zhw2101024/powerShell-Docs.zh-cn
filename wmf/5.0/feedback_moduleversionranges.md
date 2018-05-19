---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="e8fcd-102">对声明版本范围的模块支持（1.\* 等）</span><span class="sxs-lookup"><span data-stu-id="e8fcd-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="e8fcd-103">现与 **-MaximumVersion** 结合的 **-MinimumVersion** 让用户能够在特定范围内获取/导入模块。</span><span class="sxs-lookup"><span data-stu-id="e8fcd-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="e8fcd-104">该参数还支持 .\*。</span><span class="sxs-lookup"><span data-stu-id="e8fcd-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="e8fcd-105">以下示例演示其工作原理：</span><span class="sxs-lookup"><span data-stu-id="e8fcd-105">The following example shows how it works:</span></span>

<span data-ttu-id="e8fcd-106">现在，可以组合 -MinimumVersion 和 -MaximumVersion，导入特定范围内的模块：</span><span class="sxs-lookup"><span data-stu-id="e8fcd-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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

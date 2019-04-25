---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057496"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="51774-102">对声明版本范围的模块支持（1.\* 等）</span><span class="sxs-lookup"><span data-stu-id="51774-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="51774-103">现与 **-MaximumVersion** 结合的 **-MinimumVersion** 让用户能够在特定范围内获取/导入模块。</span><span class="sxs-lookup"><span data-stu-id="51774-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="51774-104">该参数还支持 .\*。</span><span class="sxs-lookup"><span data-stu-id="51774-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="51774-105">以下示例演示其工作原理：</span><span class="sxs-lookup"><span data-stu-id="51774-105">The following example shows how it works:</span></span>

<span data-ttu-id="51774-106">现在，可以组合 -MinimumVersion 和 -MaximumVersion，导入特定范围内的模块：</span><span class="sxs-lookup"><span data-stu-id="51774-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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

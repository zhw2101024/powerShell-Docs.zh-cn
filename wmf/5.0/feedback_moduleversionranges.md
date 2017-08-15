---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: fa972b68015d9b6e14508ccda562cfa5ebd632ac
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2017
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>对声明版本范围的模块支持（1.* 等）
现与 **-MaximumVersion** 结合的 **-MinimumVersion** 让用户能够在特定范围内获取/导入模块。 该参数还支持 **.***。 以下示例演示其工作原理：

```powershell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```


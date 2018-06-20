---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 2d6a25908de746e296bef91e05c3d4e250aa77c9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189799"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="e0e6d-102">NoNewLine 参数</span><span class="sxs-lookup"><span data-stu-id="e0e6d-102">NoNewLine parameter</span></span>
<span data-ttu-id="e0e6d-103">**Out-file**、**Add-content**和 **Set-content** 现在具有新的 **–NoNewline** 开关，它将在输出后直接省略换行。</span><span class="sxs-lookup"><span data-stu-id="e0e6d-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="e0e6d-104">如果不指定 **–NoNewline**，每个片段将出现在单独的行上：</span><span class="sxs-lookup"><span data-stu-id="e0e6d-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```

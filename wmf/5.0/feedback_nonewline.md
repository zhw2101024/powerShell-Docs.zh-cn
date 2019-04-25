---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057224"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="41408-102">NoNewLine 参数</span><span class="sxs-lookup"><span data-stu-id="41408-102">NoNewLine parameter</span></span>
<span data-ttu-id="41408-103">**Out-file**、**Add-content**和 **Set-content** 现在具有新的 **–NoNewline** 开关，它将在输出后直接省略换行。</span><span class="sxs-lookup"><span data-stu-id="41408-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="41408-104">如果不指定 **–NoNewline**，每个片段将出现在单独的行上：</span><span class="sxs-lookup"><span data-stu-id="41408-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```

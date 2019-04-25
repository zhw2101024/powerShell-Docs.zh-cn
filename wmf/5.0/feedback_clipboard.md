---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057292"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="36e14-102">剪贴板 cmdlet</span><span class="sxs-lookup"><span data-stu-id="36e14-102">Clipboard cmdlets</span></span>
<span data-ttu-id="36e14-103">通过 **Get-Clipboard** 和 **Set-Clipboard**，你可以更轻松地将内容传入和传出 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="36e14-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="36e14-104">例如，如果你使用 Windows 资源管理器将三个文件复制到剪贴板（例如，通过选择它们并按 `ctrl-c`），然后就可以轻松地以文件列表的方式访问剪贴板的内容：</span><span class="sxs-lookup"><span data-stu-id="36e14-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="36e14-105">剪贴板 cmdlet 支持图像、音频文件、文件列表和文本。</span><span class="sxs-lookup"><span data-stu-id="36e14-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

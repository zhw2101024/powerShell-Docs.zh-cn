---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="a50e7-102">剪贴板 cmdlet</span><span class="sxs-lookup"><span data-stu-id="a50e7-102">Clipboard cmdlets</span></span>
<span data-ttu-id="a50e7-103">通过 **Get-Clipboard** 和 **Set-Clipboard**，你可以更轻松地将内容传入和传出 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="a50e7-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="a50e7-104">例如，如果你使用 Windows 资源管理器将三个文件复制到剪贴板（例如，通过选择它们并按 `ctrl-c`），然后就可以轻松地以文件列表的方式访问剪贴板的内容：</span><span class="sxs-lookup"><span data-stu-id="a50e7-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="a50e7-105">剪贴板 cmdlet 支持图像、音频文件、文件列表和文本。</span><span class="sxs-lookup"><span data-stu-id="a50e7-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>


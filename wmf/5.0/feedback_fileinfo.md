---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="b667a-102">对 FileInfo 对象的更新</span><span class="sxs-lookup"><span data-stu-id="b667a-102">Updates to FileInfo object</span></span>
<span data-ttu-id="b667a-103">文件版本信息可能会产生误导，尤其是在对文件进行了修补的情况下。</span><span class="sxs-lookup"><span data-stu-id="b667a-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="b667a-104">此版本的 WMF 5.0 向 FileInfo 对象添加了新的 **FileVersionRaw** 和 **ProductVersionRaw** 脚本属性。</span><span class="sxs-lookup"><span data-stu-id="b667a-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="b667a-105">以下是为 powershell.exe 显示的属性（假设 $pid 为 PowerShell 进程的 ID）：</span><span class="sxs-lookup"><span data-stu-id="b667a-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

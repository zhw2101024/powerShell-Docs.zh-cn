---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="a6634-102">卸载说明</span><span class="sxs-lookup"><span data-stu-id="a6634-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="a6634-103">使用命令提示符</span><span class="sxs-lookup"><span data-stu-id="a6634-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="a6634-104">打开“命令提示符”。</span><span class="sxs-lookup"><span data-stu-id="a6634-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="a6634-105">运行 [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6634-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="a6634-106">在 Windows Server 2012 R2 和 Windows 8.1 上：</span><span class="sxs-lookup"><span data-stu-id="a6634-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="a6634-107">在 Windows Server 2012 上：</span><span class="sxs-lookup"><span data-stu-id="a6634-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="a6634-108">在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上：</span><span class="sxs-lookup"><span data-stu-id="a6634-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="a6634-109">使用控制面板。</span><span class="sxs-lookup"><span data-stu-id="a6634-109">Using Control Panel</span></span>
1.  <span data-ttu-id="a6634-110">打开“控制面板”。</span><span class="sxs-lookup"><span data-stu-id="a6634-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="a6634-111">打开“程序”，然后打开“卸载程序”。</span><span class="sxs-lookup"><span data-stu-id="a6634-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="a6634-112">单击“查看已安装的更新”。</span><span class="sxs-lookup"><span data-stu-id="a6634-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="a6634-113">从已安装的更新列表中选择“Windows Management Framework 5.0”。</span><span class="sxs-lookup"><span data-stu-id="a6634-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="a6634-114">这对应于 *KB3134758*、*KB3134759* 或 *KB3134760*。</span><span class="sxs-lookup"><span data-stu-id="a6634-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="a6634-115">单击“卸载”。</span><span class="sxs-lookup"><span data-stu-id="a6634-115">Click **Uninstall.**</span></span>
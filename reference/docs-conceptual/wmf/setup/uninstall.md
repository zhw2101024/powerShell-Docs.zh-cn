---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 卸载WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147857"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="55b9d-103">卸载说明</span><span class="sxs-lookup"><span data-stu-id="55b9d-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="55b9d-104">使用命令提示符</span><span class="sxs-lookup"><span data-stu-id="55b9d-104">Using Command Prompt</span></span>

1. <span data-ttu-id="55b9d-105">打开  “命令提示符”。</span><span class="sxs-lookup"><span data-stu-id="55b9d-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="55b9d-106">运行 [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="55b9d-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="55b9d-107">在 Windows Server 2012 R2 和 Windows 8.1 上：</span><span class="sxs-lookup"><span data-stu-id="55b9d-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="55b9d-108">在 Windows Server 2012 上：</span><span class="sxs-lookup"><span data-stu-id="55b9d-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="55b9d-109">在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上：</span><span class="sxs-lookup"><span data-stu-id="55b9d-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="55b9d-110">使用控制面板。</span><span class="sxs-lookup"><span data-stu-id="55b9d-110">Using Control Panel</span></span>

1. <span data-ttu-id="55b9d-111">打开  “控制面板”。</span><span class="sxs-lookup"><span data-stu-id="55b9d-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="55b9d-112">打开“程序”  ，然后打开  “卸载程序”。</span><span class="sxs-lookup"><span data-stu-id="55b9d-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="55b9d-113">单击  “查看已安装的更新”。</span><span class="sxs-lookup"><span data-stu-id="55b9d-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="55b9d-114">从已安装的更新列表中选择“Windows Management Framework 5.0”  。</span><span class="sxs-lookup"><span data-stu-id="55b9d-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="55b9d-115">这对应于 *KB3134758*、*KB3134759* 或 *KB3134760*。</span><span class="sxs-lookup"><span data-stu-id="55b9d-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="55b9d-116">单击  “卸载”。</span><span class="sxs-lookup"><span data-stu-id="55b9d-116">Click **Uninstall.**</span></span>

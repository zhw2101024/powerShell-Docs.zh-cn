---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 选择对象部件 (Select Objec)
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737162"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="f5df2-103">选择对象部件 (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="f5df2-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="f5df2-104">可以使用 `Select-Object` cmdlet 创建新的自定义 PowerShell 对象（包含从用于创建它们的对象中选择的属性）。</span><span class="sxs-lookup"><span data-stu-id="f5df2-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="f5df2-105">键入下面的命令以创建仅包括 Win32_LogicalDisk WMI 类的 Name 和 FreeSpace 属性的新对象：   </span><span class="sxs-lookup"><span data-stu-id="f5df2-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="f5df2-106">可以使用 `Select-Object` 创建计算属性。</span><span class="sxs-lookup"><span data-stu-id="f5df2-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="f5df2-107">这样即可以以十亿字节为单位显示 FreeSpace，而非以字节为单位。 </span><span class="sxs-lookup"><span data-stu-id="f5df2-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```

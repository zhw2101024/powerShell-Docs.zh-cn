---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 选择对象部件 (Select Objec)
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="df231-103">选择对象部件 (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="df231-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="df231-104">可以使用 **Select-Object** cmdlet 创建新的自定义 Windows PowerShell 对象（包含从用于创建它们的对象中选择的属性）。</span><span class="sxs-lookup"><span data-stu-id="df231-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="df231-105">键入下面的命令以创建仅包括 Win32_LogicalDisk WMI 类的 Name 和 FreeSpace 属性的新对象：</span><span class="sxs-lookup"><span data-stu-id="df231-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="df231-106">发出该命令后，无法看到数据类型，但是如果在 Select-Object 后将结果发送到 Get-Member，可以说明你拥有新类型的对象 PSCustomObject：</span><span class="sxs-lookup"><span data-stu-id="df231-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

<span data-ttu-id="df231-107">Select-Object 有许多用途。</span><span class="sxs-lookup"><span data-stu-id="df231-107">Select-Object has many uses.</span></span> <span data-ttu-id="df231-108">其中之一就是复制你稍后可修改的数据。</span><span class="sxs-lookup"><span data-stu-id="df231-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="df231-109">现在，我们可以处理在上一节中遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="df231-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="df231-110">我们可以在新建对象中更新 FreeSpace 的值，输出内容将包括描述性标签：</span><span class="sxs-lookup"><span data-stu-id="df231-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
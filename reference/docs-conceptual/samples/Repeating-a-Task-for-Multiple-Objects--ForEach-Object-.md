---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 为多个对象重复执行任务 (ForEach Object)
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736873"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>为多个对象重复执行任务 (ForEach-Object)

`ForEach-Object` cmdlet 为当前管道对象使用脚本块和 `$_` 描述符，以便你可以对管道中的每个对象运行命令。 这可用于执行某些复杂的任务。

一种有帮助的情况就是操纵数据使其更为有用。 例如，WMI 的 Win32_LogicalDisk 类可用于返回每个本地磁盘的可用空间信息。  返回以字节表示的数据，但是，这也将增加阅读的难度：

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

通过将每个值除以 1 MB，可以将 FreeSpace 值转换为以十亿字节为单位。  你可通过键入以下内容在 `ForEach-Object` 脚本块中实现此操作：

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

遗憾的是，该输出现在是没有关联标签的数据。 因为这样的 WMI 属性为只读，所以不能直接转换 FreeSpace。  如果键入以下内容：

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

则将收到错误消息：

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

可以通过使用一些高级技术重新组织数据，但更简单的方法是通过使用 `Select-Object` 创建新对象。

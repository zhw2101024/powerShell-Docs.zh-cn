---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 对对象进行排序
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="sorting-objects"></a>对对象进行排序

可以通过使用 **Sort-Object** cmdlet 组织已显示的数据，使其更易于扫描。 **Sort-Object** 依据一个或多个属性的名称进行排序，并返回按这些属性的值进行排序的数据。

请考虑列出 Win32_SystemDriver 实例的问题。 如果想要依次按 **State** 和 **Name** 进行排序，可键入：

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

虽然显示的内容较长，但是你可以看到具有相同状态的项组合在一起：

```output
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

也可通过指定 **Descending** 参数按相反顺序对对象进行排序。 这将反转排序顺序，即按反向字母顺序对名称进行排序，按降序大小对数字进行排序。

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```
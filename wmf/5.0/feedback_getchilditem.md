---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085259"
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem 具有 -Depth 参数
**Get-ChildItem** 现在具有 **–Depth** 参数，你可以将其与 **–Recurse** 一起使用来限制递归：

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0

目录：C:\\Users\\slee\\Downloads\\Example

模式 上次写入时间 长度 名称

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1

目录：C:\\Users\\slee\\Downloads\\Example

模式 上次写入时间 长度 名称

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

目录：C:\\Users\\slee\\Downloads\\Example\\Depth0

模式 上次写入时间 长度 名称

---- ------------- ------ ----

d----- 4/14/2015 5:33 PM Depth1

---
title: 日期和时间参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369786"
---
# <a name="date-and-time-parameters"></a>日期和时间参数

下表列出了用于处理日期和时间信息的参数的建议名称和功能。 日期和时间参数通常用于在创建或访问某些内容时进行记录。

|参数|功能|
|---|---|
|**存取**<br>数据类型： SwitchParameter|实现此参数以便在指定时，该 cmdlet 将对基于**前后** **参数指定**的日期和时间访问的资源进行操作。 如果指定此参数，则必须指定**创建**的参数和**修改后**的参数。|
|**晚**<br>数据类型： DateTime|实现此参数以指定使用 cmdlet 的日期和时间。 若要使**After**参数正常工作，cmdlet 还必须有一个已**访问**的、**创建**的或**修改**的参数。 而且，调用 cmdlet 时，必须将该参数设置为**true** 。|
|**早**<br>数据类型： DateTime|实现此参数以指定使用 cmdlet 之前的日期和时间。 若要使**Before**参数正常工作，cmdlet 还必须有一个已**访问**的、**创建**的或**修改**的参数。 而且，调用 cmdlet 时，必须将该参数设置为**true** 。|
|**建立**<br>数据类型： SwitchParameter|实现此参数以便在指定时，该 cmdlet 将对基于**前后** **参数指定**的日期和时间创建的资源进行操作。 如果指定此参数，则不能指定**访问**的参数和**修改后**的参数。|
|**确切**<br>数据类型： SwitchParameter|实现此参数，以便在指定资源时，资源项必须与资源名称完全匹配。 如果未指定参数，则资源字词和名称不需要完全匹配。|
|**时间**<br>数据类型： DateTime|实现此参数以便在指定时，该 cmdlet 将对基于**前后** **参数指定**的日期和时间已更改的资源进行操作。 如果指定此参数，则不得指定**访问**的和**创建**的参数。|
## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

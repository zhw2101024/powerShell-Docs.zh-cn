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
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251347"
---
# <a name="date-and-time-parameters"></a>日期和时间参数

下表列出了建议的名称和处理日期和时间信息的参数的功能。 日期和时间参数通常用于记录时创建或访问内容。

|参数|功能|
|---|---|
|**Accessed**<br>数据类型：SwitchParameter|实现此参数，以便它指定该 cmdlet 将对已访问的资源时基于日期和指定的时间**之前**并**后**参数。 如果指定此参数，则**Created**并**Modified**参数必须是不能指定。|
|**After**<br>数据类型：DateTime|实现此参数以指定的日期和时间之后使用此 cmdlet。 有关**之后**参数来工作，该 cmdlet 还必须具有**Accessed**，**创建**，或**已修改**参数。 并且，该参数必须设置为 **，则返回 true**调用 cmdlet 时。|
|**之前**<br>数据类型：DateTime|实现此参数以指定的日期和时间在其前面使用此 cmdlet。 有关**之前**参数来工作，该 cmdlet 还必须具有**Accessed**，**创建**，或**已修改**参数。 并且，该参数必须设置为 **，则返回 true**调用 cmdlet 时。|
|**创建**<br>数据类型：SwitchParameter|实现此参数，以便它指定该 cmdlet 将对已创建的资源时基于日期和指定的时间**之前**并**后**参数。 如果指定此参数，则**Accessed**并**Modified**不得指定参数。|
|**Exact**<br>数据类型：SwitchParameter|实现此参数，以便它指定资源字词时必须完全匹配的资源名称。 如果未指定参数的资源术语和名称不必完全匹配。|
|**修改**<br>数据类型：DateTime|实现此参数，以便它指定该 cmdlet 将对已更改的资源时基于日期和指定的时间**之前**并**后**参数。 如果指定此参数，则**Accessed**并**创建**不得指定参数。|
## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

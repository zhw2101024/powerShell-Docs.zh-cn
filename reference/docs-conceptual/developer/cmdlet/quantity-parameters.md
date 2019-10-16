---
title: 数量参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369556"
---
# <a name="quantity-parameters"></a>数量参数

下表列出了用于数量参数的建议名称和功能。

|参数|功能|
|---|---|
|**一切**<br>数据类型：布尔值|实现此参数以便 `true` 指示应对所有资源，而不是默认的资源子集。 实现此参数以便 `false` 表示资源的子集。|
|**分区**<br>数据类型： Int32|实现此参数，以便用户可以指定要分配的项数。|
|**BlockCount**<br>数据类型： Int64|实现此参数，以便用户可以指定块计数。|
|**计**<br>数据类型： Int64|实现此参数，以便用户可以指定计数。|
|**内**<br>数据类型：关键字|实现此参数，以便用户可以指定要操作的范围。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

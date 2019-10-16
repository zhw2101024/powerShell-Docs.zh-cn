---
title: 格式参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369746"
---
# <a name="format-parameters"></a>格式参数

下表列出了用于格式化或生成数据的参数的建议名称和功能。

|参数|功能|
|---|---|
|**方式**<br>数据类型：关键字|实现此参数以指定 cmdlet 输出格式。 例如，可能的值可以是文本或脚本。|
|**二进制**<br>数据类型： SwitchParameter|实现此参数以指示该 cmdlet 处理二进制值。|
|**编码器**<br>数据类型：关键字|实现此参数可指定支持的编码类型。 例如，可能的值可能是 ASCII、UTF8、Unicode、UTF7、BigEndianUnicode、Byte 和 String。|
|**换**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时支持换行字符。|
|**短名称**<br>数据类型： SwitchParameter|实现此参数以便在指定参数时支持短名称。|
|**宽度**<br>数据类型： Int32|实现此参数，以便用户可以指定输出设备的宽度。|
|**最后**<br>数据类型： SwitchParameter|实现此参数以便在指定参数时支持文本换行。|
## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

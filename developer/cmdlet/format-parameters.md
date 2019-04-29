---
title: 设置参数的格式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068107"
---
# <a name="format-parameters"></a>格式参数

下表列出了建议的名称和参数，用于设置格式或生成数据的功能。

|参数|功能|
|---|---|
|**As**<br>数据类型：关键字|实现此参数来指定 cmdlet 的输出格式。 例如，可能的值可以是文本或脚本。|
|**二进制文件**<br>数据类型：SwitchParameter|实现此参数以指示该 cmdlet 处理二进制值。|
|**编码**<br>数据类型：关键字|实现此参数来指定支持的编码类型。 例如，可能的值可能是 ASCII、 UTF8、 Unicode、 UTF7、 BigEndianUnicode、 字节、 和字符串。|
|**NewLine**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时，支持换行字符。|
|**ShortName**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时，支持的短名称。|
|**Width**<br>数据类型：Int32|实现此参数，以便用户可以指定输出设备的宽度。|
|**Wrap**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时，才支持文本换行。|
## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

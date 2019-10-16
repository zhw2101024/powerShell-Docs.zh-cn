---
title: 属性参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369576"
---
# <a name="property-parameters"></a>属性参数

下表列出了属性参数的建议名称和功能。

|参数|功能|
|---|---|
|**计**<br>数据类型： Int32|实现此参数，以便用户可以指定要处理的对象数。|
|**描述**<br>数据类型：字符串|实现此参数，以便用户可以为资源指定说明。|
|**从**<br>数据类型：字符串|实现此参数，以便用户可以指定要从中获取信息的引用对象。|
|**识别**<br>数据类型：资源相关|实现此参数，以便用户可以指定资源的标识符。|
|**送**<br>数据类型：字符串|实现此参数，以便用户可以指定输入文件规范。|
|**位置**<br>数据类型：字符串|实现此参数，以便用户可以指定资源的位置。|
|**LogName**<br>数据类型：字符串|实现此参数，以便用户可以指定要处理或使用的日志文件的名称。|
|**Name**<br>数据类型：字符串|实现此参数，以便用户可以指定资源的名称。|
|**输出**<br>数据类型：字符串|实现此参数，以便用户可以指定输出文件。|
|**Owner**<br>数据类型：字符串|实现此参数，以便用户可以指定资源所有者的名称。|
|**知识产权**<br>数据类型：字符串|实现此参数，以便用户可以指定要使用的属性的名称或名称。|
|**在于**<br>数据类型：字符串|实现此参数，以便用户可以指定调用此 cmdlet 的原因。|
|**Regex**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时使用正则表达式。 如果指定此参数，则不解析通配符。|
|**快速**<br>数据类型： Int32|实现此参数，以便用户可以指定波特率。 用户将此参数设置为资源的速度。|
|**状态**<br>数据类型：关键字数组|实现此参数，以便用户可以指定状态的名称，如 KEYDOWN。|
|**负值**<br>数据类型：对象|实现此参数，以便用户可以指定要提供给 cmdlet 的值。|
|**版本**<br>数据类型：字符串|实现此参数，以便用户可以指定属性的版本。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

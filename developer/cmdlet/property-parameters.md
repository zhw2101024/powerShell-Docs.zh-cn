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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067563"
---
# <a name="property-parameters"></a>属性参数

下表列出了建议的名称和属性参数的功能。

|参数|功能|
|---|---|
|**Count**<br>数据类型：Int32|实现此参数，以便用户可以指定要处理的对象数。|
|**描述**<br>数据类型：字符串|实现此参数，使用户能够指定资源的说明。|
|**从**<br>数据类型：字符串|实现此参数，以便用户可以指定要获取信息的引用对象。|
|**Id**<br>数据类型：资源依赖|实现此参数，使用户能够指定资源的标识符。|
|**输入**<br>数据类型：字符串|实现此参数，以便用户可以指定输入的文件的详细信息。|
|**位置**<br>数据类型：字符串|实现此参数，以便用户可以指定该资源的位置。|
|**LogName**<br>数据类型：字符串|实现此参数，以便用户可以指定要处理或使用的日志文件的名称。|
|**Name**<br>数据类型：字符串|实现此参数，以便用户可以指定资源的名称。|
|**Output**<br>数据类型：字符串|实现此参数，以便用户可以指定输出文件。|
|**Owner**<br>数据类型：字符串|实现此参数，以便用户可以指定资源的所有者的名称。|
|**属性**<br>数据类型：字符串|实现此参数，以便用户可以指定的名称或要使用的属性的名称。|
|**Reason**<br>数据类型：字符串|实现此参数，以便用户可以指定调用此 cmdlet。|
|**Regex**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时使用的正则表达式。 如果指定此参数，则不解析通配符字符。|
|**速度**<br>数据类型：Int32|实现此参数，以便用户可以指定的波特率。 用户将此参数设置为该资源的速度。|
|**状态**<br>数据类型：关键字数组|实现此参数，以便用户可以指定的状态，例如 KEYDOWN 的名称。|
|**值**<br>数据类型：对象|实现此参数，以便用户可以指定要向该 cmdlet 提供的值。|
|**版本**<br>数据类型：字符串|实现此参数，以便用户可以指定属性的版本。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

---
title: 资源参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067444"
---
# <a name="resource-parameters"></a>资源参数

下表列出了建议的名称和资源参数的功能。 这些参数的资源可能包含在 cmdlet 类或正在运行该 cmdlet 的主机应用程序的程序集。

|参数|功能|
|---|---|
|**Application**<br>数据类型：字符串|实现此参数，以便用户可以指定应用程序。|
|**程序集**<br>数据类型：字符串|实现此参数，以便用户可以指定程序集。|
|**属性**<br>数据类型：字符串|实现此参数，以便用户可以指定一个属性。|
|**类**<br>数据类型：字符串|实现此参数，以便用户可以指定 Microsoft.NET Framework 类。|
|**Cluster**<br>数据类型：字符串|实现此参数，以便用户可以指定群集。|
|**区域性**<br>数据类型：字符串|实现此参数，以便用户可以指定要在其中运行该 cmdlet 的区域性。|
|**域**<br>数据类型：字符串|实现此参数，以便用户可以指定的域名。|
|**Drive**<br>数据类型：字符串|实现此参数，以便用户可以指定驱动器名称。|
|**事件**<br>数据类型：字符串|实现此参数，以便用户可以指定事件名称。|
|**接口**<br>数据类型：字符串|实现此参数，以便用户可以指定网络接口名称。|
|**IpAddress**<br>数据类型：字符串|实现此参数，以便用户可以指定的 IP 地址。|
|**Job**<br>数据类型：字符串|实现此参数，以便用户可以指定某项作业。|
|**LiteralPath**<br>数据类型：字符串|实现此参数，以便不支持通配符时，用户能够指定资源的路径。 (使用**路径**参数支持通配符字符时。)|
|**Mac**<br>数据类型：字符串|实现此参数，以便用户可以指定媒体访问控制器 (MAC) 地址。|
|**ParentId**<br>数据类型：字符串|实现此参数，以便用户可以指定的父标识符。|
|**Path**<br>数据类型：String, String[]|实现此参数，以便支持通配符时，用户可以指示资源的路径。 (使用**LiteralPath**参数时不支持通配符字符。)我们建议您开发此参数，以便它支持完整`provider:path`由提供程序使用的语法。 我们还建议，使其尽可能与尽可能多的提供商可以开发它。|
|**端口**<br>数据类型：整数、 字符串|实现此参数，以便用户可以指定网络的整数值或一个字符串值，如"biztalk"对于其他类型的端口。|
|**打印机**<br>数据类型：整数、 字符串|实现此参数，以便用户可以指定使该 cmdlet 可使用的打印机。|
|**Size**<br>数据类型：Int32|实现此参数，以便用户可以指定一个大小。|
|**TID**<br>数据类型：字符串|实现此参数，以便用户可以指定该 cmdlet 将事务标识符 (TID)。|
|**Type**<br>数据类型：字符串|实现此参数，以便用户可以指定用于执行操作的资源的类型。|
|**URL**<br>数据类型：字符串|实现此参数，以便用户可以指定统一资源定位器 (URL)。|
|**用户**<br>数据类型：字符串|实现此参数，以便用户可以指定其名称或另一个用户的名称。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

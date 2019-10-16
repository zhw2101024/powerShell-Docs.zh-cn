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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369506"
---
# <a name="resource-parameters"></a>资源参数

下表列出了资源参数的建议名称和功能。 对于这些参数，资源可以是包含 cmdlet 类的程序集，也可以是运行 cmdlet 的主机应用程序。

|参数|功能|
|---|---|
|**程序**<br>数据类型：字符串|实现此参数，以便用户可以指定应用程序。|
|**件**<br>数据类型：字符串|实现此参数，以便用户可以指定程序集。|
|**Attribute**<br>数据类型：字符串|实现此参数，以便用户可以指定属性。|
|**班级**<br>数据类型：字符串|实现此参数，以便用户可以指定 Microsoft .NET 框架类。|
|**聚集**<br>数据类型：字符串|实现此参数，以便用户可以指定群集。|
|**区分**<br>数据类型：字符串|实现此参数，以便用户可以指定要在其中运行 cmdlet 的区域性。|
|**域名**<br>数据类型：字符串|实现此参数，以便用户可以指定域名。|
|**光驱**<br>数据类型：字符串|实现此参数，以便用户可以指定驱动器名称。|
|**引发**<br>数据类型：字符串|实现此参数，以便用户可以指定事件名称。|
|**交互**<br>数据类型：字符串|实现此参数，以便用户可以指定网络接口名称。|
|**地址**<br>数据类型：字符串|实现此参数，以便用户可以指定 IP 地址。|
|**任务**<br>数据类型：字符串|实现此参数，以便用户可以指定作业。|
|**LiteralPath**<br>数据类型：字符串|实现此参数，以便在不支持通配符时，用户可以指定资源的路径。 （当支持通配符字符时，请使用**Path**参数。）|
|**Mac**<br>数据类型：字符串|实现此参数，以便用户可以指定媒体访问控制器（MAC）地址。|
|**ParentId**<br>数据类型：字符串|实现此参数，以便用户可以指定父标识符。|
|**通道**<br>数据类型： String，String []|实现此参数，以便用户可以在支持通配符时指示资源的路径。 （如果不支持通配符字符，请使用**LiteralPath**参数。）建议你开发此参数，使其支持提供程序使用的完整 @no__t 1 语法。 我们还建议你对其进行开发，使其适用于尽可能多的提供程序。|
|**口**<br>数据类型： Integer、String|实现此参数，以便用户可以为网络指定整数值或为其他类型的端口指定一个字符串值（如 "biztalk"）。|
|**打印机**<br>数据类型： Integer、String|实现此参数，以便用户可以指定要使用的 cmdlet 的打印机。|
|**规格**<br>数据类型： Int32|实现此参数，以便用户可以指定大小。|
|**TID**<br>数据类型：字符串|实现此参数，以便用户可以为 cmdlet 指定事务标识符（TID）。|
|**类别**<br>数据类型：字符串|实现此参数，以便用户可以指定要在其上操作的资源的类型。|
|**链接**<br>数据类型：字符串|实现此参数，以便用户可以指定统一资源定位器（URL）。|
|**用户**<br>数据类型：字符串|实现此参数，以便用户可以指定其名称或其他用户的名称。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

---
title: 模块和管理单元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067614"
---
# <a name="modules-and-snap-ins"></a>模块和管理单元

Cmdlet 可以添加到使用 （通过 Windows PowerShell 2.0 中引入） 的模块或管理单元的会话。一旦该 cmdlet 添加到会话中它可以在主机应用程序或以交互方式在命令行以编程方式运行。

我们建议你使用模块作为传递方法将 cmdlet 添加到的会话由于以下原因：

- 模块，可将 cmdlet 添加的程序集加载其中定义该 cmdlet。 没有无需实现一个管理单元中的类。

- 模块可以添加其他资源，如变量、 函数、 脚本、 类型和格式设置文件，和的详细信息。

- 可以使用管理单元只可添加到会话的 cmdlet 和提供程序。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365366"
---
# <a name="modules-and-snap-ins"></a>模块和管理单元

Cmdlet 可以使用模块（由 Windows PowerShell 2.0 引入）或管理单元添加到会话中。将 cmdlet 添加到会话后，它可以通过主机应用程序以编程方式运行，或在命令行中以编程方式运行。

出于以下原因，建议使用模块作为向会话添加 cmdlet 的传递方法：

- 模块允许通过加载定义 cmdlet 的程序集来添加 cmdlet。 无需实现管理单元类。

- 模块允许添加其他资源，例如变量、函数、脚本、类型和格式设置文件等。

- 管理单元只能用于向会话添加 cmdlet 和提供程序。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

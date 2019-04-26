---
title: Windows PowerShell 会话状态 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066968"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell 会话状态

会话状态是指 Windows PowerShell 会话或模块的当前配置。 Windows PowerShell 会话是通过命令行的用户或以编程方式通过主机应用程序以交互方式使用的操作环境。 会话的会话状态称为全局会话状态。

从开发人员的角度，Windows PowerShell 会话是指当主机应用程序打开 Windows PowerShell 运行空间和它关闭时运行空间之间的时间。 介绍了另一种方法，会话是实例的在运行空间存在时调用的 Windows PowerShell 引擎的生存期。

## <a name="module-session-state"></a>模块会话状态

只要该模块或其嵌套模块之一导入会话就会创建模块的会话状态。 当模块可导出一个元素，如 cmdlet、 函数或脚本时，该元素的引用被添加到会话的全局会话状态。 但是，当运行时元素，它中执行该模块的会话状态。

## <a name="session-state-data"></a>会话状态数据

会话状态数据可以是公共或私有。 公共数据可供外部会话状态调用专用数据可仅用于从会话状态中的调用时。 例如，模块可以有一个私有函数可以仅由模块或仅在内部调用的已导出的公共元素。 这是类似于.NET Framework 类型的私有和公共成员。

会话状态数据存储的当前 Windows PowerShell 会话的上下文中的执行引擎的当前实例。 会话状态数据包含以下各项：

- 路径信息

- 驱动器信息

- Windows PowerShell 提供程序信息

- 有关导入的模块和对由模块导出的模块元素 （如 cmdlet、 函数和脚本） 的引用信息。 此信息和这些引用，可仅全局会话状态。

- 会话状态变量信息

## <a name="accessing-session-state-data-within-cmdlets"></a>访问在 Cmdlet 中的会话状态数据

Cmdlet 可以访问会话状态数据可以通过间接[System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)属性的 cmdlet 类或直接通过[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类。 [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类提供了可用于调查的会话状态数据的不同类型的属性。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell Cmdlets](./cmdlet-overview.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)

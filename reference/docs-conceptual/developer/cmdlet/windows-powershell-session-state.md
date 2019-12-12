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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369096"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell 会话状态

会话状态是指 Windows PowerShell 会话或模块的当前配置。 Windows PowerShell 会话是命令行用户以交互方式或通过主机应用程序以编程方式使用的操作环境。 会话的会话状态称为全局会话状态。

从开发人员的角度来看，Windows PowerShell 会话是指主机应用程序打开 Windows PowerShell 运行空间和关闭运行空间之间的时间。 作为另一种方法，会话是运行空间存在时调用的 Windows PowerShell 引擎实例的生存期。

## <a name="module-session-state"></a>模块会话状态

只要模块或其一个嵌套模块导入到会话中，就会创建模块会话状态。 模块导出元素（如 cmdlet、函数或脚本）时，会将对该元素的引用添加到该会话的全局会话状态。 但是，当元素运行时，它将在模块的会话状态中执行。

## <a name="session-state-data"></a>会话状态数据

会话状态数据可以是公共或私有。 公共数据可用于从会话状态外调用，而专用数据仅可用于从会话状态中调用。 例如，模块可以具有私有函数，该函数只能由模块调用，或仅由已导出的公共元素在内部调用。 这类似于 .NET Framework 类型的私有和公共成员。

会话状态数据由当前 Windows PowerShell 会话上下文中的当前执行引擎实例存储。 会话状态数据由以下项组成：

- 路径信息

- 驱动器信息

- Windows PowerShell 提供程序信息

- 有关已导入的模块以及模块导出的模块元素（如 cmdlet、函数和脚本）的引用的信息。 此信息和这些引用仅适用于全局会话状态。

- 会话状态变量信息

## <a name="accessing-session-state-data-within-cmdlets"></a>访问 Cmdlet 内的会话状态数据

Cmdlet 可以通过 cmdlet 类的[PSCmdlet. Sessionstate *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)属性间接访问会话状态数据，也可以直接通过[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类访问会话状态数据。 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类提供属性，这些属性可用于调查不同类型的会话状态数据。

## <a name="see-also"></a>另请参阅

[PSCmdlet. Sessionstate。](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[Sessionstate 吗？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell Cmdlet](./cmdlet-overview.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)

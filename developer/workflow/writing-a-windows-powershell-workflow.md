---
title: 编写 Windows PowerShell 工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857403"
---
# <a name="writing-a-windows-powershell-workflow"></a>编写 Windows PowerShell 工作流

可以通过添加到 Visual Studio 中的工作流设计器的 Windows PowerShell 程序集公开的活动来创建 XAML 工作流。 以下 Windows PowerShell 程序集公开支持工作流的活动。

> [!IMPORTANT]
> XAML 工作流必须封装为模块中，如果你想要为工作流提供帮助。 有关模块的信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

- [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft.Powershell.Core.Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft.Powershell.Diagnostics.Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft.Powershell.Security.Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft.Powershell.Utility.Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  以下主题介绍如何使用 Windows PowerShell 活动创建工作流。

- [将 Windows PowerShell 活动添加到 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [使用 Windows PowerShell 活动创建工作流](./creating-a-workflow-with-windows-powershell-activities.md)

- [使用 Windows PowerShell 脚本创建一个工作流](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [导入并调用 Windows PowerShell 工作流](./importing-and-invoking-a-windows-powershell-workflow.md)

- [从 Windows PowerShell Cmdlet 创建工作流活动](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)
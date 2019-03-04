---
title: Windows PowerShell Cmdlet 概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855783"
---
# <a name="windows-powershell-cmdlet-concepts"></a>Windows PowerShell Cmdlet 概念

本部分介绍 cmdlet 如何工作。

## <a name="in-this-section"></a>本节内容

本部分包括以下主题。

[Cmdlet 开发指导原则](./cmdlet-development-guidelines.md)本主题提供可用于生成格式正确的 cmdlet 的开发指南。

[Cmdlet 类声明](./cmdlet-class-declaration.md)本主题介绍 cmdlet 类声明。

[批准用于 Windows PowerShell 命令的动词](./approved-verbs-for-windows-powershell-commands.md)本主题列出了你在声明 cmdlet 类时，可以使用的预定义的 cmdlet 谓词。

[Cmdlet 输入处理方法](./cmdlet-input-processing-methods.md)本主题介绍允许 cmdlet 来执行预处理操作、 输入处理操作和发布的处理操作的方法。

[Cmdlet 参数](./cmdlet-parameters.md)本部分介绍了不同类型的参数，可以将添加到 cmdlet。

[Cmdlet 属性](./cmdlet-attributes.md)本部分介绍用于将.NET Framework 类声明为 cmdlet，来声明作为 cmdlet 参数的字段和声明参数的输入的验证规则的属性。

[Cmdlet 别名](./cmdlet-aliases.md)本主题介绍了 cmdlet 的别名。

[Cmdlet 输出](./cmdlet-output.md)本部分介绍的 cmdlet 可以返回的输出以及如何定义和显示由 cmdlet 返回的对象的类型。

[注册 Cmdlet](./modules-and-snap-ins.md)本部分介绍如何通过使用模块和管理单元注册 cmdlet。

[请求确认](./requesting-confirmation-from-cmdlets.md)本部分介绍它们对系统进行更改之前，cmdlet 如何请求来自用户的确认。

[Windows PowerShell 错误报告](./error-reporting-concepts.md)本部分介绍 cmdlet 如何报告的终止错误和非终止性错误，并介绍了如何解释错误记录。

[后台作业](./background-jobs.md)本主题说明了如何 cmdlet 可以执行其工作中不会干扰当前会话中执行的命令的后台作业。

[调用 Cmdlet 和脚本内 Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md)本主题描述如何 cmdlet 可以调用其他 cmdlet 和脚本从其输入处理方法。

[Cmdlet 可设置](./cmdlet-sets.md)本主题介绍如何使用基类，这些类创建的 cmdlet 集。

[Windows PowerShell 会话状态](./windows-powershell-session-state.md)本主题介绍 Windows PowerShell 会话状态。

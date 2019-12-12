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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369116"
---
# <a name="windows-powershell-cmdlet-concepts"></a>Windows PowerShell Cmdlet 概念

本部分介绍 cmdlet 的工作原理。

## <a name="in-this-section"></a>本部分内容

本部分包括以下主题。

[Cmdlet 开发指南](./cmdlet-development-guidelines.md)本主题提供可用于生成格式正确的 cmdlet 的开发指南。

[Cmdlet 类声明](./cmdlet-class-declaration.md)本主题介绍 cmdlet 类声明。

[Windows PowerShell 命令的批准的谓词](./approved-verbs-for-windows-powershell-commands.md)本主题列出了在声明 cmdlet 类时可以使用的预定义 cmdlet 谓词。

[Cmdlet 输入处理方法](./cmdlet-input-processing-methods.md)本主题介绍允许 cmdlet 执行预处理操作、输入处理操作和后处理操作的方法。

[Cmdlet 参数](./cmdlet-parameters.md)本部分介绍可添加到 cmdlet 的不同类型的参数。

[Cmdlet 属性](./cmdlet-attributes.md)本部分介绍用于将 .NET Framework 类声明为 cmdlet、将字段声明为 cmdlet 参数以及为参数声明输入验证规则的属性。

[Cmdlet 别名](./cmdlet-aliases.md)本主题介绍 cmdlet 别名。

[Cmdlet 输出](./cmdlet-output.md)本部分介绍 cmdlet 可以返回的输出的类型，以及如何定义和显示由 cmdlet 返回的对象。

[注册 cmdlet](./modules-and-snap-ins.md)本部分介绍如何使用模块和管理单元注册 cmdlet。

[请求确认](./requesting-confirmation-from-cmdlets.md)本部分介绍了在用户更改系统之前，cmdlet 如何请求用户进行确认。

[Windows PowerShell 错误报告](./error-reporting-concepts.md)本节介绍 cmdlet 如何报告终止错误和非终止错误，并说明如何解释错误记录。

[后台作业](./background-jobs.md)本主题介绍如何在不影响当前会话中执行的命令的后台作业中执行这些 cmdlet。

[在 Cmdlet 中调用 cmdlet 和脚本](./invoking-cmdlets-and-scripts-within-a-cmdlet.md)本主题介绍了 cmdlet 如何从其输入处理方法中调用其他 cmdlet 和脚本。

[Cmdlet 集](./cmdlet-sets.md)本主题介绍如何使用基类创建 cmdlet 集。

[Windows PowerShell 会话状态](./windows-powershell-session-state.md)本主题介绍 Windows PowerShell 会话状态。

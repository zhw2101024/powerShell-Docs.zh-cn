---
title: Windows PowerShell API 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360836"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 示例

本部分包含的示例代码演示如何创建可限制功能的运行空间，以及如何使用运行空间池来提供运行空间来异步运行命令。 你可以使用 Microsoft Visual Studio 来创建控制台应用程序，然后将此部分中的主题中的代码复制到主机应用程序中。

## <a name="in-this-section"></a>本部分内容

[PowerShell01 示例](./windows-powershell01-sample.md)此示例显示了如何使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象来限制运行空间的功能的。 此示例的输出演示如何限制运行空间的语言模式，如何将 cmdlet 标记为私有，如何添加和删除 cmdlet 和提供程序，如何添加代理命令等。

[PowerShell02 示例](./windows-powershell02-sample.md)此示例演示如何使用运行空间池的运行空间以异步方式运行命令。 此示例生成命令列表，然后运行这些命令，而 Windows PowerShell 引擎在需要时从池中打开运行空间。
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082577"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 示例

本节包含演示如何创建运行空间的限制功能，以及如何使用运行空间池以提供运行空间以异步方式运行命令的示例代码。 可以使用 Microsoft Visual Studio 创建控制台应用程序，然后将此部分中的主题从代码复制到主机应用程序。

## <a name="in-this-section"></a>本部分内容

[示例 PowerShell01](./windows-powershell01-sample.md)此示例演示如何使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象来限制运行空间的功能。 此示例的输出演示了如何限制的运行空间、 如何将标记为专用的 cmdlet、 如何添加和删除 cmdlet 和提供程序，将语言模式如何添加代理命令，和的详细信息。

[PowerShell02 示例](./windows-powershell02-sample.md)此示例演示如何使用运行空间的运行空间池以异步方式运行命令。 此示例将生成一系列命令，然后运行这些命令，而 Windows PowerShell 引擎将在需要时从池中打开运行空间。
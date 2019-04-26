---
title: 自定义主机示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082917"
---
# <a name="custom-host-samples"></a>自定义主机示例

本部分包含有关编写自定义主机的示例代码。 可以使用 Microsoft Visual Studio 创建控制台应用程序，然后将此部分中的主题从代码复制到主机应用程序。

## <a name="in-this-section"></a>本部分内容

 [Host01 示例](./host01-sample.md)此示例演示如何实现使用基本的自定义主机的主机应用程序。

 [Host02 示例](./host02-sample.md)此示例演示如何编写使用 Windows PowerShell 运行时与自定义主机实现的主机应用程序。 主机应用程序将主机区域性设置为 German，运行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet，并显示将结果作为你会看到它们在德语中使用 pwrsh.exe，然后打印出当前日期和时间。

 [Host03 示例](./host03-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。

 [Host04 示例](./host04-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。 此主机应用程序还支持显示允许用户指定多个选项的提示。

 [Host05 示例](./host05-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。 此主机应用程序还支持对远程计算机的调用使用[Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)并[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet

 [Host06 示例](./host06-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序从命令行读取并执行命令，然后将结果显示到控制台。 此外，此示例还使用了 Tokenizer API 来指定用户输入的文本颜色。

## <a name="see-also"></a>另请参阅

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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367506"
---
# <a name="custom-host-samples"></a>自定义主机示例

本部分包含用于编写自定义主机的示例代码。 你可以使用 Microsoft Visual Studio 来创建控制台应用程序，然后将此部分中的主题中的代码复制到主机应用程序中。

## <a name="in-this-section"></a>本部分内容

 [Host01 示例](./host01-sample.md)此示例演示如何实现使用基本自定义主机的主机应用程序。

 [Host02 示例](./host02-sample.md)此示例演示如何编写使用 Windows PowerShell 运行时以及自定义主机实现的主机应用程序。 主机应用程序将主机区域性设置为德语，运行[获取过程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet，并显示使用 pwrsh 时的结果，然后输出德语中的当前数据和时间。

 [Host03 示例](./host03-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。

 [Host04 示例](./host04-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。 此主机应用程序还支持显示允许用户指定多个选项的提示。

 [Host05 示例](./host05-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。 此主机应用程序还支持通过使用[Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)和[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet 对远程计算机进行调用

 [Host06 示例](./host06-sample.md)此示例演示如何生成基于控制台的交互式主机应用程序，该应用程序可从命令行读取命令，执行命令，然后将结果显示到控制台。 此外，此示例还使用了 Tokenizer API 来指定用户输入的文本颜色。

## <a name="see-also"></a>另请参阅

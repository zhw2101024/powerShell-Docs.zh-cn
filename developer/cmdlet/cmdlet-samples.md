---
title: Cmdlet 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: d919d4ad8554e762230c1448d81b50e27c38ba99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863363"
---
# <a name="cmdlet-samples"></a>Cmdlet 示例

本部分介绍 Windows PowerShell 2.0 SDK 中提供的示例代码。 可以将代码复制从主题中本部分中，或打开随 SDK 一起安装的源文件。 [Windows PowerShell 2.0 软件开发工具包 (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560)提供自述文件、 源文件，以及每个示例的 Visual Studio 项目文件。 已安装 sdk，可以找到下面的示例`<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`文件夹。

## <a name="in-this-section"></a>本节内容

[GetProcessSample01 示例](./getprocesssample01-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。

[GetProcessSample02 示例](./getprocesssample02-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。 它提供了可用于指定要检索的进程的名称参数。

[GetProcessSample03 示例](./getprocesssample03-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。 它提供了可接受管道中的对象或从一个对象，其属性名称为参数名称相同的属性值的名称参数。

[GetProcessSample04 示例](./getprocesssample04-sample.md)此示例演示如何编写检索本地计算机上的进程的 cmdlet。 如果在检索进程时发生错误，它会生成一个非终止错误。

[GetProcessSample05 示例](./getprocesssample05-sample.md)此示例演示 Get-proc cmdlet 的完整版本。

[StopProcessSample01 示例](./stopprocesssample01-sample.md)此示例演示如何编写一个 cmdlet，它会尝试停止进程之前, 请求用户反馈以及如何实现`PassThru`指示用户希望该 cmdlet 返回的参数对象。

[StopProcessSample02 示例](./stopprocesssample02-sample.md)此示例演示如何编写写入 verbose、 debug 和警告消息，同时在本地计算机上停止进程的 cmdlet。

[StopProcessSample03 示例](./stopprocesssample03-sample.md)此示例演示如何编写的 cmdlet 的参数的别名，并且支持通配符字符。

[StopProcessSample04 示例](./stopprocesssample04-sample.md)此示例演示如何编写声明参数集，指定默认参数集，它可以接受输入的对象的 cmdlet。

[Events01 示例](./events01-sample.md)此示例演示如何创建 cmdlet 引发的事件，则允许用户注册[System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)。 此 cmdlet 的用户可以例如，注册特定目录下创建一个文件时要执行的操作。 此示例从派生[Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基类。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

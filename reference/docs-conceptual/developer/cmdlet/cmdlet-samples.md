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
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365876"
---
# <a name="cmdlet-samples"></a>Cmdlet 示例

本部分介绍 Windows PowerShell 2.0 SDK 中提供的示例代码。 您可以从本部分中的主题复制代码，或打开随 SDK 一起安装的源文件。 [Windows PowerShell 2.0 软件开发工具包（SDK）](https://www.microsoft.com/en-us/download/details.aspx?id=2560)提供每个示例的自述文件、源文件和 Visual Studio 项目文件。 安装 SDK 后，可以在 `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` 文件夹下找到示例。

## <a name="in-this-section"></a>本部分内容

[GetProcessSample01 示例](./getprocesssample01-sample.md)此示例演示如何编写一个用于检索本地计算机上的进程的 cmdlet。

[GetProcessSample02 示例](./getprocesssample02-sample.md)此示例演示如何编写一个用于检索本地计算机上的进程的 cmdlet。 它提供了一个 Name 参数，该参数可用于指定要检索的进程。

[GetProcessSample03 示例](./getprocesssample03-sample.md)此示例演示如何编写一个用于检索本地计算机上的进程的 cmdlet。 它提供一个名称参数，该参数可接受来自管道的对象，或从对象的属性中接受值，该对象的属性名称与参数名称相同。

[GetProcessSample04 示例](./getprocesssample04-sample.md)此示例演示如何编写一个用于检索本地计算机上的进程的 cmdlet。 如果在检索过程中发生错误，则会生成非终止错误。

[GetProcessSample05 示例](./getprocesssample05-sample.md)此示例显示了获取处理器 cmdlet 的完整版本。

[StopProcessSample01 示例](./stopprocesssample01-sample.md)此示例演示如何编写一个 cmdlet，用于在尝试停止进程之前请求用户提供反馈，以及如何实现 `PassThru` 参数，该参数指示用户希望该 cmdlet 返回对象。

[StopProcessSample02 示例](./stopprocesssample02-sample.md)此示例演示如何编写一个在本地计算机上停止进程时写入调试、详细和警告消息的 cmdlet。

[StopProcessSample03 示例](./stopprocesssample03-sample.md)此示例演示如何编写一个 cmdlet，该 cmdlet 的参数具有别名并支持通配符。

[StopProcessSample04 示例](./stopprocesssample04-sample.md)此示例演示如何编写声明参数集、指定默认参数集并可接受输入对象的 cmdlet。

[Events01 示例](./events01-sample.md)此示例演示如何创建允许用户注册[Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)引发的事件的 cmdlet。 例如，使用此 cmdlet 时，用户可以注册在特定目录下创建文件时要执行的操作。 此示例是从[Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基类派生的。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

---
title: Windows PowerShell 示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: e9df44b17453e9f73f6eb388d9cbc8a69fce4ba2
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847996"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell 示例代码

Windows PowerShell®示例通过 Windows SDK 提供。 本部分包含 Windows SDK 示例中包含的示例代码。

> [!NOTE]
> 在安装 Windows SDK 时，将创建一个**示例**目录，在该目录中，将提供所有的 Windows PowerShell 示例。 典型的安装目录为**C:\Program Files\Microsoft SDKs\Windows\v6.0**。
> 启动 Windows PowerShell 并键入 **"cd Samples\SysMgmt\PowerShell"** 以查找 Windows PowerShell 示例目录。 在本文档中，Windows powershell 示例目录被称为 **\<PowerShell 示例 >** 。

## <a name="sample-code-listing"></a>示例代码列表

|示例代码|说明|
|-----------------|-----------------|
|[AccessDbProviderSample01 代码示例](./accessdbprovidersample01-code-sample.md)|这是[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)中所述的提供程序。|
|[AccessDbProviderSample02 代码示例](./accessdbprovidersample02-code-sample.md)|这是[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)中所述的提供程序。|
|[AccessDbProviderSample03 代码示例](./accessdbprovidersample03-code-sample.md)|这是[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)中所述的提供程序。|
|[AccessDbProviderSample04 代码示例](./accessdbprovidersample04-code-sample.md)|这是[创建 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)中所述的提供程序。|
|[AccessDbProviderSample05 代码示例](./accessdbprovidersample05-code-sample.md)|这是[创建 Windows PowerShell 导航提供程序](./creating-a-windows-powershell-navigation-provider.md)中所述的提供程序。|
|[AccessDbProviderSample06 代码示例](./accessdbprovidersample06-code-sample.md)|这是[创建 Windows PowerShell 内容提供程序](./creating-a-windows-powershell-content-provider.md)中所述的提供程序。|
|[GetProc01 代码示例](./getproc01-code-samples.md)|这是`Get-Process` [创建第一个 cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)中所述的基本 cmdlet 示例。|
|[GetProc02 代码示例](./getproc02-code-samples.md)|这是`Get-Process` [添加处理命令行输入的参数](../cmdlet/adding-parameters-that-process-command-line-input.md)中所述的 cmdlet 示例。|
|[GetProc03 代码示例](./getproc03-code-samples.md)|这是`Get-Process` [添加处理管道输入的参数](../cmdlet/adding-parameters-that-process-pipeline-input.md)中所述的 cmdlet 示例。|
|[GetProc04 代码示例](./getproc04-code-samples.md)|这是`Get-Process` [将非终止错误报告添加到 cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 cmdlet 示例。|
|[GetProc05 代码示例](./getproc05-code-samples.md)|此`Get-Process` cmdlet 类似于在[cmdlet 中添加非终止错误报告](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 cmdlet。|
|[StopProc01 代码示例](./stopproc01-code-samples.md)|这是`Stop-Process` [创建修改系统的 cmdlet](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md)中所述的 cmdlet 示例。|
|[StopProcessSample04 代码示例](./stopprocesssample04-code-samples.md)|这是`Stop-Process` [将参数集添加到 cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)中所述的 cmdlet 示例。|
|[Runspace01 代码示例](./runspace01-code-samples.md)|下面是[创建运行指定命令的控制台应用程序](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)中所述的运行空间的代码示例。|
|[Runspace02 代码示例](./runspace02-code-samples.md)|此示例使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来同步执行`Get-Process` cmdlet。|
|[RunSpace03 代码示例](./runspace03-code-samples.md)|下面是 "创建运行指定脚本的控制台应用程序" 中所述的运行空间的代码示例。|
|[RunSpace04 代码示例](./runspace04-code-samples.md)|这是一个运行空间的代码示例，它使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来执行生成终止错误的脚本。|
|[RunSpace05 代码示例](./runspace05-code-sample.md)|这是[使用 RunspaceConfiguration 配置运行空间](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)中所述的 Runspace05 示例的源代码。|
|[RunSpace06 代码示例](./runspace06-code-sample.md)|这是[使用 Windows PowerShell 管理单元配置运行空间](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)中所述的 Runspace06 示例的源代码。|
|[RunSpace07 代码示例](./runspace07-code-sample.md)|这是在[创建将命令添加到管道中的控制台应用程序](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述的 Runspace07 示例的源代码。|
|[RunSpace08 代码示例](./runspace08-code-sample.md)|这是在[创建将参数添加到命令中的控制台应用程序](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)中所述的 Runspace08 示例的源代码。|
|[RunSpace09 代码示例](./runspace09-code-sample.md)|这是[创建以异步方式调用管道的控制台应用程序](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)中所述的 Runspace09 示例的源代码。|
|[RunSpace10 代码示例](./runspace10-code-sample.md)|这是 Runspace10 示例的源代码，它将 cmdlet 添加到[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然后使用修改后的配置信息来创建运行空间。|

## <a name="see-also"></a>另请参阅

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
---
title: Windows PowerShell 参考 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 86595ebaac32318a4e3b9a3c4b295c73fb2e1c75
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055489"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell 参考

Windows PowerShell 是 Microsoft.NET Framework 通连环境设计用于管理自动化。 Windows PowerShell 提供了一种新方法构建命令、 编写解决方案，以及创建基于接口的管理工具的图形用户。

Windows PowerShell 使系统管理员可通过命令执行自动化的系统资源的管理直接或通过脚本。

## <a name="developer-audience"></a>开发人员受众

Windows PowerShell 软件开发工具包 (SDK) 专为命令需要开发人员有关 Windows PowerShell 提供的 Api 的参考信息。 命令开发人员使用 Windows PowerShell 创建命令和提供程序扩展可以通过 Windows PowerShell 执行的任务。

## <a name="windows-powershell-resources"></a>Windows PowerShell 资源

Windows PowerShell SDK，除了以下资源提供的详细信息。

[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)介绍了 Windows PowerShell： 语言、 cmdlet、 提供程序，以及使用的对象。

[编写 Windows PowerShell 模块](./module/writing-a-windows-powershell-module.md)管理员、 脚本开发人员和 cmdlet 需要打包并分发其使用 Windows PowerShell 模块的 Windows PowerShell 解决方案开发人员提供信息和示例。

[编写 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md)为项目经理，他们正在设计的 cmdlet 和实现 cmdlet 代码开发人员提供信息和代码示例。

[Windows PowerShell 团队博客](https://blogs.msdn.microsoft.com/PowerShell/)用于学习及与其他 Windows PowerShell 用户协作的最佳资源。 阅读 Windows PowerShell 团队博客中，然后再加入 Windows PowerShell 用户论坛 (microsoft.public.windows.powershell)。 使用 Windows Live Search 查找其他 Windows PowerShell 博客和资源。 然后，在开发您的专业知识，随时提出您的想法。

[PowerShell 模块浏览器](/powershell/module/)提供命令行帮助主题的最新版本。

## <a name="class-libraries"></a>类库

[System.Management.Automation](/dotnet/api/System.Management.Automation)此命名空间是 Windows PowerShell 的根命名空间。 它包含的类、 枚举和实现自定义 cmdlet 所需的接口。 具体而言， [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类是从哪个所有 cmdlet 必须派生类的基类。 有关 cmdlet 的详细信息，请参阅。

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider)此命名空间包含类、 枚举和实现 Windows PowerShell 提供程序所需的接口。 具体而言， [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类是从所有 Windows PowerShell 提供程序类必须派生的基类。

[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands)此命名空间包含的 cmdlet 和提供程序通过 Windows PowerShell 实现的类。 同样，建议您创建*YourName*。命令为您实现这些 cmdlet 的命名空间。

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host)此命名空间包含类、 枚举和接口，此 cmdlet 将使用来定义用户与 Windows PowerShell 之间的交互。

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal)此命名空间包含由其他命名空间类的基类。 例如， [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute)类是基类[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)类。

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces)此命名空间包含类、 枚举和接口用于创建 Windows PowerShell 运行空间。 在此上下文中，Windows PowerShell 运行空间是在其中一个或多个 Windows PowerShell 管道调用 cmdlet 的上下文。 也就是说，cmdlet 适用的 Windows PowerShell 运行空间上下文中。 有关详细信息 aboutWindows PowerShell 运行空间，请参阅[Windows PowerShell 运行空间](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)。

---
title: Windows PowerShell 程序员&#39;指南 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 75425fbd38141fc82dd834835912c357ecfa6d2b
ms.sourcegitcommit: 0ca836d1044e46d3a7dcbc69fa93d84f74848559
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920384"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell 程序员&#39;指南

此程序员指南主要面向开发人员感兴趣的系统管理员提供的命令行管理环境。 Windows PowerShell 提供了一种用于生成公开的.NET 对象，同时允许 Windows PowerShell，若要为您完成大部分工作的管理命令的简单方法。

在传统的命令开发中，需要编写参数分析器、 参数绑定器、 筛选器和公开的每个命令的所有其他功能。 Windows PowerShell 提供了以下内容以使其更轻松地编写命令：

- 一个功能强大 Windows PowerShell 运行时 （执行引擎） 其自己的分析器和用于自动绑定命令参数的机制。

- 用于设置格式并显示使用命令行解释器 (CLI) 命令结果的实用程序。

- 支持的功能 （通过 Windows PowerShell 提供程序） 轻松地访问存储的数据的高级别。

  很少的成本，可以表示.NET 对象通过丰富的命令或一套命令，将向管理员提供完整的命令行体验。

  下一部分介绍的 Windows PowerShell 的主要概念和术语。 熟悉这些概念和术语之前开始进行开发。

## <a name="about-windows-powershell"></a>关于 Windows PowerShell

Windows PowerShell 在开发过程中定义命令，可以使用几种的类型。 这些命令包括： 函数、 筛选器、 脚本、 别名和可执行文件 （应用程序）。 本指南中讨论的主要命令类型是简单的小命令中名为"cmdlet"。 Windows PowerShell 提供一组 cmdlet，并完全支持 cmdlet 自定义以满足您的环境。 使用管道的 cmdlet 一样，Windows PowerShell 运行时将处理所有命令类型。

除了命令，Windows PowerShell 支持各种可自定义 Windows PowerShell 提供程序，可提供特定的 cmdlet 集。 外壳的运行在 Windows PowerShell 提供的主机应用程序 (Windows PowerShell.exe)，但也可从自定义主机应用程序，可以开发以满足特定要求。 有关详细信息，请参阅[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell Cmdlets

Cmdlet 是 Windows PowerShell 环境中使用的轻型命令。 Windows PowerShell 运行时调用的命令行中，在提供的自动化脚本上下文中使用这些 cmdlet 和 Windows PowerShell 运行时还将调用它们以编程方式通过 Windows PowerShell Api。

有关 cmdlet 的详细信息，请参阅[编写 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

### <a name="windows-powershell-providers"></a>Windows PowerShell 提供程序

在执行管理任务，用户可能需要检查数据存储在数据存储 （例如，文件系统、 Windows 注册表中或证书存储区）。 若要简化这些操作，Windows PowerShell 定义名为可用于访问特定的数据存储，如 Windows 注册表的 Windows PowerShell 提供程序的模块。 每个提供程序支持一组相关的 cmdlet 为用户提供的数据存储区中的对称视图。

Windows PowerShell 提供了一些默认 Windows PowerShell 提供程序。 例如，注册表提供程序支持导航和操作的 Windows 注册表。 注册表项表示为项和注册表值被视为属性。

如果公开用户将需要访问的数据存储，可能需要编写自己的 Windows PowerShell 提供程序，如中所述[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)。 有关详细信息 aboutWindows PowerShell 提供程序，请参阅[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

### <a name="host-application"></a>主机应用程序

Windows PowerShell 中包含默认主机应用程序 powershell.exe，这是与用户交互和托管 Windows PowerShell 运行时使用的控制台窗口的控制台应用程序。

只是偶尔会需要编写 Windows PowerShell 中，您自己主机应用程序虽然支持自定义。 一个用例中，您可能需要自己的应用程序是具有比默认主机应用程序提供的界面更加丰富的 GUI 界面的必要条件。 使您的 GUI 命令行上时，可能还想自定义应用程序。 有关详细信息，请参阅[如何创建一个 Windows PowerShell 主机应用程序](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)。

### <a name="windows-powershell-runtime"></a>Windows PowerShell 运行时

Windows PowerShell 运行时实现命令处理的执行引擎。 它包括提供的主机应用程序和 Windows PowerShell 命令和提供程序之间的接口的类。 Windows PowerShell 运行时当前 Windows PowerShell 会话，这是 shell 和命令执行的操作环境作为运行空间对象实现。 有关操作的详细信息，请参阅[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

### <a name="windows-powershell-language"></a>Windows PowerShell 语言

Windows PowerShell 语言提供了脚本编写功能和机制来调用命令。 有关脚本的完整信息，请参阅 Windows PowerShell 语言参考随 Windows PowerShell。

### <a name="extended-type-system-ets"></a>扩展的类型系统 (ETS)

Windows PowerShell 提供了对各种不同的对象，如.NET 和 XML 对象的访问。 因此，若要显示所有对象类型的公共抽象 shell 使用其扩展的类型系统 (ETS)。 大多数 ETS 功能是透明的用户，但脚本或.NET 开发人员将其用于以下目的：

- 查看特定对象的成员的子集。 Windows PowerShell 提供了几个特定对象类型的"调整"视图。

- 将成员添加到现有对象。

- 访问序列化对象。

- 编写自定义的对象。

  使用 ETS，您可以创建灵活的新"类型"的 Windows PowerShell 语言与兼容。 如果您是.NET 开发人员，现在可以以使用 Windows PowerShell 语言适用于编写脚本，例如使用相同的语义的对象，以确定一个对象计算结果为`true`。

  有关 ETS 和 Windows PowerShell 如何使用对象的详细信息，请参阅[Windows PowerShell 对象概念](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)。

## <a name="programming-for-windows-powershell"></a>适用于 Windows PowerShell 的编程

Windows PowerShell 定义其代码命令、 提供程序，以及使用.NET Framework 的其他程序模块。 您不局限于使用 Microsoft Visual Studio 中为 Windows PowerShell 创建自定义的模块尽管本指南中提供的示例已知要运行此工具中。 可以使用任何.NET 语言，支持类继承和使用的属性。 在某些情况下，Windows PowerShell Api 需要能够访问的泛型类型的编程语言。

## <a name="programmers-reference"></a>程序员参考

有关针对 Windows PowerShell 进行开发时参考，请参阅[Windows PowerShell SDK](../windows-powershell-reference.md)。

## <a name="getting-started-using-windows-powershell"></a>使用 Windows PowerShell 入门

有关如何开始使用 Windows PowerShell 外壳的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)随 Windows PowerShell。 快速参考三折文档还提供作为 cmdlet 使用的入门读物。

## <a name="contents-of-this-guide"></a>本指南的内容

|主题|定义|
|-----------|----------------|
|[如何创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)|本部分介绍如何生成 Windows PowerShell 的 Windows PowerShell 提供程序。|
|[如何创建 Windows PowerShell 主机应用程序](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|本部分介绍如何编写操作的运行空间的主机应用程序以及如何编写实现自己的自定义主机的主机应用程序。|
|[如何创建 Windows PowerShell 管理单元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|本部分介绍如何创建管理单元，用于注册的程序集中的所有 cmdlet 和提供程序以及如何创建自定义管理单元中。|
|[如何创建控制台 Shell](./how-to-create-a-console-shell.md)|本部分介绍如何创建不可扩展的控制台 shell。|
|[Windows PowerShell 概念](./windows-powershell-concepts.md)|本部分包含可帮助您了解 Windows PowerShell 从开发人员的角度来看的概念性信息。|

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)

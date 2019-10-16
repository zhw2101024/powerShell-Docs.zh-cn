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
ms.openlocfilehash: 44a9c970d32dc6f98456227f8b02101280541dd9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360046"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell 程序员&#39;指南

此程序员指南面向有兴趣为系统管理员提供命令行管理环境的开发人员。 Windows PowerShell 提供了一种简单的方法来生成公开 .NET 对象的管理命令，同时允许 Windows PowerShell 为你完成大部分工作。

在传统的命令开发中，需要编写参数分析器、参数联编程序、筛选器以及每个命令公开的所有其他功能。 Windows PowerShell 提供下列内容，便于你编写命令：

- 强大的 Windows PowerShell 运行时（执行引擎）及其自己的分析器和用于自动绑定命令参数的机制。

- 使用命令行解释器（CLI）设置和显示命令结果的实用程序。

- 支持高级别的功能（通过 Windows PowerShell 提供程序），使访问存储的数据变得轻松。

  只需很少的成本，你可以通过一个丰富的命令或一组命令来表示 .NET 对象，这些命令将向管理员提供完整的命令行体验。

  下一部分介绍了 Windows PowerShell 的主要概念和术语。 开始开发之前，请先熟悉这些概念和术语。

## <a name="about-windows-powershell"></a>关于 Windows PowerShell

Windows PowerShell 定义了几种可用于开发的命令类型。 这些命令包括：函数、筛选器、脚本、别名和可执行文件（应用程序）。 本指南中讨论的主命令类型是一个简单的小命令，称为 "cmdlet"。 Windows PowerShell furnishes 一组 cmdlet，并完全支持 cmdlet 自定义以适合你的环境。 Windows PowerShell 运行时处理所有命令类型，就像使用管道执行 cmdlet 一样。

除了命令以外，Windows PowerShell 还支持各种可自定义的 Windows PowerShell 提供程序，这些提供程序可提供特定的 cmdlet 集。 Shell 在 Windows PowerShell 提供的主机应用程序（Windows PowerShell）中运行，但它可以通过可开发的自定义主机应用程序进行访问，以满足特定的要求。 有关详细信息，请参阅[Windows PowerShell 的工作原理](/previous-versions//ms714658(v=vs.85))。

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell Cmdlet

Cmdlet 是在 Windows PowerShell 环境中使用的轻量命令。 Windows PowerShell 运行时在命令行中提供的自动化脚本的上下文中调用这些 cmdlet，而且 Windows PowerShell 运行时还会通过 Windows PowerShell Api 以编程方式调用它们。

有关 cmdlet 的详细信息，请参阅[编写 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

### <a name="windows-powershell-providers"></a>Windows PowerShell 提供程序

在执行管理任务时，用户可能需要检查存储在数据存储中的数据（例如，文件系统、Windows 注册表或证书存储区）。 为了使这些操作更容易，Windows PowerShell 定义了一个名为 Windows PowerShell 提供程序的模块，该模块可用于访问特定的数据存储，如 Windows 注册表。 每个提供程序都支持一组相关的 cmdlet，以便为用户提供存储区中数据的对称视图。

Windows PowerShell 提供多个默认的 Windows PowerShell 提供程序。 例如，注册表提供程序支持导航和操作 Windows 注册表。 注册表项表示为项，注册表值被视为属性。

如果公开用户需要访问的数据存储区，可能需要编写自己的 Windows PowerShell 提供程序，如[创建 Windows Powershell 提供](./how-to-create-a-windows-powershell-provider.md)程序中所述。 AboutWindows PowerShell 提供程序的详细信息，请参阅[Windows powershell 的工作原理](/previous-versions//ms714658(v=vs.85))。

### <a name="host-application"></a>主机应用程序

Windows PowerShell 包含默认主机应用程序 PowerShell，它是一个控制台应用程序，它与用户交互，并使用控制台窗口托管 Windows PowerShell 运行时。

尽管支持自定义，但很少需要为 Windows PowerShell 编写自己的主机应用程序。 可能需要您自己的应用程序的一种情况是，您要求的 GUI 界面比默认主机应用程序提供的界面更丰富。 当你在命令行上将 GUI 作为基础时，你可能还需要自定义应用程序。 有关详细信息，请参阅[如何创建 Windows PowerShell 主机应用程序](/powershell/developer/hosting/writing-a-windows-powershell-host-application)。

### <a name="windows-powershell-runtime"></a>Windows PowerShell 运行时

Windows PowerShell 运行时是实现命令处理的执行引擎。 它包含提供主机应用程序和 Windows PowerShell 命令与提供程序之间的接口的类。 Windows PowerShell 运行时实现为当前 Windows PowerShell 会话的运行空间对象，这是执行 shell 和命令的操作环境。 有关操作的详细信息，请参阅[Windows PowerShell 的工作原理](/previous-versions//ms714658(v=vs.85))。

### <a name="windows-powershell-language"></a>Windows PowerShell 语言

Windows PowerShell 语言提供用于调用命令的脚本函数和机制。 有关完整的脚本信息，请参阅 Windows PowerShell 随附的 Windows PowerShell 语言参考。

### <a name="extended-type-system-ets"></a>扩展类型系统（ETS）

Windows PowerShell 提供对各种不同对象（如 .NET 和 XML 对象）的访问。 因此，为了提供所有对象类型的公共抽象，shell 使用其扩展类型系统（ETS）。 大多数 ETS 功能对于用户是透明的，但脚本或 .NET 开发人员将使用它来实现以下目的：

- 查看特定对象的部分成员。 Windows PowerShell 提供多个特定对象类型的 "改编的" 视图。

- 将成员添加到现有对象。

- 对序列化对象的访问。

- 编写自定义对象。

  使用 ETS，可以创建与 Windows PowerShell 语言兼容的灵活的新 "类型"。 如果你是 .NET 开发人员，则可以使用与 Windows PowerShell 语言相同的语义来处理对象，例如，确定对象的计算结果是否为 `true`。

  有关 ETS 以及 Windows PowerShell 如何使用对象的详细信息，请参阅[Windows Powershell 对象概念](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6)。

## <a name="programming-for-windows-powershell"></a>Windows PowerShell 编程

Windows PowerShell 使用 .NET Framework 为命令、提供程序和其他程序模块定义其代码。 尽管本指南中提供的示例在此工具中运行，但并不局限于使用 Microsoft Visual Studio 来为 Windows PowerShell 创建自定义模块。 您可以使用支持类继承和属性使用的任何 .NET 语言。 在某些情况下，Windows PowerShell Api 需要编程语言才能访问泛型类型。

## <a name="programmers-reference"></a>程序员参考

有关为 Windows PowerShell 进行开发时的参考，请参阅[Windows POWERSHELL SDK](../windows-powershell-reference.md)。

## <a name="getting-started-using-windows-powershell"></a>使用 Windows PowerShell 入门

有关开始使用 Windows PowerShell shell 的详细信息，请参阅随 windows powershell 一起提供的[Windows powershell 入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。 快速参考三栏式文档也作为 cmdlet 使用的入门教程提供。

## <a name="contents-of-this-guide"></a>本指南的内容

|主题|定义|
|-----------|----------------|
|[如何创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)|本部分介绍如何生成适用于 Windows PowerShell 的 Windows PowerShell 提供程序。|
|[如何创建 Windows PowerShell 主机应用程序](/powershell/developer/hosting/writing-a-windows-powershell-host-application)|本部分介绍如何编写操作运行空间的主机应用程序，以及如何编写可实现其自己的自定义主机的主机应用程序。|
|[如何创建 Windows PowerShell 管理单元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|本部分介绍如何创建用于在程序集中注册所有 cmdlet 和提供程序的管理单元，以及如何创建自定义管理单元。|
|[如何创建控制台 Shell](./how-to-create-a-console-shell.md)|本部分介绍如何创建不可扩展的控制台 shell。|
|[Windows PowerShell 概念](./windows-powershell-concepts.md)|本部分包含有助于从开发人员的角度了解 Windows PowerShell 的概念信息。|

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)

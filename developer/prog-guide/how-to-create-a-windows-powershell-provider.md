---
title: 如何创建 Windows PowerShell 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081744"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>如何创建 Windows PowerShell 提供程序

本部分介绍如何生成 Windows PowerShell 提供程序。 Windows PowerShell 提供程序可被视为两种方式。 对用户来说，该提供程序表示一组存储数据。 例如，存储的数据可以是 Internet 信息服务 (IIS) 元数据库、 Microsoft Windows 注册表、 Windows 文件系统、 Active Directory 和存储的 Windows PowerShell 变量和别名数据。

向开发人员，Windows PowerShell 提供程序是在用户和用户需要访问的数据之间的接口。 从这个角度看，每种类型的此部分中所述的提供程序支持一组特定的基类和接口，允许 Windows PowerShell 运行时以常见的方式公开给用户的某些 cmdlet。

## <a name="providers-provided-by-windows-powershell"></a>提供的 Windows PowerShell 提供程序

Windows PowerShell 提供了多个提供程序 （例如 FileSystem 提供程序、 注册表提供程序和 Alias 提供程序） 用来访问已知的数据存储。 有关由 Windows PowerShell 提供的提供程序的详细信息，请使用以下命令，以获取联机帮助：

**PS > 获取帮助 about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>访问存储的数据使用 Windows PowerShell 路径

Windows PowerShell 提供程序都可以访问 Windows PowerShell 运行时和以编程方式通过使用 Windows PowerShell 路径的命令。 大多数情况下，这些路径用于直接通过提供程序访问数据。 但是，某些路径可被解析为提供程序内部的路径，允许使用 Windows PowerShell 应用程序编程接口 (Api) 来访问数据的 cmdlet。 有关 Windows PowerShell 提供程序如何在 Windows PowerShell 中运行的详细信息，请参阅[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>公开提供程序 Cmdlet 使用 Windows PowerShell 驱动器

Windows PowerShell 提供程序公开其支持的 cmdlet 使用虚拟 Windows PowerShell 驱动器。 Windows PowerShell 适用的 Windows PowerShell 驱动器的以下规则：

- 驱动器的名称可以是任何字母数字的序列。

- 可以在名为"root"的路径上的任意有效点指定驱动器。

- 驱动器可以实现的任何存储的数据，而不仅仅是文件系统。

- 每个驱动器会保留其自己的当前工作位置，这样就允许用户驱动器之间切换时保留上下文。

## <a name="in-this-section"></a>本部分内容

下表列出了包含相互关联的代码示例的主题。 从开始第二个主题，基本的 Windows PowerShell 提供程序可以初始化，并通过 Windows PowerShell 运行时未初始化、 下一主题将添加用于访问数据的功能、 下一主题将添加用于处理数据 （功能存储的数据中的项），依次类推。

|主题|定义|
|-----------|----------------|
|[设计 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)|本主题讨论了实现 Windows PowerShell 提供程序之前，应考虑的事项。 它概述了 Windows PowerShell 提供程序基类和接口。|
|[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)|本主题演示如何创建允许 Windows PowerShell 运行时初始化和取消初始化提供程序的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)|本主题演示如何创建允许用户通过 Windows PowerShell 驱动器访问数据存储区的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)|本主题演示如何创建允许用户用来处理数据存储区中的项的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)|本主题演示如何创建允许用户在多层数据存储上处理的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 导航提供程序](./creating-a-windows-powershell-navigation-provider.md)|本主题演示如何创建允许用户以分层方式导航的项的数据存储区的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 内容提供程序](./creating-a-windows-powershell-content-provider.md)|本主题演示如何创建 Windows PowerShell 提供程序，允许用户用来处理数据存储区中的各项的内容。|
|[创建 Windows PowerShell 属性提供程序](./creating-a-windows-powershell-property-provider.md)|本主题演示如何创建 Windows PowerShell 提供程序，允许用户用来处理数据存储区中的项的属性。|

## <a name="see-also"></a>另请参阅

[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

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
ms.openlocfilehash: ffbf8028ba2b52e77d8e22c061baa9b8b67f6da3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366646"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>如何创建 Windows PowerShell 提供程序

本部分介绍如何生成 Windows PowerShell 提供程序。 可以通过两种方式来考虑 Windows PowerShell 提供程序。 对于用户，提供程序表示一组存储的数据。 例如，存储的数据可以是 Internet Information Services （IIS）元数据库、Microsoft Windows 注册表、Windows 文件系统、Active Directory 以及 Windows PowerShell 存储的变量和别名数据。

对于开发人员而言，Windows PowerShell 提供程序是用户与用户需要访问的数据之间的接口。 从此角度来看，本节中所述的每种类型的提供程序支持一组特定的基类和接口，这些类和接口允许 Windows PowerShell 运行时以常见方式向用户公开特定的 cmdlet。

## <a name="providers-provided-by-windows-powershell"></a>Windows PowerShell 提供的提供程序

Windows PowerShell 提供了几个提供程序（例如 FileSystem 提供程序、注册表提供程序和别名提供程序），用于访问已知的数据存储区。 有关 Windows PowerShell 提供的提供程序的详细信息，请使用以下命令访问联机帮助：

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>使用 Windows PowerShell 路径访问存储的数据

Windows powershell 运行时和通过使用 Windows PowerShell 路径以编程方式访问 windows PowerShell 提供程序。 大多数情况下，这些路径用于通过提供程序直接访问数据。 但是，某些路径可解析为提供程序内部路径，该路径允许 cmdlet 使用非 Windows PowerShell 应用程序编程接口（Api）来访问数据。 有关 Windows powershell 提供程序在 Windows PowerShell 中的运行方式的详细信息，请参阅[Windows powershell 的工作](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)原理。

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>使用 Windows PowerShell 驱动器公开提供程序 Cmdlet

Windows PowerShell 提供程序使用虚拟 Windows PowerShell 驱动器公开其支持的 cmdlet。 Windows PowerShell 适用于 Windows PowerShell 驱动器的以下规则：

- 驱动器的名称可以是任何字母数字序列。

- 可以在路径上的任何有效点指定驱动器，称为 "根"。

- 可以为任何存储的数据（而不仅仅是文件系统）实现驱动器。

- 每个驱动器都保留其自己的当前工作位置，允许用户在驱动器之间切换时保留上下文。

## <a name="in-this-section"></a>本部分内容

下表列出了一些主题，这些主题包括彼此之间生成的代码示例。 从第二个主题开始，Windows PowerShell 运行时可以初始化和取消初始化基本 Windows PowerShell 提供程序，下一主题添加了用于访问数据的功能，下一主题添加了用于操作数据的功能（存储的数据中的项）等。

|主题|定义|
|-----------|----------------|
|[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)|本主题讨论在实现 Windows PowerShell 提供程序之前应考虑的事项。 它汇总了所使用的 Windows PowerShell 提供程序的基类和接口。|
|[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)|本主题介绍如何创建 Windows PowerShell 提供程序，以允许 Windows PowerShell 运行时初始化和取消初始化提供程序。|
|[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)|本主题介绍如何创建允许用户通过 Windows PowerShell 驱动器访问数据存储的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)|本主题演示如何创建允许用户操作数据存储区中的项的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)|本主题演示如何创建允许用户处理多层数据存储的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 导航提供程序](./creating-a-windows-powershell-navigation-provider.md)|本主题介绍如何创建 Windows PowerShell 提供程序，该提供程序允许用户以分层方式浏览数据存储区中的项。|
|[创建 Windows PowerShell 内容提供程序](./creating-a-windows-powershell-content-provider.md)|本主题演示如何创建允许用户操作数据存储区中项内容的 Windows PowerShell 提供程序。|
|[创建 Windows PowerShell 属性提供程序](./creating-a-windows-powershell-property-provider.md)|本主题演示如何创建允许用户操作数据存储区中项的属性的 Windows PowerShell 提供程序。|

## <a name="see-also"></a>另请参阅

[Windows PowerShell 的工作原理](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

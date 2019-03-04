---
title: Cmdlet 类声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854443"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet 类声明

通过指定 Microsoft.NET Framework 类声明为 cmdlet **Cmdlet**作为元数据类的属性。 ( **Cmdlet**属性是唯一的必需的属性的所有 cmdlet 为)。 当指定**Cmdlet**属性，则必须指定标识向用户 cmdlet 的动词-名词对。 并且，必须说明该 cmdlet 支持的 Windows PowerShell 功能。 详细了解用于指定的声明语法**Cmdlet**属性，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

> [!NOTE]
> **Cmdlet**属性定义由[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)类。 此类的属性对应于声明属性时，将使用的声明参数。

## <a name="nouns"></a>名词

该 cmdlet 的名词指定 cmdlet 作用的资源。 （） 名词，用于 cmdlet 与其他 cmdlet 区分开来。

Cmdlet 名称中的名词必须是具体而言，对于泛型名词，如*server*，最好是添加一个短前缀，用于你的资源与其他类似资源区分开来。 例如，包括带前缀的名词的 cmdlet 名称是`Get-SQLServer`。 特定名词具有更多常规谓词的组合使用户能够快速找到该 cmdlet 通过其操作，然后按资源标识该 cmdlet，同时避免不必要的 cmdlet 名称重复。

不能在 cmdlet 名称中使用的特殊字符的列表，请参阅[所需开发指导原则](./required-development-guidelines.md)。

## <a name="verbs"></a>谓词

如果指定一个谓词，开发指导原则将要求你使用某一 Windows PowerShell 提供的预定义的谓词。 通过使用这些预定义的谓词之一，您需要确保您编写的 cmdlet 和由 Microsoft 和其他人编写的 cmdlet 之间的一致性。 例如，"Get"谓词用于检索数据的 cmdlet。

有关谓词的指导原则的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。 不能在 cmdlet 名称中使用的特殊字符的列表，请参阅[所需开发指导原则](./required-development-guidelines.md)。

## <a name="supporting-windows-powershell-functionality"></a>支持 Windows PowerShell 功能

**Cmdlet**属性还允许您指定 cmdlet 支持一些提供的 Windows PowerShell 的常见功能。 这包括对常见功能，例如用户反馈确认 （称为 ShouldProcess 功能的支持） 的支持以及对事务的支持。 （对事务的支持引入了在 Windows PowerShell 2.0 中）。

详细了解用于指定的声明语法**Cmdlet**属性，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

## <a name="cmdlet-class-definition"></a>Cmdlet 类定义

以下代码是 GetProc cmdlet 类的定义。 请注意，使用大小写，Pascal 和类的名称，包括动词和名词的 cmdlet。

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal 大小写

当命名 cmdlet 时，使用 Pascal 大小写。 例如，`Get-Item`和`Get-ItemProperty`cmdlet 显示命名 cmdlet 时使用的大小写的正确方法。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute Declaration](./cmdlet-attribute-declaration.md)

[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)

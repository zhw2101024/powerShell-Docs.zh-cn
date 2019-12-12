---
title: 正在写入 PowerShell 格式化文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361406"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="cab40-102">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="cab40-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="cab40-103">对于正在编写将对象输出到命令行的 cmdlet 或函数的命令开发人员，"编写 PowerShell 格式文件"。</span><span class="sxs-lookup"><span data-stu-id="cab40-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="cab40-104">格式化文件定义 PowerShell 如何在命令行中显示这些对象。</span><span class="sxs-lookup"><span data-stu-id="cab40-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="cab40-105">本文档概述了格式化文件、编写这些文件时应了解的概念的说明、这些文件中使用的 XML 示例以及 XML 元素的参考部分。</span><span class="sxs-lookup"><span data-stu-id="cab40-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cab40-106">本部分内容</span><span class="sxs-lookup"><span data-stu-id="cab40-106">In This Section</span></span>

<span data-ttu-id="cab40-107">[格式化文件概述](./formatting-file-overview.md)描述格式化文件的定义和格式设置文件的常规组件，包括可以在文件中定义的常见功能、可以为 .NET 对象定义的不同类型的格式视图，以及用于定义表视图的 XML 简化示例。</span><span class="sxs-lookup"><span data-stu-id="cab40-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="cab40-108">[格式化文件概念](./formatting-file-concepts.md)包含您在创建自己的格式设置文件时可能需要了解的信息，如您可以定义的不同类型的视图，以及这些视图的特殊组件。</span><span class="sxs-lookup"><span data-stu-id="cab40-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="cab40-109">[格式化文件的示例](./examples-of-formatting-files.md)提供了多个格式设置文件的 XML 示例，包括表格视图的示例、列表视图和宽视图，以及演示如何定义选项集、选择条件和公共控件等功能的示例。</span><span class="sxs-lookup"><span data-stu-id="cab40-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="cab40-110">[格式 XML 引用](./format-schema-xml-reference.md)包括用于格式化文件中的 XML 元素的参考主题。</span><span class="sxs-lookup"><span data-stu-id="cab40-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>

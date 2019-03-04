---
title: 编写 PowerShell 格式设置文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857043"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="65813-102">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="65813-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="65813-103">"编写 PowerShell 格式设置文件"适用于命令开发人员要编写 cmdlet 或函数的输出到命令行的对象。</span><span class="sxs-lookup"><span data-stu-id="65813-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="65813-104">格式设置文件定义 PowerShell 在命令行中显示这些对象的方式。</span><span class="sxs-lookup"><span data-stu-id="65813-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="65813-105">本文档中概述的格式设置文件，写入这些文件，这些文件，并参考部分中使用的 XML 元素的 XML 的示例时，应了解的概念的说明。</span><span class="sxs-lookup"><span data-stu-id="65813-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="65813-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="65813-106">In This Section</span></span>

<span data-ttu-id="65813-107">[格式设置文件概述](./formatting-file-overview.md)格式化文件的描述和格式设置文件，包括可以在文件中，不同类型的格式可以为.NET 对象定义的视图定义的常见功能的常规组件和一个用于定义表视图的 xml 的简化的示例。</span><span class="sxs-lookup"><span data-stu-id="65813-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="65813-108">[格式设置文件概念](./formatting-file-concepts.md)包括可能需要知道创建您自己的格式文件时，如不同类型的视图可以定义和特殊组件的这些视图的信息。</span><span class="sxs-lookup"><span data-stu-id="65813-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="65813-109">[格式设置文件的示例](./examples-of-formatting-files.md)的多个格式设置文件，包括示例的表视图、 列表视图中和较宽的视图，以及演示如何定义功能，例如选择集，选择条件的示例提供了 XML 示例和公共控件。</span><span class="sxs-lookup"><span data-stu-id="65813-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="65813-110">[格式化 XML 引用](./format-schema-xml-reference.md)包括格式设置文件中使用的 XML 元素参考主题。</span><span class="sxs-lookup"><span data-stu-id="65813-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>

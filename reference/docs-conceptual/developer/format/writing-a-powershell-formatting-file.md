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
# <a name="writing-a-powershell-formatting-file"></a>编写 PowerShell 格式设置文件

对于正在编写将对象输出到命令行的 cmdlet 或函数的命令开发人员，"编写 PowerShell 格式文件"。 格式化文件定义 PowerShell 如何在命令行中显示这些对象。 本文档概述了格式化文件、编写这些文件时应了解的概念的说明、这些文件中使用的 XML 示例以及 XML 元素的参考部分。

## <a name="in-this-section"></a>本部分内容

[格式化文件概述](./formatting-file-overview.md)描述格式化文件的定义和格式设置文件的常规组件，包括可以在文件中定义的常见功能、可以为 .NET 对象定义的不同类型的格式视图，以及用于定义表视图的 XML 简化示例。

[格式化文件概念](./formatting-file-concepts.md)包含您在创建自己的格式设置文件时可能需要了解的信息，如您可以定义的不同类型的视图，以及这些视图的特殊组件。

[格式化文件的示例](./examples-of-formatting-files.md)提供了多个格式设置文件的 XML 示例，包括表格视图的示例、列表视图和宽视图，以及演示如何定义选项集、选择条件和公共控件等功能的示例。

[格式 XML 引用](./format-schema-xml-reference.md)包括用于格式化文件中的 XML 元素的参考主题。

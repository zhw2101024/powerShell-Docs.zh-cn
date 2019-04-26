---
title: PowerShell cmdlet 编写帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083155"
---
# <a name="writing-help-for-powershell-cmdlets"></a>PowerShell Cmdlet 编写帮助

PowerShell cmdlet 可能很有用，但除非您的帮助主题清楚地说明该 cmdlet 的用途以及如何使用它，该 cmdlet 可能会开始使用或更糟糕的是，它可能会对用户。
基于 XML 的 cmdlet 帮助文件格式可提高一致性，但极佳的帮助要求更高。

如果您永远不会编写 cmdlet 帮助，请查看以下准则。
以下部分中描述所需编写 cmdlet 帮助主题的 XML 架构。
开头[创建 Cmdlet 帮助文件](./how-to-create-the-cmdlet-help-file.md)。
该主题包括的顶级 XML 节点的说明。

## <a name="writing-guidelines-for-cmdlet-help"></a>有关 Cmdlet 的帮助的作者指南

### <a name="write-well"></a>编写
执行任何操作将替换编写良好的主题。
如果您不是专业的编写器，找到要帮助您的编写器或编辑器。
另一种方法是将帮助文本复制到 Microsoft Word 和使用语法和拼写检查改进您的工作。

### <a name="write-simply"></a>只需编写
使用简单的词和短语。
避免术语。
请考虑许多读者都配备仅有外语言字典和帮助主题。

### <a name="write-consistently"></a>一致地编写
有关相关的 cmdlet 应类似 （如 get-x 和集 x） 帮助。
使用标准说明对于标准参数，如**Force**并**InputObject**。
（将它们复制的帮助中的核心 cmdlet。）使用标准条款。
例如，使用"参数"、 不"参数"和使用"cmdlet"不"命令"或者"command-let 命令。"

### <a name="start-the-synopsis-with-a-verb"></a>以动词开头摘要
摘要字段将通知用户哪些 cmdlet 不会它是什么或其工作原理。
谓词创建一个基于任务的语句，通知用户，此 cmdlet 满足其要求。
使用简单动词，如"get"、"创建"和"更改"。
避免"set"，可以是模糊和"修改"等花哨的单词。

### <a name="focus-on-objects"></a>专注于对象
大多数"get"cmdlet 显示某些内容，但其主要功能是用于获取的对象。
在您的帮助，重点介绍该对象，以便用户了解的默认显示的许多，其中一个，并且它们可以使用的方法和属性不同的方式为其检索到的对象。

### <a name="write-detailed-descriptions"></a>写入详细的说明
简要列出该 cmdlet 可以执行操作的详细说明中的所有内容。
如果主要功能是若要更改一个属性，但该 cmdlet 可以更改所有属性，列出该标签中详细说明。

### <a name="use-conventional-syntax"></a>使用传统语法
使用标准的巴科斯-诺尔格式将是很常见的 Windows 和 UNIX 命令行帮助。

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>使用 Microsoft.NET Framework 类型的参数值
（在语法和参数的说明） 的参数值的占位符显示该参数将接受的对象的.NET Framework 类型。
PowerShell 团队开发了此约定，可帮助指导有关.NET Framework 的用户。

### <a name="write-complete-parameter-descriptions"></a>写入完整的参数说明
参数说明必须让用户添加了两件事： 哪些参数的作用 （其会有影响），他们必须输入的参数值。

### <a name="write-practical-examples"></a>编写实际示例
这些示例应显示如何使用的所有参数，但最重要的事情是说明如何在实际的任务中使用该 cmdlet。
启动一个简单的示例，并编写日益复杂的示例。
在最后一个示例，演示如何在管道中使用 cmdlet。

### <a name="use-the-notes-field"></a>使用说明字段
说明字段用于解释用户需要了解该 cmdlet 的概念。
说明还可用于帮助用户避免常见错误。
避免 Url，因为它们会更改。
相反，提供要搜索的用户术语。

### <a name="test-your-help"></a>测试您的帮助
测试帮助，就像测试你的代码。
朋友和同事读取您的帮助内容，并提供反馈。
此外可以要求来自新闻组的反馈。

## <a name="see-also"></a>另请参阅

 [如何创建 Cmdlet 帮助文件](./how-to-create-the-cmdlet-help-file.md)

 [如何将 Cmdlet 名称和摘要添加到 Cmdlet 帮助主题](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何将详细的说明添加到 Cmdlet 帮助主题](./how-to-add-a-cmdlet-description.md)

 [如何将语法添加到 Cmdlet 帮助主题](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何将参数添加到 Cmdlet 帮助主题](./how-to-add-parameter-information.md)

 [如何添加到 Cmdlet 帮助主题的输入类型](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何将返回值添加到 Cmdlet 帮助主题](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何添加说明 Cmdlet 帮助主题](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何添加到 Cmdlet 帮助主题的示例](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何将相关的链接添加到 Cmdlet 帮助主题](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
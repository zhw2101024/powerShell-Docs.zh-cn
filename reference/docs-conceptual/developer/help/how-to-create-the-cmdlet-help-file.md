---
title: 如何创建 Cmdlet 帮助文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 186a8ceecea47564503dc181a76cc314033b6d3f
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996030"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>如何创建 Cmdlet 帮助文件

本部分介绍如何创建包含 Windows PowerShell cmdlet 帮助主题内容的有效 XML 文件。 本部分讨论如何命名帮助文件，如何添加相应的 XML 标头，以及如何添加将包含 cmdlet 帮助内容的不同部分的节点。

> [!NOTE]
> 若要获取帮助文件的完整视图，请打开位于 Windows PowerShell 安装目录中的 dll-Help 文件之一。 例如，dll-Help 文件包含多个 Windows PowerShell cmdlet 的内容，则不会。

### <a name="how-to-create-a-cmdlet-help-file"></a>如何创建 Cmdlet 帮助文件

1. 创建一个文本文件，并使用 UTF8 编码保存该文件。 文件名必须具有以下格式，以便 Windows PowerShell 可以将其作为 cmdlet 帮助文件进行检测。

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. 将以下 XML 标头添加到文本文件。 请注意，将根据多代理建模语言（MAML）架构对文件进行验证。 目前，Windows PowerShell 不提供任何工具来验证该文件。

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. 将命令节点添加到程序集中每个 cmdlet 的 cmdlet 帮助文件。 命令节点内的每个节点都与 cmdlet 帮助主题的不同部分相关。

   下表列出了每个节点的 XML 元素，后跟每个节点的说明。

   |节点|Description|
   |----------|-----------------|
   |`<details>`|为 cmdlet 帮助主题的名称和摘要部分添加内容。 有关详细信息，请参阅[如何添加 Cmdlet 名称和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。|
   |`<maml:description>`|添加 cmdlet 帮助主题的 "描述" 部分的内容。 有关详细信息，请参阅[如何将详细描述添加到 Cmdlet 的帮助主题](./how-to-add-a-cmdlet-description.md)。|
   |`<command:syntax>`|为 cmdlet 帮助主题的语法部分添加内容。 有关详细信息，请参阅[如何将语法添加到 Cmdlet 的帮助主题](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。|
   |`<command:parameters>`|添加 cmdlet 帮助主题的参数部分的内容。 有关详细信息，请参阅[如何将参数添加到 Cmdlet 的帮助主题](./how-to-add-parameter-information.md)。|
   |`<command:inputTypes>`|添加 cmdlet 帮助主题的 "输入" 部分的内容。 有关详细信息，请参阅[如何将输入类型添加到 Cmdlet 的帮助主题](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。|
   |`<command:returnValues>`|添加 cmdlet 帮助主题的 "输出" 部分的内容。 有关详细信息，请参阅[如何将返回值添加到 Cmdlet 的帮助主题](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。|
   |`<maml:alertset>`|将内容添加到 cmdlet 帮助主题的 "注释" 部分。 有关详细信息，请参阅[如何向 Cmdlet 帮助主题添加注释](./how-to-add-notes-to-a-cmdlet-help-topic.md)。|
   |`<command:examples>`|添加 cmdlet 帮助主题的 "示例" 部分的内容。 有关详细信息，请参阅[如何将示例添加到 Cmdlet 的帮助主题](./how-to-add-examples-to-a-cmdlet-help-topic.md)。|
   |`<maml:relatedLinks>`|添加 cmdlet 帮助主题的 "相关链接" 部分的内容。 有关详细信息，请参阅[如何将相关链接添加到 Cmdlet 的帮助主题](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。|

## <a name="example"></a>示例

 下面是一个命令节点示例，其中包含 cmdlet 帮助主题各个部分的节点。

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>另请参阅

 [如何添加 Cmdlet 名称和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何将详细描述添加到 Cmdlet 帮助主题](./how-to-add-a-cmdlet-description.md)

 [如何将语法添加到 Cmdlet 帮助主题](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何将参数添加到 Cmdlet 帮助主题](./how-to-add-parameter-information.md)

 [如何将输入类型添加到 Cmdlet 帮助主题](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何将返回值添加到 Cmdlet 帮助主题](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何向 Cmdlet 帮助主题添加注释](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何将示例添加到 Cmdlet 帮助主题](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何将相关链接添加到 Cmdlet 帮助主题](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
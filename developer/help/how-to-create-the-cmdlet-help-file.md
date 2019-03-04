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
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858973"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>如何创建 Cmdlet 帮助文件

本部分介绍如何创建有效的 XML 文件包含 Windows PowerShell cmdlet 帮助主题的内容。 本部分讨论如何命名的帮助文件、 如何添加适当的 XML 标头，以及如何添加将包含 cmdlet 的帮助内容的不同部分的节点。

> [!NOTE]
> 查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。 例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。

### <a name="how-to-create-a-cmdlet-help-file"></a>如何创建 Cmdlet 帮助文件

1. 创建一个文本文件并保存使用 UTF8 编码。 文件名称必须具有以下格式，以便 Windows PowerShell 可以将其检测为 cmdlet 帮助文件。

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. 将以下 XML 标头添加到文本文件。 请注意，将根据多个代理建模语言 （maml） 进行架构验证该文件。 目前，Windows PowerShell 不提供任何工具来验证文件。

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. 将命令节点添加到程序集中的每个 cmdlet 的 cmdlet 帮助文件。 命令节点中的每个节点与相关的 cmdlet 帮助主题的不同部分。

   下表列出了每个节点后, 跟每个节点的说明的 XML 元素。

   |节点|描述|
   |----------|-----------------|
   |`<details>`|添加的名称和摘要部分的 cmdlet 帮助主题的内容。 有关详细信息，请参阅[How to Add 的 Cmdlet 名称和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。|
   |`<maml:description>`|添加的 cmdlet 帮助主题的描述部分的内容。 有关详细信息，请参阅[如何添加到 Cmdlet 的帮助主题的详细说明](./how-to-add-a-cmdlet-description.md)。|
   |`<command:syntax>`|添加的 cmdlet 帮助主题语法部分的内容。 有关详细信息，请参阅[如何添加语法为 Cmdlet 帮助主题](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。|
   |`<command:parameters>`|添加的 cmdlet 帮助主题的 PARAMETERS 节的内容。 有关详细信息，请参阅[如何添加参数向 Cmdlet 帮助主题](./how-to-add-parameter-information.md)。|
   |`<command:inputTypes>`|添加的 cmdlet 帮助主题的输入部分的内容。 有关详细信息，请参阅[如何将输入类型添加到 Cmdlet 帮助主题](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。|
   |`<command:returnValues>`|添加内容的输出部分的 cmdlet 帮助主题。 有关详细信息，请参阅[如何添加返回的值为 Cmdlet 帮助主题](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。|
   |`<maml:alertset>`|将内容添加到 cmdlet 帮助主题的说明部分。 有关详细信息，请参阅[How to add 说明 Cmdlet 帮助主题到](./how-to-add-notes-to-a-cmdlet-help-topic.md)。|
   |`<command:examples>`|添加的 cmdlet 帮助主题的示例部分的内容。 有关详细信息，请参阅[示例添加到 Cmdlet 帮助主题如何](./how-to-add-examples-to-a-cmdlet-help-topic.md)。|
   |`<maml:relatedLinks>`|添加内容的相关链接部分的 cmdlet 帮助主题。 有关详细信息，请参阅[如何添加相关链接到 Cmdlet 帮助主题](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。|

## <a name="example"></a>示例

 下面是命令节点，包括 cmdlet 帮助主题的各个部分的节点的示例。

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
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

 [如何添加的 Cmdlet 名称和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何将详细的说明添加到 Cmdlet 帮助主题](./how-to-add-a-cmdlet-description.md)

 [如何将语法添加到 Cmdlet 帮助主题](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何将参数添加到 Cmdlet 帮助主题](./how-to-add-parameter-information.md)

 [如何将输入的类型添加到 Cmdlet 帮助主题](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何将返回值添加到 Cmdlet 帮助主题](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何添加说明到 Cmdlet 帮助主题](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何添加到 Cmdlet 帮助主题的示例](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何将相关的链接添加到 Cmdlet 帮助主题](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
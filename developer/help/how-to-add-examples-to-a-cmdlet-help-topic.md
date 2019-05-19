---
title: 如何添加到 Cmdlet 帮助主题的示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855112"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加示例

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>须知中的 Cmdlet 帮助示例

- 列出了所有参数名称在命令中，即使是可选的参数名称。 这可帮助用户轻松地解释该命令。

- 避免别名和部分参数名称，即使它们在 Windows PowerShell® 中工作。

- 在示例说明中，介绍了合理的有关构造的命令。 说明了为什么选择特定参数和值，以及如何使用变量。

- 如果该命令使用表达式，其详细信息中进行说明。

- 如果该命令使用对象的属性和方法，尤其是在默认显示中，不会显示的属性将使用示例，因为有机会告诉用户有关的对象信息。

## <a name="help-views-that-display-examples"></a>帮助显示示例的视图

仅 cmdlet 帮助的详细和完整视图中显示的示例。

## <a name="adding-an-examples-node"></a>添加示例节点

下面的 XML 演示如何添加包含一个示例中节点的示例节点。 添加你想要在本主题中包含每个示例的示例中其他节点。

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>添加示例标题

下面的 XML 演示如何以添加该示例的标题。 标题用于设置除其他示例的示例。 Windows PowerShell® 使用标准标头包含顺序示例号。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>添加上述字符

下面的 XML 演示如何添加 （不带任何干预空格） 的示例命令前立即显示的字符，如 Windows PowerShell 提示符下。 Windows PowerShell® 使用 Windows PowerShell 提示符：C:\PS>.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>添加命令

下面的 XML 演示如何以添加该示例的实际命令。 在添加该命令时，键入整个名称 （不使用别名） 的 cmdlet 和参数。 此外，使用小写字母，只要有可能。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>添加说明

下面的 XML 演示如何添加该示例的说明。 Windows PowerShell® 使用一组\<maml:para > 标记的描述，即使多个\<maml:para >，可以使用标记。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>添加示例输出

下面的 XML 演示如何添加命令的输出。 命令的结果信息是可选的但在某些情况下很有帮助，以演示中使用特定参数的效果。 Windows PowerShell® 使用两个集为空\<maml:para > 标记与命令分离命令输出。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```
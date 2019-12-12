---
title: 如何向 Cmdlet 帮助主题添加示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368106"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加示例

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>有关 Cmdlet 帮助中的示例的注意事项

- 列出命令中的所有参数名称，即使参数名称是可选的。 这可帮助用户轻松解释命令。

- 避免使用别名和部分参数名称，即使它们适用于 Windows PowerShell®。

- 在示例说明中，说明了该命令的构造的有理数。 说明选择特定参数和值的原因，以及如何使用变量。

- 如果该命令使用表达式，请详细说明。

- 如果该命令使用对象的属性和方法（特别是未出现在默认显示中的属性），则使用此示例作为机会向用户通知该对象。

## <a name="help-views-that-display-examples"></a>显示示例的帮助视图

示例仅出现在 cmdlet 帮助的详细视图和完整视图中。

## <a name="adding-an-examples-node"></a>添加示例节点

下面的 XML 演示如何添加一个示例节点，其中包含一个示例节点。 为要包含在主题中的每个示例添加其他示例节点。

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>添加示例标题

下面的 XML 演示如何添加示例的标题。 标题用于设置除其他示例之外的示例。 Windows PowerShell®使用包含连续示例编号的标准标头。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>添加前面的字符

下面的 XML 演示如何添加字符，如 Windows PowerShell prompt，它们紧靠在示例命令之前（无需任何插入空格）。 Windows PowerShell®使用 Windows PowerShell 提示符： C:\PS >。

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

下面的 XML 演示如何添加示例的实际命令。 添加命令时，请键入 cmdlet 和参数的完整名称（不使用别名）。 同时，尽可能使用小写字符。

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

下面的 XML 演示如何添加示例的说明。 Windows PowerShell®为说明使用一组 \<maml：段落 > 标记，即使可以使用多个 \<maml：段落 > 标记。

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

下面的 XML 演示如何添加命令的输出。 命令结果信息是可选的，但在某些情况下，演示使用特定参数的效果会很有帮助。 Windows PowerShell®使用两组空白 \<maml：段落 > 标记将命令输出与命令分离。

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
---
title: 如何将语法添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083376"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加语法

- [参数特性](#Parameter-Attributes)

- [参数值属性](#Parameter-Value-Attributes)

- [正在收集语法信息](#Gathering-Syntax-Information)

- [编码 XML 的语法关系图](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>若要了解的 Cmdlet 帮助中的语法关系图的内容

在开始编写 cmdlet 帮助文件中的语法关系图的 XML 的代码之前，阅读此部分，获取清楚地了解你需要提供的数据，如参数属性和该数据的语法关系图中的显示方式的类型...

### <a name="parameter-attributes"></a>参数特性

- 必需

  - 如果为 true，该参数必须出现在使用参数集的所有命令。

  - 如果为 false，则该参数是可选的参数集的所有命令。

- 位置

  - 如果名为，则需要参数名称。

  - 如果位置，参数名称是可选的。 如果省略，参数值必须在命令中指定的位置。 例如，如果值为位置 ="1"，参数值必须是第一个或唯一未命名的命令中的参数值。

- 管道输入

  - 如果为 true (ByValue)，您可以通过管道将传递的参数输入。 输入是关联 （"绑定到"） 与即使属性名称和对象类型与预期的类型不匹配的参数。 Windows PowerShell 中？参数绑定组件尝试将输入转换为正确的类型，并且仅当无法将类型转换时失败命令。 中的参数集只有一个参数可以按值相关联。

  - 如果为 true (ByPropertyName)，您可以通过管道将传递的参数输入。 但是，输入是属性的与参数关联，仅当该参数名称匹配的输入对象名称。 例如，如果参数名称为`Path`，仅当该对象具有名为路径的属性时，通过管道输送到 cmdlet 的对象是与该参数相关联。

  - 如果 true （ByValue、 ByPropertyName），可以通过管道传递的参数输入属性名称或值。 中的参数集只有一个参数可以按值相关联。

  - 如果为 false，你不能通过管道传递给此参数的输入。

- 通配

  - 如果为 true，用户键入的参数值的文本可以包含通配符字符。

  - 如果为 false，用户键入的参数值的文本不能包含通配符字符。

### <a name="parameter-value-attributes"></a>参数值属性

- 必需

  - 如果为 true，只要在命令中使用参数，就必须使用指定的值。

  - 如果为 false，则参数值是可选的。 通常情况下，值是可选的仅当它是一个多个有效的值对于参数，如枚举类型中。

参数值的必需的特性是参数的不同的必需属性。

参数的所需的属性指示是否参数 （和其值） 时必须包括调用该 cmdlet。 与此相反，仅当该参数包含在命令中使用的参数值的必需的属性。 它指示是否必须与参数一起使用该特定值。

通常情况下，占位符的参数值是必需的和文本的参数值不是必需的因为它们可能与参数一起使用的多个值之一。

### <a name="gathering-syntax-information"></a>正在收集语法信息

1. 启动 cmdlet 名称。

   ```
   SYNTAX
       Get-Tech
   ```

2. 列出所有 cmdlet 的参数。 键入短划线 （也称为"短划线"或"减号"(ASCII 45) 之前每个参数名称。 为参数集 （某些 cmdlet 可能必须只有一个参数设置） 分隔参数。 在此示例中获取技术 cmdlet 具有两个参数集。

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   开始使用 cmdlet 名称设置每个参数。

   列出首先设置的默认参数。 通过在 cmdlet 类指定默认参数。

   对于每个参数集，列出其唯一参数，除非必须首先出现的位置参数。 在上一示例中，名称和 ID 参数是两个参数集的唯一参数 （每个参数集必须具有一个参数，它仅适用于该参数集）。 这使用户更轻松地识别它们需要为参数提供哪些参数设置。

   列表应出现在命令中的顺序中的参数。 如果顺序不重要，将相关的参数列在一起，或者首先列出最常用的参数。

   请确保如果该 cmdlet 支持 ShouldProcess 列出 WhatIf 和 Confirm 参数。

   待办事项列表在语法关系图中的常见参数 （如 Verbose、 Debug 和 ErrorAction）。 `Get-Help` Cmdlet 将添加你的该信息时显示的帮助主题。

3. 添加参数的值。 在 Windows PowerShell？，由它们的.NET 类型表示参数值。 但是，类型名称可以采用缩写形式，如"string"的 System.String。

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   将类型缩写，只要它们的含义是很清晰，如"string"的 System.String 和 System.Int32 为"int"。

   列出所有值的枚举，如在上一示例中，都可以被设置为"基本"或"高级"-类型参数。

   切换参数，例如-上一示例中的列表，没有值。

4. 将尖括号内添加到参数值的占位符，相比是文本的参数值。

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. 将可选参数和其值括在方括号中。

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. 将可选参数 （对于位置参数） 的名称括在方括号中。 不需要的命令中包含参数的位置，如以下示例中中的名称参数的名称。

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. 如果参数值可以包含多个值，例如 Name 参数中的名称的列表添加一对方括号紧接参数值。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. 如果用户可以选择从参数或参数值，类型参数，如将这些选项括在大括号中，使用独占 OR symbol(;) 分隔。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. 如果参数值必须使用特定格式设置，例如双引号或括号内，在语法中显示格式。

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>编码 XML 的语法关系图

XML 的语法节点后说明节点，结尾，立即开始\</maml:description > 标记。 有关收集的语法关系图中使用的数据的信息，请参阅[收集语法信息](#Gathering-Syntax-Information)。

### <a name="adding-a-syntax-node"></a>添加的语法节点

显示 cmdlet 帮助主题中的语法关系图的数据生成的 XML 的语法节点中。 如果语法节点括在一对\<命令： 语法 > 标记。 与 cmdlet 括在一对中的每个参数集\<命令： syntaxitem > 标记。 数量没有限制\<命令： syntaxitem > 您可以添加的标记。

下面的示例演示具有两个参数集的语法项节点的语法节点。

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>将 Cmdlet 名称添加到该参数集的数据

该 cmdlet 的每个参数集的语法项节点中指定。 语法项的每个节点以开头的一对\<maml:name > 标记，其中包含该 cmdlet 的名称。

下面的示例包含具有两个参数集的语法项节点的语法节点。

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>添加参数

添加到语法项节点的每个参数指定一对大\<命令： 参数 > 标记。 需要一对\<命令： 参数 > 包含的参数集，但提供的 Windows PowerShell 通用参数在每个参数的标记？。

在打开的特性\<命令： 参数 > 标记确定参数的语法关系图中的显示方式。 有关参数属性的信息，请参阅[参数特性](#Parameter-Attributes)。

> [!NOTE]
> \<命令： 参数 > 标记支持子元素\<maml:description > 永远不会显示其内容。 参数说明中的 xml 的参数节点指定。 若要避免出现不一致的语法项中的信息之间 bodes 和省略的参数节点 (\<maml:description > 或将其留空。

下面的示例包含一个参数集使用两个参数的语法项节点。

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```

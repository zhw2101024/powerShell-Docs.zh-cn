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
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361206"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加语法

在开始编写 cmdlet 帮助文件中语法关系图的 XML 代码之前，请阅读此部分以清楚地了解你需要提供的数据类型，如参数特性，以及如何在语法关系图中显示这些数据。

### <a name="parameter-attributes"></a>参数特性

- 必需

  - 如果为 true，则参数必须出现在所有使用参数集的命令中。

  - 如果为 false，则参数在所有使用参数集的命令中是可选的。

- 置于

  - 如果已命名，则参数名称是必需的。

  - 如果是位置，则参数名称是可选的。 如果省略此参数，则参数值必须在命令中指定的位置。 例如，如果值为 position = "1"，则参数值必须是命令中的第一个或唯一一个未命名的参数值。

- 管道输入

  - 如果为 true （ByValue），则可以通过管道将输入传递给参数。 即使属性名称和对象类型与预期类型不匹配，输入也与（"绑定到"）参数相关联。 Windows PowerShell？参数绑定组件尝试将输入转换为正确的类型，并且仅在不能转换类型时才会导致命令失败。 参数集中只能有一个参数可以通过值来关联。

  - 如果为 true （ByPropertyName），则可以通过管道将输入传递给参数。 但是，仅当参数名称与输入对象的属性的名称匹配时，输入才与参数相关联。 例如，如果参数名称是 `Path`的，则仅当对象具有名为 path 的属性时，才与该参数关联的对象将与该参数相关联。

  - 如果为 true （ByValue，ByPropertyName），则可以通过属性名称或值通过管道将输入传递给参数。 参数集中只能有一个参数可以通过值来关联。

  - 如果为 false，则不能通过管道将输入传递给此参数。

- 通配

  - 如果为 true，则用户键入的参数值文本可以包含通配符。

  - 如果为 false，则用户为参数值键入的文本不能包含通配符。

### <a name="parameter-value-attributes"></a>参数值特性

- 必需

  - 如果为 true，则只要在命令中使用参数，就必须使用指定的值。

  - 如果为 false，则参数值是可选的。 通常，仅当值为参数的多个有效值之一（如枚举类型中的值）时，此值才是可选的。

参数值的必需特性与参数的必需特性不同。

参数的必需特性指示在调用 cmdlet 时是否必须包含参数（及其值）。 相反，仅当参数包含在命令中时，才使用参数值的必需特性。 它指示特定值是否必须与参数一起使用。

通常，作为占位符的参数值是必需的，参数值不是必需的，因为它们是可能与参数一起使用的几个值中的一个。

### <a name="gathering-syntax-information"></a>正在收集语法信息

1. 以 cmdlet 名称开头。

   ```
   SYNTAX
       Get-Tech
   ```

2. 列出 cmdlet 的所有参数。 在每个参数名称之前键入短划线（也称为 "破折号" 或 "减号" （ASCII 45）。 将参数分为多个参数集（某些 cmdlet 只能设置一个参数）。 在此示例中，"Get-help" cmdlet 具有两个参数集。

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   用 cmdlet 名称启动每个参数集。

   首先列出默认参数集。 默认参数是由 cmdlet 类指定的。

   对于每个参数集，请首先列出其唯一参数，除非存在必须首先出现的位置参数。 在上面的示例中，Name 和 ID 参数是这两个参数集的唯一参数（每个参数集必须有一个参数集独有的参数）。 这样，用户就可以更轻松地标识他们需要为参数集提供哪些参数。

   按它们应出现在命令中的顺序列出参数。 如果顺序不重要，请将相关参数一起列出，或首先列出最常用的参数。

   如果 cmdlet 支持 ShouldProcess，请务必列出 WhatIf 和 Confirm 参数。

   不要在语法关系图中列出常见参数（例如 Verbose、Debug 和 ErrorAction）。 `Get-Help` cmdlet 在显示 "帮助" 主题时会为你添加该信息。

3. 添加参数值。 在 Windows PowerShell 中，参数值按其 .NET 类型表示。 但是，类型名称可以缩写，如 system.string 的 "string"。

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   缩写类型的含义清楚，如 system.string 的 "string" 和 System.object 的 "int"。

   列出枚举的所有值，如上一示例中的-type 参数，可设置为 "基本" 或 "高级"。

   在前面的示例中，开关参数（如-list）没有值。

4. 与作为文本的参数值相比，将尖括号添加到作为占位符的参数值。

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. 将可选参数及其工位括在方括号中。

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. 将可选参数名称（用于位置参数）括在方括号中。 位置的参数的名称（例如以下示例中的 Name 参数）不必包含在命令中。

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. 如果参数值可以包含多个值，如 Name 参数中的名称列表，请在参数值之后直接添加一对方括号。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. 如果用户可以从参数或参数值（如类型参数）中进行选择，请将这些选项括在大括号中，并将它们与 xor 或符号（;) 分隔开。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. 如果参数值必须使用特定的格式设置，如引号或括号，则在语法中显示格式。

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>编码语法关系图 XML

XML 的语法节点紧随 description 节点后开始，该节点以 \</maml： description > 标记结尾。 有关收集语法关系图中使用的数据的信息，请参阅[收集语法信息](#gathering-syntax-information)。

### <a name="adding-a-syntax-node"></a>添加语法节点

Cmdlet 帮助主题中显示的语法关系图是从 XML 语法节点中的数据生成的。 如果 \<命令：语法 > 标记，则语法节点包含在对中。 将 cmdlet 的每个参数集括在一对 \<命令中： syntaxitem > 标记。 \<命令的数量没有限制： syntaxitem > 可以添加的标记。

下面的示例演示一个语法节点，该节点具有两个参数集的语法项节点。

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>将 Cmdlet 名称添加到参数集数据

Cmdlet 的每个参数集是在语法项节点中指定的。 每个语法项节点都以一对 \<maml：名称 > 标记组成，其中包括 cmdlet 的名称。

下面的示例包含一个语法节点，该节点具有两个参数集的语法项节点。

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

添加到语法项节点中的每个参数都是在一对 \<命令中指定的：参数 > 标记。 需要一对 \<命令：参数集中包含的每个参数 > 标记，Windows PowerShell 提供的通用参数除外？。

打开 \<command：参数 > 标记的属性确定参数在语法关系图中的显示方式。 有关参数属性的信息，请参阅[参数特性](#parameter-attributes)。

> [!NOTE]
> \<command：参数 > 标记支持子元素，\<maml： description >，其内容从未显示。 在 XML 的参数节点中指定参数说明。 若要避免语法项预兆中的信息与参数节点中的信息不一致，请省略（\<maml： description > 或将其保留为空。

下面的示例包含具有两个参数的参数集的语法项节点。

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

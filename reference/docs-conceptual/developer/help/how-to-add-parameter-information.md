---
title: 如何添加参数信息 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361226"
---
# <a name="how-to-add-parameter-information"></a>如何添加参数信息

本部分介绍如何添加在 cmdlet 帮助主题的 PARAMETERS 节中显示的内容。 帮助主题的参数部分列出了 cmdlet 的每个参数，并提供了每个参数的详细说明。

"参数" 部分的内容应与 "帮助" 主题的 "语法" 部分的内容一致。 帮助作者负责确保 "语法和 Parameters" 节点包含类似的 XML 元素。

> [!NOTE]
> 若要获取帮助文件的完整视图，请打开位于 Windows PowerShell 安装目录中的 dll-Help 文件之一。 例如，dll-Help 文件包含多个 Windows PowerShell cmdlet 的内容，则不会。

### <a name="to-add-parameters"></a>添加参数

1. 打开 cmdlet 帮助文件，找到所记录的 cmdlet 的命令节点。 如果要添加新的 cmdlet，则需要创建新的命令节点。 帮助文件将包含为其提供帮助内容的每个 cmdlet 的命令节点。 下面是空白命令节点的示例。

    ```xml
    <command:command>
    </command:command>
    ```

2. 在命令节点中，找到 "说明" 节点并添加 "参数" 节点，如下所示。 只允许一个参数节点，并且它应紧跟在语法节点之后。

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. 在 "参数" 节点中，添加 cmdlet 的每个参数的参数节点，如下所示。

   在此示例中，为三个参数添加了参数节点。

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   由于这些是在语法节点中使用的相同 XML 标记，因此，在此处指定的参数必须与 "语法" 节点指定的参数匹配，你可以从 "语法" 节点复制参数节点，然后将其粘贴到 "参数" 节点。 但是，请确保只复制参数节点的一个实例，即使该参数是在语法的多个参数集中指定的，也是如此。

4. 对于每个参数节点，设置定义每个参数的特征的属性值。 这些属性包括以下属性： required、pipelineinput 和 position。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. 对于每个参数节点，添加参数的名称。 下面是添加到参数节点的参数名称的示例。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. 对于每个参数节点，添加参数的描述。 下面是添加到参数节点的参数说明的示例。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. 对于每个参数节点，添加参数的 .NET Framework 类型。 参数类型与参数名称一起显示。

   下面是添加到参数节点 .NET Framework 类型的参数示例。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. 对于每个参数节点，添加参数的默认值。 显示内容时，会将以下句子添加到参数说明：默认值为 "默认值"。

   下面是一个将参数默认值添加到参数节点的示例。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. 对于每个具有多个值的参数，请添加一个可能的值节点。

   下面是可能的值节点的一个示例，它为参数定义了两个可能的值

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

下面是添加参数时要记住的一些内容。

- 参数的属性不会显示在 cmdlet 帮助主题的所有视图中。 但是，当用户要求提供完整（Get-help \<cmdletname >-Full）或本主题的参数（Get-help \<cmdletname >-parameter）视图时，它们会按照参数说明显示在表中。

- 参数说明是 cmdlet 帮助主题最重要的部分之一。 说明应简短，并且是完整的。 另外，请记住，如果参数说明太长，例如两个参数彼此交互，则可以在 cmdlet 帮助主题的 "注释" 部分添加更多内容。

  参数说明提供两种类型的信息。

- 使用参数时，cmdlet 执行的操作。

- 参数的合法值。

- 因为参数值表示为 .NET Framework 对象，所以用户需要的这些值的详细信息与传统命令行帮助中的值不同。 告诉用户参数要接受的数据类型，并包括示例。

如果未在命令行上指定参数，则参数的默认值是使用的值。 请注意，默认值是可选的，对于某些参数（如所需参数）不需要此值。 但是，您应为大多数可选参数指定默认值。

默认值可帮助用户了解不使用参数的影响。 描述可选路径的默认值，如 "当前目录" 或 "Windows PowerShell 安装目录（$pshome）"。 你还可以编写描述默认值的句子，如用于 `PassThru` 参数的以下句子： "如果未指定 PassThru，该 cmdlet 不会将对象向下传递管道。"  另外，由于值与字段名称 "**默认值**" 的显示顺序相反，因此不需要在条目中包含 "默认值" 一词。

此参数的默认值不会显示在 cmdlet 帮助主题的所有视图中。 但是，当用户要求提供完整（Get-help \<cmdletname >-Full）或本主题的参数（Get-help \<cmdletname >-parameter）视图时，它将显示在参数说明之后的表中（连同参数属性）。

下面的 XML 演示添加到 `<command:parameter>` 节点的 `<dev:defaultValue>` 标记对。 请注意，默认值紧跟在结束 `</command:parameterValue>` 标记之后（指定了参数值）或参数说明的结束 `</maml:description>` 标记后。 路径名.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

为枚举类型添加值

如果参数具有多个值或枚举类型的值，则可以使用可选的 \<dev： possibleValues > "节点。 使用此节点可以指定多个值的名称和描述。

请注意，枚举值的说明不显示在 `Get-Help` cmdlet 显示的任何默认帮助视图中，但其他帮助查看器可能会在其视图中显示此内容。

下面的 XML 显示一个 `<dev:possibleValues>` 节点，其中指定了两个值。

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```
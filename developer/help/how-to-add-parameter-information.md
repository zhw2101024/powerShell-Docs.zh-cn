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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083359"
---
# <a name="how-to-add-parameter-information"></a>如何添加参数信息

本部分介绍如何添加的 cmdlet 帮助主题的 PARAMETERS 节中显示的内容。 帮助主题的参数部分列出了每个 cmdlet 的参数，并提供每个参数的详细的说明。

参数部分的内容应与帮助主题语法部分的内容一致。 它可以负责帮助作者，以确保语法和参数节点包含类似的 XML 元素。

> [!NOTE]
> 查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。 例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。

### <a name="to-add-parameters"></a>若要添加参数

1. 打开 cmdlet 帮助文件并找到你所记录的 cmdlet 的命令节点。 如果要添加一个新的 cmdlet，需要创建一个新的命令节点。 帮助文件将包含你要提供的帮助内容的每个 cmdlet 的命令节点。 下面是空白的命令节点的示例。

    ```xml
    <command:command>
    </command:command>
    ```

2. 在命令节点中，找到说明节点并添加如下所示的参数节点。 允许只有一个参数节点，并且它应紧跟在语法节点。

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. 在参数节点中，添加如下所示的 cmdlet 的每个参数的参数节点。

   在此示例中，为三个参数添加的参数节点。

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   由于这些是相同的 XML 标记中的语法节点，使用，因为此处指定的参数必须与匹配的语法节点指定的参数，您可以从语法节点复制参数节点并将其粘贴到参数节点。 但是，必须确保要复制的参数节点的一个实例，即使该参数指定在语法中设置多个参数。

4. 对于每个参数节点中，设置定义的每个参数的特征的属性值。 这些属性包括以下： 所需，通配、 pipelineinput 和位置。

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

5. 对于每个参数节点中，添加参数的名称。 下面是参数名称添加到参数的节点的示例。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. 每个参数节点中，将添加的参数说明。 下面是添加到参数的节点的参数说明的示例。

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

7. 对于每个参数节点中，添加参数的.NET Framework 类型。 参数类型与参数名称一起显示。

   下面是添加到参数的节点的参数.NET Framework 类型的示例。

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

8. 对于每个参数节点中，添加参数的默认值。 显示内容时，下列句子被添加到参数说明：默认值为"DefaultValue"。

   下面是参数默认值的示例将添加到参数节点。

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

9. 每个具有多个值的参数，将添加一个可能的值节点。

   下面是示例定义两个可能值的参数的可能的值节点

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

以下是要添加的参数时，应注意一些事项。

- Cmdlet 帮助主题的所有视图中不显示参数的属性。 但是，在以下参数说明，当用户要求提供完整的表中显示 (获取帮助\<cmdletname >-完整) 或参数 (Get-help \<cmdletname >-参数) 主题的视图。

- 参数说明是一个 cmdlet 帮助主题的最重要部分。 说明应为简短，以及全面。 此外，请记住，是否参数说明变得太长，例如两个参数时彼此交互，则可以添加更多的内容的 cmdlet 帮助主题的备注部分。

  参数说明提供了两种类型的信息。

- 该 cmdlet 的用途时将使用此参数。

- 参数是什么的合法值。

- 参数值表示为.NET Framework 对象，因为用户需要有关这些值的信息不是像在传统的命令行帮助。 告知用户哪些类型的数据参数旨在用于接受，并且包含示例。

如果未在命令行上指定此参数，则使用值参数的默认值。 请注意，默认值是可选的不需要为某些参数，例如所需的参数。 但是，应指定大多数的可选参数的默认值。

默认值可帮助用户理解不使用参数的效果。 例如，"当前目录"或"Windows PowerShell 安装目录 ($pshome)"的可选路径非常明确地描述的默认值。 您还可以编写一个句子，介绍了默认情况下，例如用于下列句子`PassThru`参数："如果未指定 PassThru，该 cmdlet 未通过管道向下的对象。"  此外，因为相反的字段名称将显示的值"**默认值**"，不需要的项中包含术语"默认值"。

参数的默认值不显示在所有视图中的 cmdlet 帮助主题。 但是，在以下参数说明，当用户要求提供完整的表 （以及参数属性中） 中显示 (获取帮助\<cmdletname >-完整) 或参数 (Get-help \<cmdletname >-参数) 视图主题。

以下 XML 显示了一对`<dev:defaultValue>`标记添加到`<command:parameter>`节点。 请注意，默认值遵循结束后立即`</command:parameterValue>`标记 （如果指定的参数值） 或右`</maml:description>`标记的参数说明。 名称。

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

对于枚举类型添加值

如果该参数有多个值或枚举类型的值，则可以使用可选\<dev:possibleValues > 节点。 此节点允许您指定的名称和多个值的说明。

请注意的枚举值的说明不会出现任何默认情况下显示的帮助视图`Get-Help`cmdlet，但其他帮助查看器可能会显示此内容在自己的视图。

下面的 XML 演示`<dev:possibleValues>`节点具有两个指定的值。

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
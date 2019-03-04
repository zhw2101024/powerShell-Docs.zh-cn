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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863323"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="5a4ba-102">如何添加参数信息</span><span class="sxs-lookup"><span data-stu-id="5a4ba-102">How to Add Parameter Information</span></span>

<span data-ttu-id="5a4ba-103">本部分介绍如何添加的 cmdlet 帮助主题的 PARAMETERS 节中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="5a4ba-104">帮助主题的参数部分列出了每个 cmdlet 的参数，并提供每个参数的详细的说明。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="5a4ba-105">参数部分的内容应与帮助主题语法部分的内容一致。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="5a4ba-106">它可以负责帮助作者，以确保语法和参数节点包含类似的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="5a4ba-107">查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="5a4ba-108">例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="5a4ba-109">若要添加参数</span><span class="sxs-lookup"><span data-stu-id="5a4ba-109">To Add Parameters</span></span>

1. <span data-ttu-id="5a4ba-110">打开 cmdlet 帮助文件并找到你所记录的 cmdlet 的命令节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="5a4ba-111">如果要添加一个新的 cmdlet，需要创建一个新的命令节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="5a4ba-112">帮助文件将包含你要提供的帮助内容的每个 cmdlet 的命令节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="5a4ba-113">下面是空白的命令节点的示例。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="5a4ba-114">在命令节点中，找到说明节点并添加如下所示的参数节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="5a4ba-115">允许只有一个参数节点，并且它应紧跟在语法节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="5a4ba-116">在参数节点中，添加如下所示的 cmdlet 的每个参数的参数节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="5a4ba-117">在此示例中，为三个参数添加的参数节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="5a4ba-118">由于这些是相同的 XML 标记中的语法节点，使用，因为此处指定的参数必须与匹配的语法节点指定的参数，您可以从语法节点复制参数节点并将其粘贴到参数节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="5a4ba-119">但是，必须确保要复制的参数节点的一个实例，即使该参数指定在语法中设置多个参数。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="5a4ba-120">对于每个参数节点中，设置定义的每个参数的特征的属性值。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="5a4ba-121">这些属性包括以下： 所需，通配、 pipelineinput 和位置。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="5a4ba-122">对于每个参数节点中，添加参数的名称。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="5a4ba-123">下面是参数名称添加到参数的节点的示例。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="5a4ba-124">每个参数节点中，将添加的参数说明。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="5a4ba-125">下面是添加到参数的节点的参数说明的示例。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="5a4ba-126">对于每个参数节点中，添加参数的.NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="5a4ba-127">参数类型与参数名称一起显示。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="5a4ba-128">下面是添加到参数的节点的参数.NET Framework 类型的示例。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="5a4ba-129">对于每个参数节点中，添加参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="5a4ba-130">显示内容时，下列句子被添加到参数说明：默认值为"DefaultValue"。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="5a4ba-131">下面是参数默认值的示例将添加到参数节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="5a4ba-132">每个具有多个值的参数，将添加一个可能的值节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="5a4ba-133">下面是示例定义两个可能值的参数的可能的值节点</span><span class="sxs-lookup"><span data-stu-id="5a4ba-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="5a4ba-134">以下是要添加的参数时，应注意一些事项。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="5a4ba-135">Cmdlet 帮助主题的所有视图中不显示参数的属性。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="5a4ba-136">但是，在以下参数说明，当用户要求提供完整的表中显示 (获取帮助\<cmdletname >-完整) 或参数 (Get-help \<cmdletname >-参数) 主题的视图。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="5a4ba-137">参数说明是一个 cmdlet 帮助主题的最重要部分。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="5a4ba-138">说明应为简短，以及全面。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="5a4ba-139">此外，请记住，是否参数说明变得太长，例如两个参数时彼此交互，则可以添加更多的内容的 cmdlet 帮助主题的备注部分。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="5a4ba-140">参数说明提供了两种类型的信息。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="5a4ba-141">该 cmdlet 的用途时将使用此参数。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="5a4ba-142">参数是什么的合法值。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="5a4ba-143">参数值表示为.NET Framework 对象，因为用户需要有关这些值的信息不是像在传统的命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="5a4ba-144">告知用户哪些类型的数据参数旨在用于接受，并且包含示例。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="5a4ba-145">如果未在命令行上指定此参数，则使用值参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="5a4ba-146">请注意，默认值是可选的不需要为某些参数，例如所需的参数。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="5a4ba-147">但是，应指定大多数的可选参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="5a4ba-148">默认值可帮助用户理解不使用参数的效果。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="5a4ba-149">例如，"当前目录"或"Windows PowerShell 安装目录 ($pshome)"的可选路径非常明确地描述的默认值。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="5a4ba-150">您还可以编写一个句子，介绍了默认情况下，例如用于下列句子`PassThru`参数："如果未指定 PassThru，该 cmdlet 未通过管道向下的对象。"</span><span class="sxs-lookup"><span data-stu-id="5a4ba-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="5a4ba-151">此外，因为相反的字段名称将显示的值"**默认值**"，不需要的项中包含术语"默认值"。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="5a4ba-152">参数的默认值不显示在所有视图中的 cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="5a4ba-153">但是，在以下参数说明，当用户要求提供完整的表 （以及参数属性中） 中显示 (获取帮助\<cmdletname >-完整) 或参数 (Get-help \<cmdletname >-参数) 视图主题。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="5a4ba-154">以下 XML 显示了一对`<dev:defaultValue>`标记添加到`<command:parameter>`节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="5a4ba-155">请注意，默认值遵循结束后立即`</command:parameterValue>`标记 （如果指定的参数值） 或右`</maml:description>`标记的参数说明。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="5a4ba-156">名称。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-156">name.</span></span>

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

<span data-ttu-id="5a4ba-157">对于枚举类型添加值</span><span class="sxs-lookup"><span data-stu-id="5a4ba-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="5a4ba-158">如果该参数有多个值或枚举类型的值，则可以使用可选\<dev:possibleValues > 节点。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="5a4ba-159">此节点允许您指定的名称和多个值的说明。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="5a4ba-160">请注意的枚举值的说明不会出现任何默认情况下显示的帮助视图`Get-Help`cmdlet，但其他帮助查看器可能会显示此内容在自己的视图。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="5a4ba-161">下面的 XML 演示`<dev:possibleValues>`节点具有两个指定的值。</span><span class="sxs-lookup"><span data-stu-id="5a4ba-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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
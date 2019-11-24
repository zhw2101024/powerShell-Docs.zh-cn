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
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="3e846-102">如何向 Cmdlet 帮助主题添加语法</span><span class="sxs-lookup"><span data-stu-id="3e846-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="3e846-103">在开始编写 cmdlet 帮助文件中语法关系图的 XML 代码之前，请阅读此部分以清楚地了解你需要提供的数据类型，如参数特性，以及如何在语法关系图中显示这些数据。</span><span class="sxs-lookup"><span data-stu-id="3e846-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="3e846-104">参数特性</span><span class="sxs-lookup"><span data-stu-id="3e846-104">Parameter Attributes</span></span>

- <span data-ttu-id="3e846-105">必需</span><span class="sxs-lookup"><span data-stu-id="3e846-105">Required</span></span>

  - <span data-ttu-id="3e846-106">如果为 true，则参数必须出现在所有使用参数集的命令中。</span><span class="sxs-lookup"><span data-stu-id="3e846-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="3e846-107">如果为 false，则参数在所有使用参数集的命令中是可选的。</span><span class="sxs-lookup"><span data-stu-id="3e846-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="3e846-108">置于</span><span class="sxs-lookup"><span data-stu-id="3e846-108">Position</span></span>

  - <span data-ttu-id="3e846-109">如果已命名，则参数名称是必需的。</span><span class="sxs-lookup"><span data-stu-id="3e846-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="3e846-110">如果是位置，则参数名称是可选的。</span><span class="sxs-lookup"><span data-stu-id="3e846-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="3e846-111">如果省略此参数，则参数值必须在命令中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="3e846-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="3e846-112">例如，如果值为 position = "1"，则参数值必须是命令中的第一个或唯一一个未命名的参数值。</span><span class="sxs-lookup"><span data-stu-id="3e846-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="3e846-113">管道输入</span><span class="sxs-lookup"><span data-stu-id="3e846-113">Pipeline Input</span></span>

  - <span data-ttu-id="3e846-114">如果为 true （ByValue），则可以通过管道将输入传递给参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="3e846-115">即使属性名称和对象类型与预期类型不匹配，输入也与（"绑定到"）参数相关联。</span><span class="sxs-lookup"><span data-stu-id="3e846-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="3e846-116">Windows PowerShell？参数绑定组件尝试将输入转换为正确的类型，并且仅在不能转换类型时才会导致命令失败。</span><span class="sxs-lookup"><span data-stu-id="3e846-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="3e846-117">参数集中只能有一个参数可以通过值来关联。</span><span class="sxs-lookup"><span data-stu-id="3e846-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="3e846-118">如果为 true （ByPropertyName），则可以通过管道将输入传递给参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="3e846-119">但是，仅当参数名称与输入对象的属性的名称匹配时，输入才与参数相关联。</span><span class="sxs-lookup"><span data-stu-id="3e846-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="3e846-120">例如，如果参数名称是 `Path`的，则仅当对象具有名为 path 的属性时，才与该参数关联的对象将与该参数相关联。</span><span class="sxs-lookup"><span data-stu-id="3e846-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="3e846-121">如果为 true （ByValue，ByPropertyName），则可以通过属性名称或值通过管道将输入传递给参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="3e846-122">参数集中只能有一个参数可以通过值来关联。</span><span class="sxs-lookup"><span data-stu-id="3e846-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="3e846-123">如果为 false，则不能通过管道将输入传递给此参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="3e846-124">通配</span><span class="sxs-lookup"><span data-stu-id="3e846-124">Globbing</span></span>

  - <span data-ttu-id="3e846-125">如果为 true，则用户键入的参数值文本可以包含通配符。</span><span class="sxs-lookup"><span data-stu-id="3e846-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="3e846-126">如果为 false，则用户为参数值键入的文本不能包含通配符。</span><span class="sxs-lookup"><span data-stu-id="3e846-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="3e846-127">参数值特性</span><span class="sxs-lookup"><span data-stu-id="3e846-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="3e846-128">必需</span><span class="sxs-lookup"><span data-stu-id="3e846-128">Required</span></span>

  - <span data-ttu-id="3e846-129">如果为 true，则只要在命令中使用参数，就必须使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="3e846-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="3e846-130">如果为 false，则参数值是可选的。</span><span class="sxs-lookup"><span data-stu-id="3e846-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="3e846-131">通常，仅当值为参数的多个有效值之一（如枚举类型中的值）时，此值才是可选的。</span><span class="sxs-lookup"><span data-stu-id="3e846-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="3e846-132">参数值的必需特性与参数的必需特性不同。</span><span class="sxs-lookup"><span data-stu-id="3e846-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="3e846-133">参数的必需特性指示在调用 cmdlet 时是否必须包含参数（及其值）。</span><span class="sxs-lookup"><span data-stu-id="3e846-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="3e846-134">相反，仅当参数包含在命令中时，才使用参数值的必需特性。</span><span class="sxs-lookup"><span data-stu-id="3e846-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="3e846-135">它指示特定值是否必须与参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="3e846-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="3e846-136">通常，作为占位符的参数值是必需的，参数值不是必需的，因为它们是可能与参数一起使用的几个值中的一个。</span><span class="sxs-lookup"><span data-stu-id="3e846-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="3e846-137">正在收集语法信息</span><span class="sxs-lookup"><span data-stu-id="3e846-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="3e846-138">以 cmdlet 名称开头。</span><span class="sxs-lookup"><span data-stu-id="3e846-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="3e846-139">列出 cmdlet 的所有参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="3e846-140">在每个参数名称之前键入短划线（也称为 "破折号" 或 "减号" （ASCII 45）。</span><span class="sxs-lookup"><span data-stu-id="3e846-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="3e846-141">将参数分为多个参数集（某些 cmdlet 只能设置一个参数）。</span><span class="sxs-lookup"><span data-stu-id="3e846-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="3e846-142">在此示例中，"Get-help" cmdlet 具有两个参数集。</span><span class="sxs-lookup"><span data-stu-id="3e846-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="3e846-143">用 cmdlet 名称启动每个参数集。</span><span class="sxs-lookup"><span data-stu-id="3e846-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="3e846-144">首先列出默认参数集。</span><span class="sxs-lookup"><span data-stu-id="3e846-144">List the default parameter set first.</span></span> <span data-ttu-id="3e846-145">默认参数是由 cmdlet 类指定的。</span><span class="sxs-lookup"><span data-stu-id="3e846-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="3e846-146">对于每个参数集，请首先列出其唯一参数，除非存在必须首先出现的位置参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="3e846-147">在上面的示例中，Name 和 ID 参数是这两个参数集的唯一参数（每个参数集必须有一个参数集独有的参数）。</span><span class="sxs-lookup"><span data-stu-id="3e846-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="3e846-148">这样，用户就可以更轻松地标识他们需要为参数集提供哪些参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="3e846-149">按它们应出现在命令中的顺序列出参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="3e846-150">如果顺序不重要，请将相关参数一起列出，或首先列出最常用的参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="3e846-151">如果 cmdlet 支持 ShouldProcess，请务必列出 WhatIf 和 Confirm 参数。</span><span class="sxs-lookup"><span data-stu-id="3e846-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="3e846-152">不要在语法关系图中列出常见参数（例如 Verbose、Debug 和 ErrorAction）。</span><span class="sxs-lookup"><span data-stu-id="3e846-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="3e846-153">`Get-Help` cmdlet 在显示 "帮助" 主题时会为你添加该信息。</span><span class="sxs-lookup"><span data-stu-id="3e846-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="3e846-154">添加参数值。</span><span class="sxs-lookup"><span data-stu-id="3e846-154">Add the parameter values.</span></span> <span data-ttu-id="3e846-155">在 Windows PowerShell 中，参数值按其 .NET 类型表示。</span><span class="sxs-lookup"><span data-stu-id="3e846-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="3e846-156">但是，类型名称可以缩写，如 system.string 的 "string"。</span><span class="sxs-lookup"><span data-stu-id="3e846-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="3e846-157">缩写类型的含义清楚，如 system.string 的 "string" 和 System.object 的 "int"。</span><span class="sxs-lookup"><span data-stu-id="3e846-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="3e846-158">列出枚举的所有值，如上一示例中的-type 参数，可设置为 "基本" 或 "高级"。</span><span class="sxs-lookup"><span data-stu-id="3e846-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="3e846-159">在前面的示例中，开关参数（如-list）没有值。</span><span class="sxs-lookup"><span data-stu-id="3e846-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="3e846-160">与作为文本的参数值相比，将尖括号添加到作为占位符的参数值。</span><span class="sxs-lookup"><span data-stu-id="3e846-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="3e846-161">将可选参数及其工位括在方括号中。</span><span class="sxs-lookup"><span data-stu-id="3e846-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="3e846-162">将可选参数名称（用于位置参数）括在方括号中。</span><span class="sxs-lookup"><span data-stu-id="3e846-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="3e846-163">位置的参数的名称（例如以下示例中的 Name 参数）不必包含在命令中。</span><span class="sxs-lookup"><span data-stu-id="3e846-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="3e846-164">如果参数值可以包含多个值，如 Name 参数中的名称列表，请在参数值之后直接添加一对方括号。</span><span class="sxs-lookup"><span data-stu-id="3e846-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="3e846-165">如果用户可以从参数或参数值（如类型参数）中进行选择，请将这些选项括在大括号中，并将它们与 xor 或符号（;) 分隔开。</span><span class="sxs-lookup"><span data-stu-id="3e846-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="3e846-166">如果参数值必须使用特定的格式设置，如引号或括号，则在语法中显示格式。</span><span class="sxs-lookup"><span data-stu-id="3e846-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="3e846-167">编码语法关系图 XML</span><span class="sxs-lookup"><span data-stu-id="3e846-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="3e846-168">XML 的语法节点紧随 description 节点后开始，该节点以 \</maml： description > 标记结尾。</span><span class="sxs-lookup"><span data-stu-id="3e846-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="3e846-169">有关收集语法关系图中使用的数据的信息，请参阅[收集语法信息](#gathering-syntax-information)。</span><span class="sxs-lookup"><span data-stu-id="3e846-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="3e846-170">添加语法节点</span><span class="sxs-lookup"><span data-stu-id="3e846-170">Adding a Syntax Node</span></span>

<span data-ttu-id="3e846-171">Cmdlet 帮助主题中显示的语法关系图是从 XML 语法节点中的数据生成的。</span><span class="sxs-lookup"><span data-stu-id="3e846-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="3e846-172">如果 \<命令：语法 > 标记，则语法节点包含在对中。</span><span class="sxs-lookup"><span data-stu-id="3e846-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="3e846-173">将 cmdlet 的每个参数集括在一对 \<命令中： syntaxitem > 标记。</span><span class="sxs-lookup"><span data-stu-id="3e846-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="3e846-174">\<命令的数量没有限制： syntaxitem > 可以添加的标记。</span><span class="sxs-lookup"><span data-stu-id="3e846-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="3e846-175">下面的示例演示一个语法节点，该节点具有两个参数集的语法项节点。</span><span class="sxs-lookup"><span data-stu-id="3e846-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="3e846-176">将 Cmdlet 名称添加到参数集数据</span><span class="sxs-lookup"><span data-stu-id="3e846-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="3e846-177">Cmdlet 的每个参数集是在语法项节点中指定的。</span><span class="sxs-lookup"><span data-stu-id="3e846-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="3e846-178">每个语法项节点都以一对 \<maml：名称 > 标记组成，其中包括 cmdlet 的名称。</span><span class="sxs-lookup"><span data-stu-id="3e846-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="3e846-179">下面的示例包含一个语法节点，该节点具有两个参数集的语法项节点。</span><span class="sxs-lookup"><span data-stu-id="3e846-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="3e846-180">添加参数</span><span class="sxs-lookup"><span data-stu-id="3e846-180">Adding Parameters</span></span>

<span data-ttu-id="3e846-181">添加到语法项节点中的每个参数都是在一对 \<命令中指定的：参数 > 标记。</span><span class="sxs-lookup"><span data-stu-id="3e846-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="3e846-182">需要一对 \<命令：参数集中包含的每个参数 > 标记，Windows PowerShell 提供的通用参数除外？。</span><span class="sxs-lookup"><span data-stu-id="3e846-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="3e846-183">打开 \<command：参数 > 标记的属性确定参数在语法关系图中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="3e846-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="3e846-184">有关参数属性的信息，请参阅[参数特性](#parameter-attributes)。</span><span class="sxs-lookup"><span data-stu-id="3e846-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="3e846-185">\<command：参数 > 标记支持子元素，\<maml： description >，其内容从未显示。</span><span class="sxs-lookup"><span data-stu-id="3e846-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="3e846-186">在 XML 的参数节点中指定参数说明。</span><span class="sxs-lookup"><span data-stu-id="3e846-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="3e846-187">若要避免语法项预兆中的信息与参数节点中的信息不一致，请省略（\<maml： description > 或将其保留为空。</span><span class="sxs-lookup"><span data-stu-id="3e846-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="3e846-188">下面的示例包含具有两个参数的参数集的语法项节点。</span><span class="sxs-lookup"><span data-stu-id="3e846-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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

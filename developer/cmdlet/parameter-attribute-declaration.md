---
title: 参数特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735138"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="579b2-102">参数属性声明</span><span class="sxs-lookup"><span data-stu-id="579b2-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="579b2-103">参数特性标识为 cmdlet 参数在 cmdlet 类的公共属性。</span><span class="sxs-lookup"><span data-stu-id="579b2-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="579b2-104">语法</span><span class="sxs-lookup"><span data-stu-id="579b2-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="579b2-105">参数</span><span class="sxs-lookup"><span data-stu-id="579b2-105">Parameters</span></span>

<span data-ttu-id="579b2-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="579b2-107">`True` 指示 cmdlet 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="579b2-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="579b2-108">如果未提供一个必需的参数，则调用该 cmdlet 时，Windows PowerShell 会提示用户输入参数值。</span><span class="sxs-lookup"><span data-stu-id="579b2-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="579b2-109">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="579b2-109">The default is `false`.</span></span>

<span data-ttu-id="579b2-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="579b2-111">指定该参数设置，此 cmdlet 参数属于。</span><span class="sxs-lookup"><span data-stu-id="579b2-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="579b2-112">如果不指定任何参数集，则该参数属于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="579b2-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="579b2-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="579b2-114">指定的 Windows PowerShell 命令中的参数的位置。</span><span class="sxs-lookup"><span data-stu-id="579b2-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="579b2-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="579b2-116">`True` 指示此 cmdlet 参数采用其值从管道对象。</span><span class="sxs-lookup"><span data-stu-id="579b2-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="579b2-117">指定此关键字，如果该 cmdlet 将访问的完整对象，而不仅仅是对象的属性。</span><span class="sxs-lookup"><span data-stu-id="579b2-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="579b2-118">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="579b2-118">The default is `false`.</span></span>

<span data-ttu-id="579b2-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="579b2-120">`True` 指示此 cmdlet 参数采用其值从具有相同的名称或此参数的别名相同的管道对象的属性。</span><span class="sxs-lookup"><span data-stu-id="579b2-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="579b2-121">例如，如果该 cmdlet 具有`Name`参数，而管道对象还具有`Name`属性、 的值`Name`属性分配给`Name`cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="579b2-122">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="579b2-122">The default is `false`.</span></span>

<span data-ttu-id="579b2-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="579b2-124">`True` 指示 cmdlet 参数接受所有剩余的自变量传递给该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="579b2-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="579b2-125">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="579b2-125">The default is `false`.</span></span>

<span data-ttu-id="579b2-126">`HelpMessage` 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="579b2-127">指定参数的简短说明。</span><span class="sxs-lookup"><span data-stu-id="579b2-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="579b2-128">Windows PowerShell cmdlet 运行和未指定必需的参数时显示此消息。</span><span class="sxs-lookup"><span data-stu-id="579b2-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="579b2-129">`HelpMessageBaseName` 可选的命名参数。指定资源标识符所在的位置。</span><span class="sxs-lookup"><span data-stu-id="579b2-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="579b2-130">例如，此参数可以指定包含要本地化的帮助消息的资源程序集。</span><span class="sxs-lookup"><span data-stu-id="579b2-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="579b2-131">`HelpMessageResourceId` 可选的命名参数。指定的帮助消息的资源标识符。</span><span class="sxs-lookup"><span data-stu-id="579b2-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="579b2-132">备注</span><span class="sxs-lookup"><span data-stu-id="579b2-132">Remarks</span></span>

- <span data-ttu-id="579b2-133">有关如何声明此属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="579b2-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="579b2-134">一个 cmdlet 可以具有任意数量的参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="579b2-135">但是，为了更好的用户体验，限制参数的数目。</span><span class="sxs-lookup"><span data-stu-id="579b2-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="579b2-136">参数必须声明上公共非静态字段或属性。</span><span class="sxs-lookup"><span data-stu-id="579b2-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="579b2-137">应在属性上声明参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="579b2-138">该属性必须具有公共的 set 访问器，并且如果`ValueFromPipeline`或`ValueFromPipelineByPropertyName`指定关键字，该属性必须具有公共 get 访问器。</span><span class="sxs-lookup"><span data-stu-id="579b2-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="579b2-139">当您指定位置参数时，限制中将参数设置为小于五的位置参数的数目。</span><span class="sxs-lookup"><span data-stu-id="579b2-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="579b2-140">和位置参数不需要是连续的。</span><span class="sxs-lookup"><span data-stu-id="579b2-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="579b2-141">位置 5、 100 和 250 工作方式为 0、 1 和 2 的位置相同。</span><span class="sxs-lookup"><span data-stu-id="579b2-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="579b2-142">当`Position`关键字未指定，则必须通过其名称引用的 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="579b2-143">使用参数集，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="579b2-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="579b2-144">每个参数集必须具有至少一个唯一的参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="579b2-145">好 cmdlet 设计指示该唯一参数还应该强制在可能的情况。</span><span class="sxs-lookup"><span data-stu-id="579b2-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="579b2-146">如果你的 cmdlet 专为运行不带参数，唯一的参数不能为必需。</span><span class="sxs-lookup"><span data-stu-id="579b2-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="579b2-147">没有参数集应包含多个具有相同的位置的位置参数。</span><span class="sxs-lookup"><span data-stu-id="579b2-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="579b2-148">中的参数集只有一个参数应声明`ValueFromPipeline = true`。</span><span class="sxs-lookup"><span data-stu-id="579b2-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="579b2-149">可以定义多个参数`ValueFromPipelineByPropertyName = true`。</span><span class="sxs-lookup"><span data-stu-id="579b2-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="579b2-150">可以定义多个参数`ValueFromPipelineByPropertyName = true`。</span><span class="sxs-lookup"><span data-stu-id="579b2-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="579b2-151">有关参数名称的准则的详细信息，请参阅[Cmdlet 参数名称](standard-cmdlet-parameter-names-and-types.md)。</span><span class="sxs-lookup"><span data-stu-id="579b2-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="579b2-152">参数属性定义由[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="579b2-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="579b2-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="579b2-153">See Also</span></span>

[<span data-ttu-id="579b2-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="579b2-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="579b2-155">Cmdlet 参数名称</span><span class="sxs-lookup"><span data-stu-id="579b2-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="579b2-156">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="579b2-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

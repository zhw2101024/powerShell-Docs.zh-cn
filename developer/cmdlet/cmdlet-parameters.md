---
title: Cmdlet 参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853843"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="22c3d-102">Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="22c3d-102">Cmdlet Parameters</span></span>

<span data-ttu-id="22c3d-103">Cmdlet 参数提供的机制，用于接受输入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="22c3d-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="22c3d-104">参数可以接受输入直接从命令行中，或通过管道参数传递给 cmdlet 的对象 (也称为*值*) 的这些参数可以指定该 cmdlet 接受，输入方式cmdlet 应执行的操作，以及该 cmdlet 将返回到管道的数据。</span><span class="sxs-lookup"><span data-stu-id="22c3d-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="22c3d-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="22c3d-105">In This Section</span></span>

<span data-ttu-id="22c3d-106">[声明属性作为参数](./declaring-properties-as-parameters.md)提供声明的参数的 cmdlet 之前，您必须了解的基本信息。</span><span class="sxs-lookup"><span data-stu-id="22c3d-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="22c3d-107">[Cmdlet 参数的类型](./types-of-cmdlet-parameters.md)介绍不同类型的参数可以声明在 cmdlet 中。</span><span class="sxs-lookup"><span data-stu-id="22c3d-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="22c3d-108">[Cmdlet 参数名称和功能的指导原则](./standard-cmdlet-parameter-names-and-types.md)Discuses 名称，建议的数据类型和功能的标准参数。</span><span class="sxs-lookup"><span data-stu-id="22c3d-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="22c3d-109">[参数别名](./parameter-aliases.md)讨论你可以为参数定义的别名。</span><span class="sxs-lookup"><span data-stu-id="22c3d-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="22c3d-110">[常见的参数名称](./common-parameter-names.md)本主题介绍 Windows PowerShell 将添加到 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="22c3d-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="22c3d-111">[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)讨论了如何参数集，您可以编写的单个 cmdlet，可以执行不同的操作为不同的方案。</span><span class="sxs-lookup"><span data-stu-id="22c3d-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="22c3d-112">[Cmdlet 的动态参数](./cmdlet-dynamic-parameters.md)讨论了可供用户在特殊情况下的参数。</span><span class="sxs-lookup"><span data-stu-id="22c3d-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="22c3d-113">[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)介绍如何设计一个 cmdlet，将针对资源组的运行时的通配符字符提供支持。</span><span class="sxs-lookup"><span data-stu-id="22c3d-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="22c3d-114">[验证参数输入](./validating-parameter-input.md)描述了 Windows PowerShell 如何验证传递给 cmdlet 参数的参数。</span><span class="sxs-lookup"><span data-stu-id="22c3d-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="22c3d-115">[输入筛选器参数](./input-filter-parameters.md)讨论`Filter`， `Include`，和`Exclude`筛选会影响该 cmdlet 的输入对象的集合的参数。</span><span class="sxs-lookup"><span data-stu-id="22c3d-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="22c3d-116">相关章节</span><span class="sxs-lookup"><span data-stu-id="22c3d-116">Related Sections</span></span>

[<span data-ttu-id="22c3d-117">如何验证参数输入</span><span class="sxs-lookup"><span data-stu-id="22c3d-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="22c3d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22c3d-118">See Also</span></span>

[<span data-ttu-id="22c3d-119">参数特性声明</span><span class="sxs-lookup"><span data-stu-id="22c3d-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="22c3d-120">Windows PowerShell Cmdlets</span><span class="sxs-lookup"><span data-stu-id="22c3d-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

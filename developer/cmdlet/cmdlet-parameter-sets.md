---
title: Cmdlet 参数可设置 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068502"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="7b836-102">Cmdlet 参数集</span><span class="sxs-lookup"><span data-stu-id="7b836-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="7b836-103">Windows PowerShell 使用参数集，您可以编写的单个 cmdlet，可以执行不同的操作为不同的方案。</span><span class="sxs-lookup"><span data-stu-id="7b836-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="7b836-104">参数集使您能够公开给用户的不同参数，并返回基于用户指定的参数的不同信息。</span><span class="sxs-lookup"><span data-stu-id="7b836-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="7b836-105">参数集的示例</span><span class="sxs-lookup"><span data-stu-id="7b836-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="7b836-106">例如， `Get-EventLog` cmdlet （由 Windows PowerShell 提供） 将返回不同的信息，具体取决于用户是否指定`List`或`LogName`参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="7b836-107">如果`List`指定参数，则该 cmdlet 返回有关日志文件的信息本身，但不是包含事件信息。</span><span class="sxs-lookup"><span data-stu-id="7b836-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="7b836-108">如果`LogName`指定参数，则该 cmdlet 返回特定的事件日志中有关事件的信息。</span><span class="sxs-lookup"><span data-stu-id="7b836-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="7b836-109">`List`和`LogName`参数标识两个单独的参数集。</span><span class="sxs-lookup"><span data-stu-id="7b836-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="7b836-110">唯一的参数</span><span class="sxs-lookup"><span data-stu-id="7b836-110">Unique Parameter</span></span>

<span data-ttu-id="7b836-111">每个参数集必须具有一个唯一的参数，可以使用 Windows PowerShell 运行时公开相应的参数集。</span><span class="sxs-lookup"><span data-stu-id="7b836-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="7b836-112">如果可能，唯一的参数应为必需参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="7b836-113">当一个参数是必需的时强制用户来指定参数，和 Windows PowerShell 运行时可以使用该参数将设置为使用该参数标识。</span><span class="sxs-lookup"><span data-stu-id="7b836-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="7b836-114">唯一的参数不能为必需，如果你的 cmdlet 专为运行而无需指定任何参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="7b836-115">多个参数集</span><span class="sxs-lookup"><span data-stu-id="7b836-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="7b836-116">下图中，在左侧的列显示三个有效的参数集。</span><span class="sxs-lookup"><span data-stu-id="7b836-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="7b836-117">一个参数是唯一的第一个参数集，参数 B 是唯一的第二个参数集，参数 C 是唯一的第三个参数集。</span><span class="sxs-lookup"><span data-stu-id="7b836-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="7b836-118">但是，在右列中，参数集不具有唯一的参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="7b836-120">参数设置要求</span><span class="sxs-lookup"><span data-stu-id="7b836-120">Parameter Set Requirements</span></span>

<span data-ttu-id="7b836-121">以下要求适用于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="7b836-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="7b836-122">每个参数集必须具有至少一个唯一的参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="7b836-123">如果可能，请此参数强制参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="7b836-124">包含多个位置参数的参数集必须定义为每个参数的唯一位置。</span><span class="sxs-lookup"><span data-stu-id="7b836-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="7b836-125">两个位置参数可以指定相同的位置。</span><span class="sxs-lookup"><span data-stu-id="7b836-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="7b836-126">一组中的只有一个参数可以声明`ValueFromPipeline`关键字，值为`true`。</span><span class="sxs-lookup"><span data-stu-id="7b836-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="7b836-127">可以定义多个参数`ValueFromPipelineByPropertyName`关键字，值为`true`。</span><span class="sxs-lookup"><span data-stu-id="7b836-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="7b836-128">如果为参数不指定任何参数集，则该参数属于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="7b836-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="7b836-129">默认参数集</span><span class="sxs-lookup"><span data-stu-id="7b836-129">Default Parameter Sets</span></span>

<span data-ttu-id="7b836-130">如果定义多个参数集，可以使用`DefaultParameterSetName`Cmdlet 属性来指定默认参数集的关键字。</span><span class="sxs-lookup"><span data-stu-id="7b836-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="7b836-131">Windows PowerShell 使用的默认参数集如果它不能确定参数设置为使用基于命令提供的信息。</span><span class="sxs-lookup"><span data-stu-id="7b836-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="7b836-132">Cmdlet 属性有关的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7b836-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="7b836-133">声明参数集</span><span class="sxs-lookup"><span data-stu-id="7b836-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="7b836-134">若要创建的参数集，必须指定`ParameterSetName`关键字声明中的参数集的每个参数的参数属性时。</span><span class="sxs-lookup"><span data-stu-id="7b836-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="7b836-135">对于属于多个参数集的参数，将添加每个参数集的参数属性。</span><span class="sxs-lookup"><span data-stu-id="7b836-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="7b836-136">这使您可以定义不同的方式针对每个参数集的参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="7b836-137">例如，您可以为在一组必需的和可选中另一个定义参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="7b836-138">但是，每个参数集必须包含一个唯一的参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="7b836-139">在以下示例中，`UserName`参数是唯一的 Test01 参数集，参数和`ComputerName`参数是 Test02 参数集的唯一参数。</span><span class="sxs-lookup"><span data-stu-id="7b836-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="7b836-140">`SharedParam`参数属于这两个集，它是必需的 Test01 参数，但对于 Test02 参数集是可选的设置。</span><span class="sxs-lookup"><span data-stu-id="7b836-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```
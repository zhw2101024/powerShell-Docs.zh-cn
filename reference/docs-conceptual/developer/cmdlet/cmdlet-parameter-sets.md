---
title: Cmdlet 参数集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: dfe747893b4aef6376ea3b12dd79b7c144455ed0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415687"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="1c4a1-102">Cmdlet 参数集</span><span class="sxs-lookup"><span data-stu-id="1c4a1-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="1c4a1-103">PowerShell 使用参数集来编写单个 cmdlet，该 cmdlet 可以针对不同的方案执行不同的操作。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="1c4a1-104">参数集使你可以向用户公开不同参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="1c4a1-105">和，根据用户指定的参数返回不同的信息。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="1c4a1-106">参数集的示例</span><span class="sxs-lookup"><span data-stu-id="1c4a1-106">Examples of parameter sets</span></span>

<span data-ttu-id="1c4a1-107">例如，PowerShell `Get-EventLog` cmdlet 返回不同的信息，具体取决于用户是否指定了**List**或**LogName**参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="1c4a1-108">如果指定了**List**参数，则 cmdlet 将返回有关日志文件本身的信息，而不返回这些日志文件所包含的事件信息。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="1c4a1-109">如果指定了**LogName**参数，则 cmdlet 将返回有关特定事件日志中的事件的信息。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="1c4a1-110">**List**和**LogName**参数标识两个单独的参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="1c4a1-111">唯一参数</span><span class="sxs-lookup"><span data-stu-id="1c4a1-111">Unique parameter</span></span>

<span data-ttu-id="1c4a1-112">每个参数集都必须具有一个唯一参数，该参数由 PowerShell 运行时用来公开相应的参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="1c4a1-113">如果可能，唯一参数应该是必需参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="1c4a1-114">如果参数是必需的，则用户必须指定参数，并且 PowerShell 运行时使用该参数来标识参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="1c4a1-115">如果 cmdlet 设计为在不指定任何参数的情况下运行，则 unique 参数不是必需的。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="1c4a1-116">多个参数集</span><span class="sxs-lookup"><span data-stu-id="1c4a1-116">Multiple parameter sets</span></span>

<span data-ttu-id="1c4a1-117">在下图中，左栏显示了三个有效的参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="1c4a1-118">**参数 A**对于第一个参数集是唯一的，**参数 B**对于第二个参数集是唯一的，而**参数 C**对第三个参数集是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="1c4a1-119">在右列中，参数集没有唯一参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="1c4a1-121">参数集要求</span><span class="sxs-lookup"><span data-stu-id="1c4a1-121">Parameter set requirements</span></span>

<span data-ttu-id="1c4a1-122">以下要求适用于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="1c4a1-123">每个参数集必须至少具有一个唯一参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="1c4a1-124">如果可能，请将此参数设置为必需参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="1c4a1-125">包含多个位置参数的参数集必须为每个参数定义唯一的位置。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="1c4a1-126">无两个位置参数可以指定同一位置。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="1c4a1-127">集中只有一个参数可以用 `true`值声明 `ValueFromPipeline` 关键字。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="1c4a1-128">多个参数可以定义值为 `true`的 `ValueFromPipelineByPropertyName` 关键字。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="1c4a1-129">如果未指定参数的参数集，则参数属于所有参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="1c4a1-130">对于 cmdlet 或函数，有32个参数集的限制。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="1c4a1-131">默认参数集</span><span class="sxs-lookup"><span data-stu-id="1c4a1-131">Default parameter sets</span></span>

<span data-ttu-id="1c4a1-132">如果定义了多个参数集，则可以使用**Cmdlet**特性的 `DefaultParameterSetName` 关键字来指定默认参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="1c4a1-133">如果 PowerShell 无法根据命令提供的信息确定要使用的参数集，则它将使用默认参数集。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="1c4a1-134">有关**cmdlet**特性的详细信息，请参阅[cmdlet 特性声明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="1c4a1-135">声明参数集</span><span class="sxs-lookup"><span data-stu-id="1c4a1-135">Declaring parameter sets</span></span>

<span data-ttu-id="1c4a1-136">若要创建参数集，则在为参数集中的每个参数声明**参数**属性时，必须指定 `ParameterSetName` 关键字。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="1c4a1-137">对于属于多个参数集的参数，请为每个参数集添加一个**参数**特性。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="1c4a1-138">此特性使你能够以不同的方式为每个参数集定义参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="1c4a1-139">例如，可以在一组中将参数定义为强制参数，并在另一个集中定义为可选参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="1c4a1-140">但是，每个参数集必须包含一个唯一参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="1c4a1-141">有关详细信息，请参阅[参数属性声明](parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="1c4a1-142">在下面的示例中， **UserName**参数是 `Test01` 参数集的唯一参数， **ComputerName**参数是 `Test02` 参数集的唯一参数。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="1c4a1-143">**SharedParam**参数属于这两个集，对于 `Test01` 参数集是必需的，但对于 `Test02` 参数集是可选的。</span><span class="sxs-lookup"><span data-stu-id="1c4a1-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
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
private string sharedParam;
```

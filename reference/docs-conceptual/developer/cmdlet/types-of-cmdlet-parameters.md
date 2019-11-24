---
title: Cmdlet 参数的类型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369306"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="3f369-102">Cmdlet 参数的类型</span><span class="sxs-lookup"><span data-stu-id="3f369-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="3f369-103">本主题介绍可在 cmdlet 中声明的不同类型的参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="3f369-104">Cmdlet 参数可以是位置、命名、必需、可选或切换参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="3f369-105">位置和命名参数</span><span class="sxs-lookup"><span data-stu-id="3f369-105">Positional and Named Parameters</span></span>

<span data-ttu-id="3f369-106">所有 cmdlet 参数都是命名参数或位置参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="3f369-107">命名参数要求在调用 cmdlet 时键入参数名称和参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="3f369-108">位置参数只要求按相对顺序键入参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="3f369-109">然后，系统将第一个未命名的参数映射到第一个位置参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="3f369-110">系统会将第二个未命名的参数映射到第二个未命名的参数，依此类推。</span><span class="sxs-lookup"><span data-stu-id="3f369-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="3f369-111">默认情况下，所有 cmdlet 参数均为命名参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="3f369-112">若要定义命名参数，请在**参数**属性声明中省略 `Position` 关键字，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="3f369-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="3f369-113">若要定义位置参数，请在参数属性声明中添加 `Position` 关键字，然后指定位置。</span><span class="sxs-lookup"><span data-stu-id="3f369-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="3f369-114">在下面的示例中，`UserName` 参数声明为位置为0的位置参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="3f369-115">这意味着调用的第一个参数将自动绑定到此参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="3f369-116">良好的 cmdlet 设计建议将最常使用的参数声明为位置参数，使用户无需在运行 cmdlet 时输入参数名称。</span><span class="sxs-lookup"><span data-stu-id="3f369-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="3f369-117">位置和命名参数接受单个参数或用逗号分隔的多个参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="3f369-118">仅当参数接受集合（如字符串数组）时，才允许使用多个参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="3f369-119">可以在同一个 cmdlet 中混合位置和命名参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="3f369-120">在这种情况下，系统首先检索命名参数，然后尝试将其余未命名参数映射到位置参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="3f369-121">以下命令显示了不同的方法，你可以在其中指定 `Get-Command` cmdlet 的参数的单个参数和多个参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="3f369-122">请注意，在最后两个示例中， **-name**不需要指定，因为 `Name` 参数被定义为位置参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="3f369-123">必需参数和可选参数</span><span class="sxs-lookup"><span data-stu-id="3f369-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="3f369-124">你还可以将 cmdlet 参数定义为必需或可选参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="3f369-125">（必须在 Windows PowerShell 运行时调用 cmdlet 之前指定必需参数。） 默认情况下，将参数定义为可选。</span><span class="sxs-lookup"><span data-stu-id="3f369-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="3f369-126">若要定义强制参数，请在参数属性声明中添加 `Mandatory` 关键字，并将其设置为 `true`，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="3f369-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="3f369-127">若要定义可选参数，请在**参数**属性声明中省略 `Mandatory` 关键字，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="3f369-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="3f369-128">开关参数</span><span class="sxs-lookup"><span data-stu-id="3f369-128">Switch Parameters</span></span>

<span data-ttu-id="3f369-129">Windows PowerShell 提供[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，该类型允许您定义一个参数，该参数的值自动设置为 `false` 如果调用 cmdlet 时未指定参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="3f369-130">请尽可能使用开关参数代替布尔参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="3f369-131">请考虑以下示例。</span><span class="sxs-lookup"><span data-stu-id="3f369-131">Consider the following sample.</span></span> <span data-ttu-id="3f369-132">默认情况下，多个 Windows PowerShell cmdlet 不会将输出对象沿管道向下传递。</span><span class="sxs-lookup"><span data-stu-id="3f369-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="3f369-133">但是，这些 cmdlet 具有替代默认行为的 `PassThru` 开关参数。</span><span class="sxs-lookup"><span data-stu-id="3f369-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="3f369-134">如果在调用这些 cmdlet 时指定了 `PassThru` 参数，则 cmdlet 会将输出对象返回到管道。</span><span class="sxs-lookup"><span data-stu-id="3f369-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="3f369-135">如果在调用中未指定参数时，需要参数的默认值为 `true`，请考虑反转参数的意义。</span><span class="sxs-lookup"><span data-stu-id="3f369-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="3f369-136">对于示例，请将属性声明为[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，而不是将参数属性设置为布尔值 `true`，然后将该参数的默认值设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="3f369-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="3f369-137">若要定义开关参数，请将属性声明为[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="3f369-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="3f369-138">若要使 cmdlet 在指定时对参数执行操作，请在其中一个输入处理方法中使用以下结构。</span><span class="sxs-lookup"><span data-stu-id="3f369-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="3f369-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f369-139">See Also</span></span>

[<span data-ttu-id="3f369-140">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f369-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

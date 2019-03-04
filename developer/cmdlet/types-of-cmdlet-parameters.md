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
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859863"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="7783b-102">Cmdlet 参数的类型</span><span class="sxs-lookup"><span data-stu-id="7783b-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="7783b-103">本主题介绍不同类型的参数可以声明在 cmdlet 中。</span><span class="sxs-lookup"><span data-stu-id="7783b-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="7783b-104">Cmdlet 参数可以是位置、 命名、 必需、 可选的或开关参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="7783b-105">定位和命名参数</span><span class="sxs-lookup"><span data-stu-id="7783b-105">Positional and Named Parameters</span></span>

<span data-ttu-id="7783b-106">所有 cmdlet 参数都是已命名或位置参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="7783b-107">一个命名的参数需要调用 cmdlet 时键入参数名称和参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="7783b-108">位置参数仅要求您键入的参数中的相对顺序。</span><span class="sxs-lookup"><span data-stu-id="7783b-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="7783b-109">然后，系统将第一个未命名的参数映射到第一个位置参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="7783b-110">系统将第二个未命名的参数映射到第二个未命名的参数，依此类推。</span><span class="sxs-lookup"><span data-stu-id="7783b-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="7783b-111">默认情况下，所有 cmdlet 参数被都命名参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="7783b-112">若要定义一个命名的参数，则忽略`Position`中的关键字**参数**特性声明，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="7783b-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="7783b-113">若要定义的位置参数，添加`Position`参数中的关键字属性声明中，，然后指定位置。</span><span class="sxs-lookup"><span data-stu-id="7783b-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="7783b-114">在以下示例中，`UserName`参数声明为具有位置 0 位置参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="7783b-115">这意味着调用的第一个参数将自动绑定到此参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="7783b-116">好 cmdlet 设计推荐的最常用的参数声明为位置参数，以便用户无需运行该 cmdlet 时输入的参数名称。</span><span class="sxs-lookup"><span data-stu-id="7783b-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="7783b-117">位置和名称参数接受单个参数或逗号分隔的多个自变量。</span><span class="sxs-lookup"><span data-stu-id="7783b-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="7783b-118">仅当该参数接受字符串的一个数组，如集合允许多个参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="7783b-119">您可能混合在同一个 cmdlet 中的位置和名称参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="7783b-120">在这种情况下，系统首先，检索命名的参数，然后尝试映射剩余未命名位置参数的参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="7783b-121">以下命令演示了可以在其中指定单个和多个自变量的参数的不同方式`Get-Command`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7783b-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="7783b-122">请注意，在最后两个示例中，**的名称**不需要指定，因为`Name`参数定义为位置参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="7783b-123">必需和可选参数</span><span class="sxs-lookup"><span data-stu-id="7783b-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="7783b-124">您还可以定义 cmdlet 参数为必需或可选参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="7783b-125">（Windows PowerShell 运行时调用该 cmdlet 之前，必须指定必需参数。）默认情况下，定义为可选参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="7783b-126">若要定义必需参数，请添加`Mandatory`参数中的关键字属性声明中，并将其设置为`true`，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="7783b-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="7783b-127">若要定义可选参数，请省略`Mandatory`中的关键字**参数**特性声明，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="7783b-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="7783b-128">开关参数</span><span class="sxs-lookup"><span data-stu-id="7783b-128">Switch Parameters</span></span>

<span data-ttu-id="7783b-129">Windows PowerShell 提供了[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)允许你定义一个参数的值的类型自动设置为`false`如果 cmdlet 时未指定此参数调用。</span><span class="sxs-lookup"><span data-stu-id="7783b-129">Windows PowerShell provides a [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="7783b-130">只要可能，使用代替布尔参数的开关参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="7783b-131">请考虑下面的示例。</span><span class="sxs-lookup"><span data-stu-id="7783b-131">Consider the following sample.</span></span> <span data-ttu-id="7783b-132">默认情况下，多个 Windows PowerShell cmdlet 不将传递管道向下的输出对象。</span><span class="sxs-lookup"><span data-stu-id="7783b-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="7783b-133">但是，这些 cmdlet 具有`PassThru`开关重写默认行为的参数。</span><span class="sxs-lookup"><span data-stu-id="7783b-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="7783b-134">如果`PassThru`调用这些 cmdlet 时指定参数，该 cmdlet 将返回到管道输出对象。</span><span class="sxs-lookup"><span data-stu-id="7783b-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="7783b-135">如果需要该参数具有默认值为`true`时在调用中未指定参数，请考虑反转参数的意义上说。</span><span class="sxs-lookup"><span data-stu-id="7783b-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="7783b-136">有关示例，而不是将参数属性设置为布尔值`true`，将属性声明为[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，然后设置的参数的默认值`false`.</span><span class="sxs-lookup"><span data-stu-id="7783b-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="7783b-137">若要定义一个开关参数，将属性声明为[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="7783b-137">To define a switch parameter, declare the property as the [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="7783b-138">若要使作用于该参数指定私钥时，该 cmdlet，使用以下结构中的输入处理方法之一。</span><span class="sxs-lookup"><span data-stu-id="7783b-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7783b-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7783b-139">See Also</span></span>

[<span data-ttu-id="7783b-140">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7783b-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

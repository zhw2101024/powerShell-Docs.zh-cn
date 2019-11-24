---
title: 如何声明 Cmdlet 参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365676"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="2974f-102">如何声明 Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="2974f-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="2974f-103">这些示例演示如何声明命名、位置、必需、可选参数和开关参数。</span><span class="sxs-lookup"><span data-stu-id="2974f-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="2974f-104">这些示例还演示如何定义参数别名。</span><span class="sxs-lookup"><span data-stu-id="2974f-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="2974f-105">如何声明命名参数</span><span class="sxs-lookup"><span data-stu-id="2974f-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="2974f-106">定义公共属性，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="2974f-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="2974f-107">添加参数特性时，请从特性中省略 `Position` 关键字。</span><span class="sxs-lookup"><span data-stu-id="2974f-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="2974f-108">有关参数属性的详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2974f-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="2974f-109">如何声明位置参数</span><span class="sxs-lookup"><span data-stu-id="2974f-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="2974f-110">定义公共属性，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="2974f-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="2974f-111">添加参数特性时，请将 `Position` 关键字设置为参数位置。</span><span class="sxs-lookup"><span data-stu-id="2974f-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="2974f-112">值0指示第一个位置。</span><span class="sxs-lookup"><span data-stu-id="2974f-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="2974f-113">有关参数属性的详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2974f-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="2974f-114">如何声明必需参数</span><span class="sxs-lookup"><span data-stu-id="2974f-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="2974f-115">定义公共属性，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="2974f-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="2974f-116">添加参数属性时，请将 `Mandatory` 关键字设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="2974f-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="2974f-117">有关参数属性的详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2974f-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="2974f-118">如何声明可选参数</span><span class="sxs-lookup"><span data-stu-id="2974f-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="2974f-119">定义公共属性，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="2974f-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="2974f-120">添加参数属性时，请省略 `Mandatory` 关键字。</span><span class="sxs-lookup"><span data-stu-id="2974f-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="2974f-121">如何声明开关参数</span><span class="sxs-lookup"><span data-stu-id="2974f-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="2974f-122">将公共属性定义为[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，然后声明参数属性。</span><span class="sxs-lookup"><span data-stu-id="2974f-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="2974f-123">有关参数属性的详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2974f-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="2974f-124">如何使用别名声明参数</span><span class="sxs-lookup"><span data-stu-id="2974f-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="2974f-125">定义公共属性，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="2974f-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="2974f-126">添加一个别名属性，其中列出了参数的别名。</span><span class="sxs-lookup"><span data-stu-id="2974f-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="2974f-127">在此示例中，为同一参数定义了三个别名。</span><span class="sxs-lookup"><span data-stu-id="2974f-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="2974f-128">第一个别名提供快捷方式。</span><span class="sxs-lookup"><span data-stu-id="2974f-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="2974f-129">第二个和第三个别名提供了可用于不同方案的名称。</span><span class="sxs-lookup"><span data-stu-id="2974f-129">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="2974f-130">有关 Alias 特性的详细信息，请参阅[Alias 特性声明](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2974f-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2974f-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2974f-131">See Also</span></span>

[<span data-ttu-id="2974f-132">System.web. SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2974f-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="2974f-133">参数属性声明</span><span class="sxs-lookup"><span data-stu-id="2974f-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="2974f-134">Alias 特性声明</span><span class="sxs-lookup"><span data-stu-id="2974f-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="2974f-135">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2974f-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

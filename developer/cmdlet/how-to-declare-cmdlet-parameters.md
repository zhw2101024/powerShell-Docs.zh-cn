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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067904"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="7cc9a-102">如何声明 Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="7cc9a-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="7cc9a-103">这些示例显示如何声明命名、 位置、 必需、 可选的和开关参数。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="7cc9a-104">这些示例还演示如何定义参数别名。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="7cc9a-105">如何声明一个命名的参数</span><span class="sxs-lookup"><span data-stu-id="7cc9a-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="7cc9a-106">定义公共属性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="7cc9a-107">当您添加的参数属性时，请省略`Position`从属性中的关键字。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="7cc9a-108">有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="7cc9a-109">如何声明位置参数</span><span class="sxs-lookup"><span data-stu-id="7cc9a-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="7cc9a-110">定义公共属性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="7cc9a-111">当您添加的参数属性时，请设置`Position`关键字的参数位置。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="7cc9a-112">值为 0 指示第一个位置。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="7cc9a-113">有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="7cc9a-114">如何以声明的必需参数</span><span class="sxs-lookup"><span data-stu-id="7cc9a-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="7cc9a-115">定义公共属性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="7cc9a-116">当您添加的参数属性时，请设置`Mandatory`关键字`true`。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="7cc9a-117">有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="7cc9a-118">如何声明一个可选参数</span><span class="sxs-lookup"><span data-stu-id="7cc9a-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="7cc9a-119">定义公共属性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="7cc9a-120">当您添加的参数属性时，请省略`Mandatory`关键字。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="7cc9a-121">如何声明一个开关参数</span><span class="sxs-lookup"><span data-stu-id="7cc9a-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="7cc9a-122">公共属性定义为类型[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)，然后声明参数属性。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="7cc9a-123">有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="7cc9a-124">如何声明具有别名的参数</span><span class="sxs-lookup"><span data-stu-id="7cc9a-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="7cc9a-125">定义公共属性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="7cc9a-126">添加别名属性，其中列出了该参数的别名。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="7cc9a-127">在此示例中，相同的参数定义三个别名。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="7cc9a-128">第一个别名提供了一种快捷方式。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="7cc9a-129">第二个和第三个别名，提供可用于不同方案的名称。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="7cc9a-130">有关别名属性的详细信息，请参阅[别名属性声明](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc9a-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7cc9a-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cc9a-131">See Also</span></span>

[<span data-ttu-id="7cc9a-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7cc9a-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="7cc9a-133">参数特性声明</span><span class="sxs-lookup"><span data-stu-id="7cc9a-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="7cc9a-134">别名属性声明</span><span class="sxs-lookup"><span data-stu-id="7cc9a-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="7cc9a-135">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7cc9a-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

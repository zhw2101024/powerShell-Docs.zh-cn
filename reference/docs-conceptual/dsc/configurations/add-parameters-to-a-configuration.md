---
ms.date: 12/12/2018
keywords: dsc,powershell,资源,库,安装程序
title: 向配置添加参数
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954194"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="8aecb-103">向配置添加参数</span><span class="sxs-lookup"><span data-stu-id="8aecb-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="8aecb-104">和函数一样，[配置](configurations.md)也可以参数化，以便基于用户输入进行更多动态配置。</span><span class="sxs-lookup"><span data-stu-id="8aecb-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="8aecb-105">这些步骤与[带有参数的函数](/powershell/module/microsoft.powershell.core/about/about_functions)中描述的步骤类似。</span><span class="sxs-lookup"><span data-stu-id="8aecb-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="8aecb-106">本例从一个基本配置开始，该配置将“Spooler”服务配置为“Running”。</span><span class="sxs-lookup"><span data-stu-id="8aecb-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="8aecb-107">内置配置参数</span><span class="sxs-lookup"><span data-stu-id="8aecb-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="8aecb-108">但是，与函数不同，[CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 属性不会添加任何功能。</span><span class="sxs-lookup"><span data-stu-id="8aecb-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="8aecb-109">除了[通用参数](/powershell/module/microsoft.powershell.core/about/about_commonparameters)之外，配置还可以使用以下内置参数，而无需用户对其进行定义。</span><span class="sxs-lookup"><span data-stu-id="8aecb-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="8aecb-110">参数</span><span class="sxs-lookup"><span data-stu-id="8aecb-110">Parameter</span></span>  |<span data-ttu-id="8aecb-111">说明</span><span class="sxs-lookup"><span data-stu-id="8aecb-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="8aecb-112">用于定义[复合配置](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="8aecb-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="8aecb-113">用于定义[复合配置](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="8aecb-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="8aecb-114">用于定义[复合配置](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="8aecb-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="8aecb-115">用于传入结构化的[配置数据](configData.md)，以便在配置中使用。</span><span class="sxs-lookup"><span data-stu-id="8aecb-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="8aecb-116">用于指定将编译“\<computername\>.mof”文件的位置</span><span class="sxs-lookup"><span data-stu-id="8aecb-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="8aecb-117">将自己的参数添加到配置中</span><span class="sxs-lookup"><span data-stu-id="8aecb-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="8aecb-118">除了内置参数，还可以向配置添加自己的参数。</span><span class="sxs-lookup"><span data-stu-id="8aecb-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="8aecb-119">参数块直接进入配置声明，就像函数一样。</span><span class="sxs-lookup"><span data-stu-id="8aecb-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="8aecb-120">配置参数块应位于任何节点  声明之外，并且位于任何导入  语句之上。</span><span class="sxs-lookup"><span data-stu-id="8aecb-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="8aecb-121">通过添加参数，可以使配置更加可靠和动态。</span><span class="sxs-lookup"><span data-stu-id="8aecb-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="8aecb-122">添加 ComputerName 参数</span><span class="sxs-lookup"><span data-stu-id="8aecb-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="8aecb-123">可以添加的第一个参数是 `-Computername` 参数，这样就可以为任何传递给配置的 `-Computername` 动态编译“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="8aecb-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="8aecb-124">和函数一样，还以定义一个默认值，以防用户没有为 `-ComputerName` 传入值</span><span class="sxs-lookup"><span data-stu-id="8aecb-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="8aecb-125">在配置中，可以在定义节点块时指定 `-ComputerName` 参数。</span><span class="sxs-lookup"><span data-stu-id="8aecb-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="8aecb-126">使用参数调用配置</span><span class="sxs-lookup"><span data-stu-id="8aecb-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="8aecb-127">在将参数添加到配置后，可以像使用 cmdlet 一样使用它们。</span><span class="sxs-lookup"><span data-stu-id="8aecb-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="8aecb-128">编译多个 .mof 文件</span><span class="sxs-lookup"><span data-stu-id="8aecb-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="8aecb-129">节点块还可以接受逗号分隔的计算机名称列表，并为每个计算机名称生成“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="8aecb-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="8aecb-130">可以运行以下示例，为传递给 `-ComputerName` 参数的所有计算机生成“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="8aecb-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="8aecb-131">配置中的高级参数</span><span class="sxs-lookup"><span data-stu-id="8aecb-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="8aecb-132">除了 `-ComputerName` 参数之外，还可以为服务名称和状态添加参数。</span><span class="sxs-lookup"><span data-stu-id="8aecb-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="8aecb-133">下面的示例添加一个带有 `-ServiceName` 参数的参数块，并使用它动态定义 Service  资源块。</span><span class="sxs-lookup"><span data-stu-id="8aecb-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="8aecb-134">它还添加一个 `-State` 参数来动态定义 Service  资源块中的状态  。</span><span class="sxs-lookup"><span data-stu-id="8aecb-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="8aecb-135">在更高级的场景中，将动态数据移动到结构化的[配置数据](configData.md)中可能更有意义。</span><span class="sxs-lookup"><span data-stu-id="8aecb-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="8aecb-136">示例配置现采用动态 `$ServiceName`，但若未指定，编译将导致错误。</span><span class="sxs-lookup"><span data-stu-id="8aecb-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="8aecb-137">可以像本例一样添加一个默认值。</span><span class="sxs-lookup"><span data-stu-id="8aecb-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="8aecb-138">不过，在本例中，强制用户为 `$ServiceName` 参数指定一个值更有意义。</span><span class="sxs-lookup"><span data-stu-id="8aecb-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="8aecb-139">`parameter` 属性允许你向配置的参数添加进一步的验证和管道支持。</span><span class="sxs-lookup"><span data-stu-id="8aecb-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="8aecb-140">在任何参数声明之上，添加 `parameter` 属性块，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="8aecb-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="8aecb-141">可以为每个 `parameter` 属性指定自变量，以控制已定义参数的各个方面。</span><span class="sxs-lookup"><span data-stu-id="8aecb-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="8aecb-142">下面的示例使 `$ServiceName` 成为强制  参数。</span><span class="sxs-lookup"><span data-stu-id="8aecb-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="8aecb-143">对于 `$State` 参数，我们希望阻止用户指定预定义集之外的值（如 Running、Stopped），`ValidationSet*` 属性将阻止用户指定预定义集之外的值（如 Running、Stopped）。</span><span class="sxs-lookup"><span data-stu-id="8aecb-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="8aecb-144">下面的示例将 `ValidationSet` 属性添加到 `$State` 参数。</span><span class="sxs-lookup"><span data-stu-id="8aecb-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="8aecb-145">由于我们不希望使 `$State` 成为强制  参数，因此需要为它添加一个默认值。</span><span class="sxs-lookup"><span data-stu-id="8aecb-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="8aecb-146">在使用 `validation` 属性时，不需要指定 `parameter` 属性。</span><span class="sxs-lookup"><span data-stu-id="8aecb-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="8aecb-147">可以在 [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters) 中了解更多有关 `parameter` 和验证属性的信息。</span><span class="sxs-lookup"><span data-stu-id="8aecb-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="8aecb-148">完全参数化的配置</span><span class="sxs-lookup"><span data-stu-id="8aecb-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="8aecb-149">现在，我们有了一个参数化配置，该配置强制用户指定 `-InstanceName`、`-ServiceName`，并验证 `-State` 参数。</span><span class="sxs-lookup"><span data-stu-id="8aecb-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="8aecb-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8aecb-150">See also</span></span>

- [<span data-ttu-id="8aecb-151">编写 DSC 配置的帮助</span><span class="sxs-lookup"><span data-stu-id="8aecb-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="8aecb-152">动态配置</span><span class="sxs-lookup"><span data-stu-id="8aecb-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="8aecb-153">在配置中使用配置数据</span><span class="sxs-lookup"><span data-stu-id="8aecb-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="8aecb-154">分离配置和环境数据</span><span class="sxs-lookup"><span data-stu-id="8aecb-154">Separate configuration and environment data</span></span>](separatingEnvData.md)

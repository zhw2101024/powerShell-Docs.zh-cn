---
ms.date: 12/12/2018
keywords: dsc，powershell、 资源、 库、 安装程序
title: 向配置添加参数
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400459"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="e09ea-103">向配置添加参数</span><span class="sxs-lookup"><span data-stu-id="e09ea-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="e09ea-104">与的函数，类似[配置](configurations.md)可以对其进行参数化，以允许基于用户输入的更多动态配置。</span><span class="sxs-lookup"><span data-stu-id="e09ea-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="e09ea-105">步骤是类似于中所述[包含参数的函数](/powershell/module/microsoft.powershell.core/about/about_functions)。</span><span class="sxs-lookup"><span data-stu-id="e09ea-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="e09ea-106">此示例从配置为"running"的"后台处理程序"服务的基本配置。</span><span class="sxs-lookup"><span data-stu-id="e09ea-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="e09ea-107">内置配置参数</span><span class="sxs-lookup"><span data-stu-id="e09ea-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="e09ea-108">与函数不同， [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)属性添加任何功能。</span><span class="sxs-lookup"><span data-stu-id="e09ea-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="e09ea-109">除了[通用参数](/powershell/module/microsoft.powershell.core/about/about_commonparameters)，配置还可以使用以下内置参数，而无需定义它们。</span><span class="sxs-lookup"><span data-stu-id="e09ea-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="e09ea-110">参数</span><span class="sxs-lookup"><span data-stu-id="e09ea-110">Parameter</span></span>  |<span data-ttu-id="e09ea-111">说明</span><span class="sxs-lookup"><span data-stu-id="e09ea-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="e09ea-112">用于定义[复合配置](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="e09ea-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="e09ea-113">用于定义[复合配置](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="e09ea-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="e09ea-114">用于定义[复合配置](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="e09ea-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="e09ea-115">用于将传递在结构化[配置数据](configData.md)在配置中使用。</span><span class="sxs-lookup"><span data-stu-id="e09ea-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="e09ea-116">使用指定的位置在"\<computername\>.mof"的文件将编译</span><span class="sxs-lookup"><span data-stu-id="e09ea-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="e09ea-117">将您自己的参数添加到配置</span><span class="sxs-lookup"><span data-stu-id="e09ea-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="e09ea-118">除了内置参数，还可以向你的配置中添加您自己的参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="e09ea-119">在参数块将会直接配置声明，就像函数一样。</span><span class="sxs-lookup"><span data-stu-id="e09ea-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="e09ea-120">配置参数块应为任何外部**节点**声明，及更高版本任何*导入*语句。</span><span class="sxs-lookup"><span data-stu-id="e09ea-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="e09ea-121">通过添加参数，可以使你的配置，更可靠并且动态。</span><span class="sxs-lookup"><span data-stu-id="e09ea-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="e09ea-122">添加 ComputerName 参数</span><span class="sxs-lookup"><span data-stu-id="e09ea-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="e09ea-123">您可以添加的第一个参数是`-Computername`参数，因此您可以为任何动态编译".mof"文件`-Computername`传递给你的配置。</span><span class="sxs-lookup"><span data-stu-id="e09ea-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="e09ea-124">与函数一样，您还可以定义默认值，如果用户未通过中的值 `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="e09ea-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="e09ea-125">在您的配置，然后可以指定您`-ComputerName`参数定义你的节点块时。</span><span class="sxs-lookup"><span data-stu-id="e09ea-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="e09ea-126">调用您的配置参数</span><span class="sxs-lookup"><span data-stu-id="e09ea-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="e09ea-127">参数添加到你的配置后，你可以使用它们，就像使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e09ea-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="e09ea-128">编译多个.mof 文件</span><span class="sxs-lookup"><span data-stu-id="e09ea-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="e09ea-129">节点块还可以接受逗号分隔的计算机名称列表，并将每个生成".mof"文件。</span><span class="sxs-lookup"><span data-stu-id="e09ea-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="e09ea-130">可以运行下面的示例生成的所有计算机传递到文件".mof"`-ComputerName`参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="e09ea-131">在配置中的高级的参数</span><span class="sxs-lookup"><span data-stu-id="e09ea-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="e09ea-132">除了`-ComputerName`参数，我们可以添加服务名称和状态参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="e09ea-133">下面的示例添加具有一个参数块`-ServiceName`参数，并使用它以动态定义**服务**资源块。</span><span class="sxs-lookup"><span data-stu-id="e09ea-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="e09ea-134">它还添加了`-State`参数以动态定义**状态**中**服务**资源块。</span><span class="sxs-lookup"><span data-stu-id="e09ea-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="e09ea-135">在多个 advacned 情况下，它可能会更有意义将动态数据移动到一种结构化[配置数据](configData.md)。</span><span class="sxs-lookup"><span data-stu-id="e09ea-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="e09ea-136">现在，配置该示例使用动态`$ServiceName`，但如果未指定，则编译将导致错误。</span><span class="sxs-lookup"><span data-stu-id="e09ea-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="e09ea-137">可以添加如下例所示的默认值。</span><span class="sxs-lookup"><span data-stu-id="e09ea-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="e09ea-138">在这种情况，它更有意义，只需强制用户指定的值`$ServiceName`参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="e09ea-139">`parameter`特性，可将进一步验证和管道支持添加到你的配置参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="e09ea-140">任何参数声明上方，添加`parameter`特性块，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e09ea-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="e09ea-141">可以将每个参数指定`parameter`属性，控制定义的参数的各个方面。</span><span class="sxs-lookup"><span data-stu-id="e09ea-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="e09ea-142">以下示例使`$ServiceName`**必需**参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="e09ea-143">有关`$State`参数，我们希望防止用户指定一组预定义之外的值 （如正在运行、 已停止）`ValidationSet*`特性会防止用户指定一组预定义 （如正在运行，之外的值已停止）。</span><span class="sxs-lookup"><span data-stu-id="e09ea-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="e09ea-144">以下示例将添加`ValidationSet`属性为`$State`参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="e09ea-145">因为我们不想要`$State`参数**必需**，我们将需要为其添加默认值。</span><span class="sxs-lookup"><span data-stu-id="e09ea-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="e09ea-146">不需要指定`parameter`属性时使用`validation`属性。</span><span class="sxs-lookup"><span data-stu-id="e09ea-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="e09ea-147">可以阅读更多有关`parameter`和中的验证特性[about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e09ea-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="e09ea-148">完全参数化的配置</span><span class="sxs-lookup"><span data-stu-id="e09ea-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="e09ea-149">现在，我们会强制用户在指定的参数化的配置`-InstanceName`， `-ServiceName`，并验证`-State`参数。</span><span class="sxs-lookup"><span data-stu-id="e09ea-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="e09ea-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e09ea-150">See also</span></span>

- [<span data-ttu-id="e09ea-151">编写 DSC 配置的帮助</span><span class="sxs-lookup"><span data-stu-id="e09ea-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="e09ea-152">动态配置</span><span class="sxs-lookup"><span data-stu-id="e09ea-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="e09ea-153">在你的配置中使用配置数据</span><span class="sxs-lookup"><span data-stu-id="e09ea-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="e09ea-154">单独的配置和环境数据</span><span class="sxs-lookup"><span data-stu-id="e09ea-154">Separate configuration and environment data</span></span>](separatingEnvData.md)

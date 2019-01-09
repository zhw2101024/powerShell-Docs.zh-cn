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
# <a name="add-parameters-to-a-configuration"></a>向配置添加参数

与的函数，类似[配置](configurations.md)可以对其进行参数化，以允许基于用户输入的更多动态配置。 步骤是类似于中所述[包含参数的函数](/powershell/module/microsoft.powershell.core/about/about_functions)。

此示例从配置为"running"的"后台处理程序"服务的基本配置。

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

## <a name="built-in-configuration-parameters"></a>内置配置参数

与函数不同， [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)属性添加任何功能。 除了[通用参数](/powershell/module/microsoft.powershell.core/about/about_commonparameters)，配置还可以使用以下内置参数，而无需定义它们。

|参数  |说明  |
|---------|---------|
|`-InstanceName`|用于定义[复合配置](compositeconfigs.md)|
|`-DependsOn`|用于定义[复合配置](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|用于定义[复合配置](compositeconfigs.md)|
|`-ConfigurationData`|用于将传递在结构化[配置数据](configData.md)在配置中使用。|
|`-OutputPath`|使用指定的位置在"\<computername\>.mof"的文件将编译|

## <a name="adding-your-own-parameters-to-configurations"></a>将您自己的参数添加到配置

除了内置参数，还可以向你的配置中添加您自己的参数。 在参数块将会直接配置声明，就像函数一样。 配置参数块应为任何外部**节点**声明，及更高版本任何*导入*语句。 通过添加参数，可以使你的配置，更可靠并且动态。

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>添加 ComputerName 参数

您可以添加的第一个参数是`-Computername`参数，因此您可以为任何动态编译".mof"文件`-Computername`传递给你的配置。 与函数一样，您还可以定义默认值，如果用户未通过中的值 `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

在您的配置，然后可以指定您`-ComputerName`参数定义你的节点块时。

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>调用您的配置参数

参数添加到你的配置后，你可以使用它们，就像使用 cmdlet。

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>编译多个.mof 文件

节点块还可以接受逗号分隔的计算机名称列表，并将每个生成".mof"文件。 可以运行下面的示例生成的所有计算机传递到文件".mof"`-ComputerName`参数。

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

## <a name="advanced-parameters-in-configurations"></a>在配置中的高级的参数

除了`-ComputerName`参数，我们可以添加服务名称和状态参数。 下面的示例添加具有一个参数块`-ServiceName`参数，并使用它以动态定义**服务**资源块。 它还添加了`-State`参数以动态定义**状态**中**服务**资源块。

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
> 在多个 advacned 情况下，它可能会更有意义将动态数据移动到一种结构化[配置数据](configData.md)。

现在，配置该示例使用动态`$ServiceName`，但如果未指定，则编译将导致错误。 可以添加如下例所示的默认值。

```powershell
[String]
$ServiceName="Spooler"
```

在这种情况，它更有意义，只需强制用户指定的值`$ServiceName`参数。 `parameter`特性，可将进一步验证和管道支持添加到你的配置参数。

任何参数声明上方，添加`parameter`特性块，如下面的示例中所示。

```powershell
[parameter()]
[String]
$ServiceName
```

可以将每个参数指定`parameter`属性，控制定义的参数的各个方面。 以下示例使`$ServiceName`**必需**参数。

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

有关`$State`参数，我们希望防止用户指定一组预定义之外的值 （如正在运行、 已停止）`ValidationSet*`特性会防止用户指定一组预定义 （如正在运行，之外的值已停止）。 以下示例将添加`ValidationSet`属性为`$State`参数。 因为我们不想要`$State`参数**必需**，我们将需要为其添加默认值。

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> 不需要指定`parameter`属性时使用`validation`属性。

可以阅读更多有关`parameter`和中的验证特性[about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md)。

## <a name="fully-parameterized-configuration"></a>完全参数化的配置

现在，我们会强制用户在指定的参数化的配置`-InstanceName`， `-ServiceName`，并验证`-State`参数。

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

## <a name="see-also"></a>另请参阅

- [编写 DSC 配置的帮助](configHelp.md)
- [动态配置](flow-control-in-configurations.md)
- [在你的配置中使用配置数据](configData.md)
- [单独的配置和环境数据](separatingEnvData.md)

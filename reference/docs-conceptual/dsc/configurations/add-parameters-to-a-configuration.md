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
# <a name="add-parameters-to-a-configuration"></a>向配置添加参数

和函数一样，[配置](configurations.md)也可以参数化，以便基于用户输入进行更多动态配置。 这些步骤与[带有参数的函数](/powershell/module/microsoft.powershell.core/about/about_functions)中描述的步骤类似。

本例从一个基本配置开始，该配置将“Spooler”服务配置为“Running”。

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

## <a name="built-in-configuration-parameters"></a>内置配置参数

但是，与函数不同，[CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 属性不会添加任何功能。 除了[通用参数](/powershell/module/microsoft.powershell.core/about/about_commonparameters)之外，配置还可以使用以下内置参数，而无需用户对其进行定义。

|参数  |说明  |
|---------|---------|
|`-InstanceName`|用于定义[复合配置](compositeconfigs.md)|
|`-DependsOn`|用于定义[复合配置](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|用于定义[复合配置](compositeconfigs.md)|
|`-ConfigurationData`|用于传入结构化的[配置数据](configData.md)，以便在配置中使用。|
|`-OutputPath`|用于指定将编译“\<computername\>.mof”文件的位置|

## <a name="adding-your-own-parameters-to-configurations"></a>将自己的参数添加到配置中

除了内置参数，还可以向配置添加自己的参数。 参数块直接进入配置声明，就像函数一样。 配置参数块应位于任何节点  声明之外，并且位于任何导入  语句之上。 通过添加参数，可以使配置更加可靠和动态。

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>添加 ComputerName 参数

可以添加的第一个参数是 `-Computername` 参数，这样就可以为任何传递给配置的 `-Computername` 动态编译“.mof”文件。 和函数一样，还以定义一个默认值，以防用户没有为 `-ComputerName` 传入值

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

在配置中，可以在定义节点块时指定 `-ComputerName` 参数。

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>使用参数调用配置

在将参数添加到配置后，可以像使用 cmdlet 一样使用它们。

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>编译多个 .mof 文件

节点块还可以接受逗号分隔的计算机名称列表，并为每个计算机名称生成“.mof”文件。 可以运行以下示例，为传递给 `-ComputerName` 参数的所有计算机生成“.mof”文件。

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

## <a name="advanced-parameters-in-configurations"></a>配置中的高级参数

除了 `-ComputerName` 参数之外，还可以为服务名称和状态添加参数。 下面的示例添加一个带有 `-ServiceName` 参数的参数块，并使用它动态定义 Service  资源块。 它还添加一个 `-State` 参数来动态定义 Service  资源块中的状态  。

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
> 在更高级的场景中，将动态数据移动到结构化的[配置数据](configData.md)中可能更有意义。

示例配置现采用动态 `$ServiceName`，但若未指定，编译将导致错误。 可以像本例一样添加一个默认值。

```powershell
[String]
$ServiceName="Spooler"
```

不过，在本例中，强制用户为 `$ServiceName` 参数指定一个值更有意义。 `parameter` 属性允许你向配置的参数添加进一步的验证和管道支持。

在任何参数声明之上，添加 `parameter` 属性块，如下面的示例所示。

```powershell
[parameter()]
[String]
$ServiceName
```

可以为每个 `parameter` 属性指定自变量，以控制已定义参数的各个方面。 下面的示例使 `$ServiceName` 成为强制  参数。

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

对于 `$State` 参数，我们希望阻止用户指定预定义集之外的值（如 Running、Stopped），`ValidationSet*` 属性将阻止用户指定预定义集之外的值（如 Running、Stopped）。 下面的示例将 `ValidationSet` 属性添加到 `$State` 参数。 由于我们不希望使 `$State` 成为强制  参数，因此需要为它添加一个默认值。

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> 在使用 `validation` 属性时，不需要指定 `parameter` 属性。

可以在 [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters) 中了解更多有关 `parameter` 和验证属性的信息。

## <a name="fully-parameterized-configuration"></a>完全参数化的配置

现在，我们有了一个参数化配置，该配置强制用户指定 `-InstanceName`、`-ServiceName`，并验证 `-State` 参数。

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

## <a name="see-also"></a>另请参阅

- [编写 DSC 配置的帮助](configHelp.md)
- [动态配置](flow-control-in-configurations.md)
- [在配置中使用配置数据](configData.md)
- [分离配置和环境数据](separatingEnvData.md)

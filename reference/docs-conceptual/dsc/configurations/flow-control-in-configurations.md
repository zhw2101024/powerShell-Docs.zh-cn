---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 配置中的条件语句和循环
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736890"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>配置中的条件语句和循环

可以使用 PowerShell 流控制关键字使[配置](configurations.md)更加动态。 本文介绍了如何使用条件语句和循环来使 `Configuration` 更加动态。 将条件语句和循环与[参数](add-parameters-to-a-configuration.md)和[配置数据](configData.md)结合使用，用户可以在编译 `Configuration` 时更灵活地进行控制。

就像函数或脚本块一样，可以在 `Configuration` 中使用任何 PowerShell 语言。
只有在调用 `Configuration` 来编译“`.mof`”文件时才会计算使用的语句。 下面的示例展示了一些场景来演示概念。 条件语句和循环通常与参数和配置数据一起使用。

在这个简单示例中，Service  资源块在编译时检索服务的当前状态，以生成维护其当前状态的“`.mof`”文件。

> [!NOTE]
> 使用动态资源块将抢占 Intellisense 的效率。 在编译 `Configuration` 之前，PowerShell 解析器无法确定指定的值是否可接受。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

此外，可以使用 `foreach` 循环为当前计算机上的每个服务创建一个 Service  资源块。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

你还可以通过使用 `if` 语句，仅为联机的计算机创建 `Configuration`。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> 上述示例中的动态资源块引用当前计算机。 在本例中，这将是你编写 `Configuration` 的计算机，而不是目标节点。

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>总结

总之，可以在 `Configuration` 中使用任何 PowerShell 语言功能。

这包括：

- 自定义对象
- 哈希表
- 字符串操作
- 远程处理
- WMI 和 CIM
- ActiveDirectory 对象
- 更多...

在 `Configuration` 中定义的任何 PowerShell 代码都将在编译时计算，但也可以将代码置于包含 `Configuration` 的脚本中。 导入 `Configuration` 时，将执行 `Configuration` 块之外的任何代码。

## <a name="see-also"></a>另请参阅

- [向配置添加参数](add-parameters-to-a-configuration.md)
- [从配置中分离出配置数据](configData.md)

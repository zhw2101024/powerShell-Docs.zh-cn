---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 配置中的条件语句和循环
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954074"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>配置中的条件语句和循环

可以使用 PowerShell 流控制关键字使[配置](configurations.md)更加动态。 本文将介绍如何使用条件语句和循环来使配置更加动态。 将条件语句和循环与[参数](add-parameters-to-a-configuration.md)和[配置数据](configData.md)结合使用，用户可以在编译配置时更灵活地进行控制。

就像函数或脚本块一样，可以在配置中使用任何 PowerShell 语言。 只有在调用配置来编译“.mof”文件时才会计算使用的语句。 下面的示例展示了一些简单的场景来演示概念。 条件语句和循环通常与参数和配置数据一起使用。

在这个简单示例中，Service  资源块在编译时检索服务的当前状态，以生成维护其当前状态的“.mof”文件。

> [!NOTE]
> 使用动态资源块将抢占 Intellisense 的效率。 在编译配置之前，PowerShell 解析器无法确定指定的值是否可接受。

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

此外，可以使用 `foreach` 循环为当前计算机上的每个服务创建一个 Service  块资源。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
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

还可以仅使用简单的 `if` 语句为联机计算机创建配置。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> 上述示例中的动态资源块引用当前计算机。 在本例中，这将是你编写配置的计算机，而不是目标节点。

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>摘要

总之，可以在配置中使用任何 PowerShell 语言。

这包括：

- 自定义对象
- 哈希表
- 字符串操作
- 远程处理
- WMI 和 CIM
- ActiveDirectory 对象
- 更多...

在配置中定义的任何 PowerShell 代码都将在编译时计算，但也可以将代码置于包含配置的脚本中。 在导入配置时，将执行配置块之外的任何代码。

## <a name="see-also"></a>另请参阅

- [向配置添加参数](add-parameters-to-a-configuration.md)
- [从配置中分离出配置数据](configData.md)

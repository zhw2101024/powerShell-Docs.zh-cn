---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 配置中的条件语句和循环
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400399"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>配置中的条件语句和循环

可以让你[配置](configurations.md)更加动态使用 PowerShell 流控制关键字。 本文将说明如何使用条件语句和循环来使你的配置更加动态化。 组合条件分支和循环[参数](add-parameters-to-a-configuration.md)并[配置数据](configData.md)允许您更大的灵活性和控制编译你的配置时。

就像函数或脚本块，可以使用配置内的任何 PowerShell 语言。 当您调用你的配置来编译".mof"文件时，才会计算您使用的语句。 下面的示例演示简单的方案来演示概念。 条件语句都使用了循环更频繁地使用参数和配置数据。

在此简单示例中，**服务**资源块检索在编译时生成保持其当前状态的".mof"文件服务的当前状态。

> [!NOTE]
> 使用动态资源块将抢占 Intellisense 的有效性。 PowerShell 分析器无法确定指定的值是否可以接受，直到编译配置。

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

此外，您可以创建**服务**阻止在当前计算机上的每个服务的资源使用`foreach`循环。

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

你也只能创建处于在线状态，通过使用一个简单的机配置`if`语句。

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
> 动态资源块以上述示例引用在当前计算机。 在此情况下，将在创作配置的计算机，而不是目标节点。

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>摘要

总之，您可以使用配置内的任何 PowerShell 语言。

这包括诸如：

- 自定义对象
- 哈希表
- 字符串操作
- 远程处理
- WMI 和 CIM
- 与 active Directory 对象
- 更多...

在配置中定义的任何 PowerShell 代码将计算编译时，但还可以将代码放在脚本中包含你的配置。 导入你的配置时，将执行在配置块之外的任何代码。

## <a name="see-also"></a>另请参阅

- [向配置添加参数](add-parameters-to-a-configuration.md)
- [从配置中分离出配置数据](configData.md)

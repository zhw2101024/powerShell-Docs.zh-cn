---
title: "PowerShell Desired State Configuration 入门"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: c5ee7f7e7678b60700edb1ab1b66139791ea67c6

---

# PowerShell Desired State Configuration 入门 #

本指南介绍了如何开始创建 PowerShell Desired State Configuration文档并将其应用到计算机中。 假定你基本熟悉 PowerShell cmdlet、模块和函数。 


## 创建配置 ##

[**配置**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)是描述环境的文档。 环境中包含“**节点**”（通常是虚拟机或物理计算机）。 

配置会以各种形式出现。 创建新配置最简单方法就是创建 .ps1（PowerShell 脚本）文件。 若要执行此操作，请打开首选编辑器。 PowerShell ISE 是一个不错的选择，因为它本身了解 DSC。 将以下内容另存为 PS1：

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## Configuration 部分 ##
**Configuration** 是已添加到 PowerShell 4.0 的关键字。 它表示一种由 Desired State Configuration.使用的特殊 PowerShell 函数。 在此示例中，该函数被命名为 myFirstConfiguration。 

下一行是类似于导入模块的导入语句。 稍后将对其展开讨论。

“节点”定义此配置将对其进行操作的计算机名称。 尽管此配置是本地编辑的，但是这些配置可访问并配置远程节点。 

节点可以是计算机名称或 IP 地址。 单个配置文档中可有多个节点。 使用[配置数据](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)，你也可将相同的配置应用到多个节点。 在这种情况下，该节点是“localhost” - 表示本地计算机。 

下一项是[**资源**](https://msdn.microsoft.com/en-us/powershell/dsc/resources)。 资源是配置的构建基块。 每个资源都是定义计算机单方面实现逻辑的模块。 可通过在 PowerShell 中运行 **Get-DscResource** 查看计算机上的每个资源。 资源必须存在于本地计算机中并通过 **Import-DscResource**（位于此配置的第二行）导入后，才可在配置中使用它们。 

**执行配置**

如果以上脚本已保存并运行，则不会产生任何输出。 这是因为配置只是一个函数，并且上述脚本已定义但尚未运行该函数。 将函数定义后，必须调用它：
```powershell
myFirstConfiguration
```

执行时，配置函数验证配置是否有效。 不应有语法错误，资源需定义所有强制参数，同时在执行前应导入所有资源。

一旦执行配置，它将使用含 **.MOF 文件** 的配置的名称为配置中的每个节点创建文件夹。 .MOF 文件是一种基于标准的管理格式，PowerShell DSC 用其在网络上进行通信。

执行配置：
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
这将创建可访问配置中节点的 PowerShell 作业，并对其进行配置。 若要查看作业输出，请使用 -Wait。 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```




<!--HONumber=Jun16_HO4-->



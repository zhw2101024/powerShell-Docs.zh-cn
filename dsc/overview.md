---
title:   Windows PowerShell Desired State Configuration 概述 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Windows PowerShell Desired State Configuration 概述 

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

本主题介绍 Windows PowerShell 中的 Windows PowerShell Desired State Configuration (DSC) 功能。 你可以使用本主题获取 DSC 概述并查找了解和使用 DSC 所需的文档资源。

## 功能描述
DSC 是 Windows PowerShell 中的新管理平台，可用于部署和管理软件服务的配置数据，并管理这些服务的运行的环境。

DSC 提供了一组 Windows PowerShell 语言扩展、新的 Windows PowerShell cmdlet 和可用于以声明方式指定软件环境配置方式的资源。 它还提供了维护和管理现有配置的方法。

## 实际的应用程序
在以下示例方案中，你可以使用内置 DSC 资源自动化配置和管理一组计算机（也称为目标节点）：

* 启用或禁用服务器角色和功能
* 管理注册表设置
* 管理文件和目录
* 启动、停止和管理进程及服务
* 管理组和用户帐户
* 部署新软件
* 管理环境变量
* 运行 Windows PowerShell 脚本
* 修复偏离所需状态的配置
* 发现给定节点上的实际配置状态

## 关键概念
DSC 是一个声明性平台，用于配置、部署和管理系统。 它包括三个主要组件：

* [Configurations](configurations.md) 是声明性的 PowerShell 脚本，用于定义和配置资源实例。 在运行配置时，DSC（和配置调用的资源）将“使其如此”，确保系统处于配置所布局的状态。 DSC 配置也是幂等的：无论配置声明什么状态，本地配置管理器 (LCM) 都将继续确保计算机已配置为该状态。
* 资源是 DSC 的命令性构造块，编写用于对子系统的各组件进行建模，以及实现其不断变化的状态的控制流。 它们驻留在 PowerShell 模块内，可编写以便对某项内容进行建模，建模对象可以是一般的文件或 Windows 进程，也可以是在 Azure 中运行的具体 IIS 服务器或 VM。
* 本地配置管理器 (LCM) 是一个引擎，DSC 通过该引擎促进资源和配置之间的交互。 LCM 使用由资源实现的控制流定期轮询系统，以确保配置所布局的状态得到保持。 如果系统不处于相应状态，LCM 将根据配置声明使用资源内的更多逻辑“使其如此”。 

DSC 还包含用于创建配置的大量新语言关键字、cmdlet 和工具，它们可帮助你构建 DSC 资源、调用配置和管理 LCM。 其中许多 cmdlet 是 Windows 8.1 中 PsDesiredStateConfig 模块的一部分（包括 `Start-DscConfiguration`、`Set-DscLocalConfigurationManager` 和 `Get-DscResource`）。 xDscResourceDesigner（位于 [PowerShell 库](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)中）是一个 cmdlet 集合，可简化 DSC 资源的开发。

## 另请参阅
* [DSC 配置](configurations.md)
* [DSC 资源](resources.md)
* [配置本地配置管理器](metaConfig.md)



<!--HONumber=May16_HO3-->



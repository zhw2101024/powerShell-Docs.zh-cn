---
title: "Windows PowerShell Desired State Configuration 概述"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: d215289675ee9c2b7121fa3d785549c48733d2e8
ms.sourcegitcommit: 910f090edd401870fe137553c3db00d562024a4c
translationtype: HT
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell Desired State Configuration 概述 

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

DSC 是 PowerShell 中的一个管理平台，可允许通过配置为代码来管理 IT 和开发基础结构。

- 有关使用 DSC 的业务优势的概述，请参阅[适用于决策者的 Desired State Configuration 概述](decisionMaker.md)。
- 有关使用 DSC 的工程优势的概述，请参阅 [适用于工程师的 Desired State Configuration 概述]DscForEngineers.md)。
- 要快速使用 DSC，请参阅 [DSC 快速入门]quickStart.md。

## <a name="key-concepts"></a>关键概念

DSC 是一个声明性平台，用于配置、部署和管理系统。 它包括三个主要组件：

- [Configurations](configurations.md) 是声明性的 PowerShell 脚本，用于定义和配置资源实例。
    在运行配置时，DSC（和配置调用的资源）将“使其如此”，确保系统处于配置所布局的状态。 
    DSC 配置也是幂等的：无论配置声明什么状态，本地配置管理器 (LCM) 都将继续确保计算机已配置为该状态。
- 资源是 DSC 的“使其如此”部分。 它们包含将配置的目标置于并保持在指定状态的代码。 
    资源驻留在 PowerShell 模块内，可编写以便对某项内容进行建模，建模对象可以是一般的文件或 Windows 进程，也可以是在 Azure 中运行的具体 IIS 服务器或 VM。
- 本地配置管理器 (LCM) 是一个引擎，DSC 通过该引擎促进资源和配置之间的交互。 
    LCM 使用由资源实现的控制流定期轮询系统，以确保配置所定义的状态得以保持。 
    如果系统不处于相应状态，LCM 将根据配置调用资源内的代码“使其如此”。 

## <a name="see-also"></a>另请参阅

- [DSC 配置](configurations.md)
- [DSC 资源](resources.md)
- [配置本地配置管理器](metaConfig.md)


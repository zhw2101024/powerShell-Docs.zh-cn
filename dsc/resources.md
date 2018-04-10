---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: DSC 资源
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a>DSC 资源

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。 资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。

资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。  资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。

以下主题介绍了 DSC 资源：

- [内置 DSC 资源](builtInResource.md)
- [构建自定义 DSC 资源](authoringResource.md)
- [适用于 Linux 的内置 DSC 资源](lnxBuiltInResources.md)
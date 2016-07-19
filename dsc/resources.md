---
title: "DSC 资源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 0a27a40b995393c41f0496a5f7fa3f56fbd865dd

---

# DSC 资源

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。 资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。

资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。  资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。  

以下主题介绍了 DSC 资源：

- [内置 DSC 资源](builtInResource.md)
- [生成自定义 DSC 资源](authoringResource.md)
- [适用于 Linux 的内置 DSC 资源](lnxBuiltInResources.md)




<!--HONumber=Jun16_HO4-->



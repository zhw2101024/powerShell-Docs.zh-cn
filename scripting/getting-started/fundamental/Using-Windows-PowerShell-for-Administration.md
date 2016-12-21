---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "使用 Windows PowerShell 进行管理"
ms.technology: powershell
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: c0a15bc813e6fdb850fe2d957711f1ad005d853d
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="using-windows-powershell-for-administration"></a>使用 Windows PowerShell 进行管理
Windows PowerShell 的根本目标是通过交互方式或从脚本提供针对系统的更好的、更便捷的管理控制。 本章展示了针对使用 Windows PowerShell 管理 Windows 系统过程中许多特殊问题的解决方案。 虽然我们在 Windows PowerShell 用户指南中未讨论脚本或函数，但以后可以从脚本使用这些解决方案或将其用作函数。 我们将展示包括函数在内的示例，作为解决问题的解决方案的一部分。

在整个解决方案介绍中，你会看到解决方案的组合，它们使用特定的 cmdlet、常规的 Get-WmiObject cmdlet，甚至还有作为 Windows 和 .NET Framework 基础结构一部分的外部工具。 外部工具的使用是 Windows PowerShell 长久以来设计目的的一部分。 虽然此系统在不断改进，用户仍会遇到可用工具集无法实现其全部需求的情况。 Windows PowerShell 尝试将针对各种可能情况的解决方案进行整合，而不仅仅依赖于 cmdlet 的实现。


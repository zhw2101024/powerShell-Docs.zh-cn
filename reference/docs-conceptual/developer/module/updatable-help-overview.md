---
title: 可更新的帮助概述 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366956"
---
# <a name="updatable-help-overview"></a>可更新帮助概述

本文档简要介绍了 Windows PowerShell 可更新帮助功能的设计和操作。 它适用于向用户提供 Windows PowerShell 帮助主题的模块作者和其他人员。

## <a name="introduction"></a>简介

Windows PowerShell 帮助主题是 Windows PowerShell 体验中不可或缺的一部分。 与 Windows PowerShell 模块一样，帮助主题会不断地由作者和 Windows PowerShell 用户社区的内容进行更新和改进。

Windows PowerShell 3.0 中引入的 "*可更新的帮助*" 功能可确保用户在命令提示符下具有最新版本的帮助主题，即使对于内置的 Windows powershell 命令，也不会下载新模块或运行 Windows 更新。 可更新的帮助提供可从 Internet 下载最新版本的帮助主题的 cmdlet，并将其安装到用户本地计算机上的正确子目录中，使更新变得简单。 即使是防火墙后面的用户，也可以使用新的 cmdlet 从内部文件共享获取更新的帮助。

Windows®8和 Windows Server®2012中的所有 Windows PowerShell 模块都完全支持可更新的帮助，其功能适用于所有 Windows PowerShell 模块作者。 可更新帮助仅支持基于 XML 的帮助文件。 它不支持基于注释的帮助。

可更新的帮助包含以下功能。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet，该 cmdlet 确定用户是否为模块提供最新的帮助文件，如果不是，则从 Internet 下载最新的帮助文件，将其解压缩，并将其安装到用户计算机上的正确模块子目录。
  用户可以使用[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 立即查看新安装的帮助主题。
  它们不需要重新启动 PowerShell。

- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet，它从 Internet 下载最新的帮助文件，并将它们保存在文件系统目录中。 用户可以使用 `Update-Help` cmdlet 从文件系统目录中获取帮助文件，并将它们解压缩并安装到用户计算机上的模块子目录中。 `Save-Help` cmdlet 适用于限制或没有 Internet 访问权限的用户，以及希望限制 Internet 访问的企业。

- **模块的帮助**。 模块的帮助文件作为一个单元进行管理和传送，因此用户可以获取它们所使用的模块的所有帮助文件。 仅对模块支持可更新帮助，不适用于 Windows PowerShell 管理单元。

- **版本支持**。 可更新帮助使用标准的四位位置（N1。N2.N3.N4）版本号。 当用户计算机上的帮助文件的版本号（或 `Save-Help` 目录）低于 Internet 位置的帮助文件的版本号时，可更新帮助下载帮助文件。

- **多语言支持**。 可更新的帮助支持多个 UI 区域性中的模块帮助文件。 可更新的帮助文件名包括标准语言代码（如 "en-us" 和 "ja-jp"），`Update-Help` 和 `Save-Help` cmdlet 将帮助文件放在模块目录的特定于语言的子目录中。

- **自动生成的帮助**。 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 显示没有 "帮助" 文件的命令的基本帮助。 自动生成的帮助包括命令语法和别名，以及使用联机帮助和可更新帮助的说明。

- **增强的联机帮助**。 轻松访问联机帮助不再需要帮助文件。 `Get-Help` cmdlet 的**online**参数现在从任何命令的**HelpUri**属性的值获取联机帮助主题的 url （如果在帮助文件中找不到联机帮助 URL）。 可以通过将**HelpUri**属性添加到 cmdlet、函数、CIM 命令的代码或使用来填充**HelpUri**属性 **。** 在工作流和脚本中链接基于注释的帮助指令。

  为了使我们的帮助文件可更新，Windows 8 和 Windows Server vNext 中的 Windows PowerShell 模块不附带帮助文件。 用户可以使用可更新帮助安装帮助文件并对其进行更新。 其他模块的作者可以将帮助文件包含在模块中或将其省略。 支持可更新的帮助是可选的，但建议这样做。

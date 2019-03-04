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
ms.openlocfilehash: 4e962890fa1d5c282a02a89f0ae2e263844c635e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856963"
---
# <a name="updatable-help-overview"></a>可更新帮助概述

本文档提供的设计和操作的 Windows PowerShell 可更新帮助功能的基本简介。 它专为模块作者和其他人为用户提供 Windows PowerShell 帮助主题。

## <a name="introduction"></a>简介

Windows PowerShell 帮助主题是 Windows PowerShell 体验的重要组成部分。 类似于 Windows PowerShell 模块的帮助主题进行持续更新并改进了由作者和通过 Windows PowerShell 用户社区的贡献。

*可更新帮助*在 Windows PowerShell 3.0 中引入的功能可确保用户具有在命令提示符下，即使对于内置 Windows PowerShell 命令，最新版本帮助主题而无需下载新的模块或运行 Windows Update。 可更新的帮助简化更新通过提供从 Internet 下载最新版本帮助主题，并在用户的本地计算机上的正确子目录中安装的 cmdlet。 即使防火墙后的用户可以使用新的 cmdlet 从内部文件共享获取更新的帮助。

可更新的帮助完全支持 Windows® 8 和 Windows Server® 2012年中的所有 Windows PowerShell 模块，其功能都适用于所有 Windows PowerShell 模块作者。 可更新的帮助仅支持基于 XML 的帮助文件。 它不支持基于注释的帮助。

可更新帮助中包括以下功能。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet，后者将确定用户是否具有最新的帮助文件的模块和，如果没有，请从 Internet 下载最新帮助文件、 解压缩它们，并将其上安装正确的模块子目录中用户的计算机。 用户可以使用[Get-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 立即查看新安装的帮助主题。 它们不需要重新启动 Windows PowerShell。

- [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet，后者将下载最新的帮助文件从 Internet，并将其保存在文件系统目录中。 用户可以使用`Update-Help`cmdlet 从文件系统目录中，获取帮助文件并解压缩并在用户计算机上的模块子目录中对其进行安装。 `Save-Help` Cmdlet 旨在具有有限的用户或没有 Internet 访问权限，适用于企业的首选限制 Internet 访问权限。

- **有关模块的帮助**。 管理并传递作为一个单元，因此用户可以获取有关他们使用的模块的帮助文件的所有模块的帮助文件。 仅对于模块，不适用于 Windows PowerShell 管理单元支持可更新帮助。

- **版本支持**。 可更新的帮助使用标准四个位置 (N1。N2。N3。N4) 版本号。 可更新的帮助时帮助的版本编号文件在用户计算机上下载的帮助文件 (或在`Save-Help`目录) 低于 Internet 位置的帮助文件的版本号。

- **多语言支持**。 可更新的帮助支持多个 UI 区域性中的模块的帮助文件。 可更新的帮助文件名称中包含标准的语言代码 （如"EN-US"和"JA-JP"） 和`Update-Help`和`Save-Help`cmdlet 将帮助文件放入的模块目录的特定于语言的子目录。

- **自动生成的帮助**。 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 将显示没有帮助文件的命令的基本帮助。 自动生成帮助中包含的命令语法和别名和使用联机帮助和可更新帮助的说明。

- **增强的联机帮助**。 轻松访问联机帮助不再需要的帮助文件。 **联机**的参数`Get-Help`cmdlet 现在可从值中获取联机帮助主题的 URL **HelpUri**属性的任何命令，如果它找不到帮助文件中的联机帮助 URL。 您可以填充**HelpUri**通过添加属性**HelpUri**属性为代码的 cmdlet、 函数和 CIM 命令，或使用 **。链接**基于注释的帮助在工作流和脚本中的指令。

  若要使我们的帮助文件可更新，Windows 8 和 Windows Server vNext 中的 Windows PowerShell 模块不附带帮助文件。 用户可以使用可更新帮助安装帮助文件并更新它们。 其他模块的作者可以在模块中包含帮助文件或忽略这些参数。 对可更新帮助的支持是可选的但建议这样做。

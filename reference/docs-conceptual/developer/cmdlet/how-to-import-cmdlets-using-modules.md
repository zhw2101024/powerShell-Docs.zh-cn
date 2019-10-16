---
title: 如何使用模块导入 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364456"
---
# <a name="how-to-import-cmdlets-using-modules"></a>如何使用模块导入 Cmdlet

本文介绍如何使用二进制模块将 cmdlet 导入到 PowerShell 会话。

> [!NOTE]
> 模块的成员可以包括 cmdlet、提供程序、函数、变量、别名等等。 管理单元只能包含 cmdlet 和提供程序。

## <a name="how-to-load-cmdlets-using-a-module"></a>如何使用模块加载 cmdlet

1. 创建与用于实现 cmdlet 的程序集文件同名的模块文件夹。 在此过程中，将在 Windows `system32` 文件夹中创建模块文件夹。

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. 请确保 `PSModulePath` 环境变量包含新模块文件夹的路径。 默认情况下，系统文件夹已添加到 `PSModulePath` 环境变量中。 若要查看 `PSModulePath`，请键入： `$env:PSModulePath`。

1. 将 cmdlet 程序集复制到模块文件夹中。

1. 将模块清单文件（`.psd1`）添加到模块的根文件夹中。 PowerShell 使用模块清单导入模块。 有关详细信息，请参阅[如何编写 PowerShell 模块清单](../module/how-to-write-a-powershell-module-manifest.md)。

1. 运行以下命令，将 cmdlet 添加到会话：

   `Import-Module [Module_Name]`

   此过程可用于测试 cmdlet。 它将程序集中的所有 cmdlet 添加到会话中。 有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

## <a name="see-also"></a>另请参阅

[如何编写 PowerShell 模块清单](../module/how-to-write-a-powershell-module-manifest.md)

[导入 PowerShell 模块](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[安装模块](../module/installing-a-powershell-module.md)

[修改 PSModulePath 安装路径](../module/modifying-the-psmodulepath-installation-path.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

---
title: 可更新帮助的工作方式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367076"
---
# <a name="how-updatable-help-works"></a>可更新帮助的工作原理

本主题介绍了可更新的帮助如何处理每个模块的 HelpInfo XML 文件和 CAB 文件，并为用户安装更新的帮助。

## <a name="the-update-help-process"></a>Update-help 过程

以下列表描述了当用户运行命令来更新特定 UI 区域性中的模块的帮助文件时， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 的操作。

1. `Update-Help` 从模块清单中的**HelpInfoURI**键的值指定的位置获取远程 HelpInfo XML 文件，并根据架构验证该文件。 （若要查看架构，请参阅[HELPINFO XML 架构](./helpinfo-xml-schema.md)。）然后 `Update-Help` 在用户计算机上的模块目录中查找模块的本地 HelpInfo XML 文件。

2. `Update-Help` 比较模块的远程和本地 HelpInfo XML 文件中指定 UI 区域性的帮助文件的版本号。 如果远程文件上的版本号大于本地文件上的版本号，或者该模块没有本地 HelpInfo XML 文件，`Update-Help` 准备下载新的帮助文件。

3. `Update-Help` 从远程 HelpInfo XML 文件中的**HelpContentUri**元素指定的位置选择模块的 CAB 文件。 它使用模块名称、模块 GUID 和 UI 区域性来标识 CAB 文件。

4. `Update-Help` 下载 CAB 文件，解压缩它，验证帮助内容文件，并将帮助内容文件保存在用户计算机上的模块目录的特定于语言的子目录中。

5. `Update-Help` 通过复制 remote HelpInfo XML 文件来创建本地 HelpInfo XML 文件。 它编辑本地 HelpInfo XML 文件，使其仅包含它所安装的 CAB 文件的元素。 然后，它将本地 HelpInfo XML 文件保存到模块目录中并结束更新。

## <a name="the-save-help-process"></a>保存帮助过程

下面的列表介绍当用户运行命令来更新文件共享中的帮助文件，然后使用这些文件来更新用户计算机上的帮助文件时， [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)和[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 的操作。

`Save-Help` cmdlet 将执行以下操作，以响应命令，以将模块的帮助文件保存在由**DestinationPath**参数指定的文件共享中。

1. `Save-Help` 从模块清单中的**HelpInfoURI**键的值指定的位置获取远程 HelpInfo XML 文件，并根据架构验证该文件。 （若要查看架构，请参阅[HELPINFO XML 架构](./helpinfo-xml-schema.md)。）然后 `Save-Help` 在 `Save-Help` 命令中的**DestinationPath**参数所指定的目录中查找本地 HelpInfo XML 文件。

2. `Save-Help` 比较模块的远程和本地 HelpInfo XML 文件中指定 UI 区域性的帮助文件的版本号。 如果远程文件上的版本号大于本地文件上的版本号，或者，如果**DestinationPath**目录中没有该模块的本地 HelpInfo XML 文件，`Save-Help` 准备下载新的帮助文件。

3. `Save-Help` 从远程 HelpInfo XML 文件中的**HelpContentUri**元素指定的位置选择模块的 CAB 文件。 它使用模块名称、模块 GUID 和 UI 区域性来标识 CAB 文件。

4. `Save-Help` 下载 CAB 文件并将其保存在**DestinationPath**目录中。 （它不创建任何特定于语言的子目录。）

5. `Save-Help` 通过复制 remote HelpInfo XML 文件来创建本地 HelpInfo XML 文件。 它编辑本地 HelpInfo XML 文件，使其仅包含它保存的 CAB 文件的元素。 然后，它将本地 HelpInfo XML 文件保存在**DestinationPath**目录中，并结束更新。

   `Update-Help` cmdlet 将执行以下操作，以响应一个命令，以便从**SourcePath**参数所指定的文件共享中的文件更新用户计算机上的帮助文件。

1. `Update-Help` 获取**SourcePath**目录中的远程 HelpInfo XML 文件。 然后，它将在用户计算机上的模块目录中查找本地 HelpInfo XML 文件。

2. `Update-Help` 比较模块的远程和本地 HelpInfo XML 文件中指定 UI 区域性的帮助文件的版本号。 如果远程文件上的版本号大于本地文件上的版本号，或者，如果没有本地 HelpInfo XML 文件，`Update-Help` 准备安装新的帮助文件。

3. `Update-Help` 从**SourcePath**目录中选择模块的 CAB 文件。 它使用模块名称、模块 GUID 和 UI 区域性来标识 CAB 文件。

4. `Update-Help` 解压缩 CAB 文件，验证帮助内容文件，并将帮助内容文件保存在用户计算机上的模块目录的特定于语言的子目录中。

5. `Update-Help` 通过复制 remote HelpInfo XML 文件来创建本地 HelpInfo XML 文件。 它编辑本地 HelpInfo XML 文件，使其仅包含它所安装的 CAB 文件的元素。 然后，它将本地 HelpInfo XML 文件保存到模块目录中并结束更新。
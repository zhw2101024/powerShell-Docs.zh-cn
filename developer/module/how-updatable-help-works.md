---
title: 可更新帮助的工作原理 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794376"
---
# <a name="how-updatable-help-works"></a>可更新帮助的工作原理

本主题说明如何可更新帮助的进程的 HelpInfo XML 文件和 CAB 文件对于每个模块，并安装更新的用户的帮助。

## <a name="the-update-help-process"></a>更新帮助进程

下面列出的操作[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 时的用户运行更新特定的 UI 区域性中的模块的帮助文件的命令。

1. `Update-Help` 从指定的值的位置获取远程 HelpInfo XML 文件**HelpInfoURI**密钥模块清单中，然后验证针对该架构文件。 (若要查看架构，请参阅[HelpInfo XML 架构](./helpinfo-xml-schema.md)。)然后`Update-Help`模块目录中的模块的用户的计算机上的本地 HelpInfo XML 文件。

2. `Update-Help` 将指定的 UI 区域性中的远程和本地的 HelpInfo XML 文件的模块的帮助文件的版本号进行比较。 如果对远程文件的版本号大于版本号上本地文件，或如果没有对于模块，无本地 HelpInfo XML 文件`Update-Help`正在准备下载新的帮助文件。

3. `Update-Help` 从指定的位置中选择该模块的 CAB 文件**HelpContentUri**远程 HelpInfo XML 文件中的元素。 它使用的模块名称、 GUID、 模块和 UI 区域性来标识该 CAB 文件。

4. `Update-Help` 下载的 CAB 文件，对其进行解压缩，验证帮助内容文件，并帮助内容将文件保存在模块目录的特定于语言的子目录中用户的计算机上。

5. `Update-Help` 通过复制远程 HelpInfo XML 文件来创建本地 HelpInfo XML 文件。 编辑本地 HelpInfo XML 文件，以便它包括仅用于安装该 CAB 文件的元素。 然后它会将本地 HelpInfo XML 文件保存在模块目录中，并结束更新。

## <a name="the-save-help-process"></a>保存帮助进程

下面列出的操作[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)并[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 时的用户运行命令以更新文件共享中的帮助文件，然后使用这些文件在更新的帮助文件用户的计算机。

`Save-Help` Cmdlet 执行以下操作以响应命令以将模块的帮助文件保存在指定的文件共享**DestinationPath**参数。

1. `Save-Help` 从指定的值的位置获取远程 HelpInfo XML 文件**HelpInfoURI**密钥模块清单中，然后验证针对该架构文件。 (若要查看架构，请参阅[HelpInfo XML 架构](./helpinfo-xml-schema.md)。)然后`Save-Help`会查找由指定的目录中的本地 HelpInfo XML 文件**DestinationPath**中的参数`Save-Help`命令。

2. `Save-Help` 将指定的 UI 区域性中的远程和本地的 HelpInfo XML 文件的模块的帮助文件的版本号进行比较。 如果对远程文件的版本号大于上的本地文件的版本号或没有任何本地 HelpInfo XML 文件中模块**DestinationPath**目录中，`Save-Help`正在准备下载新的帮助文件。

3. `Save-Help` 从指定的位置中选择该模块的 CAB 文件**HelpContentUri**远程 HelpInfo XML 文件中的元素。 它使用的模块名称、 GUID、 模块和 UI 区域性来标识该 CAB 文件。

4. `Save-Help` 下载的 CAB 文件，并将其保存在**DestinationPath**目录。 （它不会创建任何特定于语言的子目录）。

5. `Save-Help` 通过复制远程 HelpInfo XML 文件来创建本地 HelpInfo XML 文件。 编辑本地 HelpInfo XML 文件，以便它包括仅用于将其保存 CAB 文件的元素。 然后它将保存在本地的 HelpInfo XML 文件**DestinationPath**目录，并结束更新。

   `Update-Help` Cmdlet 执行以下操作以更新的文件中指定的文件共享的用户的计算机上的帮助文件的命令响应**SourcePath**参数。

1. `Update-Help` 获取远程 HelpInfo XML 文件从**SourcePath**目录。 然后它查找模块目录中用户的计算机上的本地 HelpInfo XML 文件。

2. `Update-Help` 将指定的 UI 区域性中的远程和本地的 HelpInfo XML 文件的模块的帮助文件的版本号进行比较。 如果对远程文件的版本号大于版本号上本地文件，或如果有任何本地 HelpInfo XML 文件，`Update-Help`正在准备安装新的帮助文件。

3. `Update-Help` 选择模块从 CAB 文件**SourcePath**目录。 它使用的模块名称、 GUID、 模块和 UI 区域性来标识该 CAB 文件。

4. `Update-Help` 解压缩 CAB 文件，验证帮助内容文件，并帮助内容将文件保存在模块目录的特定于语言的子目录中用户的计算机上。

5. `Update-Help` 通过复制远程 HelpInfo XML 文件来创建本地 HelpInfo XML 文件。 编辑本地 HelpInfo XML 文件，以便它包括仅用于安装该 CAB 文件的元素。 然后它会将本地 HelpInfo XML 文件保存在模块目录中，并结束更新。
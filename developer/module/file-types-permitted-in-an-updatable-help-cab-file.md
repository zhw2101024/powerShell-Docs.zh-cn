---
title: 文件类型允许在可更新帮助的 CAB 文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794240"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>可更新帮助 CAB 文件中允许的文件类型

本主题列出并描述了可更新帮助的 CAB 文件的内容要求。

## <a name="updatable-help-cab-file-requirements"></a>可更新帮助的 CAB 文件要求

默认情况下限制为 1 GB 是未压缩的 CAB 文件内容。 若要绕过此限制，用户必须使用**Force**的参数[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。

若要确保从 Internet 下载帮助文件的安全，可更新帮助的 CAB 文件可以包括下面列出的文件类型。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 可验证所有针对帮助主题架构文件。 如果`Update-Help`cmdlet 遇到无效或不允许的类型的文件，它不会安装无效的文件，并停止从用户的计算机上的 CAB 安装文件。

- Cmdlet 的基于 XML 的帮助主题。

- 脚本和函数的基于 XML 的帮助主题。

- Windows PowerShell 提供程序的基于 XML 的帮助主题。

- 基于文本的帮助主题，例如有关主题的信息。

[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)解压缩 CAB 时，会验证 CAB 内容。 如果`Update-Help`查找不符合标准的文件类型的可更新帮助的 CAB 文件中，它将生成一个终止错误并停止操作。 它不从 CAB，甚至那些符合文件类型安装任何帮助文件。
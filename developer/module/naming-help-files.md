---
title: 命名的帮助文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082169"
---
# <a name="naming-help-files"></a>命名帮助文件

本主题说明如何基于 XML 的帮助文件命名，以便[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 可以找到它。 为每个命令类型不同的名称要求。

## <a name="cmdlet-help-files"></a>Cmdlet 帮助文件

帮助文件的C#cmdlet 必须命名为程序集在其中定义该 cmdlet。 使用以下文件名称格式：

```
<AssemblyName>.dll-help.xml
```

程序集名称格式是必需的即使该程序集是嵌套的模块。

例如， [Get-winevent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Microsoft.PowerShell.Diagnostics.dll 程序集中定义 cmdlet。 `Get-Help` Cmdlet 查找帮助主题的`Get-WinEvent`cmdlet 仅在模块目录中的 Microsoft.PowerShell.Diagnostics.dll help.xml 文件中。

## <a name="provider-help-files"></a>提供程序的帮助文件

必须在其中定义该提供程序程序集命名为 Windows PowerShell 提供程序的帮助文件。 使用以下文件名称格式：

```
<AssemblyName>.dll-help.xml
```

程序集名称格式是必需的即使该程序集是嵌套的模块。

例如，Certificate 提供程序是 Microsoft.PowerShell.Security.dll 集中定义。 `Get-Help` Cmdlet 为证书提供程序仅在模块目录中的 Microsoft.PowerShell.Security.dll help.xml 文件中查找的帮助主题。

## <a name="function-help-files"></a>函数的帮助文件

函数可以通过使用所述[基于注释的帮助](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)或 XML 帮助文件中所述。 该函数时的 XML 文件中记录该函数必须具有`.ExternalHelp`注释将函数与 XML 文件相关联的关键字。 否则为`Get-Help`cmdlet 找不到帮助文件。

没有函数帮助文件的技术要求的名称。 但是，最佳做法是在其中定义该函数的脚本模块的帮助文件的名称。 例如，以下函数定义 MyModule.psm1 文件中。

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM 命令的帮助文件

必须在其中定义 CIM 命令的 CDXML 文件命名为 CIM 命令的帮助文件。 使用以下文件名称格式：

```
<FileName>.cdxml-help.xml
```

可以作为嵌套模块的模块中包含的 CDXML 文件中定义了 CIM 命令。 Windows PowerShell CIM 命令导入到会话中作为函数时，将添加`.ExternalHelp`注释将函数与 XML 帮助相关联的函数定义的关键字文件名为在其中定义 CIM 命令的 CDXML 文件。

## <a name="script-workflow-help-files"></a>脚本工作流的帮助文件

在模块中包含的脚本工作流可以在基于 XML 的帮助文件中所述。 没有帮助文件的技术要求的名称。 但是，最佳做法是在其中定义脚本工作流脚本模块的帮助文件的名称。 例如：

```
<ScriptModule>.psm1-help.xml
```

脚本工作流不需要与其他脚本化命令不同`.ExternalHelp`注释关键字来使其与帮助文件关联。 相反，Windows PowerShell 的基于 XML 的帮助文件的模块目录的 UI 区域性特定的子目录中搜索并查找有关的所有文件中的脚本工作流的帮助。 `.ExternalHelp` 将忽略注释关键字。

因为`.ExternalHelp`注释关键字将被忽略， `Get-Help` cmdlet 可以找到帮助为脚本工作流仅当它们包含在模块中。
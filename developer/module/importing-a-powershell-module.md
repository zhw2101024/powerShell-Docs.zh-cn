---
title: 正在导入 PowerShell 模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854053"
---
# <a name="importing-a-powershell-module"></a>导入 PowerShell 模块

一次在已安装模块的系统上，则将可能想要导入模块。 导入是将该模块加载到活动内存的进程，以便用户可以在其 PowerShell 会话中访问该模块。 在 PowerShell 2.0 中，你可以导入一个新安装 PowerShell 模块，通过调用[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet。 在 PowerShell 3.0 中，PowerShell 是能够隐式导入模块时由用户调用的函数或模块中的 cmdlet 之一。 请注意，这两个版本假定能够找到它; PowerShell 所在的位置中安装模块有关详细信息，请参阅[安装 PowerShell 模块](./installing-a-powershell-module.md)。 可以使用模块清单来限制导出您的模块中的哪些部分，并可以使用参数`Import-Module`调用来限制哪些部分是导入。

## <a name="importing-a-snap-in-powershell-10"></a>导入一个单元 (PowerShell 1.0)

PowerShell 1.0 中不存在的模块： 因此，必须进行注册和使用管理单元。但是，建议不要在此情况下，使用此技术通常更轻松地安装并导入模块一样。 有关详细信息，请参阅[如何创建一个 Windows PowerShell 管理单元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)。

## <a name="importing-a-module-with-import-module-powershell-20"></a>导入的模块导入模块 (PowerShell 2.0)

PowerShell 2.0 使用适当地命名[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet 导入的模块。 运行此 cmdlet 时，Windows PowerShell 中搜索指定的目录中的指定模块`PSModulePath`变量。 找到指定的目录后，Windows PowerShell 中搜索文件按以下顺序： 模块清单文件 (.psd1)、 脚本模块文件 (.psm1) 二进制模块文件 (.dll)。 有关将目录添加到搜索的详细信息，请参阅[修改 PSModulePath 安装路径](./modifying-the-psmodulepath-installation-path.md)。 以下代码介绍了如何导入模块：

```powershell
Import-Module myModule
```

假设位于 myModule `PSModulePath`，PowerShell 会将 myModule 加载到活动内存。 如果不位于 myModule`PSModulePath`路径，您可以仍显式告知 PowerShell 在哪里可以找到它：

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

此外可以使用-verbose 参数来标识出该模块，要导出的内容和内容要导入到活动内存中。 导出和导入限制向用户公开的内容： 的区别是谁在控制可见性。 实质上是，导出模块中的代码由控制。 导入受与此相反，`Import-Module`调用。 有关详细信息，请参阅**限制成员已导入的**下文。

## <a name="implicitly-importing-a-module-powershell-30"></a>隐式导入模块 (PowerShell 3.0)

从 Windows PowerShell 3.0 开始，模块会自动导入命令中使用的任何 cmdlet 或模块中的函数时。 此功能适用于此的值中包含的目录中的任何模块**PSModulePath**环境变量。 如果不保存你的模块上的有效路径但是，您可以仍将它们加载使用显式[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)前面介绍的选项。

以下操作触发自动导入模块，也称为"模块自动加载。"

- 在命令中使用 cmdlet。 例如，如果键入`Get-ExecutionPolicy`将包含的 Microsoft.PowerShell.Security 模块导入`Get-ExecutionPolicy`cmdlet。

- 使用[Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 来获取命令。  例如，如果键入`Get-Command Get-JobTrigger`导入**PSScheduledJob**包含模块`Get-JobTrigger`cmdlet。 一个`Get-Command`包含通配符的命令被视为可发现并不会触发导入的模块。

- 使用[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 来获取有关 cmdlet 的帮助。 例如，如果键入`Get-Help Get-WinEvent`导入包含 Microsoft.PowerShell.Diagnostics 模块`Get-WinEvent`cmdlet。

若要支持自动导入模块， `Get-Command` cmdlet 获取所有 cmdlet 和函数中所有已安装的模块，即使该模块未导入会话。 有关详细信息，请参阅帮助主题[Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet。

## <a name="the-importing-process"></a>导入进程

导入模块时，为该模块，请创建一个新的会话状态和一个[System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)在内存中创建对象。 为导入的每个模块创建会话状态 （包括根模块和任何嵌套的模块）。 从根模块，其中包括被导出到的任何嵌套模块的根模块的任何成员导出的成员然后导入到调用方的会话状态。

从模块导出的成员的元数据具有模块名称属性。 导出它们的模块的名称填充此属性。

> [!WARNING]
> 如果导出的成员的名称使用未经批准的谓词或如果该成员的名称使用受限的字符，则会显示警告时[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)运行 cmdlet。

默认情况下[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet 不返回到管道的任何对象。 但是，该 cmdlet 支持`PassThru`可以用于返回参数[System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)导入的每个模块的对象。 若要将输出发送到主机，用户应运行[Write-host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet。

## <a name="restricting--the-members-that-are-imported"></a>限制导入的成员

通过使用导入模块时[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet，默认情况下，所有导出的模块成员导入到会话，包括任何命令导出到由嵌套模块的模块。 默认情况下，不导出变量和别名。 若要限制导出的成员，请使用[模块清单](./how-to-write-a-powershell-module-manifest.md)。 若要限制将导入的成员，请使用以下参数的`Import-Module`cmdlet。

- `Function`：此参数将限制导出的函数。 （如果使用的模块清单，请参阅 FunctionsToExport 密钥。）

- `Cmdlet`：此参数将限制 （如果你使用模块清单，请参阅 CmdletsToExport 密钥。） 导出的 cmdlet

- `Variable`：此参数将限制 （如果你使用模块清单，请参阅 VariablesToExport 密钥。） 导出的变量

- `Alias`：此参数将限制 （如果你使用模块清单，请参阅 AliasesToExport 密钥。） 导出的别名

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

---
title: 导入 PowerShell 模块 |Microsoft Docs
ms.custom: ''
ms.date: 02/03/2020
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: d5ce61a1cba1d91c130394c5cf7249021e95f485
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996015"
---
# <a name="importing-a-powershell-module"></a>导入 PowerShell 模块

将模块安装到系统后，可能需要导入模块。 导入是将模块加载到活动内存中，使用户可以在其 PowerShell 会话中访问该模块的过程。 在 PowerShell 2.0 中，可以通过调用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 来导入新安装的 PowerShell 模块。 在 PowerShell 3.0 中，当用户调用模块中的一个函数或 cmdlet 时，PowerShell 能够隐式导入模块。 请注意，这两个版本都假设您将模块安装在 PowerShell 能够找到它的位置;有关详细信息，请参阅[安装 PowerShell 模块](./installing-a-powershell-module.md)。
您可以使用模块清单来限制导出模块的哪些部分，并且可以使用 `Import-Module` 调用的参数来限制导入的部件。

## <a name="importing-a-snap-in-powershell-10"></a>导入管理单元（PowerShell 1.0）

PowerShell 1.0 中不存在模块：相反，你必须注册并使用管理单元。但建议您不要在此时使用这种技术，因为模块通常更易于安装和导入。 有关详细信息，请参阅[如何创建 Windows PowerShell 管理单元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)。

## <a name="importing-a-module-with-import-module-powershell-20"></a>使用 Import-module 导入模块（PowerShell 2.0）

PowerShell 2.0 使用适当命名的[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 导入模块。 运行此 cmdlet 时，Windows PowerShell 会在 `PSModulePath` 变量中指定的目录中搜索指定的模块。 找到指定的目录后，Windows PowerShell 将按以下顺序搜索文件：模块清单文件（. psd1）、脚本模块文件（hbase-runner.psm1）、二进制模块文件（.dll）。 有关向搜索添加目录的详细信息，请参阅[修改 PSModulePath 安装路径](./modifying-the-psmodulepath-installation-path.md)。
下面的代码说明如何导入模块：

```powershell
Import-Module myModule
```

假设 myModule 位于 `PSModulePath`中，则 PowerShell 会将 myModule 加载到活动内存。 如果 myModule 不在 `PSModulePath` 路径上，你仍可以显式告知 PowerShell 在何处找到它：

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

你还可以使用 `-Verbose` 参数确定要从模块中导出的内容以及要导入到活动内存中的内容。 导出和导入会限制向用户公开的内容：区别在于控制可见性。 实质上，导出由模块内的代码控制。 与此相反，导入由 `Import-Module` 调用控制。 有关详细信息，请参阅下面的**限制导入的成员**。

## <a name="implicitly-importing-a-module-powershell-30"></a>隐式导入模块（PowerShell 3.0）

从 Windows PowerShell 3.0 开始，在命令中使用模块的任意 cmdlet 或函数时会自动导入该模块。 此功能适用于目录中的任何模块，这些模块包含在**PSModulePath**环境变量的值中。 但是，如果您不将模块保存在有效路径上，则仍可以使用上面所述的显式[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)选项加载它们。

以下操作触发自动导入模块，也称为 "模块自动加载"。

- 在命令中使用 cmdlet。 例如，键入 `Get-ExecutionPolicy` 导入包含 `Get-ExecutionPolicy` cmdlet 的 Microsoft. Security 模块。

- 使用[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 获取命令。 例如，键入 `Get-Command Get-JobTrigger` 导入包含 `Get-JobTrigger` cmdlet 的**PSScheduledJob**模块。 包含通配符的 `Get-Command` 命令被视为发现，不会触发模块的导入。

- 使用[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 获取有关 cmdlet 的帮助。 例如，键入 `Get-Help Get-WinEvent` 导入包含 `Get-WinEvent` cmdlet 的 "诊断" 模块。

为了支持模块的自动导入，`Get-Command` cmdlet 获取所有已安装模块中的所有 cmdlet 和函数，即使模块未导入到会话中也是如此。 有关详细信息，请参阅[Get Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 的帮助主题。

## <a name="the-importing-process"></a>导入过程

在导入模块时，将为该模块创建一个新的会话状态，并在内存中创建一个[PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)对象。 为导入的每个模块创建一个会话状态（这包括根模块和任何嵌套的模块）。 然后，将从根模块导出的成员（包括任何嵌套模块导出到根模块的所有成员）导入到调用方的会话状态中。

从模块导出的成员的元数据具有 ModuleName 属性。 此属性由导出的模块的名称填充。

> [!WARNING]
> 如果导出成员的名称使用未经批准的谓词，或如果该成员的名称使用受限字符，则在运行[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 时，将显示一条警告。

默认情况下， [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 不会将任何对象返回到管道。 但是，该 cmdlet 支持**PassThru**参数，该参数可用于为导入的每个模块返回[PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)对象。 若要将输出发送到主机，用户应运行[写入主机](/powershell/module/Microsoft.PowerShell.Utility/Write-Host)cmdlet。

## <a name="restricting--the-members-that-are-imported"></a>限制导入的成员

当使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 导入模块时，默认情况下，所有导出的模块成员都将导入到会话中，包括通过嵌套模块导出到该模块中的任何命令。 默认情况下，不导出变量和别名。 若要限制导出的成员，请使用[模块清单](./how-to-write-a-powershell-module-manifest.md)。
若要限制导入的成员，请使用 `Import-Module` cmdlet 的以下参数。

- **函数**：此参数限制导出的函数。 （如果使用的是模块清单，请参阅 FunctionsToExport 键。）

- `**Cmdlet**：此参数限制导出的 Cmdlet （如果你使用的是模块清单，请参阅 CmdletsToExport 键。）

- **变量**：此参数限制导出的变量（如果使用的是模块清单，请参阅 VariablesToExport 键。）

- **Alias**：此参数限制导出的别名（如果使用的是模块清单，请参阅 AliasesToExport 键。）

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

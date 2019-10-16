---
title: 加载和导出格式设置数据 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365116"
---
# <a name="loading-and-exporting-formatting-data"></a>加载和导出格式设置数据

创建格式化文件后，需要通过将文件加载到当前会话中来更新会话的格式数据。 （Windows PowerShell 提供的格式化文件由在打开当前会话时注册的管理单元加载。）当前会话的格式数据更新后，Windows PowerShell 将使用该数据显示与已加载的格式设置文件中定义的视图关联的 .NET 对象。 可以加载到当前会话中的格式化文件数没有限制。 除了更新格式设置数据以外，还可以将当前会话中的格式数据导出回格式设置文件。

## <a name="loading-format-data"></a>正在加载格式数据

可以使用以下方法将格式化文件加载到当前会话中：

- 你可以从命令行将格式设置文件导入到当前会话中。 按照以下过程中所述，使用[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet。

- 你可以创建一个引用你的格式化文件的模块清单。 模块允许您打包格式化文件以进行分发。 使用[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 创建清单，并使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 将模块加载到当前会话中。 有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

- 你可以创建一个引用你的格式化文件的管理单元。 使用[add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn.Formats)可引用您的格式设置文件。 强烈建议使用模块打包 cmdlet 以及任何关联的格式和类型文件以进行分发。 有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

- 如果以编程方式调用命令，则可以将格式设置文件条目添加到运行命令的运行空间的初始会话状态。 有关用于添加格式化文件的 .NET 类型的详细信息，请参阅[Sessionstateformatentry？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry)类。

加载格式设置文件时，会将其添加到 Windows PowerShell 用来确定在命令行显示对象时使用的视图的内部列表。 您可以在列表开头添加格式文件，也可以将其追加到列表的末尾。 如果正在加载为定义了现有视图的对象定义视图（例如，当你想要更改 Windows PowerShell core cmdlet 返回的对象的方式）时，了解将格式设置文件添加到此列表中的位置非常重要。 会. 如果正在加载的格式设置文件定义对象的唯一视图，则可以使用前面所述的任何方法。  如果要加载的格式设置文件定义了对象的其他视图，则必须使用[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，并将文件预置到列表的开头。

## <a name="storing-your-formatting-file"></a>存储格式设置文件

不要求在磁盘上存储格式设置文件。 但是，强烈建议将它们存储在以下文件夹中： `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>使用 Update-formatdata 加载格式化文件

1. 将格式化文件存储到磁盘。

2. 使用以下命令之一运行[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet。

   若要在列表的前面添加格式文件，请使用此命令。 如果要更改对象的显示方式，请使用此命令。

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   若要在列表的末尾添加格式文件，请使用此命令。

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   使用[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 添加文件后，当会话处于打开状态时，不能从列表中删除该文件。 要从列表中删除格式化文件，必须关闭会话。

## <a name="exporting-format-data"></a>导出格式数据

在此处插入分区正文。

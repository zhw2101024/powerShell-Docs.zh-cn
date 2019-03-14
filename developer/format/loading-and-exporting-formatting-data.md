---
title: 加载和导出数据的格式设置 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 86a0e8b7e8967280daa57faf5c323efcd3b1368b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794189"
---
# <a name="loading-and-exporting-formatting-data"></a>加载和导出格式设置数据

创建格式设置文件后，需要更新通过将文件加载到当前会话的会话的格式数据。 （由 Windows PowerShell 提供的格式设置文件加载的管理单元打开当前会话时注册。）一旦更新当前会话的格式数据，Windows PowerShell 将使用此数据来显示与加载的格式设置文件中定义的视图相关联的.NET 对象。 可以加载到当前会话的格式设置文件的数量没有限制。 除了更新的格式设置数据，可以返回到格式设置文件在当前会话中导出的格式数据。

## <a name="loading-format-data"></a>加载数据的格式

可以将格式设置文件加载到当前会话使用以下方法：

- 您可以导入当前会话从命令行的格式设置文件。 使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，如以下过程中所述。

- 可以创建引用格式设置文件的模块清单。 模块，可打包你设置用于发布的文件的格式。 使用[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 来创建清单，并[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet 将模块加载到当前会话。 有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

- 您可以创建一个单元引用格式设置文件。 使用[System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats)引用格式设置文件。 强烈建议使用包 cmdlet 的模块和任何关联的格式设置和类型的文件来分发它。 有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

- 如果以编程方式调用命令时，您可以将格式设置文件条目添加到其中运行的命令的初始会话状态的运行空间。 若要添加的格式设置文件所使用的.NET 类型的详细信息，请参阅[System.Management.Automation.Runspaces.Sessionstateformatentry？Displayproperty =](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry)类。

加载格式设置文件时，它被添加到内部列表用于确定哪个视图对象显示在命令行时要使用 Windows PowerShell。 可以在前面添加到列表中，开始在格式设置文件或可将其追加到列表的末尾。 了解此处格式设置文件添加到此列表很重要，如果要加载格式设置文件，用于定义具有现有视图定义的例如当你想要更改 Windows PowerShell 核心 cmdlet 返回的对象时的方式的对象的视图 显示。 如果你加载的格式设置文件，用于定义对象的唯一视图，可以使用任何以前所述的方法。  如果你加载的格式设置文件，用于定义对象的另一个视图，则必须使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 并预先考虑您的文件列表的开头。

## <a name="storing-your-formatting-file"></a>将格式设置文件存储

没有任何要求的格式设置文件在磁盘上的存储位置。 但是，强烈建议您将其存储在以下文件夹中： `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>正在加载使用导入 FormatData 使用格式化文件

1. 将存储到磁盘在格式设置文件。

2. 运行[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 使用以下命令之一。

   若要添加将格式设置文件列表的开头，请使用此命令。 如果要更改对象的显示方式，请使用此命令。

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   若要添加将格式设置文件列表的末尾使用此命令。

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   已添加文件使用后[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，你不能将文件从列表中删除该会话处于打开状态时。 您必须关闭会话后，若要从列表中删除的格式设置文件。

## <a name="exporting-format-data"></a>导出格式数据

在此处插入分区正文。

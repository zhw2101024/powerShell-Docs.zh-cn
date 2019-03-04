---
title: 了解 Windows PowerShell 模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862733"
---
# <a name="understanding-a-windows-powershell-module"></a>了解 Windows PowerShell 模块

一个*模块*是一组相关的 Windows PowerShell 功能，作为方便单元 （通常保存在单个目录中） 组合在一起。 通过为模块中定义一系列相关的脚本文件、 程序集，以及相关的资源，可以引用、 加载、 保存和共享代码更容易，否则会比。

模块的主要用途是允许 Windows PowerShell 代码模块化 （ie、 重用和抽象）。 例如，创建一个模块的最基本的方法是只需将 Windows PowerShell 脚本保存为.psm1 文件。 这样做因此允许你控制 （即，使公共或专用） 的函数和脚本中包含的变量。 将脚本另存为.psm1 文件还允许您控制特定变量的作用域。 最后，您还可以使用 cmdlet 如[Install-module](/powershell/module/PowershellGet/Install-Module)组织，请安装并使用您的脚本作为构建基块更大的解决方案。

## <a name="module-components-and-types"></a>模块组件和类型

模块是由四个基本组件构成：

1. 某些排序的代码文件-通常一个 PowerShell 脚本或托管的 cmdlet 的程序集。

2. 其他任何更高版本的代码文件可能需要例如其他程序集，帮助文件或脚本。

3. 清单文件，描述了上述文件，以及将存储元数据，例如作者和版本控制信息...

4. 一个目录，其中包含所有上述内容，它位于 PowerShell 可以合理地找到的位置。

   请注意，没有任何这些组件，通过本身，实际上有必要。 例如，模块可以从技术上讲是仅为.psm1 文件中存储的脚本。 您还可以只是主要用于组织得更好的清单文件的模块。 此外可以编写一个脚本来动态创建一个模块，并因此实际上无需用于存储中的任何内容的目录。 以下部分介绍可以通过混合和匹配的模块的不同可能部分一起获取的模块的类型。

### <a name="script-modules"></a>脚本模块

正如其名字*脚本模块*是包含任何有效的 Windows PowerShell 代码的文件 (.psm1)。 脚本开发人员和管理员可以使用这种类型的模块创建模块的成员包括函数、 变量和的详细信息。 核心，脚本模块都是只需具有不同的扩展，它允许管理员在其上使用导入、 导出和管理功能的 Windows PowerShell 脚本。

此外，可以使用清单文件以包含在模块中，例如数据文件、 其他依赖模块或运行时脚本的其他资源。 清单文件，还有用于跟踪元数据，例如创作和版本控制信息。

最后，需要保存在文件夹中，可以合理地发现 PowerShell 脚本模块，例如不动态创建的任何其他模块。 通常，这是 PowerShell 模块路径;但如有必要可明确描述你的模块的安装位置。 有关详细信息，请参阅[如何编写 PowerShell 脚本模块](./how-to-write-a-powershell-script-module.md)。

### <a name="binary-modules"></a>二进制模块

一个*二进制模块*是.NET Framework 程序集 (.dll)，包含已编译的代码，如C#。 Cmdlet 开发人员可以使用这种类型的模块共享 cmdlet、 提供程序，和的详细信息。 （现有的管理单元还可作为二进制模块。）与脚本模块相比，二进制模块，可创建速度更快或使用功能的 cmdlet (如多线程处理) 不是向 Windows PowerShell 脚本中的代码一样简单。

作为使用脚本模块可以包含一个清单文件来描述其他资源的模块使用，并跟踪你的模块有关的元数据。 同样，您可能应安装二进制模块在 PowerShell 模块路径上的某个位置的文件夹中。 有关详细信息，请参阅如何[如何编写 PowerShell 二进制模块](./how-to-write-a-powershell-binary-module.md)。

### <a name="manifest-modules"></a>清单模块

一个*清单模块*是一个模块，使用清单文件来描述的所有组件，但不具有任何类型的核心程序集或脚本。 (正式情况下，清单模块离开`ModuleToProcess`或`RootModule`清单空元素。)但是，仍可以使用模块，例如加载依赖程序集或自动运行某些预处理脚本的功能的其他功能。 此外可以方便地打包将使用其他模块，如嵌套的模块、 程序集、 类型或格式的资源作为使用清单模块。 有关详细信息，请参阅[如何编写 PowerShell 模块清单](./how-to-write-a-powershell-module-manifest.md)。

### <a name="dynamic-modules"></a>动态模块

一个*动态模块*是模块未加载，或保存到文件。 相反，它们动态创建的脚本，请使用[New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet。 这种类型的模块使脚本能够按需，不需要加载或保存到持久性存储区中创建一个模块。 按其性质，动态模块用于是短暂性的并因此不能访问通过`Get-Module`cmdlet。 同样，他们通常不需要模块清单，也无可能需永久文件夹来存储其相关的程序集。

## <a name="module-manifests"></a>模块清单

一个*模块清单*是一个包含哈希表的.psd1 文件。 密钥和哈希表中的值执行以下操作：

- 介绍的内容和模块的属性。

- 定义的先决条件。

- 确定如何处理组件。

  模块并不一定需要清单。 模块可以引用脚本文件 (.ps1)、 脚本模块文件 (.psm1) 清单文件 (.psd1)，格式设置和键入文件 (.ps1xml)、 cmdlet 和提供程序程序集 (.dll)、 资源文件、 帮助文件、 本地化文件或任何其他类型的文件或资源，均打包为模块的一部分。 对于脚本国际化，模块文件夹还包含一组消息目录文件。 如果将清单文件添加到模块文件夹中，则可以通过引用清单作为单一单元引用多个文件。

  清单本身描述了以下类别的信息：

- 有关该模块，如的模块的版本编号、 作者和说明的元数据。

- 若要导入模块，例如 Windows PowerShell 版本，公共语言运行时 (CLR) 版本，以及所需的模块所需的先决条件。

- 处理指令，如脚本、 格式和类型来处理。

- 限制对成员的模块导出，如别名、 函数、 变量和用于导出的 cmdlet。

  有关详细信息，请参阅[如何编写 PowerShell 模块清单](./how-to-write-a-powershell-module-manifest.md)。

## <a name="storing-and-installing-a-module"></a>存储和安装的模块

创建脚本、 二进制或清单模块后，您可以保存您的工作在一个位置中其他人可以访问它。 例如，你的模块可以存储在其中安装 Windows PowerShell，或它可以存储在用户文件夹中的系统文件夹。

通常情况下，您可以确定你应通过使用其中一个路径存储在安装模块`$ENV:PSModulePath`变量。 使用以下方式之一意味着 PowerShell 会自动查找和加载你的模块，当用户在其代码中对它的调用。 如果存储您的模块中其他位置，可以显式让 PowerShell 调用时，通过你的模块的位置作为参数传入知道`Install-Module`。

无论如何，文件夹的路径被称为*基*模块 (ModuleBase) 和脚本的名称，二进制或清单模块文件应为相同模块文件夹的名称，但存在以下例外：

- 通过创建的动态模块`New-Module`可以使用名为 cmdlet `Name` cmdlet 参数。

- 从程序集对象的导入的模块**`Import-Module`的程序集**命令将名为根据以下语法： `"dynamic_code_module_" + assembly.GetName()`。

  有关详细信息，请参阅[安装 PowerShell 模块](./installing-a-powershell-module.md)并[修改 PSModulePath 安装路径](./modifying-the-psmodulepath-installation-path.md)。

## <a name="module-cmdlets-and-variables"></a>模块 Cmdlet 和变量

以下 cmdlet 和变量提供的 Windows PowerShell 用于创建和管理的模块。

[新模块](/powershell/module/Microsoft.PowerShell.Core/New-Module)cmdlet 此 cmdlet 将创建仅在内存中存在的新动态模块。 从脚本块中，创建此模块，其导出的成员，例如，其函数和变量，同时在会话中立即可用并在会话关闭前仍可。

[新 ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 此 cmdlet 创建一个新的模块清单 (.psd1) 文件，将填充它的值，而将清单文件保存到指定的路径。 此 cmdlet 还可用于创建一个模块清单模板，可以手动填写。

[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet 此 cmdlet 将一个或多个模块添加到当前会话。

[获取模块](/powershell/module/Microsoft.PowerShell.Core/Get-Module)cmdlet 此 cmdlet 检索已或可导入当前会话的模块有关的信息。

[导出 ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet 将此 cmdlet 指定从脚本模块 (.psm1) 文件或通过使用创建的动态模块导出的模块成员 （如 cmdlet、 函数、 变量和别名） `New-Module` cmdlet。

[删除模块](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)cmdlet 此 cmdlet 将从当前会话中删除模块。

[测试 ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet，此 cmdlet 验证是否在模块清单准确地通过验证模块清单文件 (.psd1) 中列出的文件实际存在于指定的路径来描述模块的组件。

$PSScriptRoot 此变量包含从其执行脚本模块的目录。 这样，脚本使用的模块路径来访问其他资源。

$env: PSModulePath 此环境变量包含在 Windows PowerShell 存储模块的目录的列表。 Windows PowerShell 使用自动导入模块和更新的模块的帮助主题时此变量的值。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

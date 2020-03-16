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
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "79407150"
---
# <a name="understanding-a-windows-powershell-module"></a>了解 Windows PowerShell 模块

*模块*是一组相关的 Windows PowerShell 功能，作为一个方便的单元组合在一起（通常保存在单个目录中）。 通过将一组相关的脚本文件、程序集和相关资源定义为模块，你可以像使用其他方法一样，引用、加载、保存和共享你的代码。

模块的主要用途是允许 Windows PowerShell 代码的模块化（即，重用和抽象）。 例如，创建模块的最基本方法是将 Windows PowerShell 脚本保存为 hbase-runner.psm1 文件。 这样，便可以控制（即公共或私有）脚本中包含的函数和变量。 将脚本另存为 hbase-runner.psm1 文件还可以控制某些变量的作用域。 最后，还可以使用 cmdlet （如[安装模块](/powershell/module/PowershellGet/Install-Module)）来组织、安装和使用你的脚本作为大型解决方案的构建基块。

## <a name="module-components-and-types"></a>模块组件和类型

模块由四个基本组件组成：

1. 某些类型的代码文件，通常是 PowerShell 脚本或托管 cmdlet 程序集。

2. 以上代码文件可能需要的任何其他内容，如其他程序集、帮助文件或脚本。

3. 描述上述文件以及存储作者和版本信息等元数据的清单文件。

4. 一个目录，其中包含上述所有内容，并且位于 PowerShell 可合理查找的位置。

   请注意，这些组件本身并不是必需的。 例如，从技术上讲，模块只能是存储在 hbase-runner.psm1 文件中的脚本。 你还可以有一个模块，该模块只是用于组织用途的清单文件。 您还可以编写一个动态创建模块的脚本，因此，实际上不需要使用目录来存储任何内容。 以下各节介绍了可通过混合并匹配模块的不同可能部分来获得的模块类型。

### <a name="script-modules"></a>脚本模块

顾名思义，*脚本模块*是包含任何有效 Windows PowerShell 代码的文件（. hbase-runner.psm1）。 脚本开发人员和管理员可以使用这种类型的模块来创建其成员包括函数、变量等的模块。 就说，脚本模块只是一个具有不同扩展的 Windows PowerShell 脚本，它允许管理员对它使用导入、导出和管理功能。

此外，您还可以使用清单文件来包含模块中的其他资源，如数据文件、其他相关模块或运行时脚本。 清单文件也可用于跟踪元数据，例如创作和版本信息。

最后，与任何其他不是动态创建的模块一样，都需要将脚本模块保存在 PowerShell 可合理发现的文件夹中。 通常，这是在 PowerShell 模块路径上;但如有必要，您可以显式描述模块的安装位置。 有关详细信息，请参阅[如何编写 PowerShell 脚本模块](./how-to-write-a-powershell-script-module.md)。

### <a name="binary-modules"></a>二进制模块

*二进制模块*是包含编译的代码（如）的 .NET Framework 程序集（.dll） C#。 Cmdlet 开发人员可以使用此类型的模块来共享 cmdlet、提供程序等。 （现有管理单元也可以用作二进制模块。）与脚本模块相比，二进制模块可让你创建更快或更使用功能（例如多线程）的 cmdlet，这些 cmdlet 不像在 Windows PowerShell 脚本中编写代码那么简单。

与脚本模块一样，你可以包含一个清单文件来描述模块使用的其他资源，并跟踪有关模块的元数据。 同样，您可能应该将您的二进制模块安装在 PowerShell 模块路径中某个位置的某个文件夹中。 有关详细信息，请参阅如何[编写 PowerShell 二进制模块](./how-to-write-a-powershell-binary-module.md)。

### <a name="manifest-modules"></a>清单模块

*清单模块*是一个模块，它使用清单文件来描述其所有组件，但不包含任何种类的核心程序集或脚本。 （正式，清单模块会将清单的 `ModuleToProcess` 或 `RootModule` 元素留空。）但是，您仍然可以使用模块的其他功能，例如加载依赖程序集或自动运行某些预处理脚本的能力。 你还可以使用清单模块来打包其他模块将使用的资源，例如嵌套的模块、程序集、类型或格式。 有关详细信息，请参阅[如何编写 PowerShell 模块清单](./how-to-write-a-powershell-module-manifest.md)。

### <a name="dynamic-modules"></a>动态模块

*动态模块*是指不是从文件加载或保存到文件的模块。 相反，它们是使用[新的模块](/powershell/module/Microsoft.PowerShell.Core/New-Module)cmdlet 通过脚本动态创建的。 此类型的模块使脚本能够创建无需加载或保存到持久性存储中的需要的模块。 就其本质而言，动态模块旨在缩短生存期，因此 `Get-Module` cmdlet 无法访问。 同样，它们通常不需要模块清单，也不可能需要永久文件夹来存储其相关程序集。

## <a name="module-manifests"></a>模块清单

*模块清单*是包含哈希表的 psd1 文件。 哈希表中的键和值执行以下操作：

- 描述模块的内容和属性。

- 定义必备组件。

- 确定如何处理组件。

  模块并不一定需要清单。 模块可以引用脚本文件（ps1）、脚本模块文件（hbase-runner.psm1）、清单文件（psd1）、格式设置和类型文件（types.ps1xml）、cmdlet 和提供程序程序集（.dll）、资源文件、帮助文件、本地化文件或任何其他类型的文件或资源，捆绑为模块的一部分。 对于国际化脚本，module 文件夹还包含一组消息目录文件。 如果将清单文件添加到 module 文件夹，则可以通过引用清单，将多个文件作为一个单元来引用。

  清单本身描述了以下类别的信息：

- 有关模块的元数据，如模块版本号、作者和说明。

- 导入模块所需的先决条件，如 Windows PowerShell 版本、公共语言运行时（CLR）版本和所需的模块。

- 处理指令，如要处理的脚本、格式和类型。

- 对要导出的模块成员的限制，例如要导出的别名、函数、变量和 cmdlet。

  有关详细信息，请参阅[如何编写 PowerShell 模块清单](./how-to-write-a-powershell-module-manifest.md)。

## <a name="storing-and-installing-a-module"></a>存储和安装模块

一旦创建了脚本、二进制或清单模块，就可以将工作保存到其他人可以访问的位置。 例如，模块可以存储在安装了 Windows PowerShell 的系统文件夹中，也可以存储在用户文件夹中。

一般而言，你可以通过使用 `$ENV:PSModulePath` 变量中存储的路径之一确定你应该安装模块的位置。 使用其中一种路径意味着，当用户在代码中调用模块时，PowerShell 可以自动查找并加载模块。 如果将模块存储在其他位置，则在调用 `Install-Module`时，可以通过将模块的位置作为参数传入来显式让 PowerShell 知道。

无论如何，文件夹的路径称为模块（ModuleBase）的*基*项，脚本、二进制或清单模块文件的名称应与模块文件夹名称相同，但以下情况例外：

- 可以使用 cmdlet 的 `Name` 参数来命名 `New-Module` cmdlet 创建的动态模块。

- **`Import-Module` 程序集**命令从程序集对象导入的模块按照以下语法命名： `"dynamic_code_module_" + assembly.GetName()`。

  有关详细信息，请参阅[安装 PowerShell 模块](./installing-a-powershell-module.md)和[修改 PSModulePath 安装路径](./modifying-the-psmodulepath-installation-path.md)。

## <a name="module-cmdlets-and-variables"></a>模块 Cmdlet 和变量

Windows PowerShell 提供以下 cmdlet 和变量来创建和管理模块。

[新的模块](/powershell/module/Microsoft.PowerShell.Core/New-Module)cmdlet 此 cmdlet 将创建一个仅存在于内存中的新动态模块。 模块是从脚本块创建的，它的导出成员（如其函数和变量）在会话中立即可用并保持可用状态，直到会话关闭。

[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 此 cmdlet 创建新的模块清单（. psd1）文件，填充其值，并将清单文件保存到指定的路径。 此 cmdlet 还可用于创建可以手动填充的模块清单模板。

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 此 cmdlet 将一个或多个模块添加到当前会话中。

[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 此 cmdlet 检索有关已在或可以导入到当前会话中的模块的信息。

[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet 此 cmdlet 指定从脚本模块（hbase-runner.psm1）文件或使用 `New-Module` cmdlet 创建的动态模块导出的模块成员（如 cmdlet、函数、变量和别名）。

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet 此 cmdlet 将从当前会话中删除模块。

[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet 此 cmdlet 通过验证模块清单文件（. psd1）中列出的文件是否确实存在于指定的路径中来验证模块清单是否准确描述了模块的组件。

$PSScriptRoot 此变量包含执行脚本模块所用的目录。 它使脚本能够使用模块路径来访问其他资源。

$env:P SModulePath 此环境变量包含存储 Windows PowerShell 模块的目录的列表。 当自动导入模块时，Windows PowerShell 将使用此变量的值，并更新模块的帮助主题。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

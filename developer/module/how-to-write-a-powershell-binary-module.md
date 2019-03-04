---
title: 如何编写 PowerShell 二进制模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856483"
---
# <a name="how-to-write-a-powershell-binary-module"></a>如何编写 PowerShell 二进制模块

二进制模块可以包含 cmdlet 类任何程序集 (.dll)。 默认情况下，导入二进制模块导入的程序集中的所有 cmdlet。 但是，可以限制会通过创建一个其根模块是程序集的模块清单导入的 cmdlet。 （例如，在清单的 CmdletsToExport 密钥可以用于导出所需的 cmdlet。）此外，二进制模块可以包含其他文件、 目录结构和其他许多有用的管理信息单个 cmdlet 不能。

以下过程介绍如何创建和安装 PowerShell 二进制模块。

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>如何创建和安装 PowerShell 二进制模块

1. 创建一个二进制 PowerShell 解决方案 (如编写的 cmdlet C#)，使用的功能所需，并且确保其正常运行。

   从代码角度看，二进制模块的核心是只需一个 cmdlet 的程序集。 事实上，PowerShell 会将单个 cmdlet 程序集视为一个模块中，根据加载和卸载，开发人员来说没有额外操作。 有关编写 cmdlet 的详细信息，请参阅[编写 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

2. 如有必要，创建解决方案的其余部分: （更多的 cmdlet、 XML 文件等） 并使用模块清单中描述它们。

   除了介绍你的解决方案中的 cmdlet 程序集，模块清单可以描述要如何导出和导入模块、 将公开哪些 cmdlet，和内容的其他文件将进入该模块。 如前面所述但是，PowerShell，可以将任何额外操作模块之类的二进制 cmdlet。 在这种情况下，模块清单是主要用于将多个文件组合成单个包中，或显式控制给定程序集发布有用的。 有关详细信息，请参阅[如何编写 PowerShell 模块清单](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。

   下面的代码是非常简单C#包含三个 cmdlet 可以用作模块在同一文件中的代码块。

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. 打包你的解决方案，并将包保存到某个位置中的 PowerShell 模块路径。

   `PSModulePath`全局环境变量描述将使用 PowerShell 来查找你的模块的默认路径。 例如，若要将模块保存在系统上的公共路径将`%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`。 如果不使用默认路径，您需要在安装过程中显式声明模块的位置。 请务必创建一个文件夹以保存您的模块中，您可能需要存储多个程序集和解决方案文件的文件夹。

   请注意，从技术上讲不需要在任意位置安装你的模块`PSModulePath`-这些都是只需将查找 PowerShell 模块的默认位置。 但是，它被视为最佳做法，若要执行此操作，除非您有一个充分的理由来存储您的模块中其他位置。 有关详细信息，请参阅[安装 PowerShell 模块](./installing-a-powershell-module.md)并[修改 PowerShell 模块安装路径](./modifying-the-psmodulepath-installation-path.md)。

4. 将模块导入 PowerShell，通过调用[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)。

   调用到[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)将你的模块加载到活动内存中。 如果使用 PowerShell 3.0 和更高版本，只需在代码中调用你的模块名称还将导入它;有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)。

## <a name="importing-snap-in-assemblies-as-modules"></a>作为模块导入管理单元中的程序集

可以作为二进制模块加载 Cmdlet 和提供程序中管理单元中的程序集存在。 作为二进制模块加载管理单元中的程序集时，cmdlet 和管理单元中的提供程序可供用户，但在程序集中的管理单元类将被忽略，以及未注册管理单元中。 因此，提供 Windows PowerShell 的管理单元中 cmdlet 无法检测到管理单元中即使 cmdlet 和提供程序是可用于该会话。

此外，不能作为二进制模块的一部分导入引用的管理单元中的任何格式设置或类型文件。 若要导入的文件格式和类型文件必须创建一个模块清单。 查看，请[如何编写 PowerShell 模块清单](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

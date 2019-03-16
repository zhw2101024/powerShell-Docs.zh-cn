---
title: 安装 PowerShell 模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059773"
---
# <a name="installing-a-powershell-module"></a>安装 PowerShell 模块

创建 PowerShell 模块后，将可能想要在系统上，安装该模块，以便你或其他人可能会使用它。 通常情况下，这只需包括将复制的模块文件 （即.psm1，或二进制程序集、 模块清单和相关联的任何其他文件） 到一个目录上该计算机上。 对于非常小的项目，这可能是简单复制并粘贴到一台远程计算机; 上的使用 Windows 资源管理器文件但是，对于大型解决方案可能会想要使用更复杂的安装过程。 不管如何获取您到系统上的模块，PowerShell 可以使用技巧，以将帮助用户查找并使用你的模块的数。 (有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)。)因此，安装的主要问题确保 PowerShell 将能够找到你的模块。

本主题包含下列部分：

- 安装模块的规则

- 安装模块的位置

- 安装模块的多个版本

- 处理命令名发生冲突

## <a name="rules-for-installing-modules"></a>安装模块的规则

以下信息与有关所有模块，其中包括使用、 从其他参与方，获取的模块和模块分发给其他人创建的模块。

### <a name="install-modules-in-psmodulepath"></a>在 PSModulePath 中安装模块

只要有可能，在中列出的路径中安装的所有模块**PSModulePath**环境变量或添加的模块路径**PSModulePath**环境变量值。

**PSModulePath**环境变量 ($Env: PSModulePath) 包含 Windows PowerShell 模块的位置。 若要查找模块此环境变量的值依赖于 Cmdlet。

默认情况下**PSModulePath**环境变量值包含以下系统和用户模块目录，但可以为添加和编辑值。

- $PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > 此位置保留供 Windows 附带的模块。 不要对此位置安装模块。

- $ Home\Documents\WindowsPowerShell\Modules (%userprofile%\documents\windowspowershell\modules)

- $Env: ProgramFiles\WindowsPowerShell\Modules (%programfiles%\windowspowershell\modules)

  若要获取的值**PSModulePath**环境变量，使用以下命令之一。

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  若要添加的模块路径的值**PSModulePath**环境变量值，请使用以下命令格式。 此格式使用**SetEnvironmentVariable**方法**System.Environment**类，以使对独立于会话的更改**PSModulePath**环境变量。

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > 已添加到路径后**PSModulePath**，应广播有关更改的环境消息。 广播更改允许其他应用程序，如 shell 中，若要选取更改。 若要广播进行的更改，具有产品安装代码发送**WM_SETTINGCHANGE**消息`lParam`设置为字符串"环境"。 请务必将消息发送后已更新您的模块安装代码**PSModulePath**。

### <a name="use-the-correct-module-directory-name"></a>使用正确的模块目录名称

"良好"模块是存储在模块目录中的至少一个文件的基名称与同名的目录中的模块。 如果模块不是格式正确的 Windows PowerShell 无法识别它作为一个模块。

文件的"基名称"是不带文件扩展名的名称。 在格式正确的模块中包含的模块文件的目录的名称必须与匹配模块中的至少一个文件的基名称。

例如，在示例 Fabrikam 模块中包含的模块文件的目录名为"Fabrikam"和至少一个文件具有"Fabrikam"的基名称。 在这种情况下，Fabrikam.psd1 和 Fabrikam.dll 具有"Fabrikam"的基名称。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>安装不正确的效果

如果该模块不是格式良好，并且其位置中的值不包括**PSModulePath**环境变量，如下所示的 Windows PowerShell 中，基本发现功能不起作用。

- 模块自动加载功能不能自动导入模块。

- `ListAvailable`的参数[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 找不到该模块。

- [导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet 找不到该模块。 若要导入模块，必须提供根模块文件或模块清单文件的完整路径。

  其他功能，如以下内容，除非模块已导入会话不起作用。 格式正确的模块中**PSModulePath**环境变量，这些功能可用，即使该模块未导入会话。

- [Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 找不到模块中的命令。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 无法更新或模块保存帮助。

- [Show-command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet 不能查找和显示模块中的命令。

  模块中的命令是缺少`Show-Command`窗口在 Windows PowerShell 集成脚本环境 (ISE)。

## <a name="where-to-install-modules"></a>安装模块的位置

本部分介绍在文件系统中安装 Windows PowerShell 模块的位置。 位置取决于如何使用模块。

### <a name="installing-modules-for-a-specific-user"></a>为特定用户安装模块

如果创建你自己的模块或获取模块从其他参与方，如 Windows PowerShell 社区网站，并且您希望模块可用于仅你的用户帐户，请在特定于用户的模块目录中安装模块。

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

特定于用户的 Modules 目录添加到的值**PSModulePath**默认情况下的环境变量。

### <a name="installing-modules-for-all-users-in-program-files"></a>程序文件中的所有用户安装模块

如果你想要可供所有用户帐户的计算机上的模块，模块安装在 Program Files 位置。

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> 默认情况下，Windows PowerShell 4.0 及更高版本情况下，程序文件位置添加到 PSModulePath 环境变量的值。 对于早期版本的 Windows PowerShell，您可以手动创建 Program Files 位置 ((%ProgramFiles%\WindowsPowerShell\Modules) 和将此路径添加到 PSModulePath 环境变量，如上文所述。

### <a name="installing-modules-in-a-product-directory"></a>在产品目录中安装模块

如果将分发给第三方模块，使用上文所述的默认程序文件位置或创建你自己特定于公司的或特定于产品的子目录，%programfiles%目录。

例如，Fabrikam 技术，虚构公司，将发布其 Fabrikam Manager 产品的 Windows PowerShell 模块。 其模块安装程序会创建 Fabrikam Manager 产品子目录中的模块子目录。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

若要启用 Windows PowerShell 模块发现功能，以查找 Fabrikam 模块，Fabrikam 模块安装程序将添加的模块位置的值**PSModulePath**环境变量。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>在常见的文件目录中安装模块

如果产品的多个组件或产品的多个版本使用模块，则特定于模块的 %ProgramFiles%\Common Files\Modules 子目录的子目录中安装模块。

在以下示例中，Fabrikam 模块安装 Fabrikam %ProgramFiles%\Common Files\Modules 子目录的子目录中。 请注意每个模块驻留在其自身中的模块子目录的子目录中。

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

然后，安装程序可确保的值**PSModulePath**环境变量包含常见的文件的模块子目录的路径。

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>安装模块的多个版本

若要安装的相同模块的多个版本，请使用以下过程。

1. 创建模块的每个版本的目录。 目录名称中包含的版本号。

2. 创建每个版本的模块的模块清单。 中的值**ModuleVersion**密钥在清单中，输入模块版本号。 模块的特定于版本的目录中将清单文件 (.psd1)。

3. 将模块的根文件夹路径添加到的值**PSModulePath**环境变量，如以下示例所示。

若要导入特定版本的模块，最终用户可以使用`MinimumVersion`或`RequiredVersion`的参数[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet。

例如，如果 Fabrikam 模块版本 8.0 和 9.0 中，Fabrikam 模块目录结构可能如下所示。

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

安装程序将添加这两个模块的路径**PSModulePath**环境变量值。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

完成，这些步骤后**ListAvailable**的参数[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将获取这两个 Fabrikam 模块。 若要导入特定的模块，请使用`MinimumVersion`或`RequiredVersion`的参数[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet。

如果这两个模块导入到同一会话中，并且模块包含具有相同名称的 cmdlet，最后一个导入的 cmdlet 是在会话中有效。

## <a name="handling-command-name-conflicts"></a>处理命令名发生冲突

当模块可导出的命令与命令相同的名称的用户的会话中时，可以发生命令名发生冲突。

当一个会话中包含两个具有相同名称的命令时，Windows PowerShell 运行优先的命令类型。 当会话中包含具有相同名称和相同类型的两个命令时，Windows PowerShell 将运行已添加到最新会话的命令。 若要运行不默认情况下运行的命令，用户可以限定命令名称与模块名称。

例如，如果此会话包含`Get-Date`函数和`Get-Date`cmdlet，Windows PowerShell 默认情况下运行该函数。 若要运行该 cmdlet，作为命令的开头使用模块名称，例如：

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

若要防止名称冲突，模块作者可以使用**DefaultCommandPrefix**指定名词前缀的所有命令在模块清单中的密钥从模块中导出。

用户可以使用**前缀**参数的`Import-Module`cmdlet 来使用备用前缀。 值**前缀**参数将优先于的值**DefaultCommandPrefix**密钥。

## <a name="see-also"></a>另请参阅

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

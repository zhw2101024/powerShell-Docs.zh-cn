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
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367066"
---
# <a name="installing-a-powershell-module"></a>安装 PowerShell 模块

创建 PowerShell 模块后，你可能需要在系统上安装该模块，以便你或其他人可以使用它。 一般而言，这包括将模块文件（即 hbase-runner.psm1 或二进制程序集、模块清单以及任何其他相关文件）复制到该计算机上的目录中。 对于非常小的项目，这种情况很简单，只需要使用 Windows 资源管理器将文件复制并粘贴到单台远程计算机上即可。但是，对于较大的解决方案，你可能希望使用更复杂的安装过程。 无论您将模块进入系统的方式如何，PowerShell 都可以使用多种技术，使用户能够查找和使用您的模块。 因此，安装的主要问题是确保 PowerShell 能够找到模块。 有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)。

## <a name="rules-for-installing-modules"></a>模块安装规则

以下信息适用于所有模块，包括你为自己使用而创建的模块、从其他参与方获取的模块以及分发给其他人的模块。

### <a name="install-modules-in-psmodulepath"></a>在 PSModulePath 中安装模块

尽可能将所有模块安装在**PSModulePath**环境变量中列出的路径中，或将模块路径添加到**PSModulePath**环境变量值。

**PSModulePath**环境变量（$Env:P smodulepath）包含 Windows PowerShell 模块的位置。 Cmdlet 依赖于此环境变量的值来查找模块。

默认情况下， **PSModulePath**环境变量值包含以下系统和用户模块目录，但您可以添加和编辑值。

- `$PSHome\Modules` （%Windir%\System32\WindowsPowerShell\v1.0\Modules）

  > [!WARNING]
  > 此位置是为随 Windows 提供的模块而保留的。 不要将模块安装到此位置。

- `$Home\Documents\WindowsPowerShell\Modules` （%UserProfile%\Documents\WindowsPowerShell\Modules）

- `$Env:ProgramFiles\WindowsPowerShell\Modules` （%ProgramFiles%\WindowsPowerShell\Modules）

  若要获取**PSModulePath**环境变量的值，请使用以下命令之一。

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  若要将模块路径添加到**PSModulePath**环境变量值的值中，请使用以下命令格式。 此格式使用 SetEnvironmentVariable**类的**方法对**PSModulePath**环境变量进行与会话无关的更改。

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > 将路径添加到**PSModulePath**后，应广播与更改相关的环境消息。 广播更改后，其他应用程序（如 shell）可以选取更改。 若要广播此更改，请让你的产品安装代码发送**WM_SETTINGCHANGE**消息，并将 `lParam` 设置为字符串 "环境"。 请确保在模块安装代码更新后发送消息**PSModulePath**。

### <a name="use-the-correct-module-directory-name"></a>使用正确的模块目录名称

格式正确的模块是存储在目录中的模块，其名称与模块目录中至少一个文件的基名称相同。 如果模块的格式不正确，则 Windows PowerShell 无法将其识别为模块。

文件的 "基名称" 为不带文件扩展名的名称。 在格式正确的模块中，包含模块文件的目录的名称必须与模块中至少一个文件的基名称匹配。

例如，在示例 Fabrikam 模块中，包含模块文件的目录命名为 "Fabrikam"，并且至少有一个文件具有 "Fabrikam" 基名称。 在这种情况下，psd1 和 Fabrikam 都具有 "Fabrikam" 基名称。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>错误安装的效果

如果该模块的格式不正确，并且其位置未包含在**PSModulePath**环境变量的值中，则 Windows PowerShell 的基本发现功能（如下所示）不起作用。

- 模块自动加载功能无法自动导入模块。

- [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 的 `ListAvailable` 参数找不到该模块。

- [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 找不到该模块。 若要导入模块，必须提供根模块文件或模块清单文件的完整路径。

  除非将模块导入到会话中，否则其他功能（如以下）将不起作用。 在**PSModulePath**环境变量中的格式正确的模块中，即使模块未导入到会话中，这些功能也起作用。

- [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 无法在模块中找到命令。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和 get-help cmdlet 无法更新[或保存模块](/powershell/module/Microsoft.PowerShell.Core/Save-Help)的帮助。

- [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet 无法在模块中找到并显示命令。

  Windows PowerShell 集成脚本环境（ISE）中的 "`Show-Command`" 窗口缺少模块中的命令。

## <a name="where-to-install-modules"></a>模块的安装位置

本部分介绍在文件系统中安装 Windows PowerShell 模块的位置。 位置取决于模块的使用方式。

### <a name="installing-modules-for-a-specific-user"></a>为特定用户安装模块

如果创建自己的模块或从另一方获取模块（如 Windows PowerShell 社区网站），并且希望该模块仅适用于用户帐户，请在用户特定的模块目录中安装该模块。

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

默认情况下，用户特定的模块目录将添加到**PSModulePath**环境变量的值。

### <a name="installing-modules-for-all-users-in-program-files"></a>为程序文件中的所有用户安装模块

如果希望模块可用于计算机上的所有用户帐户，请在 "程序文件" 位置中安装该模块。

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> 默认情况下，在 Windows PowerShell 4.0 和更高版本中，将程序文件位置添加到 PSModulePath 环境变量的值。 对于早期版本的 Windows PowerShell，可以手动创建程序文件位置（（%ProgramFiles%\WindowsPowerShell\Modules）并将此路径添加到 PSModulePath 环境变量，如上所述。

### <a name="installing-modules-in-a-product-directory"></a>在产品目录中安装模块

如果要将模块分发给其他参与方，请使用上面所述的默认程序文件位置，或创建自己的特定于公司的或特定于产品的% ProgramFiles% 目录。

例如，一家虚构的公司是一家虚构的公司，为其 Fabrikam 经理产品发运了一个 Windows PowerShell 模块。 它们的模块安装程序会在 Fabrikam 管理器产品子目录中创建模块子目录。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

为了使 Windows PowerShell 模块发现功能能够查找 Fabrikam 模块，Fabrikam 模块安装程序将模块位置添加到**PSModulePath**环境变量的值。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>在公共文件目录中安装模块

如果某个模块由产品的多个组件或产品的多个版本使用，请在%ProgramFiles%\Common Files\Modules 子目录的模块特定子目录中安装该模块。

在下面的示例中，Fabrikam 模块安装在 `%ProgramFiles%\Common Files\Modules` 子目录的 Fabrikam 子目录中。 请注意，每个模块都位于模块子目录中各自的子目录中。

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

然后，安装程序确保**PSModulePath**环境变量的值包含公共文件模块子目录的路径。

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

若要安装相同模块的多个版本，请使用以下过程。

1. 为模块的每个版本创建一个目录。 在目录名称中包含版本号。
2. 为每个版本的模块创建一个模块清单。 在清单中**ModuleVersion**键的值中，输入模块版本号。 将清单文件（. psd1）保存在模块的特定于版本的目录中。
3. 将模块根文件夹路径添加到**PSModulePath**环境变量的值，如以下示例中所示。

若要导入特定版本的模块，最终用户可以使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 参数。

例如，如果 Fabrikam 模块在版本8.0 和9.0 中可用，则 Fabrikam 模块目录结构可能类似于以下内容。

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

安装程序会将这两个模块路径添加到**PSModulePath**环境变量值。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

完成这些步骤后， [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的**ListAvailable**参数将获取 Fabrikam 模块。 若要导入特定模块，请使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 参数。

如果两个模块都导入到同一会话中，并且模块包含具有相同名称的 cmdlet，则最后导入的 cmdlet 在会话中有效。

## <a name="handling-command-name-conflicts"></a>处理命令名称冲突

当模块导出的命令与用户会话中的命令具有相同的名称时，可能会发生命令名称冲突。

当会话中包含两个具有相同名称的命令时，Windows PowerShell 将运行优先的命令类型。 如果会话中包含两个具有相同名称和相同类型的命令，则 Windows PowerShell 将运行最近添加到会话中的命令。 若要运行默认情况下不运行的命令，用户可以使用模块名称限定命令名称。

例如，如果会话包含 `Get-Date` 函数和 `Get-Date` cmdlet，则默认情况下，Windows PowerShell 将运行该函数。 若要运行 cmdlet，请在命令前面加上模块名称，例如：

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

若要防止名称冲突，模块作者可以使用模块清单中的**DefaultCommandPrefix**键为从该模块导出的所有命令指定名词前缀。

用户可以使用 `Import-Module` cmdlet 的**prefix**参数来使用替代前缀。 **Prefix**参数的值优先于**DefaultCommandPrefix**键的值。

## <a name="see-also"></a>另请参阅

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

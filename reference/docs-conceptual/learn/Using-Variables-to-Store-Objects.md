---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用变量存储对象
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 16e82b83df967674da11193c8ac60d637687a01b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854321"
---
# <a name="using-variables-to-store-objects"></a>使用变量存储对象

PowerShell 处理对象。 使用 PowerShell 可以创建称为“变量”的命名对象。
变量名称可以包含下划线字符和任何字母数字字符。 在 PowerShell 中使用时，始终使用变量名称后跟的 \$ 字符指定变量。

## <a name="creating-a-variable"></a>创建变量

可以通过键入有效的变量名称来创建变量：

```
PS> $loc
PS>
```

此示例不会返回任何结果，因为 `$loc` 不具有值。 你可以在同一步骤中创建变量并为其赋值。 如果不存在，PowerShell 将仅创建变量。
否则，它将指定的值分配给现有变量。 下面的示例将当前位置存储在变量 `$loc` 中：

```powershell
$loc = Get-Location
```

键入此命令时，PowerShell 不会显示任何输出。 PowerShell 将“Get-Location”的输出发送到 `$loc`。 在 PowerShell 中，未分配或未重定向的数据将发送到屏幕。 键入 `$loc` 将显示当前位置：

```
PS> $loc

Path
----
C:\temp
```

可以使用 `Get-Member` 显示有关变量内容的信息。 `Get-Member` 表示 `$loc` 是 PathInfo 对象，类似于来自 `Get-Location` 的输出：

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>操作变量

PowerShell 提供多个用以操作变量的命令。 你可以通过键入以下内容看到可读形式的完整列表：

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell 还会创建系统定义的多个变量。 可以使用 `Remove-Variable` cmdlet 来删除当前会话中所有不受 PowerShell 控制的变量。 键入以下命令来清除所有变量：

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

运行上述命令后，`Get-Variable` cmdlet 显示 PowerShell 系统变量。

PowerShell 还会创建一个变量驱动器。 使用下面的示例显示使用变量驱动器的所有 PowerShell 变量：

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>使用 cmd.exe 变量

PowerShell 可以使用任何 Windows 进程可用的相同环境变量，其中包括 cmd.exe。 这些变量通过名为 `env:` 的驱动器公开。 可以通过键入以下命令查看这些变量：

```powershell
Get-ChildItem env:
```

标准 `*-Variable` cmdlet 未设计为使用环境变量。 使用 `env:` 驱动器前缀访问环境变量。 例如，cmd.exe 中的 %SystemRoot% 变量包含操作系统的根目录名称。 在 PowerShell 中，使用 `$env:SystemRoot` 可访问相同的值。

```
PS> $env:SystemRoot
C:\WINDOWS
```

还可以从 PowerShell 内部创建和修改环境变量。 PowerShell 中的环境变量遵循操作系统中其他地方使用的环境变量的相同规则。 下面的示例创建一个新的环境变量：

```powershell
$env:LIB_PATH='/usr/local/lib'
```

尽管没有要求，但环境变量名称通常使用全部大写字母。

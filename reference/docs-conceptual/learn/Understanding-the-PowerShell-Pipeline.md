---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: 了解 PowerShell 管道
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 05ab98b7261f4d41ade1788a924193eccda6318c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086436"
---
# <a name="understanding-pipelines"></a>了解管道

管道的行为就像一系列连接的管道段一样。 沿着管道移动的项会通过每个管道段。 若要在 PowerShell 中创建管道，请使用管道运算符“|”将命令连接在一起。 每个命令的输出都将被用作下一命令的输入。

用于管道的符号类似于其他 shell 中使用的符号。 初看起来 PowerShell 中管道的不同之处可能并不明显。 尽管你会在屏幕上看到文本，但 PowerShell 通过管道在命令之间传递对象，而不是文本。

## <a name="the-powershell-pipeline"></a>PowerShell 管道

管道可能是命令行界面中使用的最有价值的概念。 如果使用得当，管道可以减少使用复杂命令的工作量，并且可以更轻松地查看命令的工作流程。 管道中的每个命令（称为管道元素）将其输出逐项传递到管道中的下一个命令。 命令不必一次处理多个项目。 结果是减少了资源消耗，并且能够立即开始获取输出。

例如，如果使用 `Out-Host` cmdlet 来强制逐页显示来自于另一个命令的输出，那么这一输出看起来就像分页显示在屏幕上的普通文本：

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

分页还会降低 CPU 利用率，因为准备好显示完整页面时，会转为处理 `Out-Host` cmdlet。 管道中位于前面的 cmdlet 暂停执行，直到输出的下一页可用。

可以看到 Windows 任务管理器监视的 PowerShell 使用的 CPU 和内存存在差异。 运行以下命令：`Get-ChildItem C:\Windows -Recurse`。 将 CPU 和内存使用情况与此命令进行比较：`Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`。

> [!NOTE]
> 并非所有的 PowerShell 主机都支持 Paging 参数。 例如，当你尝试在 PowerShell ISE 中使用 Paging 参数时，会看到以下错误：
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>管道中的对象

在 PowerShell 中运行 cmdlet 时，可以看到文本输出，因为必须在控制台窗口中以文本形式表示对象。 文本输出可能不会显示输出的对象的所有属性。

例如，请考虑 `Get-Location` cmdlet。 如果运行 `Get-Location`，而当前位置是 C 驱动器的根路径，将看到以下输出：

```
PS> Get-Location

Path
----
C:\
```

文本输出是信息摘要，而非 `Get-Location` 返回的对象的完整表示形式。 输出中的标题通过格式化屏幕显示数据的过程添加。

通过管道将输出传递到 `Get-Member` cmdlet 后，可以获取有关 `Get-Location` 返回的对象信息。

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` 返回 PathInfo 对象，其中包含当前路径和其他信息。

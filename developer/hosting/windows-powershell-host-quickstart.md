---
title: Windows PowerShell 主机快速入门 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530623"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell 主机快速入门

若要在应用程序中托管 Windows PowerShell，请使用[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)类。
此类提供了创建命令的管道，然后在运行空间中执行这些命令的方法。
创建主机应用程序的最简单方法是使用默认的运行空间。
默认的运行空间包含的所有核心 Windows PowerShell 命令。
如果你希望应用程序来公开 Windows PowerShell 命令的一个子集，则必须创建自定义的运行空间。

## <a name="using-the-default-runspace"></a>使用默认的运行空间

若要开始，我们将使用默认的运行空间，并使用的方法[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)类将命令、 参数、 语句和脚本添加到管道。

### <a name="addcommand"></a>AddCommand

您使用[System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法将命令添加到管道。
例如，假设你想要获取在计算机上运行的进程列表。
若要运行此命令的方法是按如下所示。

1. 创建[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)对象。

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. 添加你想要执行的命令。

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. 调用命令。

   ```csharp
   ps.Invoke();
   ```

如果在调用之前多次调用 AddCommand 方法[System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法，第一个命令的结果通过管道传送给第二个，依次类推。
如果您不想要通过管道传递到命令前一命令的结果，则将其添加通过调用[System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)相反。

### <a name="addparameter"></a>AddParameter

前面的示例执行不带任何参数的单个命令。
通过使用添加到命令参数[System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法。
例如，以下代码将获取所有名为的进程的列表`PowerShell`在计算机上运行。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

通过重复调用 AddParameter 方法，可以添加其他参数。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

此外可以通过调用添加参数名称和值的字典[System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

可以通过使用批处理来模拟[System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法，将一个附加的语句添加到管道的末端。
以下代码将获取正在运行的进程名列表`PowerShell`，然后获取正在运行服务的列表。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

可以通过调用运行现有脚本[System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法。
下面的示例将脚本添加到管道，并运行它。
此示例假定已存在名为的脚本`MyScript.ps1`中名为的文件夹`D:\PSScripts`。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

此外，还有新版 AddScript 方法采用布尔参数名为`useLocalScope`。
如果此参数设置为`true`，然后在本地作用域中运行该脚本。
下面的代码将在本地作用域中运行脚本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>创建自定义的运行空间

尽管上述示例中使用默认的运行空间加载所有核心 Windows PowerShell 命令，可以创建加载指定的一个子集的所有命令的自定义运行空间。
你可能想要这样做可以提高性能 （正在加载更多的命令是性能下降），或限制用户能够执行的操作。
公开只有有限的数量的命令的运行空间称为受限运行空间。
若要创建受限运行空间，请使用[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)并[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)类。

### <a name="creating-an-initialsessionstate-object"></a>创建 InitialSessionState 对象

若要创建自定义的运行空间，必须首先创建[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。
在以下示例中，我们将使用[System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory)若要创建默认 InitialSessionState 对象后创建的运行空间。

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>限制运行空间

在上述示例中，我们创建了默认值[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)加载所有内置的核心 Windows PowerShell 的对象。
我们可能也称为[System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法来创建一个 InitialSessionState 对象，将加载只有 Microsoft.PowerShell.Core 中的命令管理单元。
若要创建更多受限运行空间，必须创建一个空的 InitialSessionState 对象通过调用[System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法，以及如何将命令传递给InitialSessionState。

使用加载指定的命令的运行空间提供了显著改进了的性能。

使用的方法[System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)类来定义初始会话状态的 cmdlet。
下面的示例将创建空的初始会话状态，然后定义并添加`Get-Command`和`Import-Module`初始会话状态的命令。
然后，我们创建初始会话状态，受约束的运行空间，并在该运行空间中执行命令。

创建初始会话状态。

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

定义并将命令添加到初始会话状态。

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

创建并打开运行空间。

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

执行命令并显示结果。

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

当运行时，此代码的输出将如下所示。

```powershell
Get-Command
Import-Module
```

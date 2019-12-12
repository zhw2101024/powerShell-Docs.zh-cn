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
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360816"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell 主机快速入门

若要在应用程序中托管 Windows PowerShell，请使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)类。
此类提供创建命令管道，然后在运行空间中执行这些命令的方法。
创建主机应用程序的最简单方法是使用默认的运行空间。
默认运行空间包含所有核心 Windows PowerShell 命令。
如果希望应用程序仅公开部分 Windows PowerShell 命令，则必须创建自定义运行空间。

## <a name="using-the-default-runspace"></a>使用默认运行空间

首先，我们将使用默认的运行空间，并使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)类的方法向管道添加命令、参数、语句和脚本。

### <a name="addcommand"></a>AddCommand

您可以使用[AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法将命令添加到管道中。
例如，假设您希望获取计算机上正在运行的进程的列表。
运行此命令的方法如下所示。

1. 创建一个 "[管理](/dotnet/api/System.Management.Automation.PowerShell)" 对象。

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. 添加要执行的命令。

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. 调用命令。

   ```csharp
   ps.Invoke();
   ```

如果在调用[AddCommand 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次调用了方法，则第一个命令的结果将通过管道传递到第二个命令，依此类推。
如果你不想通过管道将前一个命令的结果传递给命令，请改为通过调用[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)来添加它。

### <a name="addparameter"></a>AddParameter

前面的示例执行一个不带任何参数的命令。
可以使用[PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法将参数添加到命令中。
例如，下面的代码获取在计算机上运行的名为 `PowerShell` 的所有进程的列表。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

可以通过重复调用 AddParameter 方法来添加其他参数。

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

你还可以通过调用[AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法来添加参数名称和值的字典。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

您可以使用[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法来模拟批处理，该方法将附加语句添加到管道的末尾。
下面的代码获取名称 `PowerShell`正在运行的进程的列表，然后获取正在运行的服务的列表。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

您可以通过调用[AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法来运行现有的脚本。
下面的示例向管道添加一个脚本并运行该脚本。
此示例假设名为 `D:\PSScripts`的文件夹中已有一个名为 `MyScript.ps1` 的脚本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

还有一个 AddScript 方法版本，该方法采用名为 `useLocalScope`的布尔参数。
如果将此参数设置为 `true`，则脚本将在本地作用域中运行。
以下代码将在本地作用域中运行该脚本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>创建自定义运行空间

虽然前面的示例中使用的默认运行空间加载了所有核心 Windows PowerShell 命令，但你可以创建一个自定义的运行空间，该运行空间仅加载指定的所有命令子集。
你可能希望执行此操作以提高性能（加载更多的命令是性能下降），或限制用户执行操作的能力。
仅公开有限数量的命令的运行空间称为受限制的运行空间。
若要创建受限制的运行空间，请使用[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) [类和 ". 管理类](/dotnet/api/System.Management.Automation.Runspaces.Runspace)"。

### <a name="creating-an-initialsessionstate-object"></a>创建 InitialSessionState 对象

若要创建自定义运行空间，必须首先创建[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。
在下面的示例中，我们将使用[RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory)来创建默认的 InitialSessionState 对象之后的运行空间。

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>约束运行空间

在上面的示例中，我们创建了一个默认的[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，该对象加载所有内置核心 Windows PowerShell。
我们还可以调用[CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法来创建一个 InitialSessionState 对象，该对象只会加载 InitialSessionState 管理单元中的命令，而不是。
若要创建更受限制的运行空间，必须通过调用[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法来创建一个空的 InitialSessionState 对象，然后将命令添加到 InitialSessionState。

使用仅加载您指定的命令的运行空间可显著提高性能。

你可以使用[SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)类的方法来定义初始会话状态的 cmdlet）。
下面的示例创建一个空的初始会话状态，然后定义 `Get-Command`，并将 `Import-Module` 命令添加到初始会话状态。
然后创建一个受该初始会话状态约束的运行空间，并执行该运行空间中的命令。

创建初始会话状态。

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

定义命令并将其添加到初始会话状态。

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

运行时，此代码的输出将如下所示。

```powershell
Get-Command
Import-Module
```

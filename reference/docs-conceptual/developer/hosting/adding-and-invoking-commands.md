---
title: 添加和调用命令 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367636"
---
# <a name="adding-and-invoking-commands"></a>添加和调用命令

创建运行空间后，可以将 Windows PowerShellcommands 和脚本添加到管道，然后以同步或异步方式调用管道。

## <a name="creating-a-pipeline"></a>创建管道

 [System.web](/dotnet/api/system.management.automation.powershell)类提供多种方法来向管道添加命令、参数和脚本。 您可以通过调用 Begininvoke [*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法的重载，或通过调用 * 的重载，以同步方式调用该管道。[管理组件](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)的重载 *然后，再将[Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

### <a name="addcommand"></a>AddCommand

1. 创建一个 "[管理](/dotnet/api/system.management.automation.powershell)" 对象。

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

 如果在调用 Addcommand [* 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次调用了[*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，则第一个命令的结果将通过管道传递到第二个命令，依此类推，直到第二个命令。 如果你不想通过管道将前一个命令的结果传递给命令，请通过调用[Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)来添加它。

### <a name="addparameter"></a>AddParameter

 前面的示例执行一个不带任何参数的命令。 你可以使用[Pscommand. Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法将参数添加到命令。例如，以下代码将获取在计算机上运行的名为 `PowerShell` 的所有进程的列表。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 可以通过重复调用[Addparameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)来添加其他参数。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 你还可以通过调用[Addparameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法添加参数名和值的字典，。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 您可以使用[Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法模拟批处理，该方法将其他语句添加到管道的末尾，以下代码将获取名称 @no__t 为的正在运行的进程的列表，然后获取正在运行的服务的列表。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 您可以通过调用[Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法来运行现有的脚本。 下面的示例向管道添加一个脚本并运行该脚本。 此示例假设名为 @no__t 的文件夹中已存在一个名为 `MyScript.ps1` 的脚本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 还有一个版本的[Addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法，该方法采用名为 `useLocalScope` 的布尔参数。 如果此参数设置为 `true`，则脚本将在本地作用域中运行。 以下代码将在本地作用域中运行该脚本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>同步调用管道

 向管道添加元素后，可以调用它。 若要以同步方式调用管道，请调用[一个方法的重载。](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 下面的示例演示如何以同步方式调用管道。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>异步调用管道

 您可以通过调用[Begininvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)的重载来异步调用管道，以创建[IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)对象，然后调用 Endinvoke 的重载对象，然后调用。 [*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

 下面的示例演示如何以异步方式调用管道。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>另请参阅

 [创建 InitialSessionState](./creating-an-initialsessionstate.md)

 [创建受限的运行空间](./creating-a-constrained-runspace.md)

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
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083019"
---
# <a name="adding-and-invoking-commands"></a>添加和调用命令

创建一个运行空间后, 可以将 Windows PowerShellcommands 和脚本添加到管道，并以同步方式还是以异步方式，然后调用管道。

## <a name="creating-a-pipeline"></a>创建管道

 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类提供了几种方法来将命令、 参数和脚本添加到管道。 您可以通过调用的重载以同步方式调用管道[System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法，或以异步方式调用的重载[System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) ，然后[System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

### <a name="addcommand"></a>AddCommand

1. 创建[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。

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

 如果您调用[System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法多次在调用之前[System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法、 的结果第一个命令将被输送到第二个，依次类推。 如果您不想要通过管道传递到命令前一命令的结果，则将其添加通过调用[System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)相反。

### <a name="addparameter"></a>AddParameter

 前面的示例执行不带任何参数的单个命令。 通过使用添加到命令参数[System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法，如以下代码获取一系列的所有进程名为`PowerShell`上运行计算机。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 可以添加其他参数，通过调用[System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)重复。

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 此外可以通过调用添加参数名称和值的字典[System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法。

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 可以通过使用批处理来模拟[System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法，该管道的以下代码获取具有名称运行进程的列表的末尾添加一个附加的语句方法`PowerShell`，然后获取正在运行服务的列表。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 可以通过调用运行现有脚本[System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法。 下面的示例将脚本添加到管道，并运行它。 此示例假定已存在名为的脚本`MyScript.ps1`中名为的文件夹`D:\PSScripts`。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 此外，还有新版[System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法采用布尔参数名为`useLocalScope`。 如果此参数设置为`true`，然后在本地作用域中运行该脚本。 下面的代码将在本地作用域中运行脚本。

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>以同步方式调用管道

 将元素添加到管道后，调用它。 若要以同步方式调用管道，则调用的重载[System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法。 下面的示例演示如何以同步方式调用管道。

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

### <a name="invoking-a-pipeline-asynchronously"></a>以异步方式调用管道

 调用管道以异步方式调用的重载[System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)来创建[IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)对象，并调用[System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

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

 [创建受限运行空间](./creating-a-constrained-runspace.md)

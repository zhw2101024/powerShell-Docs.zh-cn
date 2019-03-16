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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057648"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="c86ef-102">添加和调用命令</span><span class="sxs-lookup"><span data-stu-id="c86ef-102">Adding and invoking commands</span></span>

<span data-ttu-id="c86ef-103">创建一个运行空间后, 可以将 Windows PowerShellcommands 和脚本添加到管道，并以同步方式还是以异步方式，然后调用管道。</span><span class="sxs-lookup"><span data-stu-id="c86ef-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="c86ef-104">创建管道</span><span class="sxs-lookup"><span data-stu-id="c86ef-104">Creating a pipeline</span></span>

 <span data-ttu-id="c86ef-105">[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类提供了几种方法来将命令、 参数和脚本添加到管道。</span><span class="sxs-lookup"><span data-stu-id="c86ef-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="c86ef-106">您可以通过调用的重载以同步方式调用管道[System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法，或以异步方式调用的重载[System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) ，然后[System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。</span><span class="sxs-lookup"><span data-stu-id="c86ef-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="c86ef-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="c86ef-107">AddCommand</span></span>

1. <span data-ttu-id="c86ef-108">创建[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="c86ef-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="c86ef-109">添加你想要执行的命令。</span><span class="sxs-lookup"><span data-stu-id="c86ef-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="c86ef-110">调用命令。</span><span class="sxs-lookup"><span data-stu-id="c86ef-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="c86ef-111">如果您调用[System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法多次在调用之前[System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法、 的结果第一个命令将被输送到第二个，依次类推。</span><span class="sxs-lookup"><span data-stu-id="c86ef-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="c86ef-112">如果您不想要通过管道传递到命令前一命令的结果，则将其添加通过调用[System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)相反。</span><span class="sxs-lookup"><span data-stu-id="c86ef-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="c86ef-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="c86ef-113">AddParameter</span></span>

 <span data-ttu-id="c86ef-114">前面的示例执行不带任何参数的单个命令。</span><span class="sxs-lookup"><span data-stu-id="c86ef-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="c86ef-115">通过使用添加到命令参数[System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法，如以下代码获取一系列的所有进程名为`PowerShell`上运行计算机。</span><span class="sxs-lookup"><span data-stu-id="c86ef-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="c86ef-116">可以添加其他参数，通过调用[System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)重复。</span><span class="sxs-lookup"><span data-stu-id="c86ef-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="c86ef-117">此外可以通过调用添加参数名称和值的字典[System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="c86ef-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="c86ef-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="c86ef-118">AddStatement</span></span>

 <span data-ttu-id="c86ef-119">可以通过使用批处理来模拟[System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法，该管道的以下代码获取具有名称运行进程的列表的末尾添加一个附加的语句方法`PowerShell`，然后获取正在运行服务的列表。</span><span class="sxs-lookup"><span data-stu-id="c86ef-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="c86ef-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="c86ef-120">AddScript</span></span>

 <span data-ttu-id="c86ef-121">可以通过调用运行现有脚本[System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法。</span><span class="sxs-lookup"><span data-stu-id="c86ef-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="c86ef-122">下面的示例将脚本添加到管道，并运行它。</span><span class="sxs-lookup"><span data-stu-id="c86ef-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="c86ef-123">此示例假定已存在名为的脚本`MyScript.ps1`中名为的文件夹`D:\PSScripts`。</span><span class="sxs-lookup"><span data-stu-id="c86ef-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="c86ef-124">此外，还有新版[System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法采用布尔参数名为`useLocalScope`。</span><span class="sxs-lookup"><span data-stu-id="c86ef-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="c86ef-125">如果此参数设置为`true`，然后在本地作用域中运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="c86ef-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="c86ef-126">下面的代码将在本地作用域中运行脚本。</span><span class="sxs-lookup"><span data-stu-id="c86ef-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="c86ef-127">以同步方式调用管道</span><span class="sxs-lookup"><span data-stu-id="c86ef-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="c86ef-128">将元素添加到管道后，调用它。</span><span class="sxs-lookup"><span data-stu-id="c86ef-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="c86ef-129">若要以同步方式调用管道，则调用的重载[System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法。</span><span class="sxs-lookup"><span data-stu-id="c86ef-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="c86ef-130">下面的示例演示如何以同步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="c86ef-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="c86ef-131">以异步方式调用管道</span><span class="sxs-lookup"><span data-stu-id="c86ef-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="c86ef-132">调用管道以异步方式调用的重载[System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)来创建[IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)对象，并调用[System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。</span><span class="sxs-lookup"><span data-stu-id="c86ef-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="c86ef-133">下面的示例演示如何以异步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="c86ef-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c86ef-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c86ef-134">See Also</span></span>

 [<span data-ttu-id="c86ef-135">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="c86ef-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="c86ef-136">创建受限运行空间</span><span class="sxs-lookup"><span data-stu-id="c86ef-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

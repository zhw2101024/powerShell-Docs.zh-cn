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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367636"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="fae6c-102">添加和调用命令</span><span class="sxs-lookup"><span data-stu-id="fae6c-102">Adding and invoking commands</span></span>

<span data-ttu-id="fae6c-103">创建运行空间后，可以将 Windows PowerShellcommands 和脚本添加到管道，然后以同步或异步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="fae6c-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="fae6c-104">创建管道</span><span class="sxs-lookup"><span data-stu-id="fae6c-104">Creating a pipeline</span></span>

 <span data-ttu-id="fae6c-105">[System.web](/dotnet/api/system.management.automation.powershell)类提供多种方法来向管道添加命令、参数和脚本。</span><span class="sxs-lookup"><span data-stu-id="fae6c-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="fae6c-106">您可以通过调用 Begininvoke [\* 方法的](/dotnet/api/System.Management.Automation.PowerShell.Invoke)重载，或通过调用[\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)的重载，然后通过调用[Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法，以同步方式调用该管道，或通过调用此方法来异步调用该管道。</span><span class="sxs-lookup"><span data-stu-id="fae6c-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="fae6c-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="fae6c-107">AddCommand</span></span>

1. <span data-ttu-id="fae6c-108">创建一个 "[管理](/dotnet/api/system.management.automation.powershell)" 对象。</span><span class="sxs-lookup"><span data-stu-id="fae6c-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="fae6c-109">添加要执行的命令。</span><span class="sxs-lookup"><span data-stu-id="fae6c-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="fae6c-110">调用命令。</span><span class="sxs-lookup"><span data-stu-id="fae6c-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="fae6c-111">如果在调用 Addcommand [\* 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次调用了[\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，则第一个命令的结果将通过管道传递到第二个命令，依此类推，直到第二个命令。</span><span class="sxs-lookup"><span data-stu-id="fae6c-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="fae6c-112">如果你不想通过管道将前一个命令的结果传递给命令，请通过调用[Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)来添加它。</span><span class="sxs-lookup"><span data-stu-id="fae6c-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="fae6c-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="fae6c-113">AddParameter</span></span>

 <span data-ttu-id="fae6c-114">前面的示例执行一个不带任何参数的命令。</span><span class="sxs-lookup"><span data-stu-id="fae6c-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="fae6c-115">你可以使用[Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法将参数添加到命令。例如，以下代码将获取在计算机上运行的名为 `PowerShell` 的所有进程的列表。</span><span class="sxs-lookup"><span data-stu-id="fae6c-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="fae6c-116">可以通过重复调用[Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)来添加其他参数。</span><span class="sxs-lookup"><span data-stu-id="fae6c-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="fae6c-117">你还可以通过调用[Addparameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法添加参数名和值的字典，。</span><span class="sxs-lookup"><span data-stu-id="fae6c-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="fae6c-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="fae6c-118">AddStatement</span></span>

 <span data-ttu-id="fae6c-119">您可以使用[Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法模拟批处理，该方法将其他语句添加到管道的末尾，以下代码获取名称为 `PowerShell`的运行中进程的列表，然后获取正在运行的服务的列表。</span><span class="sxs-lookup"><span data-stu-id="fae6c-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="fae6c-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="fae6c-120">AddScript</span></span>

 <span data-ttu-id="fae6c-121">您可以通过调用[Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法来运行现有的脚本。</span><span class="sxs-lookup"><span data-stu-id="fae6c-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="fae6c-122">下面的示例向管道添加一个脚本并运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="fae6c-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="fae6c-123">此示例假设名为 `D:\PSScripts`的文件夹中已有一个名为 `MyScript.ps1` 的脚本。</span><span class="sxs-lookup"><span data-stu-id="fae6c-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="fae6c-124">还有一个版本的[Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法，该方法采用名为 `useLocalScope`的布尔参数。</span><span class="sxs-lookup"><span data-stu-id="fae6c-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="fae6c-125">如果将此参数设置为 `true`，则脚本将在本地作用域中运行。</span><span class="sxs-lookup"><span data-stu-id="fae6c-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="fae6c-126">以下代码将在本地作用域中运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="fae6c-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="fae6c-127">同步调用管道</span><span class="sxs-lookup"><span data-stu-id="fae6c-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="fae6c-128">向管道添加元素后，可以调用它。</span><span class="sxs-lookup"><span data-stu-id="fae6c-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="fae6c-129">若要以同步方式调用管道，请调用[一个方法的重载。](/dotnet/api/System.Management.Automation.PowerShell.Invoke)</span><span class="sxs-lookup"><span data-stu-id="fae6c-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="fae6c-130">下面的示例演示如何以同步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="fae6c-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="fae6c-131">异步调用管道</span><span class="sxs-lookup"><span data-stu-id="fae6c-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="fae6c-132">您可以通过调用[Begininvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)的重载来异步调用管道，以创建[IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)对象，然后调用[Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法，从而实现这一目标的调用。</span><span class="sxs-lookup"><span data-stu-id="fae6c-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="fae6c-133">下面的示例演示如何以异步方式调用管道。</span><span class="sxs-lookup"><span data-stu-id="fae6c-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fae6c-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fae6c-134">See Also</span></span>

 [<span data-ttu-id="fae6c-135">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="fae6c-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="fae6c-136">创建受限的运行空间</span><span class="sxs-lookup"><span data-stu-id="fae6c-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

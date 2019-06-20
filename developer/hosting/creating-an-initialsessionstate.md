---
title: 创建 InitialSessionState |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263834"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="0b096-102">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0b096-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="0b096-103">在运行空间中运行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="0b096-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="0b096-104">若要在应用程序中承载 PowerShell，必须创建[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)对象。</span><span class="sxs-lookup"><span data-stu-id="0b096-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="0b096-105">每个运行空间具有[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象与之关联。</span><span class="sxs-lookup"><span data-stu-id="0b096-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="0b096-106">InitialSessionState 指定的运行空间，如哪些命令、 变量和模块是可用于该运行空间的特征。</span><span class="sxs-lookup"><span data-stu-id="0b096-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="0b096-107">创建默认的 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0b096-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="0b096-108">[CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)并[CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法**InitialSessionState**类可用于创建**InitialSessionState**对象。</span><span class="sxs-lookup"><span data-stu-id="0b096-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="0b096-109">**CreateDefault**方法创建**InitialSessionState**使用的所有内置命令加载，同时**CreateDefault2**方法将加载只有命令需要对主机 PowerShell （从 Microsoft.PowerShell.Core 模块的命令）。</span><span class="sxs-lookup"><span data-stu-id="0b096-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="0b096-110">如果你想要进一步限制在主机应用程序中可用的命令需要创建受限运行空间。</span><span class="sxs-lookup"><span data-stu-id="0b096-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="0b096-111">有关信息，请参阅[创建受限运行空间](creating-a-constrained-runspace.md)。</span><span class="sxs-lookup"><span data-stu-id="0b096-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="0b096-112">下面的代码演示如何创建**InitialSessionState**、 将其分配给一个运行空间中，将命令添加到该运行空间中的管道和调用命令。</span><span class="sxs-lookup"><span data-stu-id="0b096-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="0b096-113">有关添加和调用命令的详细信息，请参阅[添加和调用命令](adding-and-invoking-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="0b096-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="0b096-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b096-114">See Also</span></span>

[<span data-ttu-id="0b096-115">创建受限运行空间</span><span class="sxs-lookup"><span data-stu-id="0b096-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="0b096-116">添加和调用命令</span><span class="sxs-lookup"><span data-stu-id="0b096-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)

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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367616"
---
# <a name="creating-an-initialsessionstate"></a>创建 InitialSessionState

PowerShell 命令在运行空间中运行。
若要在你的应用程序中托管 PowerShell，你必须[创建一个](/dotnet/api/System.Management.Automation.Runspaces.Runspace)
每个运行空间都有一个与其关联的[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。
InitialSessionState 指定运行空间的特征，例如，哪些命令、变量和模块可用于该运行空间。

## <a name="create-a-default-initialsessionstate"></a>创建默认 InitialSessionState

**InitialSessionState**类的[CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)和[CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法可用于创建**InitialSessionState**对象。
**CreateDefault**方法将创建一个**InitialSessionState** ，其中加载了所有内置命令，而**CreateDefault2**方法只加载承载 PowerShell 所需的命令（来自模块的命令）。

若要进一步限制主机应用程序中可用的命令，需要创建受约束的运行空间。
有关信息，请参阅[创建受限的运行空间](creating-a-constrained-runspace.md)。

下面的代码演示如何创建**InitialSessionState**，将其分配给运行空间，将命令添加到该运行空间中的管道，以及调用命令。
有关添加和调用命令的详细信息，请参阅[添加和调用命令](adding-and-invoking-commands.md)。

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

## <a name="see-also"></a>另请参阅

[创建受限的运行空间](creating-a-constrained-runspace.md)

[添加和调用命令](adding-and-invoking-commands.md)

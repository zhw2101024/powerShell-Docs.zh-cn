---
title: Runspace05 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1685cfc4-b32c-4bed-b221-e0c4482db955
caps.latest.revision: 9
ms.openlocfilehash: eb227b5fa5e91f59b6fc99981ff5affca1cf63fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360876"
---
# <a name="runspace05-sample"></a>Runspace05 示例

此示例演示如何将管理单元添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，以便打开运行空间时，管理单元的 cmdlet 可用于该管理单元。 该管理单元提供了一个通过使用 GetProcessSample01 对象同步运行的获取处理器 cmdlet （由该[示例](../cmdlet/getprocesssample01-sample.md)定义[）。](/dotnet/api/system.management.automation.powershell)

## <a name="requirements"></a>要求

此示例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>说明

此示例演示以下各项。

- 正在创建一个[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。

- 将该管理单元添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象中。

- 使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象创建一个使用的 system.servicemodel. e i.[管理](/dotnet/api/System.Management.Automation.Runspaces.Runspace)对象。

- 创建使用运行空间的[system.web](/dotnet/api/system.management.automation.powershell)对象。

- 将管理单元的处理器 cmdlet 添加到[系统管理](/dotnet/api/system.management.automation.powershell)对象的管道中。

- 同步运行命令。

- 从命令返回的[system.object](/dotnet/api/System.Management.Automation.PSObject)对象中提取属性。

## <a name="example"></a>示例

此示例将创建一个运行空间，该运行空间使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象来定义打开运行空间时可用的元素。 在此示例中，将定义一个过程 cmdlet 的管理单元添加到初始会话状态。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }
      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 主机应用程序](./writing-a-windows-powershell-host-application.md)
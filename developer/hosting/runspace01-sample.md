---
title: Runspace01 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057903"
---
# <a name="runspace01-sample"></a>Runspace01 示例

此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 以同步方式。 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 将返回[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象的每个进程在本地计算机上运行。 值[System.Diagnostics.Process.Processname*](/dotnet/api/System.Diagnostics.Process.ProcessName)并[System.Diagnostics.Process.Handlecount*](/dotnet/api/System.Diagnostics.Process.Handlecount)然后从返回的对象中提取并在控制台中显示属性窗口。

## <a name="requirements"></a>要求

 此示例要求 Windows PowerShell 2.0。

## <a name="demonstrates"></a>说明

- 创建[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象运行命令。

- 将命令添加到的管道[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。

- 以同步方式运行命令。

- 使用[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)要从命令返回的对象中提取属性的对象。

## <a name="example"></a>示例

 此示例运行时[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)同步中默认的运行空间提供的 Windows PowerShell cmdlet。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>另请参阅

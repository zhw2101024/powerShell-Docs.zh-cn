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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367416"
---
# <a name="runspace01-sample"></a><span data-ttu-id="f4e63-102">Runspace01 示例</span><span class="sxs-lookup"><span data-stu-id="f4e63-102">Runspace01 Sample</span></span>

<span data-ttu-id="f4e63-103">此示例演示如何使用[system.exception 类以](/dotnet/api/system.management.automation.powershell)同步方式运行[Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f4e63-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="f4e63-104">[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 将为在本地计算机上运行的每个进程返回[system.object](/dotnet/api/System.Diagnostics.Process) 。</span><span class="sxs-lookup"><span data-stu-id="f4e63-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="f4e63-105">然后，将从返回的对象中提取[Processname \*](/dotnet/api/System.Diagnostics.Process.ProcessName)和[Handlecount \*](/dotnet/api/System.Diagnostics.Process.Handlecount)属性的值，并将其显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="f4e63-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4e63-106">要求</span><span class="sxs-lookup"><span data-stu-id="f4e63-106">Requirements</span></span>

 <span data-ttu-id="f4e63-107">此示例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="f4e63-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f4e63-108">示例</span><span class="sxs-lookup"><span data-stu-id="f4e63-108">Demonstrates</span></span>

- <span data-ttu-id="f4e63-109">创建要运行命令的[system.web](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="f4e63-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="f4e63-110">将命令添加到[system.web](/dotnet/api/system.management.automation.powershell)对象的管道。</span><span class="sxs-lookup"><span data-stu-id="f4e63-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="f4e63-111">同步运行命令。</span><span class="sxs-lookup"><span data-stu-id="f4e63-111">Running the command synchronously.</span></span>

- <span data-ttu-id="f4e63-112">使用 system.exception 对象从命令返回[的对象中](/dotnet/api/System.Management.Automation.PSObject)提取属性。</span><span class="sxs-lookup"><span data-stu-id="f4e63-112">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="f4e63-113">示例</span><span class="sxs-lookup"><span data-stu-id="f4e63-113">Example</span></span>

 <span data-ttu-id="f4e63-114">此示例在 Windows PowerShell 提供的默认运行空间中以同步方式运行[Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f4e63-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f4e63-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4e63-115">See Also</span></span>

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
# <a name="runspace05-sample"></a><span data-ttu-id="e6cad-102">Runspace05 示例</span><span class="sxs-lookup"><span data-stu-id="e6cad-102">Runspace05 Sample</span></span>

<span data-ttu-id="e6cad-103">此示例演示如何将管理单元添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，以便打开运行空间时，管理单元的 cmdlet 可用于该管理单元。</span><span class="sxs-lookup"><span data-stu-id="e6cad-103">This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="e6cad-104">该管理单元提供了一个通过使用 GetProcessSample01 对象同步运行的获取处理器 cmdlet （由该[示例](../cmdlet/getprocesssample01-sample.md)定义[）。](/dotnet/api/system.management.automation.powershell)</span><span class="sxs-lookup"><span data-stu-id="e6cad-104">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6cad-105">要求</span><span class="sxs-lookup"><span data-stu-id="e6cad-105">Requirements</span></span>

<span data-ttu-id="e6cad-106">此示例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="e6cad-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e6cad-107">说明</span><span class="sxs-lookup"><span data-stu-id="e6cad-107">Demonstrates</span></span>

<span data-ttu-id="e6cad-108">此示例演示以下各项。</span><span class="sxs-lookup"><span data-stu-id="e6cad-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e6cad-109">正在创建一个[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。</span><span class="sxs-lookup"><span data-stu-id="e6cad-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e6cad-110">将该管理单元添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象中。</span><span class="sxs-lookup"><span data-stu-id="e6cad-110">Adding the snap-in to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e6cad-111">使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象创建一个使用的 system.servicemodel. e i.[管理](/dotnet/api/System.Management.Automation.Runspaces.Runspace)对象。</span><span class="sxs-lookup"><span data-stu-id="e6cad-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e6cad-112">创建使用运行空间的[system.web](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="e6cad-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="e6cad-113">将管理单元的处理器 cmdlet 添加到[系统管理](/dotnet/api/system.management.automation.powershell)对象的管道中。</span><span class="sxs-lookup"><span data-stu-id="e6cad-113">Adding the snap-in's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e6cad-114">同步运行命令。</span><span class="sxs-lookup"><span data-stu-id="e6cad-114">Running the command synchronously.</span></span>

- <span data-ttu-id="e6cad-115">从命令返回的[system.object](/dotnet/api/System.Management.Automation.PSObject)对象中提取属性。</span><span class="sxs-lookup"><span data-stu-id="e6cad-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="e6cad-116">示例</span><span class="sxs-lookup"><span data-stu-id="e6cad-116">Example</span></span>

<span data-ttu-id="e6cad-117">此示例将创建一个运行空间，该运行空间使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象来定义打开运行空间时可用的元素。</span><span class="sxs-lookup"><span data-stu-id="e6cad-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="e6cad-118">在此示例中，将定义一个过程 cmdlet 的管理单元添加到初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="e6cad-118">In this sample, a snap-in that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e6cad-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6cad-119">See Also</span></span>

[<span data-ttu-id="e6cad-120">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="e6cad-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
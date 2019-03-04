---
title: Runspace06 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 8621878a339751d2cef842af6f5b3d5d2e270346
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862613"
---
# <a name="runspace06-sample"></a><span data-ttu-id="e8425-102">Runspace06 示例</span><span class="sxs-lookup"><span data-stu-id="e8425-102">Runspace06 Sample</span></span>

<span data-ttu-id="e8425-103">此示例演示如何将添加到模块[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，以便打开运行空间时加载的模块。</span><span class="sxs-lookup"><span data-stu-id="e8425-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="e8425-104">模块提供 Get-proc cmdlet (由[GetProcessSample02 示例](../cmdlet/getprocesssample02-sample.md))，通过使用以同步方式运行[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="e8425-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8425-105">要求</span><span class="sxs-lookup"><span data-stu-id="e8425-105">Requirements</span></span>

<span data-ttu-id="e8425-106">此示例要求 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="e8425-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e8425-107">说明</span><span class="sxs-lookup"><span data-stu-id="e8425-107">Demonstrates</span></span>

<span data-ttu-id="e8425-108">此示例将演示如下。</span><span class="sxs-lookup"><span data-stu-id="e8425-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e8425-109">创建[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。</span><span class="sxs-lookup"><span data-stu-id="e8425-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e8425-110">添加到模块[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。</span><span class="sxs-lookup"><span data-stu-id="e8425-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e8425-111">创建[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)对象，它使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。</span><span class="sxs-lookup"><span data-stu-id="e8425-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e8425-112">创建[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)使用运行空间的对象。</span><span class="sxs-lookup"><span data-stu-id="e8425-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="e8425-113">将模块的 get proc cmdlet 添加到的管道[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="e8425-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e8425-114">以同步方式运行命令。</span><span class="sxs-lookup"><span data-stu-id="e8425-114">Running the command synchronously.</span></span>

- <span data-ttu-id="e8425-115">从属性中提取[System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)命令返回的对象。</span><span class="sxs-lookup"><span data-stu-id="e8425-115">Extracting properties from the [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="e8425-116">示例</span><span class="sxs-lookup"><span data-stu-id="e8425-116">Example</span></span>

<span data-ttu-id="e8425-117">此示例将创建使用的运行空间[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象定义的运行空间打开时可用的元素。</span><span class="sxs-lookup"><span data-stu-id="e8425-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="e8425-118">在此示例中，定义了一个 Get-proc cmdlet 的模块添加到初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="e8425-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

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

## <a name="see-also"></a><span data-ttu-id="e8425-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8425-119">See Also</span></span>

[<span data-ttu-id="e8425-120">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="e8425-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
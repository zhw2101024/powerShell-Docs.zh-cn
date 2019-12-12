---
title: 正在创建远程运行空间 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: c97b0dfc12d96f99c53383d3578579f1988efd52
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367676"
---
# <a name="creating-remote-runspaces"></a><span data-ttu-id="dee3e-102">创建远程运行空间</span><span class="sxs-lookup"><span data-stu-id="dee3e-102">Creating remote runspaces</span></span>

<span data-ttu-id="dee3e-103">采用**ComputerName**参数的 PowerShell 命令可以在任何运行 PowerShell 的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="dee3e-103">PowerShell commands that take a **ComputerName** parameter can be run on any computer that runs PowerShell.</span></span> <span data-ttu-id="dee3e-104">若要运行不带**ComputerName**参数的命令，你可以使用 ws-management 来配置连接到指定计算机的运行空间，并在该计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="dee3e-104">To run commands that don't take a **ComputerName** parameter, you can use WS-Management to configure a runspace that connects to a specified computer, and run commands on that computer.</span></span>

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a><span data-ttu-id="dee3e-105">使用 WSManConnection 创建远程运行空间</span><span class="sxs-lookup"><span data-stu-id="dee3e-105">Using a WSManConnection to create a remote runspace</span></span>

 <span data-ttu-id="dee3e-106">若要创建连接到远程计算机的运行空间，请创建一个[WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)对象。</span><span class="sxs-lookup"><span data-stu-id="dee3e-106">To create a runspace that connects to a remote computer, you create a [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span> <span data-ttu-id="dee3e-107">您可以通过设置对象的[WSManConnectionInfo. ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri)属性来指定连接的目标终结点。</span><span class="sxs-lookup"><span data-stu-id="dee3e-107">You specify the target endpoint for the connection by setting the [System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) property of the object.</span></span> <span data-ttu-id="dee3e-108">然后通过调用 [System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) 方法来创建一个运行空间，并将 [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 对象指定为 `connectionInfo` 参数.</span><span class="sxs-lookup"><span data-stu-id="dee3e-108">You then create a runspace by calling the [System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) method, specifying the [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object as the `connectionInfo` parameter.</span></span>

 <span data-ttu-id="dee3e-109">下面的示例演示如何创建连接到远程计算机的运行空间。</span><span class="sxs-lookup"><span data-stu-id="dee3e-109">The following example shows how to create a runspace that connects to a remote computer.</span></span> <span data-ttu-id="dee3e-110">在此示例中，`RemoteComputerUri` 用作远程计算机的实际 URI 的占位符。</span><span class="sxs-lookup"><span data-stu-id="dee3e-110">In the example, `RemoteComputerUri` is used as a placeholder for the actual URI of a remote computer.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // PowerShell namespace.
  using System.Management.Automation.Runspaces;  // PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      Uri RemoteComputerUri = new uri("http://Server01:5985/WSMAN");
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo(RemoteComputerUri);

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

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

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```

---
title: 创建受限运行空间 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 29f1be6a1215219ddd16367a31f528a4f0dbc2e3
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795114"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="f9840-102">创建受限运行空间</span><span class="sxs-lookup"><span data-stu-id="f9840-102">Creating a constrained runspace</span></span>

<span data-ttu-id="f9840-103">出于性能或安全原因，你可能想要限制对主机应用程序的可用的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="f9840-103">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="f9840-104">若要执行此操作创建一个空[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)通过调用[System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法，然后添加仅提供你所需要的命令。</span><span class="sxs-lookup"><span data-stu-id="f9840-104">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="f9840-105">使用加载指定的命令的运行空间提供了显著改进了的性能。</span><span class="sxs-lookup"><span data-stu-id="f9840-105">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="f9840-106">使用的方法[System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)类来定义初始会话状态的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f9840-106">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="f9840-107">您还可以使命令专用。</span><span class="sxs-lookup"><span data-stu-id="f9840-107">You can also make commands private.</span></span> <span data-ttu-id="f9840-108">主机应用程序，但不是通过应用程序的用户，可以使用专用命令。</span><span class="sxs-lookup"><span data-stu-id="f9840-108">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="f9840-109">将命令添加到空的运行空间</span><span class="sxs-lookup"><span data-stu-id="f9840-109">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="f9840-110">下面的示例演示如何创建空 InitialSessionState 并向其添加命令。</span><span class="sxs-lookup"><span data-stu-id="f9840-110">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a><span data-ttu-id="f9840-111">将命令为私有</span><span class="sxs-lookup"><span data-stu-id="f9840-111">Making commands private</span></span>

 <span data-ttu-id="f9840-112">此外可以使命令私有的通过将其设置的[System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility)属性设置为[System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private).</span><span class="sxs-lookup"><span data-stu-id="f9840-112">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private).</span></span> <span data-ttu-id="f9840-113">主机应用程序和其他命令可以调用该命令，但应用程序的用户不能。</span><span class="sxs-lookup"><span data-stu-id="f9840-113">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="f9840-114">在以下示例中， [Get-childitem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem)命令是私有的。</span><span class="sxs-lookup"><span data-stu-id="f9840-114">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="f9840-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9840-115">See Also</span></span>

 [<span data-ttu-id="f9840-116">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="f9840-116">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

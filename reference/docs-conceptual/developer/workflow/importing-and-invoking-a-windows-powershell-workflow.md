---
title: 导入和调用 Windows PowerShell 工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366036"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="5f36a-102">导入并调用 Windows PowerShell 工作流</span><span class="sxs-lookup"><span data-stu-id="5f36a-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="5f36a-103">Windows PowerShell 3 允许导入和调用打包为 Windows PowerShell 模块的工作流。</span><span class="sxs-lookup"><span data-stu-id="5f36a-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="5f36a-104">有关 Windows PowerShell 模块的信息，请参阅[编写 Windows Powershell 模块](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="5f36a-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="5f36a-105">[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)类用作服务器上的工作流对象的客户端代理。</span><span class="sxs-lookup"><span data-stu-id="5f36a-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="5f36a-106">下面的过程说明如何使用[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)对象来调用工作流。</span><span class="sxs-lookup"><span data-stu-id="5f36a-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="5f36a-107">创建 PSJobProxy 对象以在远程服务器上执行工作流命令。</span><span class="sxs-lookup"><span data-stu-id="5f36a-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="5f36a-108">创建一个[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)对象以创建与远程运行空间的连接。</span><span class="sxs-lookup"><span data-stu-id="5f36a-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="5f36a-109">将 Wsmanconnectioninfo 对象的 Shelluri \* 属性设置为 `Microsoft.PowerShell.Workflow` 以指定 Windows PowerShell 终结点的[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)对象的[\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri)属性。</span><span class="sxs-lookup"><span data-stu-id="5f36a-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="5f36a-110">创建一个运行空间，该运行空间使用通过完成前面的步骤创建的连接。</span><span class="sxs-lookup"><span data-stu-id="5f36a-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="5f36a-111">创建一个 "[管理](/dotnet/api/System.Management.Automation.PowerShell)" 对象，并将其 "[系统管理](/dotnet/api/System.Management.Automation.PowerShell.Runspace)版本" 属性设置为上一步中创建的运行空间。</span><span class="sxs-lookup"><span data-stu-id="5f36a-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="5f36a-112">将工作流模块及其命令导入到[系统管理层](/dotnet/api/System.Management.Automation.PowerShell)中。</span><span class="sxs-lookup"><span data-stu-id="5f36a-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="5f36a-113">创建[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)对象并使用它在远程服务器上执行工作流命令。</span><span class="sxs-lookup"><span data-stu-id="5f36a-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="5f36a-114">示例</span><span class="sxs-lookup"><span data-stu-id="5f36a-114">Example</span></span>

<span data-ttu-id="5f36a-115">下面的代码示例演示如何使用 Windows PowerShell 调用工作流。</span><span class="sxs-lookup"><span data-stu-id="5f36a-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="5f36a-116">此示例需要 Windows PowerShell 3。</span><span class="sxs-lookup"><span data-stu-id="5f36a-116">This example requires Windows PowerShell 3.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```
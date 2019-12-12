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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366036"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>导入并调用 Windows PowerShell 工作流

Windows PowerShell 3 允许导入和调用打包为 Windows PowerShell 模块的工作流。 有关 Windows PowerShell 模块的信息，请参阅[编写 Windows Powershell 模块](../module/writing-a-windows-powershell-module.md)。

[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)类用作服务器上的工作流对象的客户端代理。 下面的过程说明如何使用[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)对象来调用工作流。

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>创建 PSJobProxy 对象以在远程服务器上执行工作流命令。

1. 创建一个[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)对象以创建与远程运行空间的连接。

2. 若要 `Microsoft.PowerShell.Workflow`，请将[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)对象的[Shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri)属性设置为 ""，以指定 Windows PowerShell 终结点。

3. 创建一个运行空间，该运行空间使用通过完成前面的步骤创建的连接。

4. 创建一个 "[管理](/dotnet/api/System.Management.Automation.PowerShell)" 对象，并将其 "[系统管理](/dotnet/api/System.Management.Automation.PowerShell.Runspace)版本" 属性设置为上一步中创建的运行空间。

5. 将工作流模块及其命令导入到[系统管理层](/dotnet/api/System.Management.Automation.PowerShell)中。

6. 创建[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)对象并使用它在远程服务器上执行工作流命令。

## <a name="example"></a>示例

下面的代码示例演示如何使用 Windows PowerShell 调用工作流。

此示例需要 Windows PowerShell 3。

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
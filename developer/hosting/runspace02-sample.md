---
title: Runspace02 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082713"
---
# <a name="runspace02-sample"></a><span data-ttu-id="f9795-102">Runspace02 示例</span><span class="sxs-lookup"><span data-stu-id="f9795-102">Runspace02 Sample</span></span>

<span data-ttu-id="f9795-103">此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)并[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet 以同步方式。</span><span class="sxs-lookup"><span data-stu-id="f9795-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="f9795-104">[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 将返回[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象的每个进程在本地计算机上运行并`Sort-Object`基于对象进行排序其[System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id)属性。</span><span class="sxs-lookup"><span data-stu-id="f9795-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="f9795-105">使用显示的这些命令的结果[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控件。</span><span class="sxs-lookup"><span data-stu-id="f9795-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9795-106">要求</span><span class="sxs-lookup"><span data-stu-id="f9795-106">Requirements</span></span>

<span data-ttu-id="f9795-107">此示例要求 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="f9795-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f9795-108">演示</span><span class="sxs-lookup"><span data-stu-id="f9795-108">Demonstrates</span></span>

<span data-ttu-id="f9795-109">此示例将演示如下。</span><span class="sxs-lookup"><span data-stu-id="f9795-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="f9795-110">创建[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象运行命令。</span><span class="sxs-lookup"><span data-stu-id="f9795-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="f9795-111">将命令添加到的管道[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="f9795-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="f9795-112">以同步方式运行命令。</span><span class="sxs-lookup"><span data-stu-id="f9795-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="f9795-113">使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控件在 Windows 窗体应用程序中显示命令的输出。</span><span class="sxs-lookup"><span data-stu-id="f9795-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="f9795-114">示例</span><span class="sxs-lookup"><span data-stu-id="f9795-114">Example</span></span>

<span data-ttu-id="f9795-115">此示例运行时[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)并[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)同步中默认的运行空间提供的 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f9795-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="f9795-116">输出显示在窗体中使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控件。</span><span class="sxs-lookup"><span data-stu-id="f9795-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="f9795-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9795-117">See Also</span></span>

[<span data-ttu-id="f9795-118">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="f9795-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360976"
---
# <a name="runspace02-sample"></a><span data-ttu-id="3094c-102">Runspace02 示例</span><span class="sxs-lookup"><span data-stu-id="3094c-102">Runspace02 Sample</span></span>

<span data-ttu-id="3094c-103">此示例演示如何使用[system.exception 类来](/dotnet/api/system.management.automation.powershell)同步运行[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)和[排序对象](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3094c-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="3094c-104">[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 将为在本地计算机上运行的每个[进程返回 System.Diagnostics.Process.Id](/dotnet/api/System.Diagnostics.Process)对象，`Sort-Object` 并根据对象的[\*](/dotnet/api/System.Diagnostics.Process.Id)属性对对象进行排序。</span><span class="sxs-lookup"><span data-stu-id="3094c-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="3094c-105">这些命令的结果使用 " [system.web](/dotnet/api/System.Windows.Forms.DataGridView) " 控件显示。</span><span class="sxs-lookup"><span data-stu-id="3094c-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="3094c-106">要求</span><span class="sxs-lookup"><span data-stu-id="3094c-106">Requirements</span></span>

<span data-ttu-id="3094c-107">此示例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="3094c-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3094c-108">说明</span><span class="sxs-lookup"><span data-stu-id="3094c-108">Demonstrates</span></span>

<span data-ttu-id="3094c-109">此示例演示以下各项。</span><span class="sxs-lookup"><span data-stu-id="3094c-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3094c-110">创建要运行命令的[system.web](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="3094c-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="3094c-111">将命令添加到[system.web](/dotnet/api/system.management.automation.powershell)对象的管道。</span><span class="sxs-lookup"><span data-stu-id="3094c-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="3094c-112">同步运行命令。</span><span class="sxs-lookup"><span data-stu-id="3094c-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="3094c-113">使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控件在 Windows 窗体应用程序中显示命令的输出。</span><span class="sxs-lookup"><span data-stu-id="3094c-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="3094c-114">示例</span><span class="sxs-lookup"><span data-stu-id="3094c-114">Example</span></span>

<span data-ttu-id="3094c-115">此示例在 Windows PowerShell 提供的默认运行空间中同步运行[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)和[排序对象](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3094c-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="3094c-116">使用 " [system.web](/dotnet/api/System.Windows.Forms.DataGridView) " 控件以窗体显示输出。</span><span class="sxs-lookup"><span data-stu-id="3094c-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3094c-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3094c-117">See Also</span></span>

[<span data-ttu-id="3094c-118">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="3094c-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
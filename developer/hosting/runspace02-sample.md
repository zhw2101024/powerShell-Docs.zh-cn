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
# <a name="runspace02-sample"></a>Runspace02 示例

此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)并[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet 以同步方式。 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 将返回[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象的每个进程在本地计算机上运行并`Sort-Object`基于对象进行排序其[System.Diagnostics.Process.Id*](/dotnet/api/System.Diagnostics.Process.Id)属性。 使用显示的这些命令的结果[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控件。

## <a name="requirements"></a>要求

此示例要求 Windows PowerShell 2.0。

## <a name="demonstrates"></a>演示

此示例将演示如下。

- 创建[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象运行命令。

- 将命令添加到的管道[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。

- 以同步方式运行命令。

- 使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控件在 Windows 窗体应用程序中显示命令的输出。

## <a name="example"></a>示例

此示例运行时[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)并[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)同步中默认的运行空间提供的 Windows PowerShell cmdlet。 输出显示在窗体中使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控件。

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

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 主机应用程序](./writing-a-windows-powershell-host-application.md)
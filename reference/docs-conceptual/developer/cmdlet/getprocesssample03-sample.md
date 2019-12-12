---
title: GetProcessSample03 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369706"
---
# <a name="getprocesssample03-sample"></a>GetProcessSample03 示例

此示例演示如何实现一个用于检索本地计算机上的进程的 cmdlet。 它提供一个 `Name` 参数，该参数可接受来自管道的对象，或从对象的属性中接受值，该对象的属性名称与参数名称相同。 此 cmdlet 是 Windows PowerShell 2.0 提供的 `Get-Process` cmdlet 的简化版本。

## <a name="how-to-build-the-sample-using-visual-studio"></a>如何使用 Visual Studio 生成示例。

1. 安装 Windows PowerShell 2.0 SDK 后，导航到 GetProcessSample03 文件夹。 默认位置为 C:\Program Files （x86） \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03。

2. 双击解决方案（.sln）文件的图标。 这会在 Visual Studio 中打开示例项目。

3. 在“生成”菜单中选择“生成解决方案”。

    示例库将在默认的 \bin 或 \bin\debug 文件夹中生成。

### <a name="how-to-run-the-sample"></a>如何运行示例

1. 创建以下模块文件夹：

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. 将示例程序集复制到模块文件夹中。

3. 启动 Windows PowerShell。

4. 运行以下命令，将程序集加载到 Windows PowerShell：

    `Import-module getprossessample03`

5. 运行以下命令以运行 cmdlet：

    `get-proc`

## <a name="requirements"></a>要求

此示例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>说明

此示例演示以下各项。

- 使用 Cmdlet 特性声明 cmdlet 类。

- 使用参数属性声明 cmdlet 参数。

- 指定参数的位置。

- 指定参数从管道中获取输入。 输入可从对象或对象属性中的值获取，该对象的属性名称与参数名称相同。

- 声明参数输入的验证特性。

## <a name="example"></a>示例

此示例演示了获取处理器 cmdlet 的实现，该 cmdlet 包含接受来自管道的输入的 `Name` 参数。

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

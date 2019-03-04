---
title: GetProcessSample04 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861873"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04 示例

此示例演示如何实现用于检索本地计算机上的进程的 cmdlet。 如果在检索进程时发生错误，它会生成一个非终止错误。 此 cmdlet 是一个简化的版的`Get-Process`cmdlet 提供的 Windows PowerShell 2.0。

## <a name="how-to-build-the-sample-using-visual-studio"></a>如何使用 Visual Studio 生成示例。

1. 安装了 Windows PowerShell 2.0 sdk，导航到 GetProcessSample04 文件夹。 默认位置为 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04。

2. 双击解决方案 (.sln) 文件的图标。 这将在 Visual Studio 中打开示例项目。

3. 在中**构建**菜单中，选择**生成解决方案**。

    将默认 \bin 或 \bin\debug 文件夹中生成的示例库。

### <a name="how-to-run-the-sample"></a>如何运行示例

1. 创建以下模块文件夹：

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. 将示例程序集复制到模块文件夹中。

3. 启动 Windows PowerShell。

4. 运行以下命令以将该程序集加载到 Windows PowerShell:

    `Import-module getprossessample04`

5. 运行以下命令以运行该 cmdlet:

    `get-proc`

## <a name="requirements"></a>要求

此示例要求 Windows PowerShell 2.0。

## <a name="demonstrates"></a>说明

此示例将演示如下。

- 声明 cmdlet 类使用 Cmdlet 属性。

- 声明 cmdlet 参数使用参数属性。

- 指定参数的位置。

- 指定此参数采用输入管道中。 输入可以来自对象或从一个对象，其属性名称为参数名称相同的属性值。

- 声明为参数输入的验证属性。

- 捕获非终止错误和错误流中写入一条错误消息。

## <a name="example"></a>示例

此示例演示如何创建一个 cmdlet，用于处理非终止错误并将错误消息写入错误流。

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
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
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

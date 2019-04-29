---
title: GetProcessSample01 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068056"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01 示例

此示例演示如何实现用于检索本地计算机上的进程的 cmdlet。 此 cmdlet 是一个简化的版的`Get-Process`由 Windows PowerShell 2.0 提供的 cmdlet。

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>如何通过使用 Visual Studio 生成该示例。

1. 安装了 Windows PowerShell 2.0 sdk，导航到 GetProcessSample01 文件夹。 默认位置为 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01。

2. 双击解决方案 (.sln) 文件的图标。 这将在 Microsoft Visual Studio 中打开示例项目。

3. 在中**构建**菜单中，选择**生成解决方案**。

  将默认 \bin 或 \bin\debug 文件夹中生成的示例库。

### <a name="how-to-run-the-sample"></a>如何运行示例

1. 打开“命令提示符”窗口。

2. 导航到包含示例.dll 文件的目录。

3. 运行 installutil"GetProcessSample01.dll"。

4. 启动 Windows PowerShell。

5. 运行以下命令以将此管理单元添加到 shell。

   `Add-PSSnapin GetProcPSSnapIn01`

6. 输入以下命令以运行该 cmdlet。 `get-proc`

   `get-proc`

   这是执行以下步骤而得出的示例输出。

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>要求

此示例需要 Windows PowerShell 1.0 或更高版本。

## <a name="demonstrates"></a>演示

此示例将演示如下。

- 创建基本的示例 cmdlet。

- 使用 Cmdlet 属性定义 cmdlet 类。

- 创建适用于 Windows PowerShell 1.0 和 Windows PowerShell 2.0 管理单元。 后续示例而不是管理单元使用的模块，因此它们需要 Windows PowerShell 2.0。

## <a name="example"></a>示例

此示例演示如何创建简单的 cmdlet 和其管理单元中。

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
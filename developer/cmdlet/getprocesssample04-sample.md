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
# <a name="getprocesssample04-sample"></a><span data-ttu-id="da2fb-102">GetProcessSample04 示例</span><span class="sxs-lookup"><span data-stu-id="da2fb-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="da2fb-103">此示例演示如何实现用于检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="da2fb-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="da2fb-104">如果在检索进程时发生错误，它会生成一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="da2fb-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="da2fb-105">此 cmdlet 是一个简化的版的`Get-Process`cmdlet 提供的 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="da2fb-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="da2fb-106">如何使用 Visual Studio 生成示例。</span><span class="sxs-lookup"><span data-stu-id="da2fb-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="da2fb-107">安装了 Windows PowerShell 2.0 sdk，导航到 GetProcessSample04 文件夹。</span><span class="sxs-lookup"><span data-stu-id="da2fb-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="da2fb-108">默认位置为 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04。</span><span class="sxs-lookup"><span data-stu-id="da2fb-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="da2fb-109">双击解决方案 (.sln) 文件的图标。</span><span class="sxs-lookup"><span data-stu-id="da2fb-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="da2fb-110">这将在 Visual Studio 中打开示例项目。</span><span class="sxs-lookup"><span data-stu-id="da2fb-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="da2fb-111">在中**构建**菜单中，选择**生成解决方案**。</span><span class="sxs-lookup"><span data-stu-id="da2fb-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="da2fb-112">将默认 \bin 或 \bin\debug 文件夹中生成的示例库。</span><span class="sxs-lookup"><span data-stu-id="da2fb-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="da2fb-113">如何运行示例</span><span class="sxs-lookup"><span data-stu-id="da2fb-113">How to run the sample</span></span>

1. <span data-ttu-id="da2fb-114">创建以下模块文件夹：</span><span class="sxs-lookup"><span data-stu-id="da2fb-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="da2fb-115">将示例程序集复制到模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="da2fb-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="da2fb-116">启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="da2fb-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="da2fb-117">运行以下命令以将该程序集加载到 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da2fb-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="da2fb-118">运行以下命令以运行该 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="da2fb-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="da2fb-119">要求</span><span class="sxs-lookup"><span data-stu-id="da2fb-119">Requirements</span></span>

<span data-ttu-id="da2fb-120">此示例要求 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="da2fb-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="da2fb-121">说明</span><span class="sxs-lookup"><span data-stu-id="da2fb-121">Demonstrates</span></span>

<span data-ttu-id="da2fb-122">此示例将演示如下。</span><span class="sxs-lookup"><span data-stu-id="da2fb-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="da2fb-123">声明 cmdlet 类使用 Cmdlet 属性。</span><span class="sxs-lookup"><span data-stu-id="da2fb-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="da2fb-124">声明 cmdlet 参数使用参数属性。</span><span class="sxs-lookup"><span data-stu-id="da2fb-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="da2fb-125">指定参数的位置。</span><span class="sxs-lookup"><span data-stu-id="da2fb-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="da2fb-126">指定此参数采用输入管道中。</span><span class="sxs-lookup"><span data-stu-id="da2fb-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="da2fb-127">输入可以来自对象或从一个对象，其属性名称为参数名称相同的属性值。</span><span class="sxs-lookup"><span data-stu-id="da2fb-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="da2fb-128">声明为参数输入的验证属性。</span><span class="sxs-lookup"><span data-stu-id="da2fb-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="da2fb-129">捕获非终止错误和错误流中写入一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="da2fb-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="da2fb-130">示例</span><span class="sxs-lookup"><span data-stu-id="da2fb-130">Example</span></span>

<span data-ttu-id="da2fb-131">此示例演示如何创建一个 cmdlet，用于处理非终止错误并将错误消息写入错误流。</span><span class="sxs-lookup"><span data-stu-id="da2fb-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="da2fb-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da2fb-132">See Also</span></span>

[<span data-ttu-id="da2fb-133">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="da2fb-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

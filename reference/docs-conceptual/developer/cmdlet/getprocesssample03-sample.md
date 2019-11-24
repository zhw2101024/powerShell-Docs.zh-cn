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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369706"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="52932-102">GetProcessSample03 示例</span><span class="sxs-lookup"><span data-stu-id="52932-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="52932-103">此示例演示如何实现一个用于检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="52932-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="52932-104">它提供一个 `Name` 参数，该参数可接受来自管道的对象，或从对象的属性中接受值，该对象的属性名称与参数名称相同。</span><span class="sxs-lookup"><span data-stu-id="52932-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="52932-105">此 cmdlet 是 Windows PowerShell 2.0 提供的 `Get-Process` cmdlet 的简化版本。</span><span class="sxs-lookup"><span data-stu-id="52932-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="52932-106">如何使用 Visual Studio 生成示例。</span><span class="sxs-lookup"><span data-stu-id="52932-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="52932-107">安装 Windows PowerShell 2.0 SDK 后，导航到 GetProcessSample03 文件夹。</span><span class="sxs-lookup"><span data-stu-id="52932-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="52932-108">默认位置为 C:\Program Files （x86） \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03。</span><span class="sxs-lookup"><span data-stu-id="52932-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="52932-109">双击解决方案（.sln）文件的图标。</span><span class="sxs-lookup"><span data-stu-id="52932-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="52932-110">这会在 Visual Studio 中打开示例项目。</span><span class="sxs-lookup"><span data-stu-id="52932-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="52932-111">在 "**生成**" 菜单中，选择 "**生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="52932-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="52932-112">示例库将在默认的 \bin 或 \bin\debug 文件夹中生成。</span><span class="sxs-lookup"><span data-stu-id="52932-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="52932-113">如何运行示例</span><span class="sxs-lookup"><span data-stu-id="52932-113">How to run the sample</span></span>

1. <span data-ttu-id="52932-114">创建以下模块文件夹：</span><span class="sxs-lookup"><span data-stu-id="52932-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="52932-115">将示例程序集复制到模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="52932-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="52932-116">启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="52932-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="52932-117">运行以下命令，将程序集加载到 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="52932-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="52932-118">运行以下命令以运行 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="52932-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="52932-119">要求</span><span class="sxs-lookup"><span data-stu-id="52932-119">Requirements</span></span>

<span data-ttu-id="52932-120">此示例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="52932-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="52932-121">示例</span><span class="sxs-lookup"><span data-stu-id="52932-121">Demonstrates</span></span>

<span data-ttu-id="52932-122">此示例演示以下各项。</span><span class="sxs-lookup"><span data-stu-id="52932-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="52932-123">使用 Cmdlet 特性声明 cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="52932-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="52932-124">使用参数属性声明 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="52932-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="52932-125">指定参数的位置。</span><span class="sxs-lookup"><span data-stu-id="52932-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="52932-126">指定参数从管道中获取输入。</span><span class="sxs-lookup"><span data-stu-id="52932-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="52932-127">输入可从对象或对象属性中的值获取，该对象的属性名称与参数名称相同。</span><span class="sxs-lookup"><span data-stu-id="52932-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="52932-128">声明参数输入的验证特性。</span><span class="sxs-lookup"><span data-stu-id="52932-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="52932-129">示例</span><span class="sxs-lookup"><span data-stu-id="52932-129">Example</span></span>

<span data-ttu-id="52932-130">此示例演示了获取处理器 cmdlet 的实现，该 cmdlet 包含接受来自管道的输入的 `Name` 参数。</span><span class="sxs-lookup"><span data-stu-id="52932-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="52932-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52932-131">See Also</span></span>

[<span data-ttu-id="52932-132">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="52932-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

---
title: GetProcessSample02 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364566"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="c426b-102">GetProcessSample02 示例</span><span class="sxs-lookup"><span data-stu-id="c426b-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="c426b-103">此示例演示如何编写一个用于检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c426b-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="c426b-104">它提供了一个 `Name` 参数，该参数可用于指定要检索的进程。</span><span class="sxs-lookup"><span data-stu-id="c426b-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="c426b-105">此 cmdlet 是 Windows PowerShell 2.0 提供的 `Get-Process` cmdlet 的简化版本。</span><span class="sxs-lookup"><span data-stu-id="c426b-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="c426b-106">如何使用 Visual Studio 生成示例。</span><span class="sxs-lookup"><span data-stu-id="c426b-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="c426b-107">安装 Windows PowerShell 2.0 SDK 后，导航到 GetProcessSample02 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c426b-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="c426b-108">默认位置为 C:\Program Files （x86） \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02。</span><span class="sxs-lookup"><span data-stu-id="c426b-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="c426b-109">双击解决方案（.sln）文件的图标。</span><span class="sxs-lookup"><span data-stu-id="c426b-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="c426b-110">这会在 Visual Studio 中打开示例项目。</span><span class="sxs-lookup"><span data-stu-id="c426b-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="c426b-111">在“生成”菜单中选择“生成解决方案”。</span><span class="sxs-lookup"><span data-stu-id="c426b-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="c426b-112">示例库将在默认的 \bin 或 \bin\debug 文件夹中生成。</span><span class="sxs-lookup"><span data-stu-id="c426b-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="c426b-113">如何运行示例</span><span class="sxs-lookup"><span data-stu-id="c426b-113">How to run the sample</span></span>

1. <span data-ttu-id="c426b-114">创建以下模块文件夹：</span><span class="sxs-lookup"><span data-stu-id="c426b-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="c426b-115">将示例程序集复制到模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c426b-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="c426b-116">启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c426b-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="c426b-117">运行以下命令，将程序集加载到 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="c426b-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="c426b-118">运行以下命令以运行 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="c426b-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="c426b-119">要求</span><span class="sxs-lookup"><span data-stu-id="c426b-119">Requirements</span></span>

<span data-ttu-id="c426b-120">此示例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="c426b-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c426b-121">说明</span><span class="sxs-lookup"><span data-stu-id="c426b-121">Demonstrates</span></span>

<span data-ttu-id="c426b-122">此示例演示以下各项。</span><span class="sxs-lookup"><span data-stu-id="c426b-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="c426b-123">使用 Cmdlet 特性声明 cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="c426b-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="c426b-124">使用参数属性声明 cmdlet 参数。</span><span class="sxs-lookup"><span data-stu-id="c426b-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="c426b-125">指定参数的位置。</span><span class="sxs-lookup"><span data-stu-id="c426b-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="c426b-126">声明参数输入的验证特性。</span><span class="sxs-lookup"><span data-stu-id="c426b-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="c426b-127">示例</span><span class="sxs-lookup"><span data-stu-id="c426b-127">Example</span></span>

<span data-ttu-id="c426b-128">此示例演示包含 `Name` 参数的进程中 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="c426b-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

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
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
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
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="c426b-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c426b-129">See Also</span></span>

[<span data-ttu-id="c426b-130">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c426b-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

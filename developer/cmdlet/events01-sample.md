---
title: Events01 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: c9963819f1842d1245735dabc487babaa566c160
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068124"
---
# <a name="events01-sample"></a><span data-ttu-id="d07d0-102">Events01 示例</span><span class="sxs-lookup"><span data-stu-id="d07d0-102">Events01 Sample</span></span>

<span data-ttu-id="d07d0-103">此示例演示如何创建由引发的事件，则允许用户注册一个 cmdlet [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)。</span><span class="sxs-lookup"><span data-stu-id="d07d0-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="d07d0-104">此 cmdlet，用户可以注册在特定目录下创建一个文件时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="d07d0-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="d07d0-105">此示例从派生[Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基类。</span><span class="sxs-lookup"><span data-stu-id="d07d0-105">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="d07d0-106">如何通过使用 Visual Studio 生成该示例。</span><span class="sxs-lookup"><span data-stu-id="d07d0-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="d07d0-107">安装了 Windows PowerShell 2.0 sdk，导航到 Events01 文件夹。</span><span class="sxs-lookup"><span data-stu-id="d07d0-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="d07d0-108">默认位置为 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01。</span><span class="sxs-lookup"><span data-stu-id="d07d0-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="d07d0-109">双击解决方案 (.sln) 文件的图标。</span><span class="sxs-lookup"><span data-stu-id="d07d0-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="d07d0-110">这将在 Microsoft Visual Studio 中打开示例项目。</span><span class="sxs-lookup"><span data-stu-id="d07d0-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="d07d0-111">在中**构建**菜单中，选择**生成解决方案**。</span><span class="sxs-lookup"><span data-stu-id="d07d0-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="d07d0-112">将默认 \bin 或 \bin\debug 文件夹中生成的示例库。</span><span class="sxs-lookup"><span data-stu-id="d07d0-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="d07d0-113">如何运行示例</span><span class="sxs-lookup"><span data-stu-id="d07d0-113">How to run the sample</span></span>

1. <span data-ttu-id="d07d0-114">创建以下模块文件夹：</span><span class="sxs-lookup"><span data-stu-id="d07d0-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="d07d0-115">将该示例的库文件复制到模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d07d0-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="d07d0-116">启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d07d0-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="d07d0-117">运行以下命令将加载到 Windows PowerShell cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d07d0-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="d07d0-118">使用注册 FileSystemEvent cmdlet 注册时在 TEMP 目录下创建一个文件将写入一条消息的操作。</span><span class="sxs-lookup"><span data-stu-id="d07d0-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="d07d0-119">TEMP 目录下创建一个文件并记下执行此操作 （消息已显示）。</span><span class="sxs-lookup"><span data-stu-id="d07d0-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="d07d0-120">这是通过执行以下步骤生成的示例输出。</span><span class="sxs-lookup"><span data-stu-id="d07d0-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="d07d0-121">要求</span><span class="sxs-lookup"><span data-stu-id="d07d0-121">Requirements</span></span>

<span data-ttu-id="d07d0-122">此示例要求 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="d07d0-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d07d0-123">演示</span><span class="sxs-lookup"><span data-stu-id="d07d0-123">Demonstrates</span></span>

<span data-ttu-id="d07d0-124">此示例将演示如下。</span><span class="sxs-lookup"><span data-stu-id="d07d0-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="d07d0-125">如何编写事件注册的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d07d0-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="d07d0-126">该 cmdlet 派生[Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)类，该类提供支持公共参数的寄存器-\* 事件 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d07d0-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="d07d0-127">派生自的 Cmdlet [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)只需定义其特定的参数，并覆盖`GetSourceObject`和`GetSourceObjectEventName`抽象方法。</span><span class="sxs-lookup"><span data-stu-id="d07d0-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="d07d0-128">示例</span><span class="sxs-lookup"><span data-stu-id="d07d0-128">Example</span></span>

<span data-ttu-id="d07d0-129">此示例演示如何引发的事件注册[System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="d07d0-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d07d0-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d07d0-130">See Also</span></span>

[<span data-ttu-id="d07d0-131">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d07d0-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
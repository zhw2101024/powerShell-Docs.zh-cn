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
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229304"
---
# <a name="events01-sample"></a>Events01 示例

此示例演示如何创建由引发的事件，则允许用户注册一个 cmdlet [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)。
此 cmdlet，用户可以注册在特定目录下创建一个文件时要执行的操作。
此示例从派生[Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基类。

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>如何通过使用 Visual Studio 生成该示例。

1. 安装了 Windows PowerShell 2.0 sdk，导航到 Events01 文件夹。
   默认位置是`C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`。

2. 双击解决方案 (.sln) 文件的图标。
   这将在 Microsoft Visual Studio 中打开示例项目。

3. 在中**构建**菜单中，选择**生成解决方案**。
   将默认值中生成的示例库`\bin`或`\bin\debug`文件夹。

### <a name="how-to-run-the-sample"></a>如何运行示例

1. 创建以下模块文件夹：

    `[user]/documents/windowspowershell/modules/events01`

2. 将该示例的库文件复制到模块文件夹中。

3. 启动 Windows PowerShell。

4. 运行以下命令将加载到 Windows PowerShell cmdlet:

    ```powershell
    import-module events01
    ```

5. 使用注册 FileSystemEvent cmdlet 注册时在 TEMP 目录下创建一个文件将写入一条消息的操作。

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. TEMP 目录下创建一个文件并记下执行此操作 （消息已显示）。

这是通过执行以下步骤生成的示例输出。

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

此示例要求 Windows PowerShell 2.0。

## <a name="demonstrates"></a>演示

此示例将演示如下。

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>如何编写事件注册 cmdlet

该 cmdlet 派生[Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)类，该类提供通用的参数的支持`Register-*Event`cmdlet。
派生自的 Cmdlet [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)只需定义其特定的参数，并覆盖`GetSourceObject`和`GetSourceObjectEventName`抽象方法。

## <a name="example"></a>示例

此示例演示如何引发的事件注册[System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)。

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

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)
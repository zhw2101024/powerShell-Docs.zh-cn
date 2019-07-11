---
title: Windows PowerShell 提供程序快速入门 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734842"
---
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell 提供程序快速入门

本主题说明如何创建具有基本功能，创建一个新的驱动器的 Windows PowerShell 提供程序。 有关提供程序的常规信息，请参阅[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)。 有关更完整的功能的提供程序的示例，请参阅[提供程序示例](./provider-samples.md)。

## <a name="writing-a-basic-provider"></a>编写基本提供程序

Windows PowerShell 提供程序的最基本功能是创建和删除驱动器。 在此示例中，我们实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)并[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类。 您还将了解如何以声明提供程序类。

当您编写一个提供程序时，可以指定默认驱动器驱动器提供程序可用时自动创建的。 您还可以定义用于创建使用该提供程序的新驱动器的方法。

本主题中提供的示例基于[AccessDBProviderSample02](./accessdbprovidersample02.md)示例中，它是表示为 Windows PowerShell 驱动器的访问数据库的更大示例的一部分。

### <a name="setting-up-the-project"></a>设置项目

在 Visual Studio 中，创建一个名为 AccessDBProviderSample 的类库项目。 完成以下步骤以配置你的项目，以便将启动 Windows PowerShell，并且该提供程序将加载到会话中，当生成并启动你的项目。

##### <a name="configure-the-provider-project"></a>配置提供程序项目

1. 将 System.Management.Automation 程序集添加为对你的项目的引用。

2. 单击**项目 > AccessDBProviderSample 属性 > 调试**。 在中**入门项目**，单击**启动外部程序**，并导航到 Windows PowerShell 可执行文件 (通常是 c:\Windows\System32\WindowsPowerShell\v1.0\\。 powershell.exe)。

3. 下**启动选项**，输入到以下**命令行参数**框： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>声明提供程序类

我们的提供程序派生[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类。 提供真正的功能 （访问和操作项、 导航数据存储区，并获取和设置的项的内容） 的大多数提供程序派生[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。

除了指定的类派生[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)，必须给它装饰[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)示例中所示。

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>实现 NewDrive

[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)由 Windows PowerShell 引擎调用方法，当用户调用[Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet 并指定您的提供程序的名称。 PSDriveInfo 参数传递由 Windows PowerShell 引擎中，并且该方法返回到 Windows PowerShell 引擎的新驱动器。 此方法必须在上面创建的类内部声明。

该方法首先检查以确保该驱动器对象和驱动器根目录中传递存在，返回`null`如果其中任何一个不匹配。 它然后使用 AccessDBPSDriveInfo 的内部类的构造函数来创建一个新的驱动器，连接到 Access 数据库驱动器表示。

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

下面是包括构造函数用于创建新的驱动器，并包含驱动器的状态信息的 AccessDBPSDriveInfo 内部类。

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>实现 RemoveDrive

[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)由 Windows PowerShell 引擎调用方法，当用户调用[Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet。 此提供程序中的方法关闭到 Access 数据库的连接。

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```
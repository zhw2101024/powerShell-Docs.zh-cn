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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359916"
---
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell 提供程序快速入门

本主题说明如何创建具有创建新驱动器的基本功能的 Windows PowerShell 提供程序。 有关提供程序的一般信息，请参阅[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)。 有关具有更完整功能的提供程序的示例，请参阅[提供程序示例](./provider-samples.md)。

## <a name="writing-a-basic-provider"></a>编写基本提供程序

Windows PowerShell 提供程序的最基本功能是创建和删除驱动器。 在此示例中，我们实现了的[Drivecmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，该[方法"Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) " 类。 你还将了解如何声明提供程序类。

当你编写提供程序时，可以指定默认驱动器-在提供程序可用时自动创建的驱动器。 还定义了一个方法来创建使用该提供程序的新驱动器。

本主题中提供的示例基于[AccessDBProviderSample02](./accessdbprovidersample02.md)示例，该示例是将 Access 数据库表示为 Windows PowerShell 驱动器的更大示例的一部分。

### <a name="setting-up-the-project"></a>设置项目

在 Visual Studio 中，创建一个名为 AccessDBProviderSample 的类库项目。 完成以下步骤以配置你的项目，以便在生成和启动项目时，将启动 Windows PowerShell 并将该提供程序加载到会话中。

##### <a name="configure-the-provider-project"></a>配置提供程序项目

1. 添加 System.web 程序集作为对项目的引用。

2. 单击 "**项目 > AccessDBProviderSample Properties > 调试**"。 在 "**启动项目**" 中，单击 "**启动外部程序**"，并导航到 Windows PowerShell 可执行文件（通常为 c:\Windows\System32\WindowsPowerShell\v1.0 \\）。

3. 在 "**启动选项**" 下的 "**命令行参数**" 框中输入以下内容： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>声明提供程序类

我们的提供程序派生自[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类。 大多数提供实际功能的提供程序（访问和操作项、导航数据存储区以及获取和设置项的内容）都派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。

除了指定类派生自 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 外，还必须将其与 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 示例中所示的进行修饰，如示例中所示。

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

当用户调用 Drivecmdletprovider cmdlet 时，Windows PowerShell 引擎会调用[Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，该方法用于指定你的用户的名称[。 NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet程序. 即 system.management.automation.psdriveinfo 参数由 Windows PowerShell 引擎传递，方法会将新驱动器返回给 Windows PowerShell 引擎。 此方法必须在上面创建的类中声明。

此方法首先检查以确保传入的驱动器对象和驱动器根都存在，如果不存在，则返回 `null`。 然后，它使用内部类 AccessDBPSDriveInfo 的构造函数来创建新的驱动器以及与该驱动器表示的 Access 数据库的连接。

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

下面是 AccessDBPSDriveInfo 内部类，其中包含用于创建新驱动器的构造函数，并包含驱动器的状态信息。

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

当用户调用[RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet 时，Windows PowerShell 引擎将调用[Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，这是由 Windows PowerShell 引擎调用的。 此提供程序中的方法关闭了到 Access 数据库的连接。

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
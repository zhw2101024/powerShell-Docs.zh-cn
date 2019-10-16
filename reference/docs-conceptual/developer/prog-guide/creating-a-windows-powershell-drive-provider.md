---
title: 创建 Windows PowerShell 驱动器提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366826"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>创建 Windows PowerShell 驱动器提供程序

本主题介绍如何创建 Windows PowerShell 驱动器提供程序，该提供程序通过 Windows PowerShell 驱动器提供访问数据存储区的方式。 这种类型的提供程序也称为 Windows PowerShell 驱动器提供程序。 提供程序使用的 Windows PowerShell 驱动器提供连接到数据存储的方法。

此处所述的 Windows PowerShell 驱动器提供程序提供对 Microsoft Access 数据库的访问权限。 对于此提供程序，Windows PowerShell 驱动器表示数据库（可以向驱动器提供程序添加任意数量的驱动器），驱动器的顶层容器表示数据库中的表，而容器中的项表示表。

## <a name="defining-the-windows-powershell-provider-class"></a>定义 Windows PowerShell 提供程序类

你的驱动器提供程序必须定义一个从[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类派生的 .net 类。 下面是此驱动器提供程序的类定义：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

请注意，在此示例中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性指定提供程序的用户友好名称，以及提供程序向 windows 公开的 windows PowerShell 特定功能PowerShell 运行时在命令处理过程中。 提供程序功能的可能值是由[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举定义的。 此驱动器提供程序不支持其中任何一种功能。

## <a name="defining-base-functionality"></a>定义基本功能

如[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)中所述， [Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类派生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类，该基类可实现。定义初始化和取消初始化提供程序所需的方法。 若要实现添加特定于会话的初始化信息以及释放提供程序所用资源的功能，请参阅[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。 但是，大多数提供程序（包括此处所述的提供程序）可以使用 Windows PowerShell 提供的此功能的默认实现。

## <a name="creating-drive-state-information"></a>正在创建驱动器状态信息

所有 Windows PowerShell 提供程序都被视为无状态，这意味着驱动器提供程序需要创建 Windows PowerShell 运行时在调用提供程序时所需的任何状态信息。

对于此驱动器提供程序，状态信息包括与数据库的连接，并将其保存为驱动器信息的一部分。 下面的代码演示如何将此信息存储在描述驱动器的[即 system.management.automation.psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)对象中：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>创建驱动器

若要允许 Windows PowerShell 运行时创建驱动器，驱动器提供程序必须实现[Drivecmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法。 下面的代码演示了此驱动器提供程序的[Drivecmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法的实现：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

重写此方法应执行以下操作：

- 验证[即 system.management.automation.psdriveinfo *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root)成员是否存在，以及是否可以建立与数据存储区的连接。

- 创建一个驱动器并填充该连接成员，以支持 @no__t 的 cmdlet。

- 验证建议的驱动器的[即 system.management.automation.psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)对象。

- 修改使用任何所需性能或可靠性信息描述驱动器的[即 system.management.automation.psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)对象，或使用驱动器为调用方提供额外的数据。

- 使用[Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法处理故障，然后返回 `null`。

  此方法返回传递给方法的驱动器信息或其特定于提供程序的版本。

## <a name="attaching-dynamic-parameters-to-newdrive"></a>将动态参数附加到 NewDrive

驱动器提供商支持的 @no__t 0 cmdlet 可能需要其他参数。 若要将这些动态参数附加到 cmdlet，提供程序将实现[Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。 此方法返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。

此驱动器提供程序不重写此方法。 但是，以下代码显示了此方法的默认实现：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>删除驱动器

若要关闭数据库连接，驱动器提供程序必须实现[Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。 此方法在清理任何提供程序特定的信息后关闭到驱动器的连接。

下面的代码演示了此驱动器提供程序的[Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法的实现：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

如果可以删除驱动器，方法应返回通过 @no__t 参数传递给方法的信息。 如果无法删除驱动器，方法应写入异常，然后返回 `null`。 如果提供程序未重写此方法，则此方法的默认实现只返回作为输入传递的驱动器信息。

## <a name="initializing-default-drives"></a>正在初始化默认驱动器

驱动器提供程序实现了[Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法来装入驱动器。 例如，如果计算机加入到域中，Active Directory 提供程序可能会为默认命名上下文装载驱动器。

此方法返回有关已初始化驱动器的驱动器信息的集合，或空集合。 对此方法的调用是在 Windows PowerShell 运行时调用[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以初始化提供程序后进行的。

此驱动器提供程序不重写[Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法。 但是，以下代码演示了返回空驱动器集合的默认实现：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>有关实现 InitializeDefaultDrives 的注意事项

所有驱动器提供商都应装载根驱动器，以帮助用户发现。 根驱动器可能会列出用作其他已装入驱动器的根的位置。 例如，Active Directory 提供程序可能会创建一个驱动器，其中列出了根分布式系统环境（DSE）上 `namingContext` 属性中的命名上下文。 这有助于用户发现其他驱动器的装入点。

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample02 代码示例](./accessdbprovidersample02-code-sample.md)。

## <a name="testing-the-windows-powershell-drive-provider"></a>测试 Windows PowerShell 驱动器提供程序

向 Windows powershell 注册 Windows PowerShell 提供程序后，可以通过在命令行上运行支持的 cmdlet （包括派生提供的任何 cmdlet）来测试 Windows PowerShell 提供程序。 让我们测试示例驱动器提供程序。

1. 运行 @no__t cmdlet 以检索提供程序列表，以确保存在 AccessDB 驱动器提供程序：

   **PS > `Get-PSProvider`**

   将显示以下输出：

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. 通过访问操作系统的 "**管理工具**" 的 "**数据源**" 部分，确保数据库的数据库服务器名称（DSN）存在。 在 "**用户 DSN** " 表中，双击 " **MS Access 数据库**" 并添加驱动器路径 C:\ps\northwind.mdb。

3. 使用示例驱动器提供程序创建新驱动器：

   **PS > new-psdrive-name mydb-root c:\ps\northwind.mdb-psprovider AccessDb**

   将显示以下输出：

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. 验证连接。 由于连接被定义为驱动器的成员，因此你可以使用 PDDrive cmdlet 检查它。

   > [!NOTE]
   > 用户仍无法作为驱动器与提供程序交互，因为提供程序需要容器功能才能进行该交互。 有关详细信息，请参阅[创建 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。

   **PS > （new-psdrive mydb）。连接**

   将显示以下输出：

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. 删除驱动器并退出 shell：

   **PS > new-psdrive mydb**

   **PS > 退出**

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)

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
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055642"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>创建 Windows PowerShell 驱动器提供程序

本主题介绍如何创建可用于通过 Windows PowerShell 驱动器访问数据存储区的 Windows PowerShell 驱动器提供程序。 这种类型的提供程序也称为 Windows PowerShell 驱动器提供程序。 提供程序使用的 Windows PowerShell 驱动器提供了用来连接到数据存储。

此处所述的 Windows PowerShell 驱动器提供程序提供对 Microsoft Access 数据库的访问。 为此提供程序，Windows PowerShell 驱动器表示 （它是可以将任意数量的驱动器添加到驱动器提供程序） 的数据库，该驱动器的顶级容器表示在数据库中，表和容器的项表示中的行表中。

下面是此主题中的部分列表。 如果您不熟悉编写 Windows PowerShell 驱动器提供程序，阅读这些部分中显示的顺序。 但是，如果你熟悉编写驱动器提供程序，请直接转到所需的信息。

- [定义 Windows PowerShell 提供程序类](#Defining-the-Windows-PowerShell-Provider-Class)

- [定义基本功能](#Defining-Base-Functionality)

- [创建驱动器状态信息](#Creating-Drive-State-Information)

- [创建驱动器](#Creating-a-Drive)

- [将动态参数附加到 NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [移除驱动器](#Removing-a-Drive)

- [初始化默认驱动器](#Initializing-Default-Drives)

- [代码示例](#Code-Sample)

- [测试 Windows PowerShell 驱动器提供程序](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>定义 Windows PowerShell 提供程序类

驱动器提供程序必须定义一个.NET 类，派生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。 下面是此驱动器提供程序的类定义：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

请注意，在此示例中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性指定的提供程序和 Windows PowerShell 的特定功能的用户友好名称的提供程序在命令处理过程公开为 Windows PowerShell 运行时。 定义提供程序功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 此驱动器提供程序不支持任何这些功能。

## <a name="defining-base-functionality"></a>定义基本功能

如中所述[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类派生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类定义所需的初始化和取消初始化访问接口的方法。 若要实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能，请参阅[创建一个基本的 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。 但是，大多数提供程序 （包括此处所述的提供程序） 可以使用 Windows PowerShell 提供此功能的默认实现。

## <a name="creating-drive-state-information"></a>创建驱动器状态信息

所有 Windows PowerShell 提供程序被都视为无状态的这意味着您的驱动器提供程序，需要创建时它将调用您的提供程序通过 Windows PowerShell 运行时所需的任何状态信息。

对于此驱动器提供程序中，状态信息包括作为驱动器信息的一部分保留数据库的连接。 下面是代码显示如何将此信息存储在[即 System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)对象，描述驱动器：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>创建驱动器

若要允许 Windows PowerShell 运行时创建的驱动器，驱动器提供程序必须实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法。 下面的代码演示如何实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)此驱动器提供程序的方法：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

重写此方法应执行以下操作：

- 确认[System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root)成员存在，并且可进行数据存储区的连接。

- 创建驱动器，并填充连接成员支持`New-PSDrive`cmdlet。

- 验证[即 System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)建议驱动器的对象。

- 修改[即 System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)对象，它描述与任何所需的性能或可靠性信息的驱动器或调用方使用驱动器提供额外的数据。

- 处理使用的故障[System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，然后返回`null`。

  此方法返回的驱动器信息传递到方法或它的特定于提供程序的版本。

## <a name="attaching-dynamic-parameters-to-newdrive"></a>将动态参数附加到 NewDrive

`New-PSDrive`驱动器提供程序支持的 cmdlet 可能需要附加参数。 若要将这些动态参数附加到该 cmdlet，该提供程序实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。 此方法返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。

此驱动器提供程序不重写此方法。 但是，下面的代码演示此方法的默认实现：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>移除驱动器

若要关闭数据库连接后，驱动器提供程序必须实现[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。 此方法关闭连接到的驱动器后清理的任何特定于提供程序的信息。

下面的代码演示如何实现[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)此驱动器提供程序的方法：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

如果可以移除驱动器，该方法应返回的信息传递给该方法通过`drive`参数。 如果不能移除驱动器，该方法应编写异常，然后返回`null`。 如果您的提供程序不重写此方法，此方法的默认实现只返回作为输入传递的驱动器信息。

## <a name="initializing-default-drives"></a>初始化默认驱动器

你的驱动器提供程序实现[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法以装入驱动器。 例如，Active Directory 提供程序可能会装载驱动器默认情况下，如果将计算机加入到域命名上下文。

此方法返回有关初始化的驱动器，驱动器信息的集合或一个空集合。 对此方法的调用后 Windows PowerShell 运行时调用进行[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以初始化访问接口。

此驱动器提供程序不会覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法。 但是，以下代码显示了默认实现，它将返回一个空驱动器集合：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>要实现 InitializeDefaultDrives 记住的事项

所有驱动器提供程序应将都装载为根驱动器，以帮助用户使用可发现性。 根驱动器可能还会列出作为其他已装载的驱动器的根位置。 例如，Active Directory 提供程序可以创建列出了命名上下文中找到的驱动器`namingContext`根分布式系统环境 (DSE) 上的属性。 这有助于用户发现的其他驱动器装入点。

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample02 代码示例](./accessdbprovidersample02-code-sample.md)。

## <a name="testing-the-windows-powershell-drive-provider"></a>测试 Windows PowerShell 驱动器提供程序

Windows PowerShell 提供程序具有已注册到 Windows PowerShell，可以通过运行命令行，其中包括可供派生的任何 cmdlet 上受支持的 cmdlet 来测试它。 让我们测试示例驱动器提供程序。

1. 运行`Get-PSProvider`cmdlet 来检索提供程序以确保存在 AccessDB 驱动器提供程序的列表：

   **PS> `Get-PSProvider`**

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

2. 请确保存在用于数据库的数据库服务器名称 (DSN) 通过访问**数据源**一部分**管理工具**的操作系统。 在中**用户 DSN**表中，双击**MS Access 数据库**并添加 C:\ps\northwind.mdb 的驱动器路径。

3. 创建新的驱动器使用示例驱动器提供程序：

   **PS > 新 psdrive-名称 mydb-根 c:\ps\northwind.mdb psprovider AccessDb**

   将显示以下输出：

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. 验证的连接。 因为连接被定义为驱动器的成员，可以检查其使用 Get PDDrive cmdlet。

   > [!NOTE]
   > 随着该提供程序需要为此交互的容器功能，用户不能与提供程序作为一个驱动器，尚未进行交互。 有关详细信息，请参阅[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。

   **PS > (get psdrive mydb).connection**

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

5. 移除驱动器并退出 shell:

   **PS > 删除 psdrive mydb**

   **PS > 退出**

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)
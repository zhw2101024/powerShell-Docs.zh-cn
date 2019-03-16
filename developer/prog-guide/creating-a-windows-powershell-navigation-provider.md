---
title: 创建 Windows PowerShell 导航提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055064"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>创建 Windows PowerShell 导航提供程序

本主题介绍如何创建可以浏览数据存储区的 Windows PowerShell 导航提供程序。 这种类型的提供程序支持递归命令、 嵌套的容器和相对路径。

> [!NOTE]
> 您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider05.cs)。 有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下载的源文件中有 **\<PowerShell 示例 >** 目录。
>
> 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。

此处所述的提供程序使用户句柄 Access 数据库作为驱动器，从而使用户可以导航到数据库中数据的表。 在创建自己的导航提供程序，可以实现方法，可使驱动器限定路径所需的导航、 规范化的相对路径，移动项的数据存储，以及获取子名称、 获取项的父路径和测试的方法若要确定某个项是一个容器中。

> [!CAUTION]
> 请注意，此设计假定具有名为 id，字段的数据库字段的类型是 LongInteger。

以下列表包含本主题中的部分。 如果您不熟悉编写 Windows PowerShell 导航提供程序，读取此信息显示的顺序。 但是，如果你熟悉编写 Windows PowerShell 导航提供程序，请直接转到所需的信息。

- [定义 PS 导航提供程序类](#Define-the-Windows-PowerShell-provider)

- [定义基本功能](#Defining-Base-Functionality)

- [创建 PS 路径](#Creating-a-Windows-PowerShell-Path)

- [检索父路径](#Retrieving-the-Parent-Path)

- [检索子路径名称](#Retrieve-the-Child-Path-Name)

- [确定某个项是否容器](#Determining-if-an-Item-is-a-Container)

- [将项移](#Moving-an-Item)

- [附加到的动态参数`Move-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [规范化的相对路径](#Normalizing-a-Relative-Path)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置](#Defining-Object-Types-and-Formatting)

- [生成 Windows PowerShell 提供程序](#Building-the-Windows-PowerShell-provider)

- [测试 Windows PowerShell 提供程序](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>定义 Windows PowerShell 提供程序

Windows PowerShell 导航提供程序必须创建一个.NET 类派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类。 下面是在本部分中所述的导航提供程序的类定义。

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

请注意，在此提供程序[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包含两个参数。 第一个参数指定由 Windows PowerShell 提供程序的用户友好名称。 第二个参数指定的 Windows PowerShell 的特定功能的提供程序公开到 Windows PowerShell 运行时在命令处理过程。 为此提供程序，没有 Windows PowerShell 特定功能添加的。

## <a name="defining-base-functionality"></a>定义基本功能

如中所述[设计您的 PS 提供者](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类派生提供不同的提供程序的多个其他类功能。 Windows PowerShell 导航提供程序，因此，必须定义所有这些类提供的功能。

若要实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能，请参阅[创建基本的 PS 提供程序](./creating-a-basic-windows-powershell-provider.md)。 但是，大多数提供程序 （包括此处所述的提供程序） 可以使用 Windows PowerShell 提供此功能的默认实现。

若要通过 Windows PowerShell 驱动器中获取对数据存储的访问，必须实现的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

若要操作的数据存储，如获取、 设置和清除项的项提供程序必须实现提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。

若要访问的子项或它们的名称的数据存储，以及创建、 复制、 重命名和删除项，方法必须实现提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。

## <a name="creating-a-windows-powershell-path"></a>创建 Windows PowerShell 路径

Windows PowerShell 导航提供程序使用提供程序内部的 Windows PowerShell 路径导航数据存储的项。 若要创建的提供程序内部的路径提供程序必须实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)到支持的方法调用从合并路径 cmdlet。 此方法将父和子路径合并到提供程序内部的路径，使用特定于提供程序的路径分隔符之间的父和子路径。

默认实现采用路径替换为"/"或"\\"作为路径分隔符，规范化为路径分隔符"\\"，将父和子路径部分与它们之间的分隔符相结合，然后返回一个字符串，包含组合的路径。

此导航提供程序未实现此方法。 但是，下面的代码是的默认实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>要实现 MakePath 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- 实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法应验证为合法的完全限定路径提供程序命名空间中的路径。 请注意，每个参数只能表示一个路径的一部分，组合的部件可能不会生成完全限定路径。 例如， [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) filesystem 提供程序的方法中可能会出现"windows\system32"`parent`参数，并在中的"abc.dll"`child`参数。 该方法联接这些值用于"\\"分隔符和返回"windows\system32\abc.dll"，这不是完全限定文件系统路径。

  > [!IMPORTANT]
  > 对的调用中提供的路径部分[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)可能包含提供程序命名空间中不允许的字符。 这些字符很可能用于通配符扩展，此方法的实现不应删除它们。

## <a name="retrieving-the-parent-path"></a>检索父路径

Windows PowerShell 导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法来检索父部件所指示的完整或部分特定于提供程序的路径。 该方法删除路径的子部分，并返回对象的父路径部分。 `root`参数指定的驱动器的根目录的完全限定路径。 此参数可以为 null 或为空，如果已装载的驱动器不是用于检索操作。 如果指定一个根，则该方法必须返回路径到根所在的同一树中的容器。

示例导航提供程序不重写此方法，但使用的默认实现。 它接受同时使用的路径"/"和"\\"作为路径分隔符。 它首先规范化的路径以仅具有"\\"分隔符，然后将关闭的父路径拆分最后一个"\\"，并返回父路径。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>若要记住有关实现 GetParentPath

实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法应拆分词法上提供程序命名空间的路径分隔符的路径。 例如，filesystem 提供程序使用此方法查找最后一个"\\"，并返回的所有内容分隔符的左侧。

## <a name="retrieve-the-child-path-name"></a>检索子路径名称

在导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法来检索项的子级的名称 （叶元素） 位于所指示的完整或部分特定于提供程序的路径。

示例导航提供程序不重写此方法。 如下所示的默认实现。 它接受同时使用的路径"/"和"\\"作为路径分隔符。 它首先规范化的路径以仅具有"\\"分隔符，然后将关闭的父路径拆分最后一个"\\"，并返回路径部分的子级的名称。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>要实现 GetChildName 记住的事项

实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法应拆分词法上的路径分隔符的路径。 如果提供的路径不包含任何路径分隔符，该方法应返回以未修改形式的路径。

> [!IMPORTANT]
> 对此方法调用中提供的路径可能包含在提供程序命名空间中是非法的字符。 这些字符很可能用于通配符扩展或正则表达式匹配，并且此方法的实现不应删除它们。

## <a name="determining-if-an-item-is-a-container"></a>确定某个项是否容器

导航提供程序可以实现[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法来确定指定的路径是否指示容器。 它返回路径表示容器和 false 否则如果为 true。 用户需要能够使用此方法`Test-Path`cmdlet 提供的路径。

下面的代码演示[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)中我们的示例导航提供程序的实现。 该方法会验证指定的路径正确，以及如果表存在，并且如果该路径表示一个容器，则返回 true。

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>要实现 IsItemContainer 记住的事项

导航提供程序.NET 类可能会从声明提供程序的功能的 ExpandWildcards、 筛选器、 Include 或 Exclude [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在此情况下，实现[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)需要确保传递的路径是否满足要求。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)属性。

## <a name="moving-an-item"></a>将项移

支持`Move-Item`cmdlet 导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。 此方法将移动指定的项`path`参数中提供的路径处容器`destination`参数。

示例导航提供程序不会覆盖[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。 下面是默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>要实现 MoveItem 记住的事项

导航提供程序.NET 类可能会从声明提供程序的功能的 ExpandWildcards、 筛选器、 Include 或 Exclude [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在此情况下，实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)必须确保传递的路径是否满足要求。 若要执行此操作，该方法应访问相应的属性，例如，则**CmdletProvider.Exclude**属性。

默认情况下，重写此方法不应将移动对象对现有对象除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 例如，filesystem 提供程序不会将复制 c:\temp\abc.txt 通过现有 c:\bar.txt 文件除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果在指定的路径`destination`参数存在，它是一个容器， [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性不是必需。 在这种情况下， [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)应移动的项由`path`到容器参数为由`destination`作为子参数。

实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并向数据存储区进行任何更改之前检查它的返回值。 此方法用于确认操作的执行时更改为系统状态，例如，删除文件。 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改对用户来说，与 Windows PowerShell 运行时将考虑在内的任何命令行设置或首选项变量中的资源的名称确定向用户应显示的内容。

在调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 此方法将消息发送到用户允许反馈以说是否应继续执行该操作。 您的提供程序应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作为具有潜在危险的系统修改为额外检查。

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>附加到 Move-item Cmdlet 的动态参数

有时`Move-Item`cmdlet 需要在运行时动态提供的其他参数。 若要提供这些动态参数，请导航提供程序必须实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法以获取所需的参数值从指定的路径，并返回处的项具有属性和字段与分析的对象属性类似于 cmdlet 类或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。

此导航提供程序未实现此方法。 但是，下面的代码是的默认实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>规范化的相对路径

在导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)中所示方法进行标准化的完全限定路径`path`参数为指定的路径的相对路径`basePath`参数。 该方法返回的字符串表示形式的规范化路径。 它将写入错误，如果`path`参数指定不存在的路径。

示例导航提供程序不重写此方法。 下面是默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>要实现 NormalizeRelativePath 记住的事项

实现[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)应分析`path`参数，但它不需要使用纯粹的语法分析。 此方法以使用路径来查找数据存储区中的路径信息，并创建路径匹配大小写的设计建议和标准化路径语法。

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample05 代码示例](./accessdbprovidersample05-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

很可能要将成员添加到现有对象或定义新对象的提供程序。 有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

有关详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

Windows PowerShell 提供程序具有已注册到 Windows PowerShell，可以通过运行命令行，其中包括可供派生的 cmdlet 上受支持的 cmdlet 来测试它。 此示例将测试的示例导航提供程序。

1. 运行新的 shell，并使用`Set-Location`cmdlet 设置用于指示访问数据库的路径。

   ```powershell
   Set-Location mydb:
   ```

2. 现在，运行`Get-Childitem`cmdlet 来检索是可用的数据库表的数据库项的列表。 对于每个表，此 cmdlet 还将检索表行数。

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. 使用`Set-Location`cmdlet 再次设置员工数据表的位置。

   ```powershell
   Set-Location Employees
   ```

4. 现在，使用`Get-Location`cmdlet 来检索 Employees 表的路径。

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. 现在，使用`Get-Childitem`cmdlet 通过管道传递给`Format-Table`cmdlet。 此组的 cmdlet 检索员工数据，为表的表行的项。 格式所指定的`Format-Table`cmdlet。

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. 现在可以运行`Get-Item`cmdlet 来检索员工数据的表的第 0 行的项。

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. 使用`Get-Item`cmdlet 再次检索第 0 行中的项的员工数据。

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[实现容器的 Windows PowerShell 提供程序](./creating-a-windows-powershell-container-provider.md)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
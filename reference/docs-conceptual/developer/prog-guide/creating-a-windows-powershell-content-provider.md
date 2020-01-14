---
title: 创建 Windows PowerShell 内容提供程序
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
ms.openlocfilehash: 2d48c18cb41dcca372b1e12e1f3abc4c3f5e4bee
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870721"
---
# <a name="creating-a-windows-powershell-content-provider"></a>创建 Windows PowerShell 内容提供程序

本主题介绍如何创建 Windows PowerShell 提供程序，该提供程序使用户能够操作数据存储区中的项的内容。 因此，可操作项内容的提供程序称为 Windows PowerShell 内容提供程序。

> [!NOTE]
> 你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此提供程序的源文件（AccessDBSampleProvider06.cs）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下载的源文件在 **\<PowerShell 示例 >** 目录中提供。 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。

## <a name="define-the-windows-powershell-content-provider-class"></a>定义 Windows PowerShell 内容提供程序类

Windows PowerShell 内容提供程序必须创建一个支持[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口的 .net 类。 下面是本部分中所述的项提供程序的类定义。

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33
"AccessDBProviderSample06.cs")]

请注意，在此类定义中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包括两个参数。 第一个参数指定 Windows PowerShell 使用的提供程序的用户友好名称。 第二个参数指定 Windows PowerShell 特定功能，该功能是在命令处理过程中提供给 Windows PowerShell 运行时的。 对于此提供程序，没有添加 Windows PowerShell 特定功能。

## <a name="define-functionality-of-base-class"></a>定义基类的功能

如[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)中所述， [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类从提供不同提供程序功能的其他一些类派生。 因此，Windows PowerShell 内容提供程序通常定义这些类提供的所有功能。

若要详细了解如何实现添加特定于会话的初始化信息以及释放提供程序所用资源的功能，请参阅[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。
但是，大多数提供程序（包括此处所述的提供程序）都可以使用 Windows PowerShell 提供的此功能的默认实现。

若要访问数据存储区，该提供程序必须实现[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类的方法。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

若要操作数据存储区的项（如获取、设置和清除项），提供程序必须实现[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类提供的方法。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。

若要处理多层数据存储区，提供程序必须实现[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类所提供的方法。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。

若要支持递归命令、嵌套容器和相对路径，提供程序必须实现[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类。 此外，此 Windows PowerShell 内容提供程序还可以将[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口附加到[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类，因此必须实现该类提供的方法，这也是必需的。 有关详细信息，请参阅实现这些方法。请参阅[实现导航 Windows PowerShell 提供程序](./creating-a-windows-powershell-navigation-provider.md)。

## <a name="implementing-a-content-reader"></a>实现内容读取器

若要从项读取内容，提供程序必须实现从[Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)派生的内容读取器类。
此提供程序的内容读取器允许访问数据表中某行的内容。 内容读取器类定义一个**读取**方法，该方法从指示的行中检索数据并返回一个表示该数据的列表、一个移动内容读取器的**查找**方法、一个关闭内容读取器的**关闭**方法以及一个**Dispose**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241
"AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>实现内容编写器

若要向项写入内容，提供程序必须实现从[Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)派生的内容编写器类。
内容编写器类定义**写入**方法，该方法写入指定的行内容、移动内容编写器的**Seek**方法、关闭内容编写器的**关闭**方法以及**Dispose**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>检索内容读取器

若要从项获取内容，提供程序必须实现[Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)以支持 `Get-Content` cmdlet。 此方法返回位于指定路径处的项的内容读取器。 然后，可以打开读取器对象来读取内容。

下面是此提供程序的此方法的[Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)实现。

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>有关实现 GetContentReader 的注意事项

以下条件可能适用于[Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)的实现：。

- 定义提供程序类时，Windows PowerShell 内容提供程序可以声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法的实现必须确保传递给该方法的路径满足指定功能的要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，此方法的重写不应检索用户隐藏的对象的读取器，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 如果路径表示从用户和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)中隐藏的项被设置为 `false`，则应写入错误，则为。

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>将动态参数附加到获取内容 Cmdlet

`Get-Content` cmdlet 可能需要在运行时动态指定的其他参数。 为了提供这些动态参数，Windows PowerShell 内容提供程序必须实现[Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>检索内容编写器

若要向项写入内容，提供程序必须实现[Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)以支持 `Set-Content` 和 `Add-Content` cmdlet。 此方法返回位于指定路径处的项的内容编写器。

下面是此方法的[Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)的实现方法。

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>有关实现 GetContentWriter 的注意事项

以下情况可能适用于你的[Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)实现：

- 定义提供程序类时，Windows PowerShell 内容提供程序可以声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法的实现必须确保传递给该方法的路径满足指定功能的要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，此方法的重写不应检索用户隐藏的对象的编写器，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 如果路径表示从用户和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)中隐藏的项被设置为 `false`，则应写入错误，则为。

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>将动态参数附加到添加内容和集内容 Cmdlet

`Add-Content` 和 `Set-Content` cmdlet 可能需要添加了运行时的其他动态参数。 为了提供这些动态参数，Windows PowerShell 内容提供程序必须实现[Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法来处理这些参数。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>清除内容

你的内容提供商实现了[Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以支持 `Clear-Content` cmdlet。 此方法删除指定路径处的项的内容，但保留该项不变。

下面是此提供程序的[Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的实现。

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>有关实现 ClearContent 的注意事项

以下条件可能适用于[Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)的实现：。

- 定义提供程序类时，Windows PowerShell 内容提供程序可以声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的实现必须确保传递给该方法的路径满足指定功能的要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`，否则此方法的重写不应清除用户隐藏的对象的内容。 如果路径表示从用户和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)中隐藏的项被设置为 `false`，则应写入错误，则为。

- 在对数据存储进行任何更改之前，你的[Icontentcmdletprovider 和 Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并验证其返回值的返回值。 此方法用于确认对数据存储进行更改时（如清除内容）执行操作。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法发送要更改为用户的资源的名称，并在 Windows PowerShell 运行时处理任何命令行设置或首选项变量来确定应显示的内容。

  在对 Cmdletprovider 的调用返回 `true`后，* 方法应调用[ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法，则为，否则返回[Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法的调用方，则为。 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 此方法向用户发送一条消息，以允许反馈验证是否应继续进行操作。 对[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)的调用允许对潜在的危险系统修改进行额外检查。

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>将动态参数附加到清除内容 Cmdlet

`Clear-Content` cmdlet 可能需要在运行时添加的其他动态参数。 为了提供这些动态参数，Windows PowerShell 内容提供程序必须实现[Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法来处理这些参数。 此方法检索指定路径处的项的参数。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample06 代码示例](./accessdbprovidersample06-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

编写提供程序时，可能需要将成员添加到现有对象或定义新的对象。 完成此操作后，你必须创建一个类型文件，Windows PowerShell 可以使用该文件来标识该对象的成员和定义如何显示该对象的格式化文件。 有关详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

向 Windows powershell 注册 Windows PowerShell 提供程序后，可以通过在命令行上运行支持的 cmdlet 来对其进行测试。 例如，测试示例内容提供程序。

使用 `Get-Content` cmdlet 可检索数据库表中由 `Path` 参数指定的路径处的指定项的内容。 `ReadCount` 参数指定已定义内容读取器读取的项数（默认值为1）。 对于以下命令项，该 cmdlet 将从表中检索两行（items）并显示其内容。 请注意，下面的示例输出使用虚构的 Access 数据库。

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))

[实现导航 Windows PowerShell 提供程序](./creating-a-windows-powershell-navigation-provider.md)

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

---
title: 创建 Windows PowerShell 内容提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 6e5d79487539d4f58922e2686f1fdba08797f305
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855303"
---
# <a name="creating-a-windows-powershell-content-provider"></a>创建 Windows PowerShell 内容提供程序

本主题介绍如何创建 Windows PowerShell 提供程序，使用户用来处理数据存储区中项的内容。 因此，可以操作项的内容的提供程序被称为 Windows PowerShell 内容提供程序。

> [!NOTE]
> 您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider06.cs)。 有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
> 您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider06.cs)。 有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下载的源文件中有 **\<PowerShell 示例 >** 目录。
>
> 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。

以下列表包含本主题中的部分。 如果您不熟悉编写 Windows PowerShell 内容提供商，阅读这些部分中显示的顺序。 但是，如果你熟悉编写 Windows PowerShell 内容提供程序，直接转到所需的信息。

- [定义 Windows PowerShell 内容提供程序类](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [定义基本功能](#Define-Functionality-of-Base-Class)

- [实现内容的读取器](#Implementing-a-Content-Reader)

- [实现内容的编写器](#Implementing-a-Content-Writer)

- [检索内容的读取器](#Retrieving-the-Content-Reader)

- [附加到的动态参数`Get-Content`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [检索内容编写器](#Retrieving-the-Content-Writer)

- [将动态参数附加到 Add_Content 和`Set-Content`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [清除内容](#Clearing-Content)

- [附加到的动态参数`Clear-Content`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置]()

- [生成 Windows PowerShell 提供程序](#Building-the-Windows-PowerShell-Provider)

- [测试 Windows PowerShell 提供程序](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>定义 Windows PowerShell 内容提供程序类

Windows PowerShell 内容提供商必须创建一个支持的.NET 类[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。 下面是在本部分中所述的项提供程序的类定义。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

请注意，在此类定义后， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包含两个参数。 第一个参数指定由 Windows PowerShell 提供程序的用户友好名称。 第二个参数指定的 Windows PowerShell 的特定功能的提供程序公开到 Windows PowerShell 运行时在命令处理过程。 为此提供程序，没有添加了的 Windows PowerShell 特定功能。

## <a name="define-functionality-of-base-class"></a>定义功能的基类

如中所述[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类派生自多个提供其他类不同的提供程序功能。 Windows PowerShell 内容提供程序，因此，通常定义的所有这些类提供的功能。

有关如何实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能的详细信息，请参阅[创建一个基本的 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。 但是，大多数提供程序，包括本文所述的提供程序可以使用 Windows PowerShell 提供此功能的默认实现。

若要访问数据存储区，该提供程序必须实现的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

若要操作的数据存储，如获取、 设置和清除项的项提供程序必须实现提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。

若要在多层数据存储上，提供程序必须实现提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。

若要支持递归命令、 嵌套的容器和相对路径，该提供程序必须实现[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类。 此外，此 Windows PowerShell 内容提供商可以附加[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类，并因此必须实现此类提供的方法。 有关详细信息，请参阅实现这些方法，请参阅[实现导航 Windows PowerShell 提供程序](./creating-a-windows-powershell-navigation-provider.md)。

## <a name="implementing-a-content-reader"></a>实现内容的读取器

若要读取来自某个项的内容，提供程序必须实现的内容的读取器类派生自[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)。 此提供程序的内容读取器允许访问行的内容中的数据表。 内容的读取器类定义**读**方法，用于从指示的行中检索数据并返回表示该数据的列表**Seek**移动内容的读取器，方法**关闭**关闭内容读取器的方法和一个**Dispose**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>实现内容的编写器

若要将内容写到某个项，提供程序必须实现内容编写器类派生自[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)。 内容编写器类定义**编写**写入指定的行内容的方法**Seek**移动的内容的编写器，方法**关闭**关闭的方法内容编写器和一个**Dispose**方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>检索内容的读取器

要获取的内容从一个项，该提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)以支持`Get-Content`cmdlet。 此方法返回位于指定路径处的项的内容读取器。 然后，可打开的读取器对象来读取内容。

下面是实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)为此提供程序的此方法。

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>要实现 GetContentReader 记住的事项

以下条件可能适用于的实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- 在定义的提供程序类时，Windows PowerShell 内容提供商可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法必须确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法应检索除非用户隐藏的对象的读取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>附加到的 Get-content Cmdlet 的动态参数

`Get-Content` Cmdlet 可能需要在运行时动态指定的附加参数。 若要提供这些动态参数，Windows PowerShell 内容提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。 此方法检索动态参数指定的路径处的项并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>检索内容编写器

若要将内容写到某个项，该提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)以支持`Set-Content`和`Add-Content`cmdlet。 此方法返回位于指定路径处的项的内容编写器。

下面是实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)为此方法。

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>要实现 GetContentWriter 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- 在定义的提供程序类时，Windows PowerShell 内容提供商可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法必须确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法应检索的编写器对象，除非用户隐藏[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>附加到 Add-content 和 Set-content Cmdlet 的动态参数

`Add-Content`和`Set-Content`cmdlet 可能需要添加一个运行时的其他动态参数。 若要提供这些动态参数，Windows PowerShell 内容提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法来处理这些参数。 此方法检索动态参数指定的路径处的项并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>清除内容

内容提供程序实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法支持`Clear-Content`cmdlet。 此方法移除位于指定路径处的项的内容，但使项保持不变。

下面是实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)此提供程序的方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>要实现 ClearContent 记住的事项

以下条件可能适用于的实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- 在定义的提供程序类时，Windows PowerShell 内容提供商可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法必须确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法不应清除除非用户隐藏的对象的内容[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

- 实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和到数据存储进行任何更改之前验证它的返回值。 此方法用于更改数据存储，例如清除内容时确认执行操作。 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法发送的要与 Windows PowerShell 运行时处理的任何命令行设置或首选项更改为用户的资源名称确定应显示的内容中的变量。

  在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 此方法将消息发送到用户允许反馈，以验证是否应继续执行该操作。 在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允许具有潜在危险的系统修改为其他检查。

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>附加到 Clear-content Cmdlet 的动态参数

`Clear-Content` Cmdlet 可能需要在运行时添加的其他动态参数。 若要提供这些动态参数，Windows PowerShell 内容提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法来处理这些参数。 此方法检索指定的路径处的项的参数。 此方法检索动态参数指定的路径处的项并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample06 代码示例](./accessdbprovidersample06-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

当编写提供程序，它可能有必要，若要将成员添加到现有对象或定义新对象。 完成此操作后，必须创建 Windows PowerShell 可用于标识对象的成员的类型文件和格式化文件，用于定义如何显示该对象。 有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。
当编写提供程序，它可能有必要，若要将成员添加到现有对象或定义新对象。 完成此操作后，必须创建 Windows PowerShell 可用于标识对象的成员的类型文件和格式化文件，用于定义如何显示该对象。 有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。
请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

Windows PowerShell 提供程序具有已注册到 Windows PowerShell，可以通过在命令行上运行的受支持的 cmdlet 来测试它。 例如，测试示例内容提供程序。

使用`Get-Content`cmdlet 来检索指定的路径中的数据库表中指定项的内容`Path`参数。 `ReadCount`参数指定用于定义内容的读取器读取 （默认值 1） 的项的数目。 使用以下命令项时，该 cmdlet 从表中检索两个行 （项），并显示其内容。 请注意，下面的示例输出使用虚构的 Access 数据库。

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
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

[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[实现导航 Windows PowerShell 提供程序](./creating-a-windows-powershell-navigation-provider.md)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

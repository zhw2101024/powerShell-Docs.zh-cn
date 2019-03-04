---
title: 创建 Windows PowerShell 容器提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 8c111f8f2943043e4ad2a6a8677db4afe1b3cdab
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863163"
---
# <a name="creating-a-windows-powershell-container-provider"></a>创建 Windows PowerShell 容器提供程序

本主题介绍如何创建可在多层数据存储的 Windows PowerShell 提供程序。 对于此类型的数据存储区中，存储的最高级别包含根项和每个后续级别被称为子项目的节点。 通过允许用户若要在这些子节点上运行，用户可以通过在数据存储区按层次结构交互。

适用于多级别数据存储区的提供程序称为 Windows PowerShell 容器提供程序。 但是，请注意只有在没有一个容器 （没有嵌套的容器） 中它的项时，可以使用 Windows PowerShell 容器提供程序。 如果有嵌套的容器，则必须实现一个 Windows PowerShell 导航提供程序。 有关实现 Windows PowerShell 导航提供程序的详细信息，请参阅[创建一个 Windows PowerShell 导航提供程序](./creating-a-windows-powershell-navigation-provider.md)。

> [!NOTE]
> 您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider04.cs)。 有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
> 您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider04.cs)。 有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下载的源文件中有 **\<PowerShell 示例 >** 目录。
>
> 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。

此处所述的 Windows PowerShell 容器提供程序定义为其单个容器，使用表和行作为容器的项定义的数据库的数据库。

> [!CAUTION]
> 请注意，此设计假定具有名为 id，字段的数据库字段的类型是 LongInteger。

下面是此主题中的部分列表。 如果您不熟悉编写 Windows PowerShell 容器提供程序，请阅读此信息中出现的顺序。 但是，如果你熟悉编写 Windows PowerShell 容器提供程序，请直接转到所需的信息。

- [定义 Windows PowerShell 容器提供程序类](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [定义基本功能]()

- [正在检索子项目](#Retrieving-Child-Items)

- [附加到的动态参数`Get-ChildItem`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [检索子项名称](#Retrieving-Child-Item-Names)

- [附加到的动态参数`Get-ChildItem`Cmdlet （名称）](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [重命名项](#Renaming-Items)

- [附加到的动态参数`Rename-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [创建新项](#Creating-New-Items)

- [附加到的动态参数`New-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [删除项](#Removing-Items)

- [附加到的动态参数`Remove-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [查询子项目](#Querying-for-Child-Items)

- [如何运用给出的项](#Copying-Items)

- [附加到的动态参数`Copy-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置]()

- [生成 Windows PowerShell 提供程序](#Building-the-Windows-PowerShell-Provider)

- [测试 Windows PowerShell 提供程序](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>定义 Windows PowerShell 容器提供程序类

Windows PowerShell 容器提供程序必须定义一个.NET 类，派生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类。 下面是在本部分中所述的 Windows PowerShell 容器提供程序的类定义。

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

请注意，在这类定义后， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包含两个参数。 第一个参数指定由 Windows PowerShell 提供程序的用户友好名称。 第二个参数指定的 Windows PowerShell 的特定功能的提供程序公开到 Windows PowerShell 运行时在命令处理过程。 为此提供程序，没有 Windows PowerShell 特定功能添加的。

## <a name="defining-base-functionality"></a>定义基本功能

如中所述[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类派生自多个提供其他类不同的提供程序功能。 Windows PowerShell 容器提供程序，因此，需要定义的所有这些类提供的功能。

若要实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能，请参阅[创建一个基本的 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。 但是，大多数提供程序 （包括此处所述的提供程序） 可以使用 Windows PowerShell 提供此功能的默认实现。

若要获取对数据存储的访问，提供程序必须实现的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

若要操作的数据存储，如获取、 设置和清除项的项提供程序必须实现提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。

## <a name="retrieving-child-items"></a>正在检索子项目

若要检索的子项，Windows PowerShell 容器提供程序必须重写[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以支持来自调用`Get-ChildItem`cmdlet。 此方法从数据存储中检索子项目，并将其写入到管道作为对象。 如果`recurse`指定 cmdlet 参数，方法检索而不考虑这些服务都处于何种级别的所有子级。 如果`recurse`未指定参数，该方法检索单个级别的子级。

下面是实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)此提供程序的方法。 请注意，路径指示访问数据库，并从表中的行检索子项目，如果该路径表示数据表时，此方法，检索所有数据库表中的子项。

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>要实现 GetChildItems 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- 在定义的提供程序类时，Windows PowerShell 容器提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 此方法的实现应考虑到帐户的访问权限的任何窗体可能会使该项对用户可见的项。 例如，如果用户具有到通过 FileSystem 提供程序 （由 Windows PowerShell 提供），但不能读取访问的文件的写访问权限，该文件仍存在和[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)返回`true`。 您的实现可能需要检查父项以查看子可进行枚举。

- 编写多个项时[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法可能需要一些时间。 您可以设计你的提供商将使用项写入[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法一次。 使用此方法将会向流中的用户的项。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)负责有循环的链接，以及类似时防止无限递归。 应引发相应的终止异常，以反映此类情况。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>附加到的 Get-childitem Cmdlet 的动态参数

有时`Get-ChildItem`调用的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法。 此方法检索动态参数指定的路径处的项并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Get-ChildItem`cmdlet。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>检索子项名称

若要检索的子项目的名称，Windows PowerShell 容器提供程序必须重写[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以支持来自调用`Get-ChildItem`cmdlet 时其`Name`指定参数。 此方法检索的所有容器指定的路径或子项名称的子项目的名称，如果`returnAllContainers`指定 cmdlet 参数。 子名称是路径的叶部分。 例如，路径 c:\windows\system32\abc.dll 子名称是"abc.dll"。 目录 c:\windows\system32 的子名称是"system32"。

下面是实现[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)此提供程序的方法。 请注意，该方法，是否指定的路径指示的 Access 数据库 （驱动器） 和行号，如果该路径表示表中检索表名。

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>要实现 GetChildNames 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- 在定义的提供程序类时，Windows PowerShell 容器提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

  > [!NOTE]
  > 此规则的例外发生时`returnAllContainers`指定 cmdlet 参数。 在这种情况下，该方法应检索任何子容器名称，即使与的值不匹配[System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)， [System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)，或[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)属性。

- 默认情况下，重写此方法应检索的对象，除非通常隐藏的用户名称[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)指定属性。 如果指定的路径指示容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性不是必需。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)负责有循环的链接，以及类似时防止无限递归。 应引发相应的终止异常，以反映此类情况。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>将动态参数附加到的 Get-childitem Cmdlet （名称）

有时`Get-ChildItem`cmdlet (使用`Name`参数) 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。 此方法检索指定的路径处的项的动态参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Get-ChildItem`cmdlet。

此提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>重命名项

若要重命名某个项，Windows PowerShell 容器提供程序必须重写[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，以支持来自调用`Rename-Item`cmdlet。 此方法的指定路径处的项的名称更改为提供的新名称。 新名称必须始终为相对于父项 （容器）。

此提供程序不会覆盖[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。 但是，以下是默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>要实现 RenameItem 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- 在定义的提供程序类时，Windows PowerShell 容器提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法旨在针对仅限，项名称的修改而不是针对移动操作。 如果该方法的实现应编写错误`newName`参数包含路径分隔符，或可能会导致要更改其父位置的项。

- 默认情况下，重写此方法不应重命名对象除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)指定属性。 如果指定的路径指示容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性不是必需。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并向数据存储区进行任何更改之前检查它的返回值。 此方法用于确认操作的执行时更改为系统状态，例如，重命名文件。 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改对用户来说，与 Windows PowerShell 运行时将考虑在内的任何命令行设置或首选项变量中的资源的名称确定应显示的内容。

  在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 此方法发送一条消息的确认消息给用户以允许其他反馈以说是否应继续执行该操作。 一个提供程序应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作为具有潜在危险的系统修改为额外检查。

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>附加到重命名项 Cmdlet 的动态参数

有时`Rename-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。 此方法检索指定的路径处的项的参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Rename-Item`cmdlet。

此容器提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>创建新项

若要创建新项目，容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以支持来自调用`New-Item`cmdlet。 此方法创建在位于指定路径的数据项。 `type` Cmdlet 参数包含新项的定义提供程序的类型。 例如，FileSystem 提供程序使用`type`参数，其值为"文件"或"directory"。 `newItemValue` Cmdlet 参数指定新项的特定于提供程序的值。

下面是实现[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)此提供程序的方法。

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>要实现 NewItem 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法应执行不区分大小写比较的字符串中传入`type`参数。 它还应允许至少不明确的匹配项。 例如，对于类型"文件"和"directory"中，只将第一个字母被需要消除歧义。 如果`type`参数指示的类型不能创建您的提供程序，请[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法应编写一条消息与 ArgumentException指示类型可以创建提供程序。

- 有关`newItemValue`参数，请实现[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，建议接受最小值的字符串。 它还应接受将检索的对象的类型[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)相同路径的方法。 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法可以使用[System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法来转换到类型所需的类型。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并向数据存储区进行任何更改之前检查它的返回值。 在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，则返回 true， [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)具有潜在危险的系统修改作为额外检查方法。

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>附加到新项 Cmdlet 的动态参数

有时`New-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。 此方法检索指定的路径处的项的参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`New-Item`cmdlet。

此提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>删除项

若要删除的项，Windows PowerShell 提供程序必须重写[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以支持来自调用`Remove-Item`cmdlet。 此方法从指定的路径的数据存储区中删除的项。 如果`recurse`的参数`Remove-Item`cmdlet 设置为`true`，方法将移除所有子项目，而不考虑其级别。 如果该参数设置为`false`，方法将移除单个项在指定的路径。

此提供程序不支持删除项。 但是，下面的代码是的默认实现[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>要实现 RemoveItem 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- 在定义的提供程序类时，Windows PowerShell 容器提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法不应删除对象除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 true。 如果指定的路径指示容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性不是必需。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)负责有循环的链接，以及类似时防止无限递归。 应引发相应的终止异常，以反映此类情况。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并向数据存储区进行任何更改之前检查它的返回值。 在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)具有潜在危险的系统修改作为额外检查方法。

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>附加到 Remove-item Cmdlet 的动态参数

有时`Remove-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法来处理这些参数。 此方法检索指定的路径处的项的动态参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Remove-Item`cmdlet。

此容器提供程序未实现此方法。 但是，下面的代码是的默认实现[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>查询子项目

若要检查的指定路径处是否存在子项目，Windows PowerShell 容器提供程序必须重写[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。 此方法返回`true`的项具有子项，如果和`false`否则为。 为 null 或为空路径，该方法会考虑要为子级的数据存储区中的任何项，并返回`true`。

下面是用于重写[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。 如果有两个路径部分 ChunkPath 帮助器方法创建的该方法返回`false`，因为定义数据库容器和表容器。 有关此帮助器方法的详细信息，请参阅 ChunkPath 方法详见[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>要实现 HasChildItems 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- 如果容器提供程序公开的根包含有趣装入点的实现[System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法应返回`true`为 null 或空字符串传递时中的路径。

## <a name="copying-items"></a>复制项

若要复制的项，容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以支持来自调用`Copy-Item`cmdlet。 此方法将从所指示的位置中复制的数据项`path`到所指示的位置 cmdlet 参数`copyPath`参数。 如果`recurse`指定参数，该方法将复制所有子容器。 如果未指定参数，该方法将复制单个级别的项。

此提供程序未实现此方法。 但是，下面的代码是的默认实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>要实现 CopyItem 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- 在定义的提供程序类时，Windows PowerShell 容器提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法需要确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法不应将复制对象对现有对象除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 例如，FileSystem 提供程序不会将复制 c:\temp\abc.txt 通过现有 c:\abc.txt 文件除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果在指定的路径`copyPath`参数存在，并指示容器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性不是必需。 在这种情况下， [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)应将复制所指示的项`path`到容器参数为由`copyPath`作为子参数。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)负责有循环的链接，以及类似时防止无限递归。 应引发相应的终止异常，以反映此类情况。

- 实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并向数据存储区进行任何更改之前检查它的返回值。 在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，则返回 true， [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)具有潜在危险的系统修改作为额外检查方法。 有关调用这些方法的详细信息，请参阅[重命名项](#Renaming-Items)。

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>附加到 Copy-item Cmdlet 的动态参数

有时`Copy-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 容器提供程序必须实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法来处理这些参数。 此方法检索指定的路径处的项的参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Copy-Item`cmdlet。

此提供程序未实现此方法。 但是，下面的代码是的默认实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample04 代码示例](./accessdbprovidersample04-code-sample.md)。

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。
请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

Windows PowerShell 提供程序具有已注册到 Windows PowerShell，可以通过在命令行上运行的受支持的 cmdlet 来测试它。 请注意下面的示例输出使用虚构的 Access 数据库。

1. 运行`Get-ChildItem`cmdlet 从 Access 数据库中的客户表中检索子项目的列表。

   ```powershell
   Get-ChildItem mydb:customers
   ```

   将显示以下输出。

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. 运行`Get-ChildItem`cmdlet 再次检索表中的数据。

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   将显示以下输出。

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. 现在，使用`Get-Item`cmdlet 来检索数据的表中的第 0 行处的项。

   ```powershell
   Get-Item mydb:\customers\0
   ```

   将显示以下输出。

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. 重复使用`Get-Item`若要检索的数据的第 0 行中的项。

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   将显示以下输出。

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. 现在，使用`New-Item`cmdlet 将行添加到现有表。 `Path`参数指定行的完整路径，并且必须指明行数大于现有表中的行数。 `Type`参数指示"行"指定要添加的项的类型。 最后，`Value`参数指定的列的行的值以逗号分隔列表。

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAdress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. 验证新项操作的正确性，如下所示。

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   将显示以下输出。

   ```output
   ID        : 3
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
   ```

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[实现项 Windows PowerShell 提供程序](./creating-a-windows-powershell-item-provider.md)

[实现导航 Windows PowerShell 提供程序](./creating-a-windows-powershell-navigation-provider.md)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)
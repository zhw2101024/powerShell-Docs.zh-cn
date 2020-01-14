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
ms.openlocfilehash: 69e45de4220a234783d35a877116ad5a5e47d182
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870772"
---
# <a name="creating-a-windows-powershell-container-provider"></a>创建 Windows PowerShell 容器提供程序

本主题介绍如何创建可在多层数据存储上使用的 Windows PowerShell 提供程序。 对于这种类型的数据存储，存储区的顶层包含根项，而每个后续级别称为子项的节点。 通过允许用户在这些子节点上工作，用户可以通过数据存储区进行分层交互。

可在多级别数据存储上使用的提供程序称为 "Windows PowerShell 容器提供程序"。 但请注意，只有当一个容器（无嵌套容器）包含项时，才能使用 Windows PowerShell 容器提供程序。 如果有嵌套容器，则必须实现 Windows PowerShell 导航提供程序。 有关实现 Windows PowerShell 导航提供程序的详细信息，请参阅[创建 Windows Powershell 导航提供程序](./creating-a-windows-powershell-navigation-provider.md)。

> [!NOTE]
> 你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此提供程序的源文件（AccessDBSampleProvider04.cs）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下载的源文件在 **\<PowerShell 示例 >** 目录中提供。 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。

此处所述的 Windows PowerShell 容器提供程序将数据库定义为其单个容器，并将数据库的表和行定义为容器的项。

> [!CAUTION]
> 请注意，此设计假设有一个数据库，该数据库具有名称为 ID 的字段，并且该字段的类型为 LongInteger。

## <a name="defining-a-windows-powershell-container-provider-class"></a>定义 Windows PowerShell 容器提供程序类

Windows PowerShell 容器提供程序必须定义一个从[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类派生的 .net 类的 .net 类。 下面是本部分中所述的 Windows PowerShell 容器提供程序的类定义。

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

请注意，在此类定义中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包括两个参数。 第一个参数指定 Windows PowerShell 使用的提供程序的用户友好名称。 第二个参数指定 Windows PowerShell 特定功能，该功能是在命令处理过程中提供给 Windows PowerShell 运行时的。 对于此提供程序，没有添加的 Windows PowerShell 特定功能。

## <a name="defining-base-functionality"></a>定义基本功能

如[设计你的 Windows PowerShell 提供](./designing-your-windows-powershell-provider.md)程序中所述， [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类派生自其他一些类，这些类提供了不同的提供程序功能。 因此，Windows PowerShell 容器提供程序需要定义这些类提供的所有功能。

若要实现添加特定于会话的初始化信息以及释放提供程序所用资源的功能，请参阅[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。
但是，大多数提供程序（包括此处所述的提供程序）可以使用 Windows PowerShell 提供的此功能的默认实现。

若要获取对数据存储区的访问权限，提供程序必须实现[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类的方法。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

若要操作数据存储区的项（如获取、设置和清除项），提供程序必须实现[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类提供的方法。 有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。

## <a name="retrieving-child-items"></a>检索子项

若要检索子项，Windows PowerShell 容器提供程序必须重写[Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以支持来自 `Get-ChildItem` cmdlet 的调用。 此方法从数据存储中检索子项目，并将其作为对象写入管道。 如果指定了 cmdlet 的 `recurse` 参数，则该方法将检索所有子项，而不管它们处于什么级别。 如果未指定 `recurse` 参数，则方法只检索一级子级。

下面是此提供程序的[Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的实现。 请注意，当路径指示 Access 数据库时，此方法将检索所有数据库表中的子项目，如果路径指示数据表，则从该表的行中检索子项。

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

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>有关实现 GetChildItems 的注意事项

以下情况可能适用于你的[Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)实现：

- 定义提供程序类时，Windows PowerShell 容器提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的实现需要确保传递给方法的路径满足指定的功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 此方法的实现应将对该项的任何形式的访问权限考虑到对用户可见的项。 例如，如果用户通过 FileSystem 提供程序（由 Windows PowerShell 提供）对文件的写入访问权限，但不是读取访问权限，则该文件仍然存在，并且[Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)返回 `true`。 您的实现可能需要检查父项，以查看是否可以枚举子级。

- 写入多个项时， [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法可能需要一些时间。 你可以设计提供程序，以一次一个地使用[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法来编写项。 使用此方法会向用户提供流中的项。

- 当存在循环链接时， [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的实现会阻止无限递归，如所示。 应该引发适当的终止异常来反映这种情况。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>将动态参数附加到 Get-childitem Cmdlet

有时，调用[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)的 `Get-ChildItem` cmdlet 会要求在运行时动态指定的附加参数。 若要提供这些动态参数，Windows PowerShell 容器提供程序必须实现[Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Get-ChildItem` cmdlet 中。

此 Windows PowerShell 容器提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>检索子项名称

若要检索子项目的名称，Windows PowerShell 容器提供程序必须重写[Containercmdletprovider Getchildnames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以便在指定其 `Name` 参数时支持 `Get-ChildItem` cmdlet 中的调用。 如果指定了 cmdlet 的 `returnAllContainers` 参数，则此方法将检索所有容器的指定路径或子项目名称的子项目的名称。 子名称是路径的叶部分。 例如，路径 c:\windows\system32\abc.dll 的子名称为 "abc .dll"。 目录 c:\windows\system32 的子名称为 "system32"。

下面是此提供程序的[Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法的实现。 请注意，如果指定的路径指示 Access 数据库（驱动器）和行号（如果路径指示表），则方法将检索表名称。

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

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>有关实现 GetChildNames 的注意事项

以下情况可能适用于你的[Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)实现：

- 定义提供程序类时，Windows PowerShell 容器提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的实现需要确保传递给方法的路径满足指定的功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

  > [!NOTE]
  > 当指定 cmdlet 的 `returnAllContainers` 参数时，将发生此规则的例外情况。 在这种情况下，该方法应检索某个容器的任何子名称，即使该名称与[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)* 或[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)* 或 Cmdletprovider * 属性的值不匹配，也是如此。 [System.Management.Automation.Provider.Cmdletprovider.Exclude](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) * 属性的值的值相同，则为。

- 默认情况下，除非指定了[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性，否则此方法的重写不应检索用户通常隐藏的对象的名称。 如果指定的路径指示一个容器，则不需要[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性（& e）。

- 当存在循环链接时， [Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)的实现会阻止无限递归，如所示。 应该引发适当的终止异常来反映这种情况。

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>将动态参数附加到 Get-childitem Cmdlet （Name）

有时 `Get-ChildItem` cmdlet （具有 `Name` 参数）需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 容器提供程序必须实现[Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有分析特性类似于 cmdlet 类或 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 对象的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Get-ChildItem` cmdlet 中。

此提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>重命名项

若要重命名某个项，Windows PowerShell 容器提供程序必须重写[Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，以支持来自 `Rename-Item` cmdlet 的调用。 此方法将指定路径处的项的名称更改为提供的新名称。 新名称必须始终相对于父项（容器）。

此提供程序不重写[Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。 但是，下面是默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>有关实现 RenameItem 的注意事项

以下情况可能适用于你的[Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)实现：

- 定义提供程序类时，Windows PowerShell 容器提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的实现需要确保传递给方法的路径满足指定的功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- [Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法仅用于修改某个项的名称，而不是用于移动操作的修改。
  如果 `newName` 参数包含路径分隔符，则方法的实现应写入错误，否则可能导致项更改其父位置。

- 默认情况下，除非指定了[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性，否则此方法的重写不应重命名对象。 如果指定的路径指示一个容器，则不需要[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性（& e）。

- 在对数据存储进行任何更改之前，你的[Containercmdletprovider 和 Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并检查其返回值，然后再进行更改。 此方法用于在对系统状态进行更改时（例如，重命名文件）确认操作的执行。
  [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改为用户的资源的名称，Windows PowerShell 运行时在确定应显示的内容时考虑了任何命令行设置或首选项变量。

  在对 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 的调用返回 `true` 后，[System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法应调用 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 方法。 此方法向用户发送一条确认消息，以允许其他反馈显示是否应继续进行操作。 提供程序应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作为额外检查来检查是否存在潜在的危险系统修改。

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>将动态参数附加到重命名项 Cmdlet

有时 `Rename-Item` cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 容器提供程序必须实现[Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。 此方法检索指定路径处的项的参数，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Rename-Item` cmdlet 中。

此容器提供程序不实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>正在创建新项

若要创建新项，容器提供程序必须实现[Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以支持来自 `New-Item` cmdlet 的调用。 此方法创建位于指定路径的数据项。 Cmdlet 的 `type` 参数包含用于新项的提供程序定义的类型。 例如，FileSystem 提供程序使用值为 "file" 或 "directory" 的 `type` 参数。 Cmdlet 的 `newItemValue` 参数为新项指定特定于提供程序的值。

下面是此提供程序的[Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的实现。

```csharp
protected override void NewItem( string path, string type, object newItemValue )
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

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>有关实现 NewItem 的注意事项

以下情况可能适用于你的[Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)实现：

- [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法应对 `type` 参数中传递的字符串执行不区分大小写的比较。
  它还应允许最小不明确匹配。 例如，对于类型 "file" 和 "directory"，只需第一个字母来消除歧义。 如果 `type` 参数指示提供程序无法创建的类型，则[Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法应使用指示提供程序可以创建的类型的消息编写 ArgumentException。

- 对于 "`newItemValue`" 参数，建议使用[Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的实现来最小限度地接受字符串。 它还应接受由[Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法为同一路径检索的对象的类型的对象。 [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法可以使用[languageprimitives.physicalequality. convertto-html *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo)方法将类型转换为所需的类型（& i）。

- 在对数据存储进行任何更改之前，你的[Containercmdletprovider 和 Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并检查其返回值，然后再进行更改。 在对 Cmdletprovider 的调用返回 true 后，ShouldProcess[方法应](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法作为额外的检查，以应对潜在的危险系统修改情况进行检查，然后再调用[Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，则为。

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>将动态参数附加到新项 Cmdlet

有时 `New-Item` cmdlet 需要在运行时动态指定的其他参数。 为了提供这些动态参数，容器提供程序必须实现[Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。 此方法检索指定路径处的项的参数，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `New-Item` cmdlet 中。

此提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>删除项

若要删除项，Windows PowerShell 提供程序必须重写[Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以支持来自 `Remove-Item` cmdlet 的调用。 此方法从数据存储区中的指定路径删除一个项。 如果 `Remove-Item` cmdlet 的 `recurse` 参数设置为 `true`，则方法将删除所有子项，而不考虑它们的级别。 如果将参数设置为 `false`，则方法只删除指定路径中的单个项。

此提供程序不支持删除项。 但是，下面的代码是[Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>有关实现 RemoveItem 的注意事项

以下情况可能适用于你的[Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)实现：

- 定义提供程序类时，Windows PowerShell 容器提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的实现需要确保传递给方法的路径满足指定的功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 true，否则此方法的重写不应删除对象。 如果指定的路径指示一个容器，则不需要[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性（& e）。

- 当存在循环链接时， [Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)的实现会阻止无限递归，如所示。 应该引发适当的终止异常来反映这种情况。

- 在对数据存储进行任何更改之前，你的[Containercmdletprovider 和 Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并检查其返回值，然后再进行更改。 在对 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 的调用返回 `true` 后，[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 方法应调用 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 方法，作为额外检查是否存在潜在的危险系统修改。

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>将动态参数附加到移除项 Cmdlet

有时 `Remove-Item` cmdlet 需要在运行时动态指定的其他参数。 为了提供这些动态参数，容器提供程序必须实现[Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法来处理这些参数。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有分析特性类似于 cmdlet 类或 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 对象的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Remove-Item` cmdlet 中。

此容器提供程序不实现此方法。 但是，下面的代码是[Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>查询子项

若要检查子项目是否存在于指定的路径，Windows PowerShell 容器提供程序必须重写[Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法。 如果项具有子级，则此方法返回 `true`; 否则返回 `false`。 对于 null 或空路径，方法会将数据存储区中的任何项视为子级并返回 `true`。

下面是对[Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的重写。 如果 ChunkPath helper 方法创建了两个以上的路径部分，则方法将返回 `false`，因为只定义了一个数据库容器和一个表容器。 有关此帮助器方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)中介绍的 ChunkPath 方法。

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>有关实现 HasChildItems 的注意事项

以下情况可能适用于你的[Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)实现：

- 如果容器提供程序公开包含有趣装入点的根，则当为路径传递了 null 或空字符串时， [Containercmdletprovider 和 Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法的实现应返回 `true`。

## <a name="copying-items"></a>复制项

若要复制项，容器提供程序必须实现[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法以支持来自 `Copy-Item` cmdlet 的调用。 此方法将数据项从 cmdlet 的 `path` 参数指示的位置复制到 `copyPath` 参数指示的位置。 如果指定 `recurse` 参数，则该方法将复制所有子容器。 如果未指定参数，则方法只复制单个级别的项。

此提供程序未实现此方法。 但是，下面的代码是[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>有关实现 CopyItem 的注意事项

以下情况可能适用于你的 ContainerCmdletProvider 的实现。 [CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)：

- 定义提供程序类时，Windows PowerShell 容器提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法的实现需要确保传递给方法的路径满足指定的功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，此方法的重写不应将对象复制到现有对象上，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 例如，FileSystem 提供程序将不会通过现有的 c:\abc.txt 文件复制 c:\temp\abc.txt，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 如果在 `copyPath` 参数中指定的路径存在，并指示一个容器，则不需要[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性。 在这种情况下， [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)应将 `path` 参数指示的项复制到由 `copyPath` 参数指示为子级的容器。

- 当存在循环链接时，你的[ContainerCmdletProvider CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)的实现负责阻止无限递归，如所示。 应该引发适当的终止异常来反映这种情况。

- 在对数据存储进行任何更改之前，你的[ContainerCmdletProvider CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并检查其返回值，然后再进行更改。 在对 Cmdletprovider 的调用返回 true 后，ShouldProcess 方法应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法作为额外的检查，以检查是否存在潜在的危险系统修改的情况下出现的其他[检查功能。](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ） [。 "。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 有关调用这些方法的详细信息，请参阅[Rename 项](#renaming-items)。

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>将动态参数附加到复制项 Cmdlet

有时 `Copy-Item` cmdlet 需要在运行时动态指定的其他参数。 为了提供这些动态参数，Windows PowerShell 容器提供程序必须实现[Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法来处理这些参数。 此方法检索指定路径处的项的参数，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Copy-Item` cmdlet 中。

此提供程序未实现此方法。 但是，下面的代码是[Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample04 代码示例](./accessdbprovidersample04-code-sample.md)。

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

向 Windows powershell 注册 Windows PowerShell 提供程序后，可以通过在命令行上运行支持的 cmdlet 来对其进行测试。 请注意，以下示例输出使用虚构的 Access 数据库。

1. 运行 `Get-ChildItem` cmdlet 可在 Access 数据库中检索 Customers 表中的子项列表。

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

2. 再次运行 `Get-ChildItem` cmdlet 以检索表的数据。

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

3. 现在使用 `Get-Item` cmdlet 来检索数据表中第0行的项。

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

4. 重复使用 `Get-Item` 检索第0行中的项的数据。

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

5. 现在使用 `New-Item` cmdlet 向现有表添加行。 `Path` 参数指定行的完整路径，并且必须指示大于表中现有行数的行号。 `Type` 参数指示 "行" 以指定要添加的项的类型。
   最后，`Value` 参数为行指定以逗号分隔的列值列表。

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
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

[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[实现 Windows PowerShell 提供程序项](./creating-a-windows-powershell-item-provider.md)

[实现导航 Windows PowerShell 提供程序](./creating-a-windows-powershell-navigation-provider.md)

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

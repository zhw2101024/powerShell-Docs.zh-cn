---
title: 写入项提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359876"
---
# <a name="writing-an-item-provider"></a>编写项提供程序

本主题介绍如何实现访问和操作数据存储区中的项的 Windows PowerShell 提供程序的方法。 若要能够访问项，提供程序必须从[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类派生而来。

本主题中的示例中的提供程序使用 Access 数据库作为其数据存储。 有几个帮助器方法和用于与数据库进行交互的类。 有关包含帮助程序方法的完整示例，请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)

有关 Windows PowerShell 提供程序的详细信息，请参阅[Windows Powershell 提供程序概述](./windows-powershell-provider-overview.md)。

## <a name="implementing-item-methods"></a>实现项方法

[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类公开了若干可用于访问和操作数据存储区中的项的方法。 有关这些方法的完整列表，请参阅[ItemCmdletProvider 方法](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods)。 在此示例中，我们将实现这四种方法。 [Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)将获取指定路径处的项。 Setitem * 设置指定项的值。 [Itemcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)设置指定项的值。 [Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)检查项是否存在于指定的路径。 [Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)检查路径，查看其是否映射到数据存储中的某个位置。

> [!NOTE]
> 本主题以[Windows PowerShell 提供程序快速入门](./windows-powershell-provider-quickstart.md)中的信息为基础。 本主题不包含有关如何设置提供程序项目的基本知识，或者如何实现从[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类继承的方法，这些方法可创建和删除驱动器。

### <a name="declaring-the-provider-class"></a>声明提供程序类

将提供程序声明为派生自[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类，并将其与[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)的修饰进行对其修饰。

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>实现 GetItem

当用户在提供程序上调用[GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet 时，PowerShell 引擎将调用[Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) . e x * *。 方法返回指定路径处的项。 在 Access 数据库示例中，方法检查项是否为驱动器本身、数据库中的表或数据库中的行。 此方法通过调用[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法将该项发送到 PowerShell 引擎中。

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>实现 SetItem

当用户调用[SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet 时，PowerShell 引擎调用会调用[Itemcmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法。 "*" 方法。 它设置指定路径处的项的值。

在 Access 数据库示例中，只有当项是行时才设置该项的值是有意义的，因此，当项不是行时，方法将引发[NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) 。

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>实现 ItemExists

当用户调用[TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet 时，PowerShell 引擎将调用[Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，这是由 PowerShell 引擎调用的。 方法确定指定路径是否存在项。 如果该项存在，则方法会通过调用 Cmdletprovider 将其传递回 PowerShell 引擎。 [Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)。

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>实现 IsValidPath

[Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法用于检查指定路径对于当前提供程序是否语法是否有效。 它不检查项是否存在于路径中。

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>后续步骤

典型的实际提供商可以支持包含其他项目的项目，还可以将项目从驱动器中的某个路径移动到另一个路径。 有关支持容器的提供程序的示例，请参阅[编写容器提供程序](./writing-a-container-provider.md)。 有关支持移动项的提供程序的示例，请参阅[编写导航提供程序](./writing-a-navigation-provider.md)。

## <a name="see-also"></a>另请参阅

[编写容器提供程序](./writing-a-container-provider.md)

[编写导航提供程序](./writing-a-navigation-provider.md)

[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)

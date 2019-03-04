---
title: 编写项提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: e3289e9336b863b5e0998a2beb29353c82a31f79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856703"
---
# <a name="writing-an-item-provider"></a>编写项提供程序

本主题介绍如何实现 Windows PowerShell 提供程序的访问和操作数据存储区中的项的方法。 若要能够访问的项，提供程序必须派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。

本主题中的示例中的提供程序使用 Access 数据库作为其数据存储区。 有几个帮助器方法和用于与数据库交互的类。 有关完整示例，包括帮助器方法，请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)

有关 Windows PowerShell 提供程序的详细信息，请参阅[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)。

## <a name="implementing-item-methods"></a>实现的项方法

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类公开可用于访问和操作数据存储区中的项的几种方法。 有关这些方法的完整列表，请参阅[ItemCmdletProvider 方法](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx)。 在此示例中，我们将实现四个这些方法。 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)获取指定路径处的项。 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)设置指定项的值。 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)检查指定路径处是否存在的项。 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)检查以查看是否映射到数据存储区中的位置的路径。

> [!NOTE]
> 本主题中的信息为基础[Windows PowerShell 提供程序快速入门](./windows-powershell-provider-quickstart.md)。 本主题不会介绍如何设置提供程序项目的基础知识，或如何实现的方法继承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类，该类创建并删除驱动器。

### <a name="declaring-the-provider-class"></a>声明提供程序类

声明提供程序派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类，并给它装饰[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>实现 GetItem

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)当用户调用时，PowerShell 引擎将调用[Microsoft.Powershell.Commands.Get 项](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item)cmdlet 将提供程序。 该方法返回位于指定路径处的项。 在访问数据库示例中，该方法检查该项是否为驱动器本身，而在数据库或数据库中的行中的表。 该方法将项发送到 PowerShell 引擎，通过调用[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。

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

[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) PowerShell 引擎调用由调用方法，当用户调用[Microsoft.Powershell.Commands.Set 项](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item)cmdlet. 它在指定的路径设置项的值。

在访问数据库示例中，则最好设置项的值，仅当该项目是一个行，因此该方法将引发[NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx)时此项不是行。

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

[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) PowerShell 引擎通过调用方法，当用户调用[Microsoft.Powershell.Commands.Test 路径](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path)cmdlet。 该方法确定在指定的路径是否存在某个项。 如果存在此项，该方法将其传递给 PowerShell 引擎通过调用[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)。

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

[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法检查指定的路径是否为当前提供程序语法上有效。 它不会检查路径是否存在的项。

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

典型的真实提供程序是支持包含其他项的项，并将项从一条路径移动到另一种内部驱动器的支持。 支持容器的提供程序的示例，请参阅[编写容器提供程序](./writing-a-container-provider.md)。 支持移动的项的提供程序的示例，请参阅[编写导航提供程序](./writing-a-navigation-provider.md)。

## <a name="see-also"></a>另请参阅

[编写容器提供程序](./writing-a-container-provider.md)

[编写导航提供程序](./writing-a-navigation-provider.md)

[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)
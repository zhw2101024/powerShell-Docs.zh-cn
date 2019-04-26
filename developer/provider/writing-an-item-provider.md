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
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080809"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="cdf58-102">编写项提供程序</span><span class="sxs-lookup"><span data-stu-id="cdf58-102">Writing an item provider</span></span>

<span data-ttu-id="cdf58-103">本主题介绍如何实现 Windows PowerShell 提供程序的访问和操作数据存储区中的项的方法。</span><span class="sxs-lookup"><span data-stu-id="cdf58-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="cdf58-104">若要能够访问的项，提供程序必须派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="cdf58-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="cdf58-105">本主题中的示例中的提供程序使用 Access 数据库作为其数据存储区。</span><span class="sxs-lookup"><span data-stu-id="cdf58-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="cdf58-106">有几个帮助器方法和用于与数据库交互的类。</span><span class="sxs-lookup"><span data-stu-id="cdf58-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="cdf58-107">有关完整示例，包括帮助器方法，请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="cdf58-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="cdf58-108">有关 Windows PowerShell 提供程序的详细信息，请参阅[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf58-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="cdf58-109">实现的项方法</span><span class="sxs-lookup"><span data-stu-id="cdf58-109">Implementing item methods</span></span>

<span data-ttu-id="cdf58-110">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类公开可用于访问和操作数据存储区中的项的几种方法。</span><span class="sxs-lookup"><span data-stu-id="cdf58-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="cdf58-111">有关这些方法的完整列表，请参阅[ItemCmdletProvider 方法](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="cdf58-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="cdf58-112">在此示例中，我们将实现四个这些方法。</span><span class="sxs-lookup"><span data-stu-id="cdf58-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="cdf58-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)获取指定路径处的项。</span><span class="sxs-lookup"><span data-stu-id="cdf58-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="cdf58-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)设置指定项的值。</span><span class="sxs-lookup"><span data-stu-id="cdf58-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="cdf58-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)检查指定路径处是否存在的项。</span><span class="sxs-lookup"><span data-stu-id="cdf58-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="cdf58-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)检查以查看是否映射到数据存储区中的位置的路径。</span><span class="sxs-lookup"><span data-stu-id="cdf58-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="cdf58-117">本主题中的信息为基础[Windows PowerShell 提供程序快速入门](./windows-powershell-provider-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf58-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="cdf58-118">本主题不会介绍如何设置提供程序项目的基础知识，或如何实现的方法继承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类，该类创建并删除驱动器。</span><span class="sxs-lookup"><span data-stu-id="cdf58-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="cdf58-119">声明提供程序类</span><span class="sxs-lookup"><span data-stu-id="cdf58-119">Declaring the provider class</span></span>

<span data-ttu-id="cdf58-120">声明提供程序派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类，并给它装饰[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="cdf58-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="cdf58-121">实现 GetItem</span><span class="sxs-lookup"><span data-stu-id="cdf58-121">Implementing GetItem</span></span>

<span data-ttu-id="cdf58-122">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)当用户调用时，PowerShell 引擎将调用[Microsoft.PowerShell.Commands.Get 项](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item)cmdlet 将提供程序。</span><span class="sxs-lookup"><span data-stu-id="cdf58-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="cdf58-123">该方法返回位于指定路径处的项。</span><span class="sxs-lookup"><span data-stu-id="cdf58-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="cdf58-124">在访问数据库示例中，该方法检查该项是否为驱动器本身，而在数据库或数据库中的行中的表。</span><span class="sxs-lookup"><span data-stu-id="cdf58-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="cdf58-125">该方法将项发送到 PowerShell 引擎，通过调用[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。</span><span class="sxs-lookup"><span data-stu-id="cdf58-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="cdf58-126">实现 SetItem</span><span class="sxs-lookup"><span data-stu-id="cdf58-126">Implementing SetItem</span></span>

<span data-ttu-id="cdf58-127">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) PowerShell 引擎调用由调用方法，当用户调用[Microsoft.PowerShell.Commands.Set 项](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item)cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cdf58-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="cdf58-128">它在指定的路径设置项的值。</span><span class="sxs-lookup"><span data-stu-id="cdf58-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="cdf58-129">在访问数据库示例中，则最好设置项的值，仅当该项目是一个行，因此该方法将引发[NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx)时此项不是行。</span><span class="sxs-lookup"><span data-stu-id="cdf58-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="cdf58-130">实现 ItemExists</span><span class="sxs-lookup"><span data-stu-id="cdf58-130">Implementing ItemExists</span></span>

<span data-ttu-id="cdf58-131">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) PowerShell 引擎通过调用方法，当用户调用[Microsoft.PowerShell.Commands.Test 路径](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cdf58-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="cdf58-132">该方法确定在指定的路径是否存在某个项。</span><span class="sxs-lookup"><span data-stu-id="cdf58-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="cdf58-133">如果存在此项，该方法将其传递给 PowerShell 引擎通过调用[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)。</span><span class="sxs-lookup"><span data-stu-id="cdf58-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="cdf58-134">实现 IsValidPath</span><span class="sxs-lookup"><span data-stu-id="cdf58-134">Implementing IsValidPath</span></span>

<span data-ttu-id="cdf58-135">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法检查指定的路径是否为当前提供程序语法上有效。</span><span class="sxs-lookup"><span data-stu-id="cdf58-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="cdf58-136">它不会检查路径是否存在的项。</span><span class="sxs-lookup"><span data-stu-id="cdf58-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="cdf58-137">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cdf58-137">Next steps</span></span>

<span data-ttu-id="cdf58-138">典型的真实提供程序是支持包含其他项的项，并将项从一条路径移动到另一种内部驱动器的支持。</span><span class="sxs-lookup"><span data-stu-id="cdf58-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="cdf58-139">支持容器的提供程序的示例，请参阅[编写容器提供程序](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf58-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="cdf58-140">支持移动的项的提供程序的示例，请参阅[编写导航提供程序](./writing-a-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf58-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cdf58-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdf58-141">See Also</span></span>

[<span data-ttu-id="cdf58-142">编写容器提供程序</span><span class="sxs-lookup"><span data-stu-id="cdf58-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="cdf58-143">编写导航提供程序</span><span class="sxs-lookup"><span data-stu-id="cdf58-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="cdf58-144">Windows PowerShell 提供程序概述</span><span class="sxs-lookup"><span data-stu-id="cdf58-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
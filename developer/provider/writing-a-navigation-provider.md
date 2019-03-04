---
title: 编写导航提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: a789b392bddd344ad583c93a1a55302329df9917
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863533"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="3f102-102">编写导航提供程序</span><span class="sxs-lookup"><span data-stu-id="3f102-102">Writing a navigation provider</span></span>

<span data-ttu-id="3f102-103">本主题介绍如何实现支持嵌套的容器 （多级别数据存储区），移动项和相对路径的 Windows PowerShell 提供程序方法。</span><span class="sxs-lookup"><span data-stu-id="3f102-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="3f102-104">导航提供程序必须派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="3f102-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="3f102-105">本主题中的示例中的提供程序使用 Access 数据库作为其数据存储区。</span><span class="sxs-lookup"><span data-stu-id="3f102-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="3f102-106">有几个帮助器方法和用于与数据库交互的类。</span><span class="sxs-lookup"><span data-stu-id="3f102-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="3f102-107">有关完整示例，包括帮助器方法，请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="3f102-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="3f102-108">有关 Windows PowerShell 提供程序的详细信息，请参阅[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3f102-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="3f102-109">实现导航方法</span><span class="sxs-lookup"><span data-stu-id="3f102-109">Implementing navigation methods</span></span>

<span data-ttu-id="3f102-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类实现支持嵌套的容器、 相对路径和移动的项的方法。</span><span class="sxs-lookup"><span data-stu-id="3f102-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="3f102-111">有关这些方法的完整列表，请参阅[NavigationCmdletProvider 方法](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3f102-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="3f102-112">本主题中的信息为基础[Windows PowerShell 提供程序快速入门](./windows-powershell-provider-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="3f102-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="3f102-113">本主题不会介绍如何设置提供程序项目的基础知识，或如何实现的方法继承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类，该类创建并删除驱动器。</span><span class="sxs-lookup"><span data-stu-id="3f102-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="3f102-114">本主题还不会涉及如何实现公开的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)或[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。</span><span class="sxs-lookup"><span data-stu-id="3f102-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="3f102-115">有关演示如何实现项 cmdlet 的示例，请参阅[编写项提供程序](./writing-an-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="3f102-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="3f102-116">有关演示如何实现容器的 cmdlet 示例，请参阅[编写容器提供程序](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="3f102-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="3f102-117">声明提供程序类</span><span class="sxs-lookup"><span data-stu-id="3f102-117">Declaring the provider class</span></span>

<span data-ttu-id="3f102-118">声明提供程序派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并给它装饰[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="3f102-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="3f102-119">实现 IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="3f102-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="3f102-120">[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法检查指定的路径处的项是否是一个容器。</span><span class="sxs-lookup"><span data-stu-id="3f102-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="3f102-121">实现 GetChildName</span><span class="sxs-lookup"><span data-stu-id="3f102-121">Implementing GetChildName</span></span>

<span data-ttu-id="3f102-122">[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法指定路径处获取的子项目的名称属性。</span><span class="sxs-lookup"><span data-stu-id="3f102-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="3f102-123">如果指定路径处的项不是容器的子级，则此方法应返回路径。</span><span class="sxs-lookup"><span data-stu-id="3f102-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="3f102-124">实现 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="3f102-124">Implementing GetParentPath</span></span>

<span data-ttu-id="3f102-125">[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法获取指定路径处的项的父级的路径。</span><span class="sxs-lookup"><span data-stu-id="3f102-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="3f102-126">如果指定的路径处的项是数据存储 （因此它没有父级） 的根，此方法应返回根路径。</span><span class="sxs-lookup"><span data-stu-id="3f102-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="3f102-127">实现 MakePath</span><span class="sxs-lookup"><span data-stu-id="3f102-127">Implementing MakePath</span></span>

<span data-ttu-id="3f102-128">[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法加入指定的父路径和指定的子路径来创建提供程序内部的路径 （的路径的信息类型，提供程序可以支持，请参阅[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3f102-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="3f102-129">PowerShell 引擎调用此方法，当用户调用[Microsoft.Powershell.Commands.Join 路径](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3f102-129">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="3f102-130">实现 NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="3f102-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="3f102-131">[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法采用`path`和`basepath`参数，并返回规范化的路径，它等效于`path`参数，相对于`basepath`参数。</span><span class="sxs-lookup"><span data-stu-id="3f102-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="3f102-132">实现 MoveItem</span><span class="sxs-lookup"><span data-stu-id="3f102-132">Implementing MoveItem</span></span>

<span data-ttu-id="3f102-133">[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法将项从指定的路径移动到指定的目标路径。</span><span class="sxs-lookup"><span data-stu-id="3f102-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="3f102-134">PowerShell 引擎调用此方法，当用户调用[Microsoft.Powershell.Commands.Move 项](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3f102-134">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="3f102-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f102-135">See Also</span></span>

[<span data-ttu-id="3f102-136">编写容器提供程序</span><span class="sxs-lookup"><span data-stu-id="3f102-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="3f102-137">Windows PowerShell 提供程序概述</span><span class="sxs-lookup"><span data-stu-id="3f102-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
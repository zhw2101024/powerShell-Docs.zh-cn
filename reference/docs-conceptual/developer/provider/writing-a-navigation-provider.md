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
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359866"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="469d7-102">编写导航提供程序</span><span class="sxs-lookup"><span data-stu-id="469d7-102">Writing a navigation provider</span></span>

<span data-ttu-id="469d7-103">本主题介绍如何实现支持嵌套容器的 Windows PowerShell 提供程序（多级别数据存储区）、移动项和相对路径。</span><span class="sxs-lookup"><span data-stu-id="469d7-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="469d7-104">导航提供程序必须从[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类中派生。</span><span class="sxs-lookup"><span data-stu-id="469d7-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="469d7-105">本主题中的示例中的提供程序使用 Access 数据库作为其数据存储。</span><span class="sxs-lookup"><span data-stu-id="469d7-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="469d7-106">有几个帮助器方法和用于与数据库进行交互的类。</span><span class="sxs-lookup"><span data-stu-id="469d7-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="469d7-107">有关包含帮助程序方法的完整示例，请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="469d7-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="469d7-108">有关 Windows PowerShell 提供程序的详细信息，请参阅[Windows Powershell 提供程序概述](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="469d7-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="469d7-109">实现导航方法</span><span class="sxs-lookup"><span data-stu-id="469d7-109">Implementing navigation methods</span></span>

<span data-ttu-id="469d7-110">[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类实现支持嵌套的容器、相对路径和移动项的方法。</span><span class="sxs-lookup"><span data-stu-id="469d7-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="469d7-111">有关这些方法的完整列表，请参阅[NavigationCmdletProvider 方法](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods)。</span><span class="sxs-lookup"><span data-stu-id="469d7-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="469d7-112">本主题以[Windows PowerShell 提供程序快速入门](./windows-powershell-provider-quickstart.md)中的信息为基础。</span><span class="sxs-lookup"><span data-stu-id="469d7-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="469d7-113">本主题不包含有关如何设置提供程序项目的基本知识，或者如何实现从[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类继承的方法，这些方法可创建和删除驱动器。</span><span class="sxs-lookup"><span data-stu-id="469d7-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="469d7-114">本主题还不介绍如何实现由[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)或[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类公开的方法的实现方法的实现方法的方法。</span><span class="sxs-lookup"><span data-stu-id="469d7-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="469d7-115">有关演示如何实现项 cmdlet 的示例，请参阅[编写项提供程序](./writing-an-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="469d7-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="469d7-116">有关演示如何实现容器 cmdlet 的示例，请参阅[编写容器提供程序](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="469d7-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="469d7-117">声明提供程序类</span><span class="sxs-lookup"><span data-stu-id="469d7-117">Declaring the provider class</span></span>

<span data-ttu-id="469d7-118">将提供程序声明为派生自[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类，并将其与[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)的修饰进行对其修饰。</span><span class="sxs-lookup"><span data-stu-id="469d7-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="469d7-119">实现 IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="469d7-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="469d7-120">[Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法用于检查指定路径处的项是否是一个容器。</span><span class="sxs-lookup"><span data-stu-id="469d7-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="469d7-121">实现 GetChildName</span><span class="sxs-lookup"><span data-stu-id="469d7-121">Implementing GetChildName</span></span>

<span data-ttu-id="469d7-122">[Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法获取指定路径处的子项的 name 属性的名称。</span><span class="sxs-lookup"><span data-stu-id="469d7-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="469d7-123">如果指定路径处的项不是容器的子级，则此方法应返回路径。</span><span class="sxs-lookup"><span data-stu-id="469d7-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="469d7-124">实现 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="469d7-124">Implementing GetParentPath</span></span>

<span data-ttu-id="469d7-125">[Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法获取指定路径处的项的父项的位置的路径。</span><span class="sxs-lookup"><span data-stu-id="469d7-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="469d7-126">如果指定路径中的项是数据存储区的根（因此没有父项），则此方法应返回根路径。</span><span class="sxs-lookup"><span data-stu-id="469d7-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="469d7-127">实现 MakePath</span><span class="sxs-lookup"><span data-stu-id="469d7-127">Implementing MakePath</span></span>

<span data-ttu-id="469d7-128">[Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法联接指定的父路径和指定的子路径以创建提供程序内部路径（有关提供程序可以支持的路径类型的信息，请参阅[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="469d7-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="469d7-129">当用户调用[JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet 时，PowerShell 引擎将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="469d7-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="469d7-130">实现 NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="469d7-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="469d7-131">[Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法采用 `path` 和 `basepath` 参数，并返回一个与第 3 @no__t 参数相对应的规范化路径，该路径相对于 `basepath`参数.</span><span class="sxs-lookup"><span data-stu-id="469d7-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="469d7-132">实现 MoveItem</span><span class="sxs-lookup"><span data-stu-id="469d7-132">Implementing MoveItem</span></span>

<span data-ttu-id="469d7-133">[Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法将项从指定的路径移动到指定的目标路径。</span><span class="sxs-lookup"><span data-stu-id="469d7-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="469d7-134">当用户调用[MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet 时，PowerShell 引擎将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="469d7-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="469d7-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="469d7-135">See Also</span></span>

[<span data-ttu-id="469d7-136">编写容器提供程序</span><span class="sxs-lookup"><span data-stu-id="469d7-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="469d7-137">Windows PowerShell 提供程序概述</span><span class="sxs-lookup"><span data-stu-id="469d7-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
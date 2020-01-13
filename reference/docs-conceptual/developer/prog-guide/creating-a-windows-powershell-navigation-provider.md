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
ms.openlocfilehash: f73e732ca9416b906b3647c5090dfa04ad940484
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416196"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="c565e-102">创建 Windows PowerShell 导航提供程序</span><span class="sxs-lookup"><span data-stu-id="c565e-102">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="c565e-103">本主题介绍如何创建可在数据存储中导航的 Windows PowerShell 导航提供程序。</span><span class="sxs-lookup"><span data-stu-id="c565e-103">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="c565e-104">这种类型的提供程序支持递归命令、嵌套容器和相对路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-104">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="c565e-105">你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此提供程序的源文件（AccessDBSampleProvider05.cs）。</span><span class="sxs-lookup"><span data-stu-id="c565e-105">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c565e-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="c565e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c565e-107">下载的源文件在 **\<PowerShell 示例 >** 目录中提供。</span><span class="sxs-lookup"><span data-stu-id="c565e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="c565e-108">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c565e-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="c565e-109">此处所述的提供程序使用户能够将 Access 数据库作为驱动器处理，使用户可以导航到数据库中的数据表。</span><span class="sxs-lookup"><span data-stu-id="c565e-109">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="c565e-110">在创建自己的导航提供程序时，您可以实现一些方法，这些方法可以使导航所需的驱动器限定路径，规范化相对路径，移动数据存储区的项，以及获取子名称的方法，获取项的父路径，以及测试确定项是否为容器。</span><span class="sxs-lookup"><span data-stu-id="c565e-110">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="c565e-111">请注意，此设计假设有一个数据库，该数据库具有名称为 ID 的字段，并且该字段的类型为 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="c565e-111">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="c565e-112">定义 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="c565e-112">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="c565e-113">Windows PowerShell 导航提供程序必须创建一个从[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类派生的 .net 类的 .net 类。</span><span class="sxs-lookup"><span data-stu-id="c565e-113">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="c565e-114">下面是本部分中所述的导航提供程序的类定义。</span><span class="sxs-lookup"><span data-stu-id="c565e-114">Here is the class definition for the navigation provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

<span data-ttu-id="c565e-115">请注意，在此提供程序中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包括两个参数。</span><span class="sxs-lookup"><span data-stu-id="c565e-115">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="c565e-116">第一个参数指定 Windows PowerShell 使用的提供程序的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="c565e-116">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="c565e-117">第二个参数指定 Windows PowerShell 特定功能，该功能是在命令处理过程中提供给 Windows PowerShell 运行时的。</span><span class="sxs-lookup"><span data-stu-id="c565e-117">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="c565e-118">对于此提供程序，没有添加的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="c565e-118">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="c565e-119">定义基本功能</span><span class="sxs-lookup"><span data-stu-id="c565e-119">Defining Base Functionality</span></span>

<span data-ttu-id="c565e-120">如[设计 PS 提供程序](./designing-your-windows-powershell-provider.md)中所述， [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类派生自多个提供不同提供程序功能的其他类。</span><span class="sxs-lookup"><span data-stu-id="c565e-120">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="c565e-121">因此，Windows PowerShell 导航提供程序必须定义这些类提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="c565e-121">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="c565e-122">若要实现添加特定于会话的初始化信息以及释放提供程序使用的资源的功能，请参阅[创建基本 PS 提供程序](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c565e-122">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="c565e-123">但是，大多数提供程序（包括此处所述的提供程序）可以使用 Windows PowerShell 提供的此功能的默认实现。</span><span class="sxs-lookup"><span data-stu-id="c565e-123">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="c565e-124">若要通过 Windows PowerShell 驱动器访问数据存储区，必须实现[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类的这些方法的实现方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-124">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="c565e-125">有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c565e-125">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="c565e-126">若要操作数据存储区的项（如获取、设置和清除项），提供程序必须实现[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类提供的方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-126">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="c565e-127">有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c565e-127">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="c565e-128">若要访问数据存储区的子项目或其名称，以及创建、复制、重命名和删除项的方法，必须实现[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类提供的方法，然后再执行。</span><span class="sxs-lookup"><span data-stu-id="c565e-128">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="c565e-129">有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c565e-129">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="c565e-130">创建 Windows PowerShell 路径</span><span class="sxs-lookup"><span data-stu-id="c565e-130">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="c565e-131">Windows PowerShell 导航提供程序使用提供程序内部的 Windows PowerShell 路径导航数据存储区中的项。</span><span class="sxs-lookup"><span data-stu-id="c565e-131">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="c565e-132">若要创建提供程序内部路径，提供程序必须实现[Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法，以支持来自组合路径 cmdlet 的调用。</span><span class="sxs-lookup"><span data-stu-id="c565e-132">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="c565e-133">此方法使用父路径和子路径之间的特定于提供程序的路径分隔符将父路径和子路径合并到提供程序内部路径中。</span><span class="sxs-lookup"><span data-stu-id="c565e-133">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="c565e-134">默认实现采用带有 "/" 或 "\\" 的路径作为路径分隔符，将路径分隔符规范化为 "\\"，将父路径部分与子路径部分组合在一起，然后返回包含组合路径的字符串。</span><span class="sxs-lookup"><span data-stu-id="c565e-134">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="c565e-135">此导航提供程序不实现此方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-135">This navigation provider does not implement this method.</span></span> <span data-ttu-id="c565e-136">但是，下面的代码是[Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法的默认实现方式。</span><span class="sxs-lookup"><span data-stu-id="c565e-136">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="c565e-137">有关实现 MakePath 的注意事项</span><span class="sxs-lookup"><span data-stu-id="c565e-137">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="c565e-138">以下情况可能适用于你的[Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)实现：</span><span class="sxs-lookup"><span data-stu-id="c565e-138">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="c565e-139">[Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法的实现不应将该路径作为提供程序命名空间中的合法完全限定路径进行验证。</span><span class="sxs-lookup"><span data-stu-id="c565e-139">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="c565e-140">请注意，每个参数只能表示部分路径，并且组合部件可能不会生成完全限定的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-140">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="c565e-141">例如，filesystem 提供程序的[Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法可能在 `parent` 参数中接收 "windows\system32"，在 `child` 参数中接收 ""。</span><span class="sxs-lookup"><span data-stu-id="c565e-141">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="c565e-142">方法使用 "\\" 分隔符来联接这些值，并返回 "windows\system32\abc.dll"，这不是一个完全限定的文件系统路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-142">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="c565e-143">在对[Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)的调用中提供的路径部分可能包含提供程序命名空间中不允许使用的字符。</span><span class="sxs-lookup"><span data-stu-id="c565e-143">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="c565e-144">这些字符最有可能用于通配符扩展，而此方法的实现不应将其删除。</span><span class="sxs-lookup"><span data-stu-id="c565e-144">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="c565e-145">检索父路径</span><span class="sxs-lookup"><span data-stu-id="c565e-145">Retrieving the Parent Path</span></span>

<span data-ttu-id="c565e-146">Windows PowerShell 导航提供程序可实现[Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法，以检索指定完整或部分提供程序特定路径的父部分。</span><span class="sxs-lookup"><span data-stu-id="c565e-146">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="c565e-147">方法移除路径的子部分，并返回父路径部分。</span><span class="sxs-lookup"><span data-stu-id="c565e-147">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="c565e-148">`root` 参数指定驱动器根目录的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-148">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="c565e-149">如果已装载的驱动器未用于检索操作，则此参数可以为 null 或空。</span><span class="sxs-lookup"><span data-stu-id="c565e-149">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="c565e-150">如果指定了根，则该方法必须返回与根位于同一树中的容器的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-150">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="c565e-151">示例导航提供程序不会重写此方法，但会使用默认实现。</span><span class="sxs-lookup"><span data-stu-id="c565e-151">The sample navigation provider does not override this method, but uses the default implementation.</span></span> <span data-ttu-id="c565e-152">它接受使用 "/" 和 "\\" 作为路径分隔符的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-152">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="c565e-153">它首先将路径规范化为仅具有 "\\" 分隔符，然后在最后一个 "\\" 处拆分父路径，并返回父路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-153">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="c565e-154">要记住如何实现 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="c565e-154">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="c565e-155">[Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法的实现应将词法上的路径拆分为提供程序命名空间的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="c565e-155">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="c565e-156">例如，filesystem 提供程序使用此方法查找最后一个 "\\"，并将所有内容返回到分隔符的左侧。</span><span class="sxs-lookup"><span data-stu-id="c565e-156">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="c565e-157">检索子路径名称</span><span class="sxs-lookup"><span data-stu-id="c565e-157">Retrieve the Child Path Name</span></span>

<span data-ttu-id="c565e-158">你的导航提供程序将实现[Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法，以检索位于指定的完整或部分提供程序特定路径上的项的子级的名称（叶元素）。</span><span class="sxs-lookup"><span data-stu-id="c565e-158">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="c565e-159">示例导航提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-159">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="c565e-160">默认实现如下所示。</span><span class="sxs-lookup"><span data-stu-id="c565e-160">The default implementation is shown below.</span></span> <span data-ttu-id="c565e-161">它接受使用 "/" 和 "\\" 作为路径分隔符的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-161">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="c565e-162">它首先将路径规范化为仅具有 "\\" 分隔符，然后在最后一个 "\\" 处拆分父路径，并返回子路径部分的名称。</span><span class="sxs-lookup"><span data-stu-id="c565e-162">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="c565e-163">有关实现 GetChildName 的注意事项</span><span class="sxs-lookup"><span data-stu-id="c565e-163">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="c565e-164">你的[Navigationcmdletprovider Getchildname](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法的实现应在路径分隔符上拆分词法上的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-164">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="c565e-165">如果提供的路径不包含任何路径分隔符，方法应返回未修改的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-165">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c565e-166">对此方法的调用中提供的路径可能包含提供程序命名空间中的非法字符。</span><span class="sxs-lookup"><span data-stu-id="c565e-166">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="c565e-167">这些字符最有可能用于通配符扩展或正则表达式匹配，而此方法的实现不应将其删除。</span><span class="sxs-lookup"><span data-stu-id="c565e-167">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="c565e-168">确定项是否为容器</span><span class="sxs-lookup"><span data-stu-id="c565e-168">Determining if an Item is a Container</span></span>

<span data-ttu-id="c565e-169">导航提供程序可以实现[Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法，以确定指定的路径是否指示一个容器。</span><span class="sxs-lookup"><span data-stu-id="c565e-169">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="c565e-170">如果路径表示容器，则返回 true; 否则返回 false。</span><span class="sxs-lookup"><span data-stu-id="c565e-170">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="c565e-171">用户需要此方法才能将 `Test-Path` cmdlet 用于提供的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-171">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="c565e-172">下面的代码演示了示例导航提供程序中的[Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)实现。</span><span class="sxs-lookup"><span data-stu-id="c565e-172">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="c565e-173">方法验证指定的路径是否正确，并且如果表存在，则返回 true; 如果路径指示容器，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="c565e-173">The method verifies that  the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="c565e-174">有关实现 IsItemContainer 的注意事项</span><span class="sxs-lookup"><span data-stu-id="c565e-174">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="c565e-175">你的导航提供程序 .NET 类可以声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="c565e-175">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="c565e-176">在这种情况下， [Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)的实现会要求确保传递的路径满足要求的要求。</span><span class="sxs-lookup"><span data-stu-id="c565e-176">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="c565e-177">为此，此方法应访问相应的属性，例如， [Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)属性的属性为。</span><span class="sxs-lookup"><span data-stu-id="c565e-177">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="c565e-178">移动项</span><span class="sxs-lookup"><span data-stu-id="c565e-178">Moving an Item</span></span>

<span data-ttu-id="c565e-179">为了支持 `Move-Item` cmdlet，你的导航提供程序将实现[Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-179">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="c565e-180">此方法将 `path` 参数指定的项移动到在 `destination` 参数提供的路径中的容器。</span><span class="sxs-lookup"><span data-stu-id="c565e-180">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="c565e-181">示例导航提供程序不重写[Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-181">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="c565e-182">下面是默认实现。</span><span class="sxs-lookup"><span data-stu-id="c565e-182">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="c565e-183">有关实现 MoveItem 的注意事项</span><span class="sxs-lookup"><span data-stu-id="c565e-183">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="c565e-184">你的导航提供程序 .NET 类可以声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="c565e-184">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="c565e-185">在这种情况下， [Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)的实现必须确保传递的路径符合要求。</span><span class="sxs-lookup"><span data-stu-id="c565e-185">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="c565e-186">为此，方法应访问相应的属性，例如**CmdletProvider**属性。</span><span class="sxs-lookup"><span data-stu-id="c565e-186">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="c565e-187">默认情况下，此方法的重写不应将对象移到现有对象上，除非[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="c565e-187">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="c565e-188">例如，filesystem 提供程序将不会通过现有的 c:\bar.txt 文件复制 c:\temp\abc.txt，除非[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="c565e-188">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="c565e-189">如果 `destination` 参数中指定的路径存在并且是一个容器，则不需要[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性（& e）。</span><span class="sxs-lookup"><span data-stu-id="c565e-189">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="c565e-190">在这种情况下， [Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)应将 `path` 参数指示的项移动到由 `destination` 参数指示为子级的容器。</span><span class="sxs-lookup"><span data-stu-id="c565e-190">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="c565e-191">在对数据存储进行任何更改之前，你的[Navigationcmdletprovider 和 Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并检查其返回值，然后再进行更改。</span><span class="sxs-lookup"><span data-stu-id="c565e-191">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="c565e-192">此方法用于在对系统状态进行更改时（例如，删除文件时）确认操作的执行。</span><span class="sxs-lookup"><span data-stu-id="c565e-192">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span> <span data-ttu-id="c565e-193">[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改为用户的资源的名称，Windows PowerShell 运行时在确定应该向用户显示的内容时，会考虑到任何命令行设置或首选项变量。</span><span class="sxs-lookup"><span data-stu-id="c565e-193">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="c565e-194">在对 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 的调用返回 `true` 后，[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法应调用 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 方法，则为，否则返回Navigationcmdletprovider. Moveitem \*方法的调用方，则为。</span><span class="sxs-lookup"><span data-stu-id="c565e-194">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="c565e-195">此方法将向用户发送一条消息，以允许反馈以指示是否应继续进行操作。</span><span class="sxs-lookup"><span data-stu-id="c565e-195">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="c565e-196">提供程序应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作为额外检查来检查是否存在潜在的危险系统修改。</span><span class="sxs-lookup"><span data-stu-id="c565e-196">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="c565e-197">将动态参数附加到移动项 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c565e-197">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="c565e-198">有时 `Move-Item` cmdlet 需要在运行时动态提供的其他参数。</span><span class="sxs-lookup"><span data-stu-id="c565e-198">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="c565e-199">若要提供这些动态参数，导航提供程序必须实现[Navigationcmdletprovider. Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法，以便从所指示的路径处的项获取所需的参数值，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。</span><span class="sxs-lookup"><span data-stu-id="c565e-199">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="c565e-200">此导航提供程序不实现此方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-200">This navigation provider does not implement this method.</span></span> <span data-ttu-id="c565e-201">但是，下面的代码是[Navigationcmdletprovider. Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)的默认实现。</span><span class="sxs-lookup"><span data-stu-id="c565e-201">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="c565e-202">规范化相对路径</span><span class="sxs-lookup"><span data-stu-id="c565e-202">Normalizing a Relative Path</span></span>

<span data-ttu-id="c565e-203">你的导航提供程序将实现[Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法，以将 `path` 参数中指示的完全限定路径规范化为相对于 `basePath` 参数所指定的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-203">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="c565e-204">方法返回规范化路径的字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="c565e-204">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="c565e-205">如果 `path` 参数指定了不存在的路径，则它会写入错误。</span><span class="sxs-lookup"><span data-stu-id="c565e-205">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="c565e-206">示例导航提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-206">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="c565e-207">下面是默认实现。</span><span class="sxs-lookup"><span data-stu-id="c565e-207">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="c565e-208">有关实现 NormalizeRelativePath 的注意事项</span><span class="sxs-lookup"><span data-stu-id="c565e-208">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="c565e-209">你的[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)的实现应分析 `path` 参数，但它不一定要使用纯粹的语法分析方法。</span><span class="sxs-lookup"><span data-stu-id="c565e-209">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="c565e-210">建议设计此方法，以便使用路径在数据存储中查找路径信息，并创建与大小写和标准化路径语法匹配的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-210">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c565e-211">代码示例</span><span class="sxs-lookup"><span data-stu-id="c565e-211">Code Sample</span></span>

<span data-ttu-id="c565e-212">有关完整的示例代码，请参阅[AccessDbProviderSample05 代码示例](./accessdbprovidersample05-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c565e-212">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c565e-213">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="c565e-213">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c565e-214">提供程序可以将成员添加到现有对象或定义新的对象。</span><span class="sxs-lookup"><span data-stu-id="c565e-214">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="c565e-215">有关详细信息，请参阅[扩展对象类型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="c565e-215">For more information, see[Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="c565e-216">生成 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="c565e-216">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="c565e-217">有关详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="c565e-217">For more information, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="c565e-218">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="c565e-218">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="c565e-219">向 windows powershell 注册 Windows PowerShell 提供程序后，可以通过在命令行上运行支持的 cmdlet （包括派生提供的 cmdlet）来测试 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="c565e-219">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="c565e-220">此示例将测试示例导航提供程序。</span><span class="sxs-lookup"><span data-stu-id="c565e-220">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="c565e-221">运行新的 shell，并使用 `Set-Location` cmdlet 来设置用于指示 Access 数据库的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-221">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="c565e-222">现在，运行 `Get-Childitem` cmdlet 以检索数据库项的列表，这些项是可用的数据库表。</span><span class="sxs-lookup"><span data-stu-id="c565e-222">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="c565e-223">对于每个表，此 cmdlet 还将检索表行的数目。</span><span class="sxs-lookup"><span data-stu-id="c565e-223">For each table, this cmdlet also retrieves the number of table rows.</span></span>

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

3. <span data-ttu-id="c565e-224">再次使用 `Set-Location` cmdlet 设置 Employees 数据表的位置。</span><span class="sxs-lookup"><span data-stu-id="c565e-224">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="c565e-225">现在，让我们使用 `Get-Location` cmdlet 来检索 Employees 表的路径。</span><span class="sxs-lookup"><span data-stu-id="c565e-225">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="c565e-226">现在，使用 `Get-Childitem` cmdlet 通过管道传递到 `Format-Table` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c565e-226">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="c565e-227">这组 cmdlet 可检索 Employees 数据表（表行）的项。</span><span class="sxs-lookup"><span data-stu-id="c565e-227">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="c565e-228">它们按照 `Format-Table` cmdlet 指定的格式进行格式化。</span><span class="sxs-lookup"><span data-stu-id="c565e-228">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

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

6. <span data-ttu-id="c565e-229">你现在可以运行 `Get-Item` cmdlet 来检索 Employees 数据表的第0行的项。</span><span class="sxs-lookup"><span data-stu-id="c565e-229">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

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

7. <span data-ttu-id="c565e-230">再次使用 `Get-Item` cmdlet 来检索第0行中各项的雇员数据。</span><span class="sxs-lookup"><span data-stu-id="c565e-230">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c565e-231">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c565e-231">See Also</span></span>

[<span data-ttu-id="c565e-232">创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="c565e-232">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="c565e-233">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="c565e-233">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="c565e-234">扩展对象类型和格式</span><span class="sxs-lookup"><span data-stu-id="c565e-234">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c565e-235">实现容器 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="c565e-235">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

[<span data-ttu-id="c565e-236">如何注册 Cmdlet、提供程序和主机应用程序</span><span class="sxs-lookup"><span data-stu-id="c565e-236">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c565e-237">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="c565e-237">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c565e-238">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c565e-238">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

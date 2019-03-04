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
ms.openlocfilehash: 066aa188d5d7dfde5af424a3bb8f15ff51c1e936
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856953"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="eed59-102">创建 Windows PowerShell 导航提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-102">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="eed59-103">本主题介绍如何创建可以浏览数据存储区的 Windows PowerShell 导航提供程序。</span><span class="sxs-lookup"><span data-stu-id="eed59-103">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="eed59-104">这种类型的提供程序支持递归命令、 嵌套的容器和相对路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-104">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="eed59-105">您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider05.cs)。</span><span class="sxs-lookup"><span data-stu-id="eed59-105">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="eed59-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="eed59-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="eed59-107">您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider05.cs)。</span><span class="sxs-lookup"><span data-stu-id="eed59-107">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="eed59-108">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="eed59-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="eed59-109">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="eed59-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="eed59-110">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="eed59-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="eed59-111">此处所述的提供程序使用户句柄 Access 数据库作为驱动器，从而使用户可以导航到数据库中数据的表。</span><span class="sxs-lookup"><span data-stu-id="eed59-111">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="eed59-112">在创建自己的导航提供程序，可以实现方法，可使驱动器限定路径所需的导航、 规范化的相对路径，移动项的数据存储，以及获取子名称、 获取项的父路径和测试的方法若要确定某个项是一个容器中。</span><span class="sxs-lookup"><span data-stu-id="eed59-112">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="eed59-113">请注意，此设计假定具有名为 id，字段的数据库字段的类型是 LongInteger。</span><span class="sxs-lookup"><span data-stu-id="eed59-113">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

<span data-ttu-id="eed59-114">以下列表包含本主题中的部分。</span><span class="sxs-lookup"><span data-stu-id="eed59-114">The following list includes sections in this topic.</span></span> <span data-ttu-id="eed59-115">如果您不熟悉编写 Windows PowerShell 导航提供程序，读取此信息显示的顺序。</span><span class="sxs-lookup"><span data-stu-id="eed59-115">If you are unfamiliar with writing a Windows PowerShell navigation provider, read this information in the order that it appears.</span></span> <span data-ttu-id="eed59-116">但是，如果你熟悉编写 Windows PowerShell 导航提供程序，请直接转到所需的信息。</span><span class="sxs-lookup"><span data-stu-id="eed59-116">However, if you are familiar with writing a Windows PowerShell navigation provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="eed59-117">定义 PS 导航提供程序类</span><span class="sxs-lookup"><span data-stu-id="eed59-117">Defining a PS Navigation Provider Class</span></span>](#Define-the-Windows-PowerShell-provider)

- [<span data-ttu-id="eed59-118">定义基本功能</span><span class="sxs-lookup"><span data-stu-id="eed59-118">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="eed59-119">创建 PS 路径</span><span class="sxs-lookup"><span data-stu-id="eed59-119">Creating a PS Path</span></span>](#Creating-a-Windows-PowerShell-Path)

- [<span data-ttu-id="eed59-120">检索父路径</span><span class="sxs-lookup"><span data-stu-id="eed59-120">Retrieving the Parent Path</span></span>](#Retrieving-the-Parent-Path)

- [<span data-ttu-id="eed59-121">检索子路径名称</span><span class="sxs-lookup"><span data-stu-id="eed59-121">Retrieving the Child Path Name</span></span>](#Retrieve-the-Child-Path-Name)

- [<span data-ttu-id="eed59-122">确定某个项是否容器</span><span class="sxs-lookup"><span data-stu-id="eed59-122">Determining if an Item is a Container</span></span>](#Determining-if-an-Item-is-a-Container)

- [<span data-ttu-id="eed59-123">将项移</span><span class="sxs-lookup"><span data-stu-id="eed59-123">Moving an Item</span></span>](#Moving-an-Item)

- [<span data-ttu-id="eed59-124">附加到的动态参数`Move-Item`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eed59-124">Attaching Dynamic Parameters to the `Move-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [<span data-ttu-id="eed59-125">规范化的相对路径</span><span class="sxs-lookup"><span data-stu-id="eed59-125">Normalizing a Relative Path</span></span>](#Normalizing-a-Relative-Path)

- [<span data-ttu-id="eed59-126">代码示例</span><span class="sxs-lookup"><span data-stu-id="eed59-126">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="eed59-127">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="eed59-127">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="eed59-128">生成 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-128">Building the Windows PowerShell Provider</span></span>](#Building-the-Windows-PowerShell-provider)

- [<span data-ttu-id="eed59-129">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-129">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="eed59-130">定义 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-130">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="eed59-131">Windows PowerShell 导航提供程序必须创建一个.NET 类派生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="eed59-131">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="eed59-132">下面是在本部分中所述的导航提供程序的类定义。</span><span class="sxs-lookup"><span data-stu-id="eed59-132">Here is the class definition for the navigation provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

<span data-ttu-id="eed59-133">请注意，在此提供程序[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包含两个参数。</span><span class="sxs-lookup"><span data-stu-id="eed59-133">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="eed59-134">第一个参数指定由 Windows PowerShell 提供程序的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="eed59-134">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="eed59-135">第二个参数指定的 Windows PowerShell 的特定功能的提供程序公开到 Windows PowerShell 运行时在命令处理过程。</span><span class="sxs-lookup"><span data-stu-id="eed59-135">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="eed59-136">为此提供程序，没有 Windows PowerShell 特定功能添加的。</span><span class="sxs-lookup"><span data-stu-id="eed59-136">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="eed59-137">定义基本功能</span><span class="sxs-lookup"><span data-stu-id="eed59-137">Defining Base Functionality</span></span>

<span data-ttu-id="eed59-138">如中所述[设计您的 PS 提供者](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类派生提供不同的提供程序的多个其他类功能。</span><span class="sxs-lookup"><span data-stu-id="eed59-138">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="eed59-139">Windows PowerShell 导航提供程序，因此，必须定义所有这些类提供的功能。</span><span class="sxs-lookup"><span data-stu-id="eed59-139">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="eed59-140">若要实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能，请参阅[创建基本的 PS 提供程序](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="eed59-140">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="eed59-141">但是，大多数提供程序 （包括此处所述的提供程序） 可以使用 Windows PowerShell 提供此功能的默认实现。</span><span class="sxs-lookup"><span data-stu-id="eed59-141">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="eed59-142">若要通过 Windows PowerShell 驱动器中获取对数据存储的访问，必须实现的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="eed59-142">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="eed59-143">有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="eed59-143">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="eed59-144">若要操作的数据存储，如获取、 设置和清除项的项提供程序必须实现提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="eed59-144">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="eed59-145">有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="eed59-145">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="eed59-146">若要访问的子项或它们的名称的数据存储，以及创建、 复制、 重命名和删除项，方法必须实现提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="eed59-146">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="eed59-147">有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="eed59-147">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="eed59-148">创建 Windows PowerShell 路径</span><span class="sxs-lookup"><span data-stu-id="eed59-148">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="eed59-149">Windows PowerShell 导航提供程序使用提供程序内部的 Windows PowerShell 路径导航数据存储的项。</span><span class="sxs-lookup"><span data-stu-id="eed59-149">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="eed59-150">若要创建的提供程序内部的路径提供程序必须实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)到支持的方法调用从合并路径 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eed59-150">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="eed59-151">此方法将父和子路径合并到提供程序内部的路径，使用特定于提供程序的路径分隔符之间的父和子路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-151">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="eed59-152">默认实现采用路径替换为"/"或"\\"作为路径分隔符，规范化为路径分隔符"\\"，将父和子路径部分与它们之间的分隔符相结合，然后返回一个字符串，包含组合的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-152">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="eed59-153">此导航提供程序未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-153">This navigation provider does not implement this method.</span></span> <span data-ttu-id="eed59-154">但是，下面的代码是的默认实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-154">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="eed59-155">要实现 MakePath 记住的事项</span><span class="sxs-lookup"><span data-stu-id="eed59-155">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="eed59-156">以下条件可能适用于特定的实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span><span class="sxs-lookup"><span data-stu-id="eed59-156">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="eed59-157">实现[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法应验证为合法的完全限定路径提供程序命名空间中的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-157">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="eed59-158">请注意，每个参数只能表示一个路径的一部分，组合的部件可能不会生成完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-158">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="eed59-159">例如， [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) filesystem 提供程序的方法中可能会出现"windows\system32"`parent`参数，并在中的"abc.dll"`child`参数。</span><span class="sxs-lookup"><span data-stu-id="eed59-159">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="eed59-160">该方法联接这些值用于"\\"分隔符和返回"windows\system32\abc.dll"，这不是完全限定文件系统路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-160">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="eed59-161">对的调用中提供的路径部分[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)可能包含提供程序命名空间中不允许的字符。</span><span class="sxs-lookup"><span data-stu-id="eed59-161">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="eed59-162">这些字符很可能用于通配符扩展，此方法的实现不应删除它们。</span><span class="sxs-lookup"><span data-stu-id="eed59-162">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="eed59-163">检索父路径</span><span class="sxs-lookup"><span data-stu-id="eed59-163">Retrieving the Parent Path</span></span>

<span data-ttu-id="eed59-164">Windows PowerShell 导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法来检索父部件所指示的完整或部分特定于提供程序的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-164">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="eed59-165">该方法删除路径的子部分，并返回对象的父路径部分。</span><span class="sxs-lookup"><span data-stu-id="eed59-165">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="eed59-166">`root`参数指定的驱动器的根目录的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-166">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="eed59-167">此参数可以为 null 或为空，如果已装载的驱动器不是用于检索操作。</span><span class="sxs-lookup"><span data-stu-id="eed59-167">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="eed59-168">如果指定一个根，则该方法必须返回路径到根所在的同一树中的容器。</span><span class="sxs-lookup"><span data-stu-id="eed59-168">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="eed59-169">示例导航提供程序不重写此方法，但使用的默认实现。</span><span class="sxs-lookup"><span data-stu-id="eed59-169">The sample navigation provider does not override this method, but uses the default implementation.</span></span> <span data-ttu-id="eed59-170">它接受同时使用的路径"/"和"\\"作为路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="eed59-170">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="eed59-171">它首先规范化的路径以仅具有"\\"分隔符，然后将关闭的父路径拆分最后一个"\\"，并返回父路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-171">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="eed59-172">若要记住有关实现 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="eed59-172">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="eed59-173">实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法应拆分词法上提供程序命名空间的路径分隔符的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-173">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="eed59-174">例如，filesystem 提供程序使用此方法查找最后一个"\\"，并返回的所有内容分隔符的左侧。</span><span class="sxs-lookup"><span data-stu-id="eed59-174">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="eed59-175">检索子路径名称</span><span class="sxs-lookup"><span data-stu-id="eed59-175">Retrieve the Child Path Name</span></span>

<span data-ttu-id="eed59-176">在导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法来检索项的子级的名称 （叶元素） 位于所指示的完整或部分特定于提供程序的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-176">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="eed59-177">示例导航提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-177">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="eed59-178">如下所示的默认实现。</span><span class="sxs-lookup"><span data-stu-id="eed59-178">The default implementation is shown below.</span></span> <span data-ttu-id="eed59-179">它接受同时使用的路径"/"和"\\"作为路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="eed59-179">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="eed59-180">它首先规范化的路径以仅具有"\\"分隔符，然后将关闭的父路径拆分最后一个"\\"，并返回路径部分的子级的名称。</span><span class="sxs-lookup"><span data-stu-id="eed59-180">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="eed59-181">要实现 GetChildName 记住的事项</span><span class="sxs-lookup"><span data-stu-id="eed59-181">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="eed59-182">实现[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法应拆分词法上的路径分隔符的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-182">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="eed59-183">如果提供的路径不包含任何路径分隔符，该方法应返回以未修改形式的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-183">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eed59-184">对此方法调用中提供的路径可能包含在提供程序命名空间中是非法的字符。</span><span class="sxs-lookup"><span data-stu-id="eed59-184">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="eed59-185">这些字符很可能用于通配符扩展或正则表达式匹配，并且此方法的实现不应删除它们。</span><span class="sxs-lookup"><span data-stu-id="eed59-185">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="eed59-186">确定某个项是否容器</span><span class="sxs-lookup"><span data-stu-id="eed59-186">Determining if an Item is a Container</span></span>

<span data-ttu-id="eed59-187">导航提供程序可以实现[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法来确定指定的路径是否指示容器。</span><span class="sxs-lookup"><span data-stu-id="eed59-187">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="eed59-188">它返回路径表示容器和 false 否则如果为 true。</span><span class="sxs-lookup"><span data-stu-id="eed59-188">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="eed59-189">用户需要能够使用此方法`Test-Path`cmdlet 提供的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-189">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="eed59-190">下面的代码演示[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)中我们的示例导航提供程序的实现。</span><span class="sxs-lookup"><span data-stu-id="eed59-190">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="eed59-191">该方法会验证指定的路径正确，以及如果表存在，并且如果该路径表示一个容器，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="eed59-191">The method verifies that  the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="eed59-192">要实现 IsItemContainer 记住的事项</span><span class="sxs-lookup"><span data-stu-id="eed59-192">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="eed59-193">导航提供程序.NET 类可能会从声明提供程序的功能的 ExpandWildcards、 筛选器、 Include 或 Exclude [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="eed59-193">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="eed59-194">在此情况下，实现[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)需要确保传递的路径是否满足要求。</span><span class="sxs-lookup"><span data-stu-id="eed59-194">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="eed59-195">若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)属性。</span><span class="sxs-lookup"><span data-stu-id="eed59-195">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="eed59-196">将项移</span><span class="sxs-lookup"><span data-stu-id="eed59-196">Moving an Item</span></span>

<span data-ttu-id="eed59-197">支持`Move-Item`cmdlet 导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-197">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="eed59-198">此方法将移动指定的项`path`参数中提供的路径处容器`destination`参数。</span><span class="sxs-lookup"><span data-stu-id="eed59-198">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="eed59-199">示例导航提供程序不会覆盖[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-199">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="eed59-200">下面是默认实现。</span><span class="sxs-lookup"><span data-stu-id="eed59-200">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="eed59-201">要实现 MoveItem 记住的事项</span><span class="sxs-lookup"><span data-stu-id="eed59-201">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="eed59-202">导航提供程序.NET 类可能会从声明提供程序的功能的 ExpandWildcards、 筛选器、 Include 或 Exclude [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="eed59-202">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="eed59-203">在此情况下，实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)必须确保传递的路径是否满足要求。</span><span class="sxs-lookup"><span data-stu-id="eed59-203">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="eed59-204">若要执行此操作，该方法应访问相应的属性，例如，则**CmdletProvider.Exclude**属性。</span><span class="sxs-lookup"><span data-stu-id="eed59-204">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="eed59-205">默认情况下，重写此方法不应将移动对象对现有对象除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="eed59-205">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="eed59-206">例如，filesystem 提供程序不会将复制 c:\temp\abc.txt 通过现有 c:\bar.txt 文件除非[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="eed59-206">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="eed59-207">如果在指定的路径`destination`参数存在，它是一个容器， [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性不是必需。</span><span class="sxs-lookup"><span data-stu-id="eed59-207">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="eed59-208">在这种情况下， [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)应移动的项由`path`到容器参数为由`destination`作为子参数。</span><span class="sxs-lookup"><span data-stu-id="eed59-208">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="eed59-209">实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并向数据存储区进行任何更改之前检查它的返回值。</span><span class="sxs-lookup"><span data-stu-id="eed59-209">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="eed59-210">此方法用于确认操作的执行时更改为系统状态，例如，删除文件。</span><span class="sxs-lookup"><span data-stu-id="eed59-210">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span> <span data-ttu-id="eed59-211">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改对用户来说，与 Windows PowerShell 运行时将考虑在内的任何命令行设置或首选项变量中的资源的名称确定向用户应显示的内容。</span><span class="sxs-lookup"><span data-stu-id="eed59-211">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="eed59-212">在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-212">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="eed59-213">此方法将消息发送到用户允许反馈以说是否应继续执行该操作。</span><span class="sxs-lookup"><span data-stu-id="eed59-213">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="eed59-214">您的提供程序应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)作为具有潜在危险的系统修改为额外检查。</span><span class="sxs-lookup"><span data-stu-id="eed59-214">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="eed59-215">附加到 Move-item Cmdlet 的动态参数</span><span class="sxs-lookup"><span data-stu-id="eed59-215">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="eed59-216">有时`Move-Item`cmdlet 需要在运行时动态提供的其他参数。</span><span class="sxs-lookup"><span data-stu-id="eed59-216">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="eed59-217">若要提供这些动态参数，请导航提供程序必须实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法以获取所需的参数值从指定的路径，并返回处的项具有属性和字段与分析的对象属性类似于 cmdlet 类或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。</span><span class="sxs-lookup"><span data-stu-id="eed59-217">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="eed59-218">此导航提供程序未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-218">This navigation provider does not implement this method.</span></span> <span data-ttu-id="eed59-219">但是，下面的代码是的默认实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)。</span><span class="sxs-lookup"><span data-stu-id="eed59-219">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="eed59-220">规范化的相对路径</span><span class="sxs-lookup"><span data-stu-id="eed59-220">Normalizing a Relative Path</span></span>

<span data-ttu-id="eed59-221">在导航提供程序实现[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)中所示方法进行标准化的完全限定路径`path`参数为指定的路径的相对路径`basePath`参数。</span><span class="sxs-lookup"><span data-stu-id="eed59-221">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="eed59-222">该方法返回的字符串表示形式的规范化路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-222">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="eed59-223">它将写入错误，如果`path`参数指定不存在的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-223">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="eed59-224">示例导航提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="eed59-224">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="eed59-225">下面是默认实现。</span><span class="sxs-lookup"><span data-stu-id="eed59-225">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="eed59-226">要实现 NormalizeRelativePath 记住的事项</span><span class="sxs-lookup"><span data-stu-id="eed59-226">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="eed59-227">实现[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)应分析`path`参数，但它不需要使用纯粹的语法分析。</span><span class="sxs-lookup"><span data-stu-id="eed59-227">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="eed59-228">此方法以使用路径来查找数据存储区中的路径信息，并创建路径匹配大小写的设计建议和标准化路径语法。</span><span class="sxs-lookup"><span data-stu-id="eed59-228">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="eed59-229">代码示例</span><span class="sxs-lookup"><span data-stu-id="eed59-229">Code Sample</span></span>

<span data-ttu-id="eed59-230">有关完整的示例代码，请参阅[AccessDbProviderSample05 代码示例](./accessdbprovidersample05-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eed59-230">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="eed59-231">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="eed59-231">Defining Object Types and Formatting</span></span>

<span data-ttu-id="eed59-232">很可能要将成员添加到现有对象或定义新对象的提供程序。</span><span class="sxs-lookup"><span data-stu-id="eed59-232">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="eed59-233">有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="eed59-233">For more information, see[Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>
<span data-ttu-id="eed59-234">很可能要将成员添加到现有对象或定义新对象的提供程序。</span><span class="sxs-lookup"><span data-stu-id="eed59-234">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="eed59-235">有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="eed59-235">For more information, see[Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="eed59-236">生成 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-236">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="eed59-237">有关详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="eed59-237">For more information, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>
<span data-ttu-id="eed59-238">有关详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="eed59-238">For more information, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="eed59-239">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-239">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="eed59-240">Windows PowerShell 提供程序具有已注册到 Windows PowerShell，可以通过运行命令行，其中包括可供派生的 cmdlet 上受支持的 cmdlet 来测试它。</span><span class="sxs-lookup"><span data-stu-id="eed59-240">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="eed59-241">此示例将测试的示例导航提供程序。</span><span class="sxs-lookup"><span data-stu-id="eed59-241">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="eed59-242">运行新的 shell，并使用`Set-Location`cmdlet 设置用于指示访问数据库的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-242">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="eed59-243">现在，运行`Get-Childitem`cmdlet 来检索是可用的数据库表的数据库项的列表。</span><span class="sxs-lookup"><span data-stu-id="eed59-243">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="eed59-244">对于每个表，此 cmdlet 还将检索表行数。</span><span class="sxs-lookup"><span data-stu-id="eed59-244">For each table, this cmdlet also retrieves the number of table rows.</span></span>

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

3. <span data-ttu-id="eed59-245">使用`Set-Location`cmdlet 再次设置员工数据表的位置。</span><span class="sxs-lookup"><span data-stu-id="eed59-245">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="eed59-246">现在，使用`Get-Location`cmdlet 来检索 Employees 表的路径。</span><span class="sxs-lookup"><span data-stu-id="eed59-246">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="eed59-247">现在，使用`Get-Childitem`cmdlet 通过管道传递给`Format-Table`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eed59-247">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="eed59-248">此组的 cmdlet 检索员工数据，为表的表行的项。</span><span class="sxs-lookup"><span data-stu-id="eed59-248">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="eed59-249">格式所指定的`Format-Table`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eed59-249">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

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

6. <span data-ttu-id="eed59-250">现在可以运行`Get-Item`cmdlet 来检索员工数据的表的第 0 行的项。</span><span class="sxs-lookup"><span data-stu-id="eed59-250">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

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

7. <span data-ttu-id="eed59-251">使用`Get-Item`cmdlet 再次检索第 0 行中的项的员工数据。</span><span class="sxs-lookup"><span data-stu-id="eed59-251">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eed59-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eed59-252">See Also</span></span>

[<span data-ttu-id="eed59-253">创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-253">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="eed59-254">设计您的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-254">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="eed59-255">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="eed59-255">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="eed59-256">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="eed59-256">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="eed59-257">实现容器的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="eed59-257">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

[<span data-ttu-id="eed59-258">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="eed59-258">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="eed59-259">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="eed59-259">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="eed59-260">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="eed59-260">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="eed59-261">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="eed59-261">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
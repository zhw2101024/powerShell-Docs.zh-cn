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
# <a name="creating-a-windows-powershell-content-provider"></a><span data-ttu-id="39553-102">创建 Windows PowerShell 内容提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-102">Creating a Windows PowerShell Content Provider</span></span>

<span data-ttu-id="39553-103">本主题介绍如何创建 Windows PowerShell 提供程序，使用户用来处理数据存储区中项的内容。</span><span class="sxs-lookup"><span data-stu-id="39553-103">This topic describes how to create a Windows PowerShell provider that enables the user to manipulate the contents of the items in a data store.</span></span> <span data-ttu-id="39553-104">因此，可以操作项的内容的提供程序被称为 Windows PowerShell 内容提供程序。</span><span class="sxs-lookup"><span data-stu-id="39553-104">As a consequence, a provider that can manipulate the contents of items is referred to as a Windows PowerShell content provider.</span></span>

> [!NOTE]
> <span data-ttu-id="39553-105">您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider06.cs)。</span><span class="sxs-lookup"><span data-stu-id="39553-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="39553-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="39553-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="39553-107">您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider06.cs)。</span><span class="sxs-lookup"><span data-stu-id="39553-107">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="39553-108">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="39553-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="39553-109">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="39553-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="39553-110">有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="39553-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="39553-111">以下列表包含本主题中的部分。</span><span class="sxs-lookup"><span data-stu-id="39553-111">The following list contains the sections in this topic.</span></span> <span data-ttu-id="39553-112">如果您不熟悉编写 Windows PowerShell 内容提供商，阅读这些部分中显示的顺序。</span><span class="sxs-lookup"><span data-stu-id="39553-112">If you are unfamiliar with writing a Windows PowerShell content provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="39553-113">但是，如果你熟悉编写 Windows PowerShell 内容提供程序，直接转到所需的信息。</span><span class="sxs-lookup"><span data-stu-id="39553-113">However, if you are familiar with writing a Windows PowerShell content provider, go directly to the information that you need.</span></span>

- [<span data-ttu-id="39553-114">定义 Windows PowerShell 内容提供程序类</span><span class="sxs-lookup"><span data-stu-id="39553-114">Defining the Windows PowerShell Content Provider Class</span></span>](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [<span data-ttu-id="39553-115">定义基本功能</span><span class="sxs-lookup"><span data-stu-id="39553-115">Defining Base Functionality</span></span>](#Define-Functionality-of-Base-Class)

- [<span data-ttu-id="39553-116">实现内容的读取器</span><span class="sxs-lookup"><span data-stu-id="39553-116">Implementing a Content Reader</span></span>](#Implementing-a-Content-Reader)

- [<span data-ttu-id="39553-117">实现内容的编写器</span><span class="sxs-lookup"><span data-stu-id="39553-117">Implementing a Content Writer</span></span>](#Implementing-a-Content-Writer)

- [<span data-ttu-id="39553-118">检索内容的读取器</span><span class="sxs-lookup"><span data-stu-id="39553-118">Retrieving the Content Reader</span></span>](#Retrieving-the-Content-Reader)

- [<span data-ttu-id="39553-119">附加到的动态参数`Get-Content`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39553-119">Attaching Dynamic Parameters to the `Get-Content` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [<span data-ttu-id="39553-120">检索内容编写器</span><span class="sxs-lookup"><span data-stu-id="39553-120">Retrieving the Content Writer</span></span>](#Retrieving-the-Content-Writer)

- [<span data-ttu-id="39553-121">将动态参数附加到 Add_Content 和`Set-Content`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39553-121">Attaching Dynamic Parameters to the Add_Content and `Set-Content` Cmdlets</span></span>](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [<span data-ttu-id="39553-122">清除内容</span><span class="sxs-lookup"><span data-stu-id="39553-122">Clearing Content</span></span>](#Clearing-Content)

- [<span data-ttu-id="39553-123">附加到的动态参数`Clear-Content`Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39553-123">Attaching Dynamic Parameters to the  `Clear-Content` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [<span data-ttu-id="39553-124">代码示例</span><span class="sxs-lookup"><span data-stu-id="39553-124">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="39553-125">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="39553-125">Defining Object Types and Formatting</span></span>]()

- [<span data-ttu-id="39553-126">生成 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-126">Building the Windows PowerShell provider</span></span>](#Building-the-Windows-PowerShell-Provider)

- [<span data-ttu-id="39553-127">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-127">Testing the Windows PowerShell provider</span></span>](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a><span data-ttu-id="39553-128">定义 Windows PowerShell 内容提供程序类</span><span class="sxs-lookup"><span data-stu-id="39553-128">Define the Windows PowerShell Content Provider Class</span></span>

<span data-ttu-id="39553-129">Windows PowerShell 内容提供商必须创建一个支持的.NET 类[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口。</span><span class="sxs-lookup"><span data-stu-id="39553-129">A Windows PowerShell content provider must create a .NET class that supports the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span> <span data-ttu-id="39553-130">下面是在本部分中所述的项提供程序的类定义。</span><span class="sxs-lookup"><span data-stu-id="39553-130">Here is the class definition for the item provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

<span data-ttu-id="39553-131">请注意，在此类定义后， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包含两个参数。</span><span class="sxs-lookup"><span data-stu-id="39553-131">Note that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="39553-132">第一个参数指定由 Windows PowerShell 提供程序的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="39553-132">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="39553-133">第二个参数指定的 Windows PowerShell 的特定功能的提供程序公开到 Windows PowerShell 运行时在命令处理过程。</span><span class="sxs-lookup"><span data-stu-id="39553-133">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="39553-134">为此提供程序，没有添加了的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="39553-134">For this provider, there are no added Windows PowerShell specific capabilities.</span></span>

## <a name="define-functionality-of-base-class"></a><span data-ttu-id="39553-135">定义功能的基类</span><span class="sxs-lookup"><span data-stu-id="39553-135">Define Functionality of Base Class</span></span>

<span data-ttu-id="39553-136">如中所述[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类派生自多个提供其他类不同的提供程序功能。</span><span class="sxs-lookup"><span data-stu-id="39553-136">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="39553-137">Windows PowerShell 内容提供程序，因此，通常定义的所有这些类提供的功能。</span><span class="sxs-lookup"><span data-stu-id="39553-137">A Windows PowerShell content provider, therefore, typically defines all of the functionality provided by those classes.</span></span>

<span data-ttu-id="39553-138">有关如何实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能的详细信息，请参阅[创建一个基本的 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="39553-138">For more information about how to implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="39553-139">但是，大多数提供程序，包括本文所述的提供程序可以使用 Windows PowerShell 提供此功能的默认实现。</span><span class="sxs-lookup"><span data-stu-id="39553-139">However, most providers, including the provider described here, can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="39553-140">若要访问数据存储区，该提供程序必须实现的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="39553-140">To access the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="39553-141">有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="39553-141">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="39553-142">若要操作的数据存储，如获取、 设置和清除项的项提供程序必须实现提供的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="39553-142">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="39553-143">有关实现这些方法的详细信息，请参阅[创建 Windows PowerShell 项提供程序](./creating-a-windows-powershell-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="39553-143">For more information about implementing these methods, see [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="39553-144">若要在多层数据存储上，提供程序必须实现提供的方法[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="39553-144">To work on multi-layer data stores, the provider must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="39553-145">有关实现这些方法的详细信息，请参阅[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="39553-145">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

<span data-ttu-id="39553-146">若要支持递归命令、 嵌套的容器和相对路径，该提供程序必须实现[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="39553-146">To support recursive commands, nested containers, and relative paths, the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="39553-147">此外，此 Windows PowerShell 内容提供商可以附加[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)基类，并因此必须实现此类提供的方法。</span><span class="sxs-lookup"><span data-stu-id="39553-147">In addition, this Windows PowerShell content provider can attaches [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface to the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class, and must therefore implement the methods provided by that class.</span></span> <span data-ttu-id="39553-148">有关详细信息，请参阅实现这些方法，请参阅[实现导航 Windows PowerShell 提供程序](./creating-a-windows-powershell-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="39553-148">For more information, see implementing those methods, see [Implement a Navigation Windows PowerShell Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

## <a name="implementing-a-content-reader"></a><span data-ttu-id="39553-149">实现内容的读取器</span><span class="sxs-lookup"><span data-stu-id="39553-149">Implementing a Content Reader</span></span>

<span data-ttu-id="39553-150">若要读取来自某个项的内容，提供程序必须实现的内容的读取器类派生自[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)。</span><span class="sxs-lookup"><span data-stu-id="39553-150">To read content from an item, a provider must implements a content reader class that derives from [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).</span></span> <span data-ttu-id="39553-151">此提供程序的内容读取器允许访问行的内容中的数据表。</span><span class="sxs-lookup"><span data-stu-id="39553-151">The content reader for this provider allows access to the contents of a row in a data table.</span></span> <span data-ttu-id="39553-152">内容的读取器类定义**读**方法，用于从指示的行中检索数据并返回表示该数据的列表**Seek**移动内容的读取器，方法**关闭**关闭内容读取器的方法和一个**Dispose**方法。</span><span class="sxs-lookup"><span data-stu-id="39553-152">The content reader class defines a **Read** method that retrieves the data from the indicated row and returns a list representing that data, a **Seek** method that moves the content reader, a **Close** method that closes the content reader, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a><span data-ttu-id="39553-153">实现内容的编写器</span><span class="sxs-lookup"><span data-stu-id="39553-153">Implementing a Content Writer</span></span>

<span data-ttu-id="39553-154">若要将内容写到某个项，提供程序必须实现内容编写器类派生自[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)。</span><span class="sxs-lookup"><span data-stu-id="39553-154">To write content to an item, a provider must implement a content writer class derives from [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).</span></span> <span data-ttu-id="39553-155">内容编写器类定义**编写**写入指定的行内容的方法**Seek**移动的内容的编写器，方法**关闭**关闭的方法内容编写器和一个**Dispose**方法。</span><span class="sxs-lookup"><span data-stu-id="39553-155">The content writer class defines a **Write** method that writes the specified row content, a **Seek** method that moves the content writer, a **Close** method that closes the content writer, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a><span data-ttu-id="39553-156">检索内容的读取器</span><span class="sxs-lookup"><span data-stu-id="39553-156">Retrieving the Content Reader</span></span>

<span data-ttu-id="39553-157">要获取的内容从一个项，该提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)以支持`Get-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39553-157">To get content from an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) to support the `Get-Content` cmdlet.</span></span> <span data-ttu-id="39553-158">此方法返回位于指定路径处的项的内容读取器。</span><span class="sxs-lookup"><span data-stu-id="39553-158">This method returns the content reader for the item located at the specified path.</span></span> <span data-ttu-id="39553-159">然后，可打开的读取器对象来读取内容。</span><span class="sxs-lookup"><span data-stu-id="39553-159">The reader object can then be opened to read the content.</span></span>

<span data-ttu-id="39553-160">下面是实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)为此提供程序的此方法。</span><span class="sxs-lookup"><span data-stu-id="39553-160">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) for this method for this provider.</span></span>

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

#### <a name="things-to-remember-about-implementing-getcontentreader"></a><span data-ttu-id="39553-161">要实现 GetContentReader 记住的事项</span><span class="sxs-lookup"><span data-stu-id="39553-161">Things to Remember About Implementing GetContentReader</span></span>

<span data-ttu-id="39553-162">以下条件可能适用于的实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span><span class="sxs-lookup"><span data-stu-id="39553-162">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span></span>

- <span data-ttu-id="39553-163">在定义的提供程序类时，Windows PowerShell 内容提供商可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="39553-163">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="39553-164">在这些情况下，实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法必须确保传递给方法的路径满足指定的要求功能。</span><span class="sxs-lookup"><span data-stu-id="39553-164">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="39553-165">若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。</span><span class="sxs-lookup"><span data-stu-id="39553-165">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="39553-166">默认情况下，重写此方法应检索除非用户隐藏的对象的读取器[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="39553-166">By default, overrides of this method should not retrieve a reader for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="39553-167">如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。</span><span class="sxs-lookup"><span data-stu-id="39553-167">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a><span data-ttu-id="39553-168">附加到的 Get-content Cmdlet 的动态参数</span><span class="sxs-lookup"><span data-stu-id="39553-168">Attaching Dynamic Parameters to the Get-Content Cmdlet</span></span>

<span data-ttu-id="39553-169">`Get-Content` Cmdlet 可能需要在运行时动态指定的附加参数。</span><span class="sxs-lookup"><span data-stu-id="39553-169">The `Get-Content` cmdlet might require additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="39553-170">若要提供这些动态参数，Windows PowerShell 内容提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="39553-170">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span> <span data-ttu-id="39553-171">此方法检索动态参数指定的路径处的项并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。</span><span class="sxs-lookup"><span data-stu-id="39553-171">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="39553-172">Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39553-172">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="39553-173">此 Windows PowerShell 容器提供程序未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="39553-173">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="39553-174">但是，以下代码是此方法的默认实现。</span><span class="sxs-lookup"><span data-stu-id="39553-174">However, the following code is the default implementation of this method.</span></span>

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a><span data-ttu-id="39553-175">检索内容编写器</span><span class="sxs-lookup"><span data-stu-id="39553-175">Retrieving the Content Writer</span></span>

<span data-ttu-id="39553-176">若要将内容写到某个项，该提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)以支持`Set-Content`和`Add-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39553-176">To write content to an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) to support the `Set-Content` and `Add-Content` cmdlets.</span></span> <span data-ttu-id="39553-177">此方法返回位于指定路径处的项的内容编写器。</span><span class="sxs-lookup"><span data-stu-id="39553-177">This method returns the content writer for the item located at the specified path.</span></span>

<span data-ttu-id="39553-178">下面是实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)为此方法。</span><span class="sxs-lookup"><span data-stu-id="39553-178">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) for this method.</span></span>

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

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a><span data-ttu-id="39553-179">要实现 GetContentWriter 记住的事项</span><span class="sxs-lookup"><span data-stu-id="39553-179">Things to Remember About Implementing GetContentWriter</span></span>

<span data-ttu-id="39553-180">以下条件可能适用于特定的实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span><span class="sxs-lookup"><span data-stu-id="39553-180">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span></span>

- <span data-ttu-id="39553-181">在定义的提供程序类时，Windows PowerShell 内容提供商可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="39553-181">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="39553-182">在这些情况下，实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法必须确保传递给方法的路径满足指定的要求功能。</span><span class="sxs-lookup"><span data-stu-id="39553-182">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="39553-183">若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。</span><span class="sxs-lookup"><span data-stu-id="39553-183">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="39553-184">默认情况下，重写此方法应检索的编写器对象，除非用户隐藏[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="39553-184">By default, overrides of this method should not retrieve a writer for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="39553-185">如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。</span><span class="sxs-lookup"><span data-stu-id="39553-185">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a><span data-ttu-id="39553-186">附加到 Add-content 和 Set-content Cmdlet 的动态参数</span><span class="sxs-lookup"><span data-stu-id="39553-186">Attaching Dynamic Parameters to the Add-Content and Set-Content Cmdlets</span></span>

<span data-ttu-id="39553-187">`Add-Content`和`Set-Content`cmdlet 可能需要添加一个运行时的其他动态参数。</span><span class="sxs-lookup"><span data-stu-id="39553-187">The `Add-Content` and `Set-Content` cmdlets might require additional dynamic parameters that are added a runtime.</span></span> <span data-ttu-id="39553-188">若要提供这些动态参数，Windows PowerShell 内容提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法来处理这些参数。</span><span class="sxs-lookup"><span data-stu-id="39553-188">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="39553-189">此方法检索动态参数指定的路径处的项并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。</span><span class="sxs-lookup"><span data-stu-id="39553-189">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="39553-190">Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39553-190">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlets.</span></span>

<span data-ttu-id="39553-191">此 Windows PowerShell 容器提供程序未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="39553-191">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="39553-192">但是，以下代码是此方法的默认实现。</span><span class="sxs-lookup"><span data-stu-id="39553-192">However, the following code is the default implementation of this method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a><span data-ttu-id="39553-193">清除内容</span><span class="sxs-lookup"><span data-stu-id="39553-193">Clearing Content</span></span>

<span data-ttu-id="39553-194">内容提供程序实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法支持`Clear-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39553-194">Your content provider implements the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method in support of the `Clear-Content` cmdlet.</span></span> <span data-ttu-id="39553-195">此方法移除位于指定路径处的项的内容，但使项保持不变。</span><span class="sxs-lookup"><span data-stu-id="39553-195">This method removes the contents of the item at the specified path, but leaves the item intact.</span></span>

<span data-ttu-id="39553-196">下面是实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)此提供程序的方法。</span><span class="sxs-lookup"><span data-stu-id="39553-196">Here is the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method for this provider.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a><span data-ttu-id="39553-197">要实现 ClearContent 记住的事项</span><span class="sxs-lookup"><span data-stu-id="39553-197">Things to Remember About Implementing ClearContent</span></span>

<span data-ttu-id="39553-198">以下条件可能适用于的实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span><span class="sxs-lookup"><span data-stu-id="39553-198">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span></span>

- <span data-ttu-id="39553-199">在定义的提供程序类时，Windows PowerShell 内容提供商可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="39553-199">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="39553-200">在这些情况下，实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法必须确保传递给方法的路径满足指定的要求功能。</span><span class="sxs-lookup"><span data-stu-id="39553-200">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="39553-201">若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。</span><span class="sxs-lookup"><span data-stu-id="39553-201">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="39553-202">默认情况下，重写此方法不应清除除非用户隐藏的对象的内容[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。</span><span class="sxs-lookup"><span data-stu-id="39553-202">By default, overrides of this method should not clear the contents of objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="39553-203">如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。</span><span class="sxs-lookup"><span data-stu-id="39553-203">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

- <span data-ttu-id="39553-204">实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和到数据存储进行任何更改之前验证它的返回值。</span><span class="sxs-lookup"><span data-stu-id="39553-204">Your implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and verify its return value before making any changes to the data store.</span></span> <span data-ttu-id="39553-205">此方法用于更改数据存储，例如清除内容时确认执行操作。</span><span class="sxs-lookup"><span data-stu-id="39553-205">This method is used to confirm execution of an operation when a change is made to the data store, such as clearing content.</span></span> <span data-ttu-id="39553-206">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法发送的要与 Windows PowerShell 运行时处理的任何命令行设置或首选项更改为用户的资源名称确定应显示的内容中的变量。</span><span class="sxs-lookup"><span data-stu-id="39553-206">The [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) method sends the name of the resource to be changed to the user, with the Windows PowerShell runtime handling any command-line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="39553-207">在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="39553-207">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="39553-208">此方法将消息发送到用户允许反馈，以验证是否应继续执行该操作。</span><span class="sxs-lookup"><span data-stu-id="39553-208">This method sends a message to the user to allow feedback to verify if the operation should be continued.</span></span> <span data-ttu-id="39553-209">在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允许具有潜在危险的系统修改为其他检查。</span><span class="sxs-lookup"><span data-stu-id="39553-209">The call to [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) allows an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a><span data-ttu-id="39553-210">附加到 Clear-content Cmdlet 的动态参数</span><span class="sxs-lookup"><span data-stu-id="39553-210">Attaching Dynamic Parameters to the Clear-Content Cmdlet</span></span>

<span data-ttu-id="39553-211">`Clear-Content` Cmdlet 可能需要在运行时添加的其他动态参数。</span><span class="sxs-lookup"><span data-stu-id="39553-211">The `Clear-Content` cmdlet might require additional dynamic parameters that are added at runtime.</span></span> <span data-ttu-id="39553-212">若要提供这些动态参数，Windows PowerShell 内容提供程序必须实现[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法来处理这些参数。</span><span class="sxs-lookup"><span data-stu-id="39553-212">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="39553-213">此方法检索指定的路径处的项的参数。</span><span class="sxs-lookup"><span data-stu-id="39553-213">This method retrieves the parameters for the item at the indicated path.</span></span> <span data-ttu-id="39553-214">此方法检索动态参数指定的路径处的项并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。</span><span class="sxs-lookup"><span data-stu-id="39553-214">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="39553-215">Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39553-215">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="39553-216">此 Windows PowerShell 容器提供程序未实现此方法。</span><span class="sxs-lookup"><span data-stu-id="39553-216">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="39553-217">但是，以下代码是此方法的默认实现。</span><span class="sxs-lookup"><span data-stu-id="39553-217">However, the following code is the default implementation of this method.</span></span>

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a><span data-ttu-id="39553-218">代码示例</span><span class="sxs-lookup"><span data-stu-id="39553-218">Code Sample</span></span>

<span data-ttu-id="39553-219">有关完整的示例代码，请参阅[AccessDbProviderSample06 代码示例](./accessdbprovidersample06-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="39553-219">For complete sample code, see [AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="39553-220">定义对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="39553-220">Defining Object Types and Formatting</span></span>

<span data-ttu-id="39553-221">当编写提供程序，它可能有必要，若要将成员添加到现有对象或定义新对象。</span><span class="sxs-lookup"><span data-stu-id="39553-221">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="39553-222">完成此操作后，必须创建 Windows PowerShell 可用于标识对象的成员的类型文件和格式化文件，用于定义如何显示该对象。</span><span class="sxs-lookup"><span data-stu-id="39553-222">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="39553-223">有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="39553-223">For more information, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>
<span data-ttu-id="39553-224">当编写提供程序，它可能有必要，若要将成员添加到现有对象或定义新对象。</span><span class="sxs-lookup"><span data-stu-id="39553-224">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="39553-225">完成此操作后，必须创建 Windows PowerShell 可用于标识对象的成员的类型文件和格式化文件，用于定义如何显示该对象。</span><span class="sxs-lookup"><span data-stu-id="39553-225">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="39553-226">有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="39553-226">For more information, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="39553-227">生成 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-227">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="39553-228">请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="39553-228">See [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>
<span data-ttu-id="39553-229">请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="39553-229">See [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="39553-230">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-230">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="39553-231">Windows PowerShell 提供程序具有已注册到 Windows PowerShell，可以通过在命令行上运行的受支持的 cmdlet 来测试它。</span><span class="sxs-lookup"><span data-stu-id="39553-231">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="39553-232">例如，测试示例内容提供程序。</span><span class="sxs-lookup"><span data-stu-id="39553-232">For example, test the sample content provider.</span></span>

<span data-ttu-id="39553-233">使用`Get-Content`cmdlet 来检索指定的路径中的数据库表中指定项的内容`Path`参数。</span><span class="sxs-lookup"><span data-stu-id="39553-233">Use the `Get-Content` cmdlet to retrieve the contents of specified item in the database table at the path specified by the `Path` parameter.</span></span> <span data-ttu-id="39553-234">`ReadCount`参数指定用于定义内容的读取器读取 （默认值 1） 的项的数目。</span><span class="sxs-lookup"><span data-stu-id="39553-234">The `ReadCount` parameter specifies the number of items for the defined content reader to read (default 1).</span></span> <span data-ttu-id="39553-235">使用以下命令项时，该 cmdlet 从表中检索两个行 （项），并显示其内容。</span><span class="sxs-lookup"><span data-stu-id="39553-235">With the following command entry, the cmdlet retrieves two rows (items) from the table and displays their contents.</span></span> <span data-ttu-id="39553-236">请注意，下面的示例输出使用虚构的 Access 数据库。</span><span class="sxs-lookup"><span data-stu-id="39553-236">Note that the following example output uses a fictitious Access database.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="39553-237">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39553-237">See Also</span></span>

[<span data-ttu-id="39553-238">创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-238">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="39553-239">设计您的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-239">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="39553-240">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="39553-240">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="39553-241">扩展对象类型和格式设置</span><span class="sxs-lookup"><span data-stu-id="39553-241">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="39553-242">实现导航 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="39553-242">Implement a Navigation Windows PowerShell provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

[<span data-ttu-id="39553-243">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="39553-243">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="39553-244">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="39553-244">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="39553-245">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="39553-245">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="39553-246">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="39553-246">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

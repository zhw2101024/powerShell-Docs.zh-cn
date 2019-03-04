---
title: 创建 Windows PowerShell 驱动器提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855793"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="9a004-102">创建 Windows PowerShell 驱动器提供程序</span><span class="sxs-lookup"><span data-stu-id="9a004-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="9a004-103">本主题介绍如何创建可用于通过 Windows PowerShell 驱动器访问数据存储区的 Windows PowerShell 驱动器提供程序。</span><span class="sxs-lookup"><span data-stu-id="9a004-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="9a004-104">这种类型的提供程序也称为 Windows PowerShell 驱动器提供程序。</span><span class="sxs-lookup"><span data-stu-id="9a004-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="9a004-105">提供程序使用的 Windows PowerShell 驱动器提供了用来连接到数据存储。</span><span class="sxs-lookup"><span data-stu-id="9a004-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="9a004-106">此处所述的 Windows PowerShell 驱动器提供程序提供对 Microsoft Access 数据库的访问。</span><span class="sxs-lookup"><span data-stu-id="9a004-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="9a004-107">为此提供程序，Windows PowerShell 驱动器表示 （它是可以将任意数量的驱动器添加到驱动器提供程序） 的数据库，该驱动器的顶级容器表示在数据库中，表和容器的项表示中的行表中。</span><span class="sxs-lookup"><span data-stu-id="9a004-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="9a004-108">下面是此主题中的部分列表。</span><span class="sxs-lookup"><span data-stu-id="9a004-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="9a004-109">如果您不熟悉编写 Windows PowerShell 驱动器提供程序，阅读这些部分中显示的顺序。</span><span class="sxs-lookup"><span data-stu-id="9a004-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="9a004-110">但是，如果你熟悉编写驱动器提供程序，请直接转到所需的信息。</span><span class="sxs-lookup"><span data-stu-id="9a004-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="9a004-111">定义 Windows PowerShell 提供程序类</span><span class="sxs-lookup"><span data-stu-id="9a004-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="9a004-112">定义基本功能</span><span class="sxs-lookup"><span data-stu-id="9a004-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="9a004-113">创建驱动器状态信息</span><span class="sxs-lookup"><span data-stu-id="9a004-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="9a004-114">创建驱动器</span><span class="sxs-lookup"><span data-stu-id="9a004-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="9a004-115">将动态参数附加到 NewDrive</span><span class="sxs-lookup"><span data-stu-id="9a004-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="9a004-116">移除驱动器</span><span class="sxs-lookup"><span data-stu-id="9a004-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="9a004-117">初始化默认驱动器</span><span class="sxs-lookup"><span data-stu-id="9a004-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="9a004-118">代码示例</span><span class="sxs-lookup"><span data-stu-id="9a004-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="9a004-119">测试 Windows PowerShell 驱动器提供程序</span><span class="sxs-lookup"><span data-stu-id="9a004-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="9a004-120">定义 Windows PowerShell 提供程序类</span><span class="sxs-lookup"><span data-stu-id="9a004-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="9a004-121">驱动器提供程序必须定义一个.NET 类，派生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="9a004-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="9a004-122">下面是此驱动器提供程序的类定义：</span><span class="sxs-lookup"><span data-stu-id="9a004-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="9a004-123">请注意，在此示例中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性指定的提供程序和 Windows PowerShell 的特定功能的用户友好名称的提供程序在命令处理过程公开为 Windows PowerShell 运行时。</span><span class="sxs-lookup"><span data-stu-id="9a004-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="9a004-124">定义提供程序功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="9a004-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="9a004-125">此驱动器提供程序不支持任何这些功能。</span><span class="sxs-lookup"><span data-stu-id="9a004-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="9a004-126">定义基本功能</span><span class="sxs-lookup"><span data-stu-id="9a004-126">Defining Base Functionality</span></span>

<span data-ttu-id="9a004-127">如中所述[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类派生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类定义所需的初始化和取消初始化访问接口的方法。</span><span class="sxs-lookup"><span data-stu-id="9a004-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="9a004-128">若要实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能，请参阅[创建一个基本的 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9a004-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="9a004-129">但是，大多数提供程序 （包括此处所述的提供程序） 可以使用 Windows PowerShell 提供此功能的默认实现。</span><span class="sxs-lookup"><span data-stu-id="9a004-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="9a004-130">创建驱动器状态信息</span><span class="sxs-lookup"><span data-stu-id="9a004-130">Creating Drive State Information</span></span>

<span data-ttu-id="9a004-131">所有 Windows PowerShell 提供程序被都视为无状态的这意味着您的驱动器提供程序，需要创建时它将调用您的提供程序通过 Windows PowerShell 运行时所需的任何状态信息。</span><span class="sxs-lookup"><span data-stu-id="9a004-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="9a004-132">对于此驱动器提供程序中，状态信息包括作为驱动器信息的一部分保留数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="9a004-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="9a004-133">下面是代码显示如何将此信息存储在[即 System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)对象，描述驱动器：</span><span class="sxs-lookup"><span data-stu-id="9a004-133">Here is code that shows how this information is stored in the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="9a004-134">创建驱动器</span><span class="sxs-lookup"><span data-stu-id="9a004-134">Creating a Drive</span></span>

<span data-ttu-id="9a004-135">若要允许 Windows PowerShell 运行时创建的驱动器，驱动器提供程序必须实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法。</span><span class="sxs-lookup"><span data-stu-id="9a004-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="9a004-136">下面的代码演示如何实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)此驱动器提供程序的方法：</span><span class="sxs-lookup"><span data-stu-id="9a004-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="9a004-137">重写此方法应执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9a004-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="9a004-138">确认[System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root)成员存在，并且可进行数据存储区的连接。</span><span class="sxs-lookup"><span data-stu-id="9a004-138">Verify that the [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="9a004-139">创建驱动器，并填充连接成员支持`New-PSDrive`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a004-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="9a004-140">验证[即 System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)建议驱动器的对象。</span><span class="sxs-lookup"><span data-stu-id="9a004-140">Validate the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="9a004-141">修改[即 System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)对象，它描述与任何所需的性能或可靠性信息的驱动器或调用方使用驱动器提供额外的数据。</span><span class="sxs-lookup"><span data-stu-id="9a004-141">Modify the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="9a004-142">处理使用的故障[System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，然后返回`null`。</span><span class="sxs-lookup"><span data-stu-id="9a004-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="9a004-143">此方法返回的驱动器信息传递到方法或它的特定于提供程序的版本。</span><span class="sxs-lookup"><span data-stu-id="9a004-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="9a004-144">将动态参数附加到 NewDrive</span><span class="sxs-lookup"><span data-stu-id="9a004-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="9a004-145">`New-PSDrive`驱动器提供程序支持的 cmdlet 可能需要附加参数。</span><span class="sxs-lookup"><span data-stu-id="9a004-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="9a004-146">若要将这些动态参数附加到该 cmdlet，该提供程序实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="9a004-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="9a004-147">此方法返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。</span><span class="sxs-lookup"><span data-stu-id="9a004-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="9a004-148">此驱动器提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="9a004-148">This drive provider does not override this method.</span></span> <span data-ttu-id="9a004-149">但是，下面的代码演示此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="9a004-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="9a004-150">移除驱动器</span><span class="sxs-lookup"><span data-stu-id="9a004-150">Removing a Drive</span></span>

<span data-ttu-id="9a004-151">若要关闭数据库连接后，驱动器提供程序必须实现[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。</span><span class="sxs-lookup"><span data-stu-id="9a004-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="9a004-152">此方法关闭连接到的驱动器后清理的任何特定于提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="9a004-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="9a004-153">下面的代码演示如何实现[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)此驱动器提供程序的方法：</span><span class="sxs-lookup"><span data-stu-id="9a004-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="9a004-154">如果可以移除驱动器，该方法应返回的信息传递给该方法通过`drive`参数。</span><span class="sxs-lookup"><span data-stu-id="9a004-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="9a004-155">如果不能移除驱动器，该方法应编写异常，然后返回`null`。</span><span class="sxs-lookup"><span data-stu-id="9a004-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="9a004-156">如果您的提供程序不重写此方法，此方法的默认实现只返回作为输入传递的驱动器信息。</span><span class="sxs-lookup"><span data-stu-id="9a004-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="9a004-157">初始化默认驱动器</span><span class="sxs-lookup"><span data-stu-id="9a004-157">Initializing Default Drives</span></span>

<span data-ttu-id="9a004-158">你的驱动器提供程序实现[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法以装入驱动器。</span><span class="sxs-lookup"><span data-stu-id="9a004-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="9a004-159">例如，Active Directory 提供程序可能会装载驱动器默认情况下，如果将计算机加入到域命名上下文。</span><span class="sxs-lookup"><span data-stu-id="9a004-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="9a004-160">此方法返回有关初始化的驱动器，驱动器信息的集合或一个空集合。</span><span class="sxs-lookup"><span data-stu-id="9a004-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="9a004-161">对此方法的调用后 Windows PowerShell 运行时调用进行[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以初始化访问接口。</span><span class="sxs-lookup"><span data-stu-id="9a004-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="9a004-162">此驱动器提供程序不会覆盖[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法。</span><span class="sxs-lookup"><span data-stu-id="9a004-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="9a004-163">但是，以下代码显示了默认实现，它将返回一个空驱动器集合：</span><span class="sxs-lookup"><span data-stu-id="9a004-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="9a004-164">要实现 InitializeDefaultDrives 记住的事项</span><span class="sxs-lookup"><span data-stu-id="9a004-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="9a004-165">所有驱动器提供程序应将都装载为根驱动器，以帮助用户使用可发现性。</span><span class="sxs-lookup"><span data-stu-id="9a004-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="9a004-166">根驱动器可能还会列出作为其他已装载的驱动器的根位置。</span><span class="sxs-lookup"><span data-stu-id="9a004-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="9a004-167">例如，Active Directory 提供程序可以创建列出了命名上下文中找到的驱动器`namingContext`根分布式系统环境 (DSE) 上的属性。</span><span class="sxs-lookup"><span data-stu-id="9a004-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="9a004-168">这有助于用户发现的其他驱动器装入点。</span><span class="sxs-lookup"><span data-stu-id="9a004-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9a004-169">代码示例</span><span class="sxs-lookup"><span data-stu-id="9a004-169">Code Sample</span></span>

<span data-ttu-id="9a004-170">有关完整的示例代码，请参阅[AccessDbProviderSample02 代码示例](./accessdbprovidersample02-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="9a004-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="9a004-171">测试 Windows PowerShell 驱动器提供程序</span><span class="sxs-lookup"><span data-stu-id="9a004-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="9a004-172">Windows PowerShell 提供程序具有已注册到 Windows PowerShell，可以通过运行命令行，其中包括可供派生的任何 cmdlet 上受支持的 cmdlet 来测试它。</span><span class="sxs-lookup"><span data-stu-id="9a004-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="9a004-173">让我们测试示例驱动器提供程序。</span><span class="sxs-lookup"><span data-stu-id="9a004-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="9a004-174">运行`Get-PSProvider`cmdlet 来检索提供程序以确保存在 AccessDB 驱动器提供程序的列表：</span><span class="sxs-lookup"><span data-stu-id="9a004-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="9a004-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="9a004-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="9a004-176">将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="9a004-176">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="9a004-177">请确保存在用于数据库的数据库服务器名称 (DSN) 通过访问**数据源**一部分**管理工具**的操作系统。</span><span class="sxs-lookup"><span data-stu-id="9a004-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="9a004-178">在中**用户 DSN**表中，双击**MS Access 数据库**并添加 C:\ps\northwind.mdb 的驱动器路径。</span><span class="sxs-lookup"><span data-stu-id="9a004-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="9a004-179">创建新的驱动器使用示例驱动器提供程序：</span><span class="sxs-lookup"><span data-stu-id="9a004-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="9a004-180">**PS > 新 psdrive-名称 mydb-根 c:\ps\northwind.mdb psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="9a004-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="9a004-181">将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="9a004-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="9a004-182">验证的连接。</span><span class="sxs-lookup"><span data-stu-id="9a004-182">Validate the connection.</span></span> <span data-ttu-id="9a004-183">因为连接被定义为驱动器的成员，可以检查其使用 Get PDDrive cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a004-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="9a004-184">随着该提供程序需要为此交互的容器功能，用户不能与提供程序作为一个驱动器，尚未进行交互。</span><span class="sxs-lookup"><span data-stu-id="9a004-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="9a004-185">有关详细信息，请参阅[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9a004-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="9a004-186">**PS > (get psdrive mydb).connection**</span><span class="sxs-lookup"><span data-stu-id="9a004-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="9a004-187">将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="9a004-187">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="9a004-188">移除驱动器并退出 shell:</span><span class="sxs-lookup"><span data-stu-id="9a004-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="9a004-189">**PS > 删除 psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="9a004-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="9a004-190">**PS > 退出**</span><span class="sxs-lookup"><span data-stu-id="9a004-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="9a004-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a004-191">See Also</span></span>

[<span data-ttu-id="9a004-192">创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="9a004-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="9a004-193">设计 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="9a004-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="9a004-194">创建基本 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="9a004-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
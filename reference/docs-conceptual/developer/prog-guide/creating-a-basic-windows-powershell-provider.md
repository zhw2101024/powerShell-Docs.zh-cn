---
title: 创建基本 Windows PowerShell 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360516"
---
# <a name="creating-a-basic-windows-powershell-provider"></a><span data-ttu-id="4292d-102">创建基础 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="4292d-102">Creating a Basic Windows PowerShell Provider</span></span>

<span data-ttu-id="4292d-103">本主题是学习如何创建 Windows PowerShell 提供程序的起点。</span><span class="sxs-lookup"><span data-stu-id="4292d-103">This topic is the starting point for learning how to create a Windows PowerShell provider.</span></span> <span data-ttu-id="4292d-104">此处所述的基本提供程序提供了启动和停止提供程序的方法，但尽管此提供程序不提供访问数据存储或获取或设置数据存储中数据的方法，但它确实提供了所需的基本功能所有提供程序。</span><span class="sxs-lookup"><span data-stu-id="4292d-104">The basic provider described here provides methods for starting and stopping the provider, and although this provider does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

<span data-ttu-id="4292d-105">如前所述，此处所述的基本提供程序实现了用于启动和停止提供程序的方法。</span><span class="sxs-lookup"><span data-stu-id="4292d-105">As mentioned previously, the basic provider described here implements methods for starting and stopping the provider.</span></span> <span data-ttu-id="4292d-106">Windows PowerShell 运行时调用这些方法来初始化和取消初始化提供程序。</span><span class="sxs-lookup"><span data-stu-id="4292d-106">The Windows PowerShell runtime calls these methods to initialize and uninitialize the provider.</span></span>

> [!NOTE]
> <span data-ttu-id="4292d-107">可在 Windows PowerShell 提供的 AccessDBSampleProvider01.cs 文件中找到该提供程序的示例。</span><span class="sxs-lookup"><span data-stu-id="4292d-107">You can find a sample of this provider in the AccessDBSampleProvider01.cs file provided by Windows PowerShell.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="4292d-108">定义 Windows PowerShell 提供程序类</span><span class="sxs-lookup"><span data-stu-id="4292d-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="4292d-109">创建 Windows PowerShell 提供程序的第一步是定义其 .NET 类。</span><span class="sxs-lookup"><span data-stu-id="4292d-109">The first step in creating a Windows PowerShell provider is to define its .NET class.</span></span> <span data-ttu-id="4292d-110">此基本提供程序定义了一个名为 `AccessDBProvider` 的类，该类派生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="4292d-110">This basic provider defines a class called `AccessDBProvider` that derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class.</span></span>

<span data-ttu-id="4292d-111">建议将提供程序类放在 API 命名空间的 `Providers` 命名空间中，例如 xxx。PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4292d-111">It is recommended that you place your provider classes in a `Providers` namespace of your API namespace, for example, xxx.PowerShell.Providers.</span></span> <span data-ttu-id="4292d-112">此提供程序使用 `Microsoft.Samples.PowerShell.Provider` 命名空间，在该命名空间中运行所有 Windows PowerShell 提供程序示例。</span><span class="sxs-lookup"><span data-stu-id="4292d-112">This provider uses the `Microsoft.Samples.PowerShell.Provider` namespace, in which all Windows PowerShell provider samples run.</span></span>

> [!NOTE]
> <span data-ttu-id="4292d-113">Windows PowerShell 提供程序的类必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="4292d-113">The class for a Windows PowerShell provider must be explicitly marked as public.</span></span> <span data-ttu-id="4292d-114">未标记为 "公共" 的类将默认为内部类，且不会由 Windows PowerShell 运行时找到。</span><span class="sxs-lookup"><span data-stu-id="4292d-114">Classes not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="4292d-115">下面是该基本提供程序的类定义：</span><span class="sxs-lookup"><span data-stu-id="4292d-115">Here is the class definition for this basic provider:</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

<span data-ttu-id="4292d-116">在类定义之前，您必须用语法 [CmdletProvider （）] 声明[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性，而不是。</span><span class="sxs-lookup"><span data-stu-id="4292d-116">Right before the class definition, you must declare the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute, with the syntax [CmdletProvider()].</span></span>

<span data-ttu-id="4292d-117">如有必要，可以设置属性关键字以进一步声明该类。</span><span class="sxs-lookup"><span data-stu-id="4292d-117">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="4292d-118">请注意，此处声明的[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)特性包括两个参数。</span><span class="sxs-lookup"><span data-stu-id="4292d-118">Notice that the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute declared here includes two parameters.</span></span> <span data-ttu-id="4292d-119">第一个 attribute 参数指定提供程序的默认友好名称，用户可以在以后修改该名称。</span><span class="sxs-lookup"><span data-stu-id="4292d-119">The first attribute parameter specifies the default-friendly name for the provider, which the user can modify later.</span></span> <span data-ttu-id="4292d-120">第二个参数指定 Windows PowerShell 定义的功能，提供程序在命令处理过程中将这些功能公开给 Windows PowerShell 运行时。</span><span class="sxs-lookup"><span data-stu-id="4292d-120">The second parameter specifies the Windows PowerShell-defined capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="4292d-121">提供程序功能的可能值是由[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举定义的。</span><span class="sxs-lookup"><span data-stu-id="4292d-121">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="4292d-122">因为这是一个基本提供程序，所以它不支持任何功能。</span><span class="sxs-lookup"><span data-stu-id="4292d-122">Because this is a base provider, it supports no capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="4292d-123">Windows PowerShell 提供程序的完全限定名称包括在注册提供程序时由 Windows PowerShell 确定的程序集名称和其他属性。</span><span class="sxs-lookup"><span data-stu-id="4292d-123">The fully qualified name of the Windows PowerShell provider includes the assembly name and other attributes determined by Windows PowerShell upon registration of the provider.</span></span>

## <a name="defining-provider-specific-state-information"></a><span data-ttu-id="4292d-124">定义特定于提供程序的状态信息</span><span class="sxs-lookup"><span data-stu-id="4292d-124">Defining Provider-Specific State Information</span></span>

<span data-ttu-id="4292d-125">由于 Windows PowerShell 运行时仅根据需要创建提供程序实例，因此[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类和所有派生类均被视为无状态。</span><span class="sxs-lookup"><span data-stu-id="4292d-125">The [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class and all derived classes are considered stateless because the Windows PowerShell runtime creates provider instances only as required.</span></span> <span data-ttu-id="4292d-126">因此，如果提供程序需要完全控制和状态维护特定于提供程序的数据，则必须从[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)类派生一个类。</span><span class="sxs-lookup"><span data-stu-id="4292d-126">Therefore, if your provider requires full control and state maintenance for provider-specific data, it must derive a class from the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) class.</span></span> <span data-ttu-id="4292d-127">派生类应定义维护状态所需的成员，以便在 Windows PowerShell 运行时调用[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法来初始化提供程序时可以访问提供程序特定的数据。</span><span class="sxs-lookup"><span data-stu-id="4292d-127">Your derived class should define the members necessary to maintain the state so that the provider-specific data can be accessed when the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="4292d-128">Windows PowerShell 提供程序也可以维护基于连接的状态。</span><span class="sxs-lookup"><span data-stu-id="4292d-128">A Windows PowerShell provider can also maintain connection-based state.</span></span> <span data-ttu-id="4292d-129">有关维护连接状态的详细信息，请参阅[创建 PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4292d-129">For more information about maintaining connection state, see [Creating a PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

## <a name="initializing-the-provider"></a><span data-ttu-id="4292d-130">正在初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="4292d-130">Initializing the Provider</span></span>

<span data-ttu-id="4292d-131">若要初始化该访问接口，Windows powershell 运行时将在启动 Windows PowerShell 时调用[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法。</span><span class="sxs-lookup"><span data-stu-id="4292d-131">To initialize the provider, the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method when Windows PowerShell is started.</span></span> <span data-ttu-id="4292d-132">大多数情况下，提供程序可以使用此方法的默认实现，该实现只返回描述提供程序的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象。</span><span class="sxs-lookup"><span data-stu-id="4292d-132">For the most part, your provider can use the default implementation of this method, which simply returns the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that describes your provider.</span></span> <span data-ttu-id="4292d-133">但是，如果你想要添加其他初始化信息，你应该实现你自己的 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 方法，该方法将返回修改后的版本传递给提供程序的 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 对象。</span><span class="sxs-lookup"><span data-stu-id="4292d-133">However, in the case where you want to add additional initialization information, you should implement your own [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method that returns a modified version of the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that is passed to your provider.</span></span> <span data-ttu-id="4292d-134">通常，此方法应返回传递给它的所提供的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象或包含其他初始化信息的修改后的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象。</span><span class="sxs-lookup"><span data-stu-id="4292d-134">In general, this method should return the provided [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object passed to it or a modified [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that contains other initialization information.</span></span>

<span data-ttu-id="4292d-135">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="4292d-135">This basic provider does not override this method.</span></span> <span data-ttu-id="4292d-136">但是，以下代码显示了此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="4292d-136">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

<span data-ttu-id="4292d-137">提供程序可以维护特定于提供程序的信息的状态，如[定义特定于提供程序的数据状态](#defining-provider-specific-state-information)中所述。</span><span class="sxs-lookup"><span data-stu-id="4292d-137">The provider can maintain the state of provider-specific information as described in [Defining Provider-specific Data State](#defining-provider-specific-state-information).</span></span> <span data-ttu-id="4292d-138">在这种情况下，您的实现必须重写[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法才能返回派生类的实例。</span><span class="sxs-lookup"><span data-stu-id="4292d-138">In this case, your implementation must override the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to return an instance of the derived class.</span></span>

## <a name="start-dynamic-parameters"></a><span data-ttu-id="4292d-139">启动动态参数</span><span class="sxs-lookup"><span data-stu-id="4292d-139">Start Dynamic Parameters</span></span>

<span data-ttu-id="4292d-140">你的[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法的提供程序实现可能需要其他参数。</span><span class="sxs-lookup"><span data-stu-id="4292d-140">Your provider implementation of the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method might require additional parameters.</span></span> <span data-ttu-id="4292d-141">在这种情况下，提供程序应重写[Cmdletprovider. Startdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法，并返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。</span><span class="sxs-lookup"><span data-stu-id="4292d-141">In this case, the provider should override the [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) method and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="4292d-142">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="4292d-142">This basic provider does not override this method.</span></span> <span data-ttu-id="4292d-143">但是，以下代码显示了此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="4292d-143">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a><span data-ttu-id="4292d-144">取消初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="4292d-144">Uninitializing the Provider</span></span>

<span data-ttu-id="4292d-145">为了释放 Windows PowerShell 提供程序使用的资源，提供程序应实现其自己的[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。</span><span class="sxs-lookup"><span data-stu-id="4292d-145">To free resources that the Windows PowerShell provider uses, your provider should implement its own [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) method.</span></span> <span data-ttu-id="4292d-146">Windows PowerShell 运行时调用此方法，以便在会话关闭时对提供程序进行初始化。</span><span class="sxs-lookup"><span data-stu-id="4292d-146">This method is called by the Windows PowerShell runtime to uninitialize the provider at the close of a session.</span></span>

<span data-ttu-id="4292d-147">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="4292d-147">This basic provider does not override this method.</span></span> <span data-ttu-id="4292d-148">但是，以下代码显示了此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="4292d-148">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a><span data-ttu-id="4292d-149">代码示例</span><span class="sxs-lookup"><span data-stu-id="4292d-149">Code Sample</span></span>

<span data-ttu-id="4292d-150">有关完整的示例代码，请参阅[AccessDbProviderSample01 代码示例](./accessdbprovidersample01-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="4292d-150">For complete sample code, see [AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="4292d-151">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="4292d-151">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="4292d-152">Windows PowerShell 提供程序注册到 Windows PowerShell 后，可以通过在命令行上运行支持的 cmdlet 来对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="4292d-152">Once your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="4292d-153">对于此基本提供程序，请运行新的 shell 并使用 `Get-PSProvider` cmdlet 来检索提供程序列表，并确保存在 AccessDb 提供程序。</span><span class="sxs-lookup"><span data-stu-id="4292d-153">For this basic provider, run the new shell and use the `Get-PSProvider` cmdlet to retrieve the list of providers and ensure that the AccessDb provider is present.</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="4292d-154">将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="4292d-154">The following output appears:</span></span>

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a><span data-ttu-id="4292d-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4292d-155">See Also</span></span>

[<span data-ttu-id="4292d-156">创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="4292d-156">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="4292d-157">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="4292d-157">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

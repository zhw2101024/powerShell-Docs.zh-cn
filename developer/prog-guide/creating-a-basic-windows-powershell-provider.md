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
ms.openlocfilehash: 5ebc22067b20f0e1d35d31d5f33e599f50cb7564
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855070"
---
# <a name="creating-a-basic-windows-powershell-provider"></a><span data-ttu-id="0578e-102">创建基础 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="0578e-102">Creating a Basic Windows PowerShell Provider</span></span>

<span data-ttu-id="0578e-103">本主题是学习如何创建 Windows PowerShell 提供程序的起始点。</span><span class="sxs-lookup"><span data-stu-id="0578e-103">This topic is the starting point for learning how to create a Windows PowerShell provider.</span></span> <span data-ttu-id="0578e-104">此处所述的基本提供程序提供用于启动和停止提供程序，方法，它虽然此提供程序不提供一种方法来访问数据存储区或要获取或设置数据存储区中的数据，但它不提供所需的基本功能所有提供程序。</span><span class="sxs-lookup"><span data-stu-id="0578e-104">The basic provider described here provides methods for starting and stopping the provider, and although this provider does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

<span data-ttu-id="0578e-105">如上文所述的基本提供程序在此处实现方法来启动和停止提供程序。</span><span class="sxs-lookup"><span data-stu-id="0578e-105">As mentioned previously, the basic provider described here implements methods for starting and stopping the provider.</span></span> <span data-ttu-id="0578e-106">Windows PowerShell 运行时调用这些方法来初始化和取消初始化提供程序。</span><span class="sxs-lookup"><span data-stu-id="0578e-106">The Windows PowerShell runtime calls these methods to initialize and uninitialize the provider.</span></span>

> [!NOTE]
> <span data-ttu-id="0578e-107">可以通过 Windows PowerShell 提供的 AccessDBSampleProvider01.cs 文件中找到此提供程序的示例。</span><span class="sxs-lookup"><span data-stu-id="0578e-107">You can find a sample of this provider in the AccessDBSampleProvider01.cs file provided by Windows PowerShell.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="0578e-108">定义 Windows PowerShell 提供程序类</span><span class="sxs-lookup"><span data-stu-id="0578e-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="0578e-109">创建 Windows PowerShell 提供程序的第一步是定义其.NET 类。</span><span class="sxs-lookup"><span data-stu-id="0578e-109">The first step in creating a Windows PowerShell provider is to define its .NET class.</span></span> <span data-ttu-id="0578e-110">此基本提供程序定义一个名为类`AccessDBProvider`派生[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="0578e-110">This basic provider defines a class called `AccessDBProvider` that derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class.</span></span>

<span data-ttu-id="0578e-111">建议将放在你提供程序类`Providers`API 命名空间，例如，xxx 的命名空间。PowerShell.Providers。</span><span class="sxs-lookup"><span data-stu-id="0578e-111">It is recommended that you place your provider classes in a `Providers` namespace of your API namespace, for example, xxx.PowerShell.Providers.</span></span> <span data-ttu-id="0578e-112">此提供程序使用`Microsoft.Samples.PowerShell.Provider`命名空间，在其中运行所有 Windows PowerShell 提供程序示例。</span><span class="sxs-lookup"><span data-stu-id="0578e-112">This provider uses the `Microsoft.Samples.PowerShell.Provider` namespace, in which all Windows PowerShell provider samples run.</span></span>

> [!NOTE]
> <span data-ttu-id="0578e-113">为 Windows PowerShell 提供程序类必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="0578e-113">The class for a Windows PowerShell provider must be explicitly marked as public.</span></span> <span data-ttu-id="0578e-114">未标记为公共的类将默认为内部和 Windows PowerShell 运行时将不会找到。</span><span class="sxs-lookup"><span data-stu-id="0578e-114">Classes not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="0578e-115">下面是此基本提供程序的类定义：</span><span class="sxs-lookup"><span data-stu-id="0578e-115">Here is the class definition for this basic provider:</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

<span data-ttu-id="0578e-116">类定义中前, 必须声明[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)具有语法 [CmdletProvider()] 属性。</span><span class="sxs-lookup"><span data-stu-id="0578e-116">Right before the class definition, you must declare the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute, with the syntax [CmdletProvider()].</span></span>

<span data-ttu-id="0578e-117">可以设置属性关键字，以进一步声明类，如有必要。</span><span class="sxs-lookup"><span data-stu-id="0578e-117">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="0578e-118">请注意， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)此处声明的属性包括两个参数。</span><span class="sxs-lookup"><span data-stu-id="0578e-118">Notice that the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute declared here includes two parameters.</span></span> <span data-ttu-id="0578e-119">第一个属性参数指定提供程序，用户可以更高版本修改默认的友好名称。</span><span class="sxs-lookup"><span data-stu-id="0578e-119">The first attribute parameter specifies the default-friendly name for the provider, which the user can modify later.</span></span> <span data-ttu-id="0578e-120">第二个参数指定的提供程序公开到 Windows PowerShell 运行时在命令处理过程的 Windows PowerShell 定义功能。</span><span class="sxs-lookup"><span data-stu-id="0578e-120">The second parameter specifies the Windows PowerShell-defined capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="0578e-121">定义提供程序功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="0578e-121">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="0578e-122">由于这是基本提供程序，它支持任何功能。</span><span class="sxs-lookup"><span data-stu-id="0578e-122">Because this is a base provider, it supports no capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="0578e-123">Windows PowerShell 提供程序的完全限定的名称包括程序集名称和由 Windows PowerShell 在注册的提供程序的其他属性。</span><span class="sxs-lookup"><span data-stu-id="0578e-123">The fully qualified name of the Windows PowerShell provider includes the assembly name and other attributes determined by Windows PowerShell upon registration of the provider.</span></span>

## <a name="defining-provider-specific-state-information"></a><span data-ttu-id="0578e-124">定义特定于提供程序的状态信息</span><span class="sxs-lookup"><span data-stu-id="0578e-124">Defining Provider-Specific State Information</span></span>

<span data-ttu-id="0578e-125">[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类和所有派生的类被视为无状态因为 Windows PowerShell 运行时将创建仅在需要的提供程序实例。</span><span class="sxs-lookup"><span data-stu-id="0578e-125">The [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class and all derived classes are considered stateless because the Windows PowerShell runtime creates provider instances only as required.</span></span> <span data-ttu-id="0578e-126">因此，如果您的提供程序需要完全控制和状态维护特定于提供程序的数据，它必须派生一个类从[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)类。</span><span class="sxs-lookup"><span data-stu-id="0578e-126">Therefore, if your provider requires full control and state maintenance for provider-specific data, it must derive a class from the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) class.</span></span> <span data-ttu-id="0578e-127">在派生的类应定义需维护状态，以便可以访问特定于提供程序的数据，当 Windows PowerShell 运行时调用的成员[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以初始化访问接口。</span><span class="sxs-lookup"><span data-stu-id="0578e-127">Your derived class should define the members necessary to maintain the state so that the provider-specific data can be accessed when the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="0578e-128">Windows PowerShell 提供程序还可以维护基于连接的状态。</span><span class="sxs-lookup"><span data-stu-id="0578e-128">A Windows PowerShell provider can also maintain connection-based state.</span></span> <span data-ttu-id="0578e-129">有关保持连接状态的详细信息，请参阅[创建一个 PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0578e-129">For more information about maintaining connection state, see [Creating a PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

## <a name="initializing-the-provider"></a><span data-ttu-id="0578e-130">初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="0578e-130">Initializing the Provider</span></span>

<span data-ttu-id="0578e-131">若要初始化的提供程序，Windows PowerShell 运行时调用[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法启动 Windows PowerShell 时。</span><span class="sxs-lookup"><span data-stu-id="0578e-131">To initialize the provider, the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method when Windows PowerShell is started.</span></span> <span data-ttu-id="0578e-132">大多数情况下，您的提供程序可以使用此方法，它只是返回的默认实现[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象，描述您的提供程序。</span><span class="sxs-lookup"><span data-stu-id="0578e-132">For the most part, your provider can use the default implementation of this method, which simply returns the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that describes your provider.</span></span> <span data-ttu-id="0578e-133">但是，在你想要添加附加的初始化信息的情况下，则应实现您自己[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法返回的修改的版本[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)传递给您的提供程序的对象。</span><span class="sxs-lookup"><span data-stu-id="0578e-133">However, in the case where you want to add additional initialization information, you should implement your own [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method that returns a modified version of the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that is passed to your provider.</span></span> <span data-ttu-id="0578e-134">一般情况下，此方法应返回所提供[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象传递给它或修改过[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象包含其他初始化信息。</span><span class="sxs-lookup"><span data-stu-id="0578e-134">In general, this method should return the provided [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object passed to it or a modified [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that contains other initialization information.</span></span>

<span data-ttu-id="0578e-135">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="0578e-135">This basic provider does not override this method.</span></span> <span data-ttu-id="0578e-136">但是，下面的代码演示此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="0578e-136">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

<span data-ttu-id="0578e-137">提供程序可以维护状态的特定于提供程序的信息，如中所述[定义特定于提供程序的数据状态](#defining-provider-specific-state-information)。</span><span class="sxs-lookup"><span data-stu-id="0578e-137">The provider can maintain the state of provider-specific information as described in [Defining Provider-specific Data State](#defining-provider-specific-state-information).</span></span> <span data-ttu-id="0578e-138">在这种情况下，您的实现必须重写[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以返回派生的类的实例。</span><span class="sxs-lookup"><span data-stu-id="0578e-138">In this case, your implementation must override the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to return an instance of the derived class.</span></span>

## <a name="start-dynamic-parameters"></a><span data-ttu-id="0578e-139">启动动态参数</span><span class="sxs-lookup"><span data-stu-id="0578e-139">Start Dynamic Parameters</span></span>

<span data-ttu-id="0578e-140">在提供程序实现的[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法可能需要其他参数。</span><span class="sxs-lookup"><span data-stu-id="0578e-140">Your provider implementation of the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method might require additional parameters.</span></span> <span data-ttu-id="0578e-141">在这种情况下，该提供程序应重写[System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法并返回具有属性和字段与分析的对象属性类似于cmdlet 类或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。</span><span class="sxs-lookup"><span data-stu-id="0578e-141">In this case, the provider should override the [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) method and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="0578e-142">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="0578e-142">This basic provider does not override this method.</span></span> <span data-ttu-id="0578e-143">但是，下面的代码演示此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="0578e-143">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a><span data-ttu-id="0578e-144">取消初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="0578e-144">Uninitializing the Provider</span></span>

<span data-ttu-id="0578e-145">若要释放的 Windows PowerShell 提供程序使用的资源，您的提供程序应实现其自己[System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。</span><span class="sxs-lookup"><span data-stu-id="0578e-145">To free resources that the Windows PowerShell provider uses, your provider should implement its own [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) method.</span></span> <span data-ttu-id="0578e-146">要取消初始化的提供程序在会话的结束位置的 Windows PowerShell 运行时调用此方法。</span><span class="sxs-lookup"><span data-stu-id="0578e-146">This method is called by the Windows PowerShell runtime to uninitialize the provider at the close of a session.</span></span>

<span data-ttu-id="0578e-147">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="0578e-147">This basic provider does not override this method.</span></span> <span data-ttu-id="0578e-148">但是，下面的代码演示此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="0578e-148">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a><span data-ttu-id="0578e-149">代码示例</span><span class="sxs-lookup"><span data-stu-id="0578e-149">Code Sample</span></span>

<span data-ttu-id="0578e-150">有关完整的示例代码，请参阅[AccessDbProviderSample01 代码示例](./accessdbprovidersample01-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0578e-150">For complete sample code, see [AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="0578e-151">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="0578e-151">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="0578e-152">Windows PowerShell 提供程序已注册后使用 Windows PowerShell，可以通过在命令行上运行的受支持的 cmdlet 来测试它。</span><span class="sxs-lookup"><span data-stu-id="0578e-152">Once your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="0578e-153">对于此基本提供程序，运行新的 shell，并使用`Get-PSProvider`cmdlet 检索提供程序的列表，并确保存在 AccessDb 提供程序。</span><span class="sxs-lookup"><span data-stu-id="0578e-153">For this basic provider, run the new shell and use the `Get-PSProvider` cmdlet to retrieve the list of providers and ensure that the AccessDb provider is present.</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="0578e-154">将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="0578e-154">The following output appears:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0578e-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0578e-155">See Also</span></span>

[<span data-ttu-id="0578e-156">创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="0578e-156">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="0578e-157">设计 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="0578e-157">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)
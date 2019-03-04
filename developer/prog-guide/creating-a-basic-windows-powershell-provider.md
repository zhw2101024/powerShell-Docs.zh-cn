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
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861763"
---
# <a name="creating-a-basic-windows-powershell-provider"></a><span data-ttu-id="57156-102">创建基础 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-102">Creating a Basic Windows PowerShell Provider</span></span>

<span data-ttu-id="57156-103">本主题是学习如何创建 Windows PowerShell 提供程序的起始点。</span><span class="sxs-lookup"><span data-stu-id="57156-103">This topic is the starting point for learning how to create a Windows PowerShell provider.</span></span> <span data-ttu-id="57156-104">此处所述的基本提供程序提供用于启动和停止提供程序，方法，它虽然此提供程序不提供一种方法来访问数据存储区或要获取或设置数据存储区中的数据，但它不提供所需的基本功能所有提供程序。</span><span class="sxs-lookup"><span data-stu-id="57156-104">The basic provider described here provides methods for starting and stopping the provider, and although this provider does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

<span data-ttu-id="57156-105">如上文所述的基本提供程序在此处实现方法来启动和停止提供程序。</span><span class="sxs-lookup"><span data-stu-id="57156-105">As mentioned previously, the basic provider described here implements methods for starting and stopping the provider.</span></span> <span data-ttu-id="57156-106">Windows PowerShell 运行时调用这些方法来初始化和取消初始化提供程序。</span><span class="sxs-lookup"><span data-stu-id="57156-106">The Windows PowerShell runtime calls these methods to initialize and uninitialize the provider.</span></span>

> [!NOTE]
> <span data-ttu-id="57156-107">可以通过 Windows PowerShell 提供的 AccessDBSampleProvider01.cs 文件中找到此提供程序的示例。</span><span class="sxs-lookup"><span data-stu-id="57156-107">You can find a sample of this provider in the AccessDBSampleProvider01.cs file provided by Windows PowerShell.</span></span>

<span data-ttu-id="57156-108">本主题中的部分如下所示：</span><span class="sxs-lookup"><span data-stu-id="57156-108">The sections in this topic include the following:</span></span>

- [<span data-ttu-id="57156-109">定义 Windows PowerShell 提供程序类</span><span class="sxs-lookup"><span data-stu-id="57156-109">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="57156-110">定义特定于提供程序的状态信息</span><span class="sxs-lookup"><span data-stu-id="57156-110">Defining Provider-Specific State Information</span></span>](#Defining-Provider-Specific-State-Information)

- [<span data-ttu-id="57156-111">初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-111">Initializing the Provider</span></span>](#Initializing-the-Provider)

- [<span data-ttu-id="57156-112">启动动态参数</span><span class="sxs-lookup"><span data-stu-id="57156-112">Start Dynamic Parameters</span></span>](#Start-Dynamic-Parameters)

- [<span data-ttu-id="57156-113">取消初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-113">Uninitializing the Provider</span></span>](#Uninitializing-the-Provider)

- [<span data-ttu-id="57156-114">代码示例</span><span class="sxs-lookup"><span data-stu-id="57156-114">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="57156-115">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-115">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="57156-116">定义 Windows PowerShell 提供程序类</span><span class="sxs-lookup"><span data-stu-id="57156-116">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="57156-117">创建 Windows PowerShell 提供程序的第一步是定义其.NET 类。</span><span class="sxs-lookup"><span data-stu-id="57156-117">The first step in creating a Windows PowerShell provider is to define its .NET class.</span></span> <span data-ttu-id="57156-118">此基本提供程序定义一个名为类`AccessDBProvider`派生[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类。</span><span class="sxs-lookup"><span data-stu-id="57156-118">This basic provider defines a class called `AccessDBProvider` that derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class.</span></span>

<span data-ttu-id="57156-119">建议将放在你提供程序类`Providers`API 命名空间，例如，xxx 的命名空间。PowerShell.Providers。</span><span class="sxs-lookup"><span data-stu-id="57156-119">It is recommended that you place your provider classes in a `Providers` namespace of your API namespace, for example, xxx.PowerShell.Providers.</span></span> <span data-ttu-id="57156-120">此提供程序使用`Microsoft.Samples.PowerShell.Provider`命名空间，在其中运行所有 Windows PowerShell 提供程序示例。</span><span class="sxs-lookup"><span data-stu-id="57156-120">This provider uses the `Microsoft.Samples.PowerShell.Provider` namespace, in which all Windows PowerShell provider samples run.</span></span>

> [!NOTE]
> <span data-ttu-id="57156-121">为 Windows PowerShell 提供程序类必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="57156-121">The class for a Windows PowerShell provider must be explicitly marked as public.</span></span> <span data-ttu-id="57156-122">未标记为公共的类将默认为内部和 Windows PowerShell 运行时将不会找到。</span><span class="sxs-lookup"><span data-stu-id="57156-122">Classes not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="57156-123">下面是此基本提供程序的类定义：</span><span class="sxs-lookup"><span data-stu-id="57156-123">Here is the class definition for this basic provider:</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

<span data-ttu-id="57156-124">类定义中前, 必须声明[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)具有语法 [CmdletProvider()] 属性。</span><span class="sxs-lookup"><span data-stu-id="57156-124">Right before the class definition, you must declare the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute, with the syntax [CmdletProvider()].</span></span>

<span data-ttu-id="57156-125">可以设置属性关键字，以进一步声明类，如有必要。</span><span class="sxs-lookup"><span data-stu-id="57156-125">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="57156-126">请注意， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)此处声明的属性包括两个参数。</span><span class="sxs-lookup"><span data-stu-id="57156-126">Notice that the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute declared here includes two parameters.</span></span> <span data-ttu-id="57156-127">第一个属性参数指定提供程序，用户可以更高版本修改默认的友好名称。</span><span class="sxs-lookup"><span data-stu-id="57156-127">The first attribute parameter specifies the default-friendly name for the provider, which the user can modify later.</span></span> <span data-ttu-id="57156-128">第二个参数指定的提供程序公开到 Windows PowerShell 运行时在命令处理过程的 Windows PowerShell 定义功能。</span><span class="sxs-lookup"><span data-stu-id="57156-128">The second parameter specifies the Windows PowerShell-defined capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="57156-129">定义提供程序功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。</span><span class="sxs-lookup"><span data-stu-id="57156-129">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="57156-130">由于这是基本提供程序，它支持任何功能。</span><span class="sxs-lookup"><span data-stu-id="57156-130">Because this is a base provider, it supports no capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="57156-131">Windows PowerShell 提供程序的完全限定的名称包括程序集名称和由 Windows PowerShell 在注册的提供程序的其他属性。</span><span class="sxs-lookup"><span data-stu-id="57156-131">The fully qualified name of the Windows PowerShell provider includes the assembly name and other attributes determined by Windows PowerShell upon registration of the provider.</span></span>

## <a name="defining-provider-specific-state-information"></a><span data-ttu-id="57156-132">定义特定于提供程序的状态信息</span><span class="sxs-lookup"><span data-stu-id="57156-132">Defining Provider-Specific State Information</span></span>

<span data-ttu-id="57156-133">[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类和所有派生的类被视为无状态因为 Windows PowerShell 运行时将创建仅在需要的提供程序实例。</span><span class="sxs-lookup"><span data-stu-id="57156-133">The [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class and all derived classes are considered stateless because the Windows PowerShell runtime creates provider instances only as required.</span></span> <span data-ttu-id="57156-134">因此，如果您的提供程序需要完全控制和状态维护特定于提供程序的数据，它必须派生一个类从[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)类。</span><span class="sxs-lookup"><span data-stu-id="57156-134">Therefore, if your provider requires full control and state maintenance for provider-specific data, it must derive a class from the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) class.</span></span> <span data-ttu-id="57156-135">在派生的类应定义需维护状态，以便可以访问特定于提供程序的数据，当 Windows PowerShell 运行时调用的成员[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以初始化访问接口。</span><span class="sxs-lookup"><span data-stu-id="57156-135">Your derived class should define the members necessary to maintain the state so that the provider-specific data can be accessed when the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="57156-136">Windows PowerShell 提供程序还可以维护基于连接的状态。</span><span class="sxs-lookup"><span data-stu-id="57156-136">A Windows PowerShell provider can also maintain connection-based state.</span></span> <span data-ttu-id="57156-137">有关保持连接状态的详细信息，请参阅[创建一个 PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="57156-137">For more information about maintaining connection state, see [Creating a PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

## <a name="initializing-the-provider"></a><span data-ttu-id="57156-138">初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-138">Initializing the Provider</span></span>

<span data-ttu-id="57156-139">若要初始化的提供程序，Windows PowerShell 运行时调用[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法启动 Windows PowerShell 时。</span><span class="sxs-lookup"><span data-stu-id="57156-139">To initialize the provider, the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method when Windows PowerShell is started.</span></span> <span data-ttu-id="57156-140">大多数情况下，您的提供程序可以使用此方法，它只是返回的默认实现[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象，描述您的提供程序。</span><span class="sxs-lookup"><span data-stu-id="57156-140">For the most part, your provider can use the default implementation of this method, which simply returns the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that describes your provider.</span></span> <span data-ttu-id="57156-141">但是，在你想要添加附加的初始化信息的情况下，则应实现您自己[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法返回的修改的版本[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)传递给您的提供程序的对象。</span><span class="sxs-lookup"><span data-stu-id="57156-141">However, in the case where you want to add additional initialization information, you should implement your own [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method that returns a modified version of the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that is passed to your provider.</span></span> <span data-ttu-id="57156-142">一般情况下，此方法应返回所提供[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象传递给它或修改过[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象包含其他初始化信息。</span><span class="sxs-lookup"><span data-stu-id="57156-142">In general, this method should return the provided [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object passed to it or a modified [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that contains other initialization information.</span></span>

<span data-ttu-id="57156-143">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="57156-143">This basic provider does not override this method.</span></span> <span data-ttu-id="57156-144">但是，下面的代码演示此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="57156-144">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

<span data-ttu-id="57156-145">提供程序可以维护状态的特定于提供程序的信息，如中所述[定义特定于提供程序的数据状态](#Defining-Provider-Specific-State-Information)。</span><span class="sxs-lookup"><span data-stu-id="57156-145">The provider can maintain the state of provider-specific information as described in [Defining Provider-specific Data State](#Defining-Provider-Specific-State-Information).</span></span> <span data-ttu-id="57156-146">在这种情况下，您的实现必须重写[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以返回派生的类的实例。</span><span class="sxs-lookup"><span data-stu-id="57156-146">In this case, your implementation must override the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to return an instance of the derived class.</span></span>

## <a name="start-dynamic-parameters"></a><span data-ttu-id="57156-147">启动动态参数</span><span class="sxs-lookup"><span data-stu-id="57156-147">Start Dynamic Parameters</span></span>

<span data-ttu-id="57156-148">在提供程序实现的[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法可能需要其他参数。</span><span class="sxs-lookup"><span data-stu-id="57156-148">Your provider implementation of the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method might require additional parameters.</span></span> <span data-ttu-id="57156-149">在这种情况下，该提供程序应重写[System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法并返回具有属性和字段与分析的对象属性类似于cmdlet 类或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。</span><span class="sxs-lookup"><span data-stu-id="57156-149">In this case, the provider should override the [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) method and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="57156-150">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="57156-150">This basic provider does not override this method.</span></span> <span data-ttu-id="57156-151">但是，下面的代码演示此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="57156-151">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a><span data-ttu-id="57156-152">取消初始化提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-152">Uninitializing the Provider</span></span>

<span data-ttu-id="57156-153">若要释放的 Windows PowerShell 提供程序使用的资源，您的提供程序应实现其自己[System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。</span><span class="sxs-lookup"><span data-stu-id="57156-153">To free resources that the Windows PowerShell provider uses, your provider should implement its own [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) method.</span></span> <span data-ttu-id="57156-154">要取消初始化的提供程序在会话的结束位置的 Windows PowerShell 运行时调用此方法。</span><span class="sxs-lookup"><span data-stu-id="57156-154">This method is called by the Windows PowerShell runtime to uninitialize the provider at the close of a session.</span></span>

<span data-ttu-id="57156-155">此基本提供程序不重写此方法。</span><span class="sxs-lookup"><span data-stu-id="57156-155">This basic provider does not override this method.</span></span> <span data-ttu-id="57156-156">但是，下面的代码演示此方法的默认实现：</span><span class="sxs-lookup"><span data-stu-id="57156-156">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a><span data-ttu-id="57156-157">代码示例</span><span class="sxs-lookup"><span data-stu-id="57156-157">Code Sample</span></span>

<span data-ttu-id="57156-158">有关完整的示例代码，请参阅[AccessDbProviderSample01 代码示例](./accessdbprovidersample01-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="57156-158">For complete sample code, see [AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="57156-159">测试 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-159">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="57156-160">Windows PowerShell 提供程序已注册后使用 Windows PowerShell，可以通过在命令行上运行的受支持的 cmdlet 来测试它。</span><span class="sxs-lookup"><span data-stu-id="57156-160">Once your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="57156-161">对于此基本提供程序，运行新的 shell，并使用`Get-PSProvider`cmdlet 检索提供程序的列表，并确保存在 AccessDb 提供程序。</span><span class="sxs-lookup"><span data-stu-id="57156-161">For this basic provider, run the new shell and use the `Get-PSProvider` cmdlet to retrieve the list of providers and ensure that the AccessDb provider is present.</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="57156-162">将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="57156-162">The following output appears:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="57156-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57156-163">See Also</span></span>

[<span data-ttu-id="57156-164">创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-164">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="57156-165">设计 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="57156-165">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)
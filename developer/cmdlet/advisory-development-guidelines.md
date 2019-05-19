---
title: 咨询开发指南 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854858"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="64525-102">咨询性的开发指南</span><span class="sxs-lookup"><span data-stu-id="64525-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="64525-103">本部分介绍应考虑以确保良好的开发和用户体验的指导原则。</span><span class="sxs-lookup"><span data-stu-id="64525-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="64525-104">有时它们可能适用，并且它们有时不可能。</span><span class="sxs-lookup"><span data-stu-id="64525-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="64525-105">设计指南</span><span class="sxs-lookup"><span data-stu-id="64525-105">Design Guidelines</span></span>

<span data-ttu-id="64525-106">设计 cmdlet 时，应考虑以下准则。</span><span class="sxs-lookup"><span data-stu-id="64525-106">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="64525-107">找到一个设计指导原则适用于你的情况，请务必查看类似的指导原则的代码准则。</span><span class="sxs-lookup"><span data-stu-id="64525-107">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="64525-108">支持一个 InputObject 参数 (AD01)</span><span class="sxs-lookup"><span data-stu-id="64525-108">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="64525-109">由于 Windows PowerShell 直接与 Microsoft.NET Framework 对象的工作原理，.NET Framework 对象通常是可完全匹配的类型用户需要执行特定操作。</span><span class="sxs-lookup"><span data-stu-id="64525-109">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="64525-110">`InputObject` 是一个接受此类对象作为输入参数的标准名称。</span><span class="sxs-lookup"><span data-stu-id="64525-110">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="64525-111">例如，示例**停止 Proc**中的 cmdlet [StopProc 教程](./stopproc-tutorial.md)定义`InputObject`类型支持的输入管道中的过程的参数。</span><span class="sxs-lookup"><span data-stu-id="64525-111">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="64525-112">用户可以获取一组进程对象、 操作他们选择的准确对象，若要停止，以及然后将它们传递给**停止进程**直接 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64525-112">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="64525-113">Force 参数 (AD02) 的支持</span><span class="sxs-lookup"><span data-stu-id="64525-113">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="64525-114">有时，一个 cmdlet 需要防止用户执行请求的操作。</span><span class="sxs-lookup"><span data-stu-id="64525-114">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="64525-115">此类 cmdlet 应支持`Force`参数，以允许用户重写该保护，如果用户有权执行该操作。</span><span class="sxs-lookup"><span data-stu-id="64525-115">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="64525-116">例如， [Remove-item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet 通常不删除只读文件。</span><span class="sxs-lookup"><span data-stu-id="64525-116">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="64525-117">但是，此 cmdlet 支持`Force`参数以便用户可以强制删除只读文件。</span><span class="sxs-lookup"><span data-stu-id="64525-117">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="64525-118">如果用户已有权修改只读属性，以及用户中删除文件，则使用`Force`参数简化了该操作。</span><span class="sxs-lookup"><span data-stu-id="64525-118">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="64525-119">但是，如果用户没有权限来删除文件，`Force`参数不起作用。</span><span class="sxs-lookup"><span data-stu-id="64525-119">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="64525-120">处理通过 Windows PowerShell (AD03) 的凭据</span><span class="sxs-lookup"><span data-stu-id="64525-120">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="64525-121">Cmdlet 应定义`Credential`参数以表示凭据。</span><span class="sxs-lookup"><span data-stu-id="64525-121">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="64525-122">此参数必须属于类型[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) ，且必须使用凭据特性声明定义。</span><span class="sxs-lookup"><span data-stu-id="64525-122">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="64525-123">未直接提供完整的凭据时，此支持会自动提示用户的用户名、 密码，或两个。</span><span class="sxs-lookup"><span data-stu-id="64525-123">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="64525-124">有关凭据属性的详细信息，请参阅[凭据特性声明](./credential-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="64525-124">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="64525-125">支持编码的参数 (AD04)</span><span class="sxs-lookup"><span data-stu-id="64525-125">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="64525-126">如果你的 cmdlet 读取或写入文本或二进制格式，例如写入或读取文件系统中的文件从然后 cmdlet 必须具有编码参数，用于指定如何对文本进行编码以二进制格式。</span><span class="sxs-lookup"><span data-stu-id="64525-126">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="64525-127">测试 Cmdlet 应返回一个布尔值 (AD05)</span><span class="sxs-lookup"><span data-stu-id="64525-127">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="64525-128">执行测试针对用户的资源的 Cmdlet 应返回[System.Boolean](/dotnet/api/System.Boolean)类型到管道，以便它们可以在条件表达式中使用。</span><span class="sxs-lookup"><span data-stu-id="64525-128">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="64525-129">代码指南</span><span class="sxs-lookup"><span data-stu-id="64525-129">Code Guidelines</span></span>

<span data-ttu-id="64525-130">编写 cmdlet 代码时，应考虑以下准则。</span><span class="sxs-lookup"><span data-stu-id="64525-130">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="64525-131">找到适用于您的具体情况的指导，请务必查看类似的指导原则的设计指南。</span><span class="sxs-lookup"><span data-stu-id="64525-131">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="64525-132">遵循 Cmdlet 类命名约定 (AC01)</span><span class="sxs-lookup"><span data-stu-id="64525-132">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="64525-133">通过以下标准的命名约定，使 cmdlet 更容易地发现，并帮助用户了解完全 cmdlet 进行的操作。</span><span class="sxs-lookup"><span data-stu-id="64525-133">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="64525-134">这种做法是使用 Windows PowerShell cmdlet 是公共类型，因为其他开发人员尤为重要。</span><span class="sxs-lookup"><span data-stu-id="64525-134">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="64525-135">在正确的 Namespace 中定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="64525-135">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="64525-136">通常情况下将附加的.NET Framework 命名空间中定义的 cmdlet 类"。命令"的命名空间的表示在其中运行该 cmdlet 的产品。</span><span class="sxs-lookup"><span data-stu-id="64525-136">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="64525-137">例如，在中定义的包含 Windows PowerShell cmdlet`Microsoft.PowerShell.Commands`命名空间。</span><span class="sxs-lookup"><span data-stu-id="64525-137">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="64525-138">Cmdlet 类以匹配的 Cmdlet 名称命名</span><span class="sxs-lookup"><span data-stu-id="64525-138">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="64525-139">命名时实现 cmdlet 的.NET Framework 类，类命名为"*\<谓词 >**\<名词 >**\<命令 >*"中，您可以将为*\<谓词 >* 并*\<名词 >* 占位符替换动词和名词的 cmdlet 名称使用。</span><span class="sxs-lookup"><span data-stu-id="64525-139">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="64525-140">例如， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)由一个名为类实现 cmdlet `GetProcessCommand`。</span><span class="sxs-lookup"><span data-stu-id="64525-140">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="64525-141">如果没有管道输入重写 BeginProcessing 方法 (AC02)</span><span class="sxs-lookup"><span data-stu-id="64525-141">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="64525-142">如果你的 cmdlet 不接受来自管道的输入，应在实现处理[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="64525-142">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="64525-143">使用此方法允许 Windows PowerShell 来维护 cmdlet 之间进行排序。</span><span class="sxs-lookup"><span data-stu-id="64525-143">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="64525-144">在管道中的剩余 cmdlet 获得机会开始其处理之前，在管道中的第一个 cmdlet 始终返回其对象。</span><span class="sxs-lookup"><span data-stu-id="64525-144">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="64525-145">若要处理停止请求数，重写 StopProcessing 方法 (AC03)</span><span class="sxs-lookup"><span data-stu-id="64525-145">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="64525-146">重写[System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，以便你的 cmdlet 可以处理停止信号。</span><span class="sxs-lookup"><span data-stu-id="64525-146">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="64525-147">某些 cmdlet 需要很长时间才能完成其操作，可让 Windows PowerShell 运行时，例如当该 cmdlet 将阻止中长时间运行的 RPC 调用的线程的调用之间传递很长时间。</span><span class="sxs-lookup"><span data-stu-id="64525-147">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="64525-148">这包括对进行调用的 cmdlet [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法，为[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，和其他反馈可能需要很长时间才能完成的机制。</span><span class="sxs-lookup"><span data-stu-id="64525-148">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="64525-149">这种情况下用户可能需要将停止信号发送到这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64525-149">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="64525-150">实现 IDisposable 接口 (AC04)</span><span class="sxs-lookup"><span data-stu-id="64525-150">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="64525-151">如果你的 cmdlet 具有 （写入到管道） 的未释放的对象由[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法中，你的 cmdlet 可能需要其他对象可供使用。</span><span class="sxs-lookup"><span data-stu-id="64525-151">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="64525-152">例如，如果你 cmdlet 会打开文件句柄中的其[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，并保留该句柄打开以供[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，此句柄必须处理结束时关闭。</span><span class="sxs-lookup"><span data-stu-id="64525-152">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="64525-153">Windows PowerShell 运行时不会始终调用[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="64525-153">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="64525-154">例如， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)可能不调用方法，如果该 cmdlet 通过其操作期间取消或如果终止该 cmdlet 的任何部分中会发生错误。</span><span class="sxs-lookup"><span data-stu-id="64525-154">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="64525-155">因此，需要对象清理的 cmdlet 的.NET Framework 类应实现的完整[System.IDisposable](/dotnet/api/System.IDisposable)接口模式，以便 Windows PowerShell 运行时可以调用都包括终结器，[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)并[System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)末尾的处理方法。</span><span class="sxs-lookup"><span data-stu-id="64525-155">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="64525-156">使用适合于序列化的参数类型 (AC05)</span><span class="sxs-lookup"><span data-stu-id="64525-156">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="64525-157">若要支持在远程计算机上运行你的 cmdlet，使用可以轻松地序列化客户端计算机上，然后解除冻结服务器计算机上的类型。</span><span class="sxs-lookup"><span data-stu-id="64525-157">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="64525-158">按照类型都是序列化友好。</span><span class="sxs-lookup"><span data-stu-id="64525-158">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="64525-159">基元类型：</span><span class="sxs-lookup"><span data-stu-id="64525-159">Primitive types:</span></span>

- <span data-ttu-id="64525-160">字节、 SByte、 Decimal、 单、 Double、 Int16、 Int32、 Int64、 Uint16、 UInt32 和 UInt64。</span><span class="sxs-lookup"><span data-stu-id="64525-160">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="64525-161">一个布尔值、 Guid、 字节 []、 TimeSpan、 DateTime、 Uri 和版本。</span><span class="sxs-lookup"><span data-stu-id="64525-161">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="64525-162">Char、 String，XmlDocument。</span><span class="sxs-lookup"><span data-stu-id="64525-162">Char, String, XmlDocument.</span></span>

<span data-ttu-id="64525-163">内置 rehydratable 类型：</span><span class="sxs-lookup"><span data-stu-id="64525-163">Built-in rehydratable types:</span></span>

- <span data-ttu-id="64525-164">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="64525-164">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="64525-165">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="64525-165">SwitchParameter</span></span>

- <span data-ttu-id="64525-166">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="64525-166">PSListModifier</span></span>

- <span data-ttu-id="64525-167">PSCredential</span><span class="sxs-lookup"><span data-stu-id="64525-167">PSCredential</span></span>

- <span data-ttu-id="64525-168">Ip 地址 MailAddress</span><span class="sxs-lookup"><span data-stu-id="64525-168">IPAddress, MailAddress</span></span>

- <span data-ttu-id="64525-169">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="64525-169">CultureInfo</span></span>

- <span data-ttu-id="64525-170">X509Certificate2, X500DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="64525-170">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="64525-171">DirectorySecurity，FileSecurity，RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="64525-171">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="64525-172">其他类型：</span><span class="sxs-lookup"><span data-stu-id="64525-172">Other types:</span></span>

- <span data-ttu-id="64525-173">SecureString</span><span class="sxs-lookup"><span data-stu-id="64525-173">SecureString</span></span>

- <span data-ttu-id="64525-174">容器 （列表和字典的上述类型）</span><span class="sxs-lookup"><span data-stu-id="64525-174">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="64525-175">使用 SecureString 的敏感数据 (AC06)</span><span class="sxs-lookup"><span data-stu-id="64525-175">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="64525-176">始终处理敏感数据时使用[System.Security.Securestring](/dotnet/api/System.Security.SecureString)数据类型。</span><span class="sxs-lookup"><span data-stu-id="64525-176">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="64525-177">这可能包括参数，以及将敏感数据返回到管道的管道输入。</span><span class="sxs-lookup"><span data-stu-id="64525-177">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="64525-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64525-178">See Also</span></span>

[<span data-ttu-id="64525-179">所需的开发指导原则</span><span class="sxs-lookup"><span data-stu-id="64525-179">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="64525-180">强烈建议的开发指导原则</span><span class="sxs-lookup"><span data-stu-id="64525-180">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

[<span data-ttu-id="64525-181">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="64525-181">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

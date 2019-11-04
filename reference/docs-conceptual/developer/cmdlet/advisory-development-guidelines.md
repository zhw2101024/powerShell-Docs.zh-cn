---
title: 顾问开发指南 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370036"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="3e2bd-102">咨询性的开发指南</span><span class="sxs-lookup"><span data-stu-id="3e2bd-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="3e2bd-103">本部分介绍了确保良好开发和用户体验时应考虑的准则。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="3e2bd-104">有时可能会应用这些应用，有时可能不适用。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="3e2bd-105">设计准则</span><span class="sxs-lookup"><span data-stu-id="3e2bd-105">Design Guidelines</span></span>

<span data-ttu-id="3e2bd-106">设计 cmdlet 时，应考虑以下准则。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-106">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="3e2bd-107">如果找到适用于你的情况的设计准则，请务必查看类似准则的代码准则。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-107">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="3e2bd-108">支持 InputObject 参数（AD01）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-108">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="3e2bd-109">由于 Windows PowerShell 直接与 Microsoft .NET 框架对象结合使用，因此 .NET Framework 对象通常可用，与用户执行特定操作所需的类型完全匹配。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-109">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="3e2bd-110">`InputObject` 是将此类对象作为输入的参数的标准名称。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-110">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="3e2bd-111">例如， [StopProc 教程](./stopproc-tutorial.md)中的示例**停止**过程 cmdlet 定义了支持管道输入的进程类型 `InputObject` 参数。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-111">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="3e2bd-112">用户可以获取一组进程对象，对其进行操作以选择要停止的确切对象，然后将这些对象直接传递给**Stop Proc** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-112">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="3e2bd-113">支持 Force 参数（AD02）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-113">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="3e2bd-114">有时，cmdlet 需要保护用户执行所请求的操作。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-114">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="3e2bd-115">如果用户具有执行操作的权限，则此类 cmdlet 应支持 `Force` 参数以允许用户重写该保护。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-115">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="3e2bd-116">例如，[删除项](/powershell/module/microsoft.powershell.management/remove-item)cmdlet 通常不会删除只读文件。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-116">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="3e2bd-117">但是，此 cmdlet 支持 `Force` 参数，因此用户可以强制删除只读文件。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-117">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="3e2bd-118">如果用户已有权修改只读属性，并且用户删除了该文件，则使用 `Force` 参数可以简化该操作。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-118">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="3e2bd-119">但是，如果用户没有删除文件的权限，则 `Force` 参数不起作用。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-119">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="3e2bd-120">通过 Windows PowerShell （AD03）处理凭据</span><span class="sxs-lookup"><span data-stu-id="3e2bd-120">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="3e2bd-121">Cmdlet 应定义 `Credential` 参数以表示凭据。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-121">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="3e2bd-122">此参数[的类型必须](/dotnet/api/System.Management.Automation.PSCredential)为类型，并且必须使用 Credential 特性声明进行定义。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-122">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="3e2bd-123">此支持会自动提示用户输入用户名和密码，或者在未直接提供完整凭据时提示用户。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-123">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="3e2bd-124">有关 Credential 特性的详细信息，请参阅[Credential 特性声明](./credential-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-124">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="3e2bd-125">支持编码参数（AD04）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-125">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="3e2bd-126">如果你的 cmdlet 在二进制格式（例如写入或读取文件系统中的文件）中读取或写入文本，则 cmdlet 必须具有 Encoding 参数，该参数指定如何以二进制格式对文本进行编码。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-126">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="3e2bd-127">测试 Cmdlet 应返回布尔值（AD05）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-127">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="3e2bd-128">对其资源执行测试的 cmdlet[应将 system.string 类型返回](/dotnet/api/System.Boolean)到管道，以使它们可用于条件表达式。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-128">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="3e2bd-129">代码准则</span><span class="sxs-lookup"><span data-stu-id="3e2bd-129">Code Guidelines</span></span>

<span data-ttu-id="3e2bd-130">编写 cmdlet 代码时，应考虑以下准则。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-130">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="3e2bd-131">当你发现适用于你的情况的准则时，请务必查看类似指导原则的设计指南。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-131">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="3e2bd-132">遵循 Cmdlet 类命名约定（AC01）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-132">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="3e2bd-133">遵循标准命名约定，可以更容易地发现 cmdlet，并帮助用户确切了解 cmdlet 的作用。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-133">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="3e2bd-134">这种做法对于使用 Windows PowerShell 的其他开发人员尤其重要，因为 cmdlet 是公共类型。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-134">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="3e2bd-135">在正确的命名空间中定义 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e2bd-135">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="3e2bd-136">通常会在附加 "" 的 .NET Framework 命名空间中定义 cmdlet 的类。命令 "的命名空间，表示在其中运行 cmdlet 的产品。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-136">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="3e2bd-137">例如，Windows PowerShell 附带的 cmdlet 在 `Microsoft.PowerShell.Commands` 命名空间中定义。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-137">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="3e2bd-138">将 Cmdlet 类命名为与 Cmdlet 名称匹配</span><span class="sxs-lookup"><span data-stu-id="3e2bd-138">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="3e2bd-139">为实现 cmdlet 的 .NET Framework 类命名时，请将类命名为 " *\<Verb > **\<Noun >** \<Command >* "，将 *\<Verb* > \<Noun 和 *>* 占位符替换为用于 cmdlet 名称的动词和名词。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-139">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="3e2bd-140">例如，[获取过程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 由名为 `GetProcessCommand` 的类实现。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-140">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="3e2bd-141">如果没有管道输入，则重写 BeginProcessing 方法（AC02）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-141">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="3e2bd-142">如果 cmdlet 不接受来自管道的输入，则应在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中实现处理。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-142">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="3e2bd-143">使用此方法可使 Windows PowerShell 保持 cmdlet 之间的顺序。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-143">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="3e2bd-144">管道中的第一个 cmdlet 始终返回其对象，然后管道中的其余 cmdlet 才能开始处理。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-144">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="3e2bd-145">若要处理 Stop 请求，请重写 StopProcessing 方法（AC03）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-145">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="3e2bd-146">重写[StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，以使 Cmdlet 能够处理停止信号。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-146">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="3e2bd-147">某些 cmdlet 需要很长时间才能完成其操作，并且在对 Windows PowerShell 运行时的调用之间等待较长的时间，例如当 cmdlet 在长时间运行的 RPC 调用中阻止该线程时。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-147">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="3e2bd-148">这包括一些 cmdlet，这些 cmdlet 将对[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的调用发送到[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，并将其发送到可能需要很长时间才能完成的其他反馈机制.</span><span class="sxs-lookup"><span data-stu-id="3e2bd-148">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="3e2bd-149">对于这些情况，用户可能需要将停止信号发送到这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-149">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="3e2bd-150">实现 IDisposable 接口（AC04）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-150">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="3e2bd-151">如果 cmdlet 的对象未被 ProcessRecord 方法释放（写入管道），则 cmdlet 可能需要额外的对象处理[功能](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。）。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-151">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="3e2bd-152">例如，如果 cmdlet 打开其[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中的文件句柄，并使该句柄处于打开状态以供[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法使用，则此句柄必须为处理结束后关闭。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-152">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="3e2bd-153">Windows PowerShell 运行时并不总是调用[system.web. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-153">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="3e2bd-154">例如，如果 cmdlet 在其操作中间中途取消，或在 cmdlet 的任何部分发生终止错误，则可能不会调用[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-154">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="3e2bd-155">因此，需要对象清理的 cmdlet 的 .NET Framework 类应实现完整的 [System.IDisposable](/dotnet/api/System.IDisposable) 接口模式（包括终结器），以便 Windows PowerShell 运行时可以调用处理结束时，将会进行 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 和 [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) 方法。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-155">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="3e2bd-156">使用序列化友好参数类型（AC05）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-156">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="3e2bd-157">若要支持在远程计算机上运行 cmdlet，请使用可在客户端计算机上轻松序列化的类型，然后在服务器计算机上解除冻结。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-157">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="3e2bd-158">以下类型是可序列化的。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-158">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="3e2bd-159">基元类型：</span><span class="sxs-lookup"><span data-stu-id="3e2bd-159">Primitive types:</span></span>

- <span data-ttu-id="3e2bd-160">Byte、SByte、Decimal、Single、Double、Int16、Int32、Int64、Uint16、UInt32 和 UInt64。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-160">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="3e2bd-161">布尔、Guid、Byte []、TimeSpan、DateTime、Uri 和版本。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-161">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="3e2bd-162">Char、String、Xml。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-162">Char, String, XmlDocument.</span></span>

<span data-ttu-id="3e2bd-163">内置 rehydratable 类型：</span><span class="sxs-lookup"><span data-stu-id="3e2bd-163">Built-in rehydratable types:</span></span>

- <span data-ttu-id="3e2bd-164">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="3e2bd-164">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="3e2bd-165">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3e2bd-165">SwitchParameter</span></span>

- <span data-ttu-id="3e2bd-166">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="3e2bd-166">PSListModifier</span></span>

- <span data-ttu-id="3e2bd-167">PSCredential</span><span class="sxs-lookup"><span data-stu-id="3e2bd-167">PSCredential</span></span>

- <span data-ttu-id="3e2bd-168">IPAddress、MailAddress</span><span class="sxs-lookup"><span data-stu-id="3e2bd-168">IPAddress, MailAddress</span></span>

- <span data-ttu-id="3e2bd-169">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="3e2bd-169">CultureInfo</span></span>

- <span data-ttu-id="3e2bd-170">X509Certificate2、System.security.cryptography.x509certificates.x500distinguishedname</span><span class="sxs-lookup"><span data-stu-id="3e2bd-170">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="3e2bd-171">System.security.accesscontrol.directorysecurity、FileSecurity、RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="3e2bd-171">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="3e2bd-172">其他类型：</span><span class="sxs-lookup"><span data-stu-id="3e2bd-172">Other types:</span></span>

- <span data-ttu-id="3e2bd-173">SecureString</span><span class="sxs-lookup"><span data-stu-id="3e2bd-173">SecureString</span></span>

- <span data-ttu-id="3e2bd-174">容器（以上类型的列表和字典）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-174">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="3e2bd-175">对敏感数据使用 SecureString （AC06）</span><span class="sxs-lookup"><span data-stu-id="3e2bd-175">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="3e2bd-176">当处理敏感数据时，始终使用[Securestring](/dotnet/api/System.Security.SecureString)数据类型。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-176">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="3e2bd-177">这可能包括参数的管道输入，并将敏感数据返回给管道。</span><span class="sxs-lookup"><span data-stu-id="3e2bd-177">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e2bd-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e2bd-178">See Also</span></span>

[<span data-ttu-id="3e2bd-179">必需的开发指南</span><span class="sxs-lookup"><span data-stu-id="3e2bd-179">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="3e2bd-180">强烈建议开发指南</span><span class="sxs-lookup"><span data-stu-id="3e2bd-180">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

[<span data-ttu-id="3e2bd-181">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e2bd-181">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

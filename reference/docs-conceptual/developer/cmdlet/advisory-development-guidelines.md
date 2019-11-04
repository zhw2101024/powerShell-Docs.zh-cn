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
# <a name="advisory-development-guidelines"></a>咨询性的开发指南

本部分介绍了确保良好开发和用户体验时应考虑的准则。 有时可能会应用这些应用，有时可能不适用。

## <a name="design-guidelines"></a>设计准则

设计 cmdlet 时，应考虑以下准则。 如果找到适用于你的情况的设计准则，请务必查看类似准则的代码准则。

### <a name="support-an-inputobject-parameter-ad01"></a>支持 InputObject 参数（AD01）

由于 Windows PowerShell 直接与 Microsoft .NET 框架对象结合使用，因此 .NET Framework 对象通常可用，与用户执行特定操作所需的类型完全匹配。 `InputObject` 是将此类对象作为输入的参数的标准名称。 例如， [StopProc 教程](./stopproc-tutorial.md)中的示例**停止**过程 cmdlet 定义了支持管道输入的进程类型 `InputObject` 参数。 用户可以获取一组进程对象，对其进行操作以选择要停止的确切对象，然后将这些对象直接传递给**Stop Proc** cmdlet。

### <a name="support-the-force-parameter-ad02"></a>支持 Force 参数（AD02）

有时，cmdlet 需要保护用户执行所请求的操作。 如果用户具有执行操作的权限，则此类 cmdlet 应支持 `Force` 参数以允许用户重写该保护。

例如，[删除项](/powershell/module/microsoft.powershell.management/remove-item)cmdlet 通常不会删除只读文件。 但是，此 cmdlet 支持 `Force` 参数，因此用户可以强制删除只读文件。 如果用户已有权修改只读属性，并且用户删除了该文件，则使用 `Force` 参数可以简化该操作。 但是，如果用户没有删除文件的权限，则 `Force` 参数不起作用。

### <a name="handle-credentials-through-windows-powershell-ad03"></a>通过 Windows PowerShell （AD03）处理凭据

Cmdlet 应定义 `Credential` 参数以表示凭据。 此参数[的类型必须](/dotnet/api/System.Management.Automation.PSCredential)为类型，并且必须使用 Credential 特性声明进行定义。 此支持会自动提示用户输入用户名和密码，或者在未直接提供完整凭据时提示用户。 有关 Credential 特性的详细信息，请参阅[Credential 特性声明](./credential-attribute-declaration.md)。

### <a name="support-encoding-parameters-ad04"></a>支持编码参数（AD04）

如果你的 cmdlet 在二进制格式（例如写入或读取文件系统中的文件）中读取或写入文本，则 cmdlet 必须具有 Encoding 参数，该参数指定如何以二进制格式对文本进行编码。

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>测试 Cmdlet 应返回布尔值（AD05）

对其资源执行测试的 cmdlet[应将 system.string 类型返回](/dotnet/api/System.Boolean)到管道，以使它们可用于条件表达式。

## <a name="code-guidelines"></a>代码准则

编写 cmdlet 代码时，应考虑以下准则。 当你发现适用于你的情况的准则时，请务必查看类似指导原则的设计指南。

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>遵循 Cmdlet 类命名约定（AC01）

遵循标准命名约定，可以更容易地发现 cmdlet，并帮助用户确切了解 cmdlet 的作用。 这种做法对于使用 Windows PowerShell 的其他开发人员尤其重要，因为 cmdlet 是公共类型。

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>在正确的命名空间中定义 Cmdlet

通常会在附加 "" 的 .NET Framework 命名空间中定义 cmdlet 的类。命令 "的命名空间，表示在其中运行 cmdlet 的产品。 例如，Windows PowerShell 附带的 cmdlet 在 `Microsoft.PowerShell.Commands` 命名空间中定义。

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>将 Cmdlet 类命名为与 Cmdlet 名称匹配

为实现 cmdlet 的 .NET Framework 类命名时，请将类命名为 " *\<Verb > **\<Noun >** \<Command >* "，将 *\<Verb* > \<Noun 和 *>* 占位符替换为用于 cmdlet 名称的动词和名词。 例如，[获取过程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 由名为 `GetProcessCommand` 的类实现。

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>如果没有管道输入，则重写 BeginProcessing 方法（AC02）

如果 cmdlet 不接受来自管道的输入，则应在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中实现处理。 使用此方法可使 Windows PowerShell 保持 cmdlet 之间的顺序。 管道中的第一个 cmdlet 始终返回其对象，然后管道中的其余 cmdlet 才能开始处理。

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>若要处理 Stop 请求，请重写 StopProcessing 方法（AC03）

重写[StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，以使 Cmdlet 能够处理停止信号。 某些 cmdlet 需要很长时间才能完成其操作，并且在对 Windows PowerShell 运行时的调用之间等待较长的时间，例如当 cmdlet 在长时间运行的 RPC 调用中阻止该线程时。 这包括一些 cmdlet，这些 cmdlet 将对[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的调用发送到[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，并将其发送到可能需要很长时间才能完成的其他反馈机制. 对于这些情况，用户可能需要将停止信号发送到这些 cmdlet。

### <a name="implement-the-idisposable-interface-ac04"></a>实现 IDisposable 接口（AC04）

如果 cmdlet 的对象未被 ProcessRecord 方法释放（写入管道），则 cmdlet 可能需要额外的对象处理[功能](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。）。 例如，如果 cmdlet 打开其[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中的文件句柄，并使该句柄处于打开状态以供[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法使用，则此句柄必须为处理结束后关闭。

Windows PowerShell 运行时并不总是调用[system.web. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 例如，如果 cmdlet 在其操作中间中途取消，或在 cmdlet 的任何部分发生终止错误，则可能不会调用[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 。 因此，需要对象清理的 cmdlet 的 .NET Framework 类应实现完整的 [System.IDisposable](/dotnet/api/System.IDisposable) 接口模式（包括终结器），以便 Windows PowerShell 运行时可以调用处理结束时，将会进行 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 和 [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) 方法。

### <a name="use-serialization-friendly-parameter-types-ac05"></a>使用序列化友好参数类型（AC05）

若要支持在远程计算机上运行 cmdlet，请使用可在客户端计算机上轻松序列化的类型，然后在服务器计算机上解除冻结。 以下类型是可序列化的。

基元类型：

- Byte、SByte、Decimal、Single、Double、Int16、Int32、Int64、Uint16、UInt32 和 UInt64。

- 布尔、Guid、Byte []、TimeSpan、DateTime、Uri 和版本。

- Char、String、Xml。

内置 rehydratable 类型：

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IPAddress、MailAddress

- CultureInfo

- X509Certificate2、System.security.cryptography.x509certificates.x500distinguishedname

- System.security.accesscontrol.directorysecurity、FileSecurity、RegistrySecurity

其他类型：

- SecureString

- 容器（以上类型的列表和字典）

### <a name="use-securestring-for-sensitive-data-ac06"></a>对敏感数据使用 SecureString （AC06）

当处理敏感数据时，始终使用[Securestring](/dotnet/api/System.Security.SecureString)数据类型。 这可能包括参数的管道输入，并将敏感数据返回给管道。

## <a name="see-also"></a>另请参阅

[必需的开发指南](./required-development-guidelines.md)

[强烈建议开发指南](./strongly-encouraged-development-guidelines.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

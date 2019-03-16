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
ms.openlocfilehash: 871a74a084da3c7ec36767b7195461e0e7290cb9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056560"
---
# <a name="advisory-development-guidelines"></a>咨询性的开发指南

本部分介绍应考虑以确保良好的开发和用户体验的指导原则。 有时它们可能适用，并且它们有时不可能。

## <a name="design-guidelines"></a>设计指南

- [支持一个 InputObject 参数 (AD01)](./advisory-development-guidelines.md#AD01)

- [Force 参数 (AD02) 的支持](./advisory-development-guidelines.md#AD02)

- [处理通过 Windows PowerShell (AD03) 的凭据](./advisory-development-guidelines.md#AD03)

- [支持编码的参数 (AD04)](./advisory-development-guidelines.md#AD04)

- [测试 Cmdlet 应返回一个布尔值 (AD05)](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a>代码指南

- [遵循 Cmdlet 类命名约定 (AC01)](./advisory-development-guidelines.md#AC01)

- [如果没有管道输入重写 BeginProcessing 方法 (AC02)](./advisory-development-guidelines.md#AC02)

- [若要处理停止请求数，重写 StopProcessing 方法 (AC03)](./advisory-development-guidelines.md#AC03)

- [实现 IDisposable 接口 (AC04)](./advisory-development-guidelines.md#AC04)

- [使用适合于序列化的参数类型 (AC05)](./advisory-development-guidelines.md#AC05)

- [使用 SecureString 的敏感数据 (AC06)](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a>设计指南

设计 cmdlet 时，应考虑以下准则。 找到一个设计指导原则适用于你的情况，请务必查看类似的指导原则的代码准则。

### <a name="support-an-inputobject-parameter-ad01"></a>支持一个 InputObject 参数 (AD01)

由于 Windows PowerShell 直接与 Microsoft.NET Framework 对象的工作原理，.NET Framework 对象通常是可完全匹配的类型用户需要执行特定操作。 `InputObject` 是一个接受此类对象作为输入参数的标准名称。 例如，示例**停止 Proc**中的 cmdlet [StopProc 教程](./stopproc-tutorial.md)定义`InputObject`类型支持的输入管道中的过程的参数。 用户可以获取一组进程对象、 操作他们选择的准确对象，若要停止，以及然后将它们传递给**停止进程**直接 cmdlet。

### <a name="support-the-force-parameter-ad02"></a>Force 参数 (AD02) 的支持

有时，一个 cmdlet 需要防止用户执行请求的操作。 此类 cmdlet 应支持`Force`参数，以允许用户重写该保护，如果用户有权执行该操作。

例如， [Remove-item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet 通常不删除只读文件。 但是，此 cmdlet 支持`Force`参数以便用户可以强制删除只读文件。 如果用户已有权修改只读属性，以及用户中删除文件，则使用`Force`参数简化了该操作。 但是，如果用户没有权限来删除文件，`Force`参数不起作用。

### <a name="handle-credentials-through-windows-powershell-ad03"></a>处理通过 Windows PowerShell (AD03) 的凭据

Cmdlet 应定义`Credential`参数以表示凭据。 此参数必须属于类型[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) ，且必须使用凭据特性声明定义。 未直接提供完整的凭据时，此支持会自动提示用户的用户名、 密码，或两个。 有关凭据属性的详细信息，请参阅[凭据特性声明](./credential-attribute-declaration.md)。

### <a name="support-encoding-parameters-ad04"></a>支持编码的参数 (AD04)

如果你的 cmdlet 读取或写入文本或二进制格式，例如写入或读取文件系统中的文件从然后 cmdlet 必须具有编码参数，用于指定如何对文本进行编码以二进制格式。

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>测试 Cmdlet 应返回一个布尔值 (AD05)

执行测试针对用户的资源的 Cmdlet 应返回[System.Boolean](/dotnet/api/System.Boolean)类型到管道，以便它们可以在条件表达式中使用。

## <a name="code-guidelines"></a>代码指南

编写 cmdlet 代码时，应考虑以下准则。 找到适用于您的具体情况的指导，请务必查看类似的指导原则的设计指南。

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>遵循 Cmdlet 类命名约定 (AC01)

通过以下标准的命名约定，使 cmdlet 更容易地发现，并帮助用户了解完全 cmdlet 进行的操作。 这种做法是使用 Windows PowerShell cmdlet 是公共类型，因为其他开发人员尤为重要。

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>在正确的 Namespace 中定义 Cmdlet

通常情况下将附加的.NET Framework 命名空间中定义的 cmdlet 类"。命令"的命名空间的表示在其中运行该 cmdlet 的产品。 例如，在中定义的包含 Windows PowerShell cmdlet`Microsoft.PowerShell.Commands`命名空间。

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Cmdlet 类以匹配的 Cmdlet 名称命名

命名时实现 cmdlet 的.NET Framework 类，类命名为"*\<谓词 >**\<名词 >**\<命令 >*"中，您可以将为*\<谓词 >* 并*\<名词 >* 占位符替换动词和名词的 cmdlet 名称使用。 例如， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)由一个名为类实现 cmdlet `GetProcessCommand`。

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>如果没有管道输入重写 BeginProcessing 方法 (AC02)

如果你的 cmdlet 不接受来自管道的输入，应在实现处理[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法。 使用此方法允许 Windows PowerShell 来维护 cmdlet 之间进行排序。 在管道中的剩余 cmdlet 获得机会开始其处理之前，在管道中的第一个 cmdlet 始终返回其对象。

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>若要处理停止请求数，重写 StopProcessing 方法 (AC03)

重写[System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，以便你的 cmdlet 可以处理停止信号。 某些 cmdlet 需要很长时间才能完成其操作，可让 Windows PowerShell 运行时，例如当该 cmdlet 将阻止中长时间运行的 RPC 调用的线程的调用之间传递很长时间。 这包括对进行调用的 cmdlet [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法，为[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，和其他反馈可能需要很长时间才能完成的机制。 这种情况下用户可能需要将停止信号发送到这些 cmdlet。

### <a name="implement-the-idisposable-interface-ac04"></a>实现 IDisposable 接口 (AC04)

如果你的 cmdlet 具有 （写入到管道） 的未释放的对象由[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法中，你的 cmdlet 可能需要其他对象可供使用。 例如，如果你 cmdlet 会打开文件句柄中的其[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，并保留该句柄打开以供[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，此句柄必须处理结束时关闭。

Windows PowerShell 运行时不会始终调用[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 例如， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)可能不调用方法，如果该 cmdlet 通过其操作期间取消或如果终止该 cmdlet 的任何部分中会发生错误。 因此，需要对象清理的 cmdlet 的.NET Framework 类应实现的完整[System.IDisposable](/dotnet/api/System.IDisposable)接口模式，以便 Windows PowerShell 运行时可以调用都包括终结器，[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)并[System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose)末尾的处理方法。

### <a name="use-serialization-friendly-parameter-types-ac05"></a>使用适合于序列化的参数类型 (AC05)

若要支持在远程计算机上运行你的 cmdlet，使用可以轻松地序列化客户端计算机上，然后解除冻结服务器计算机上的类型。 按照类型都是序列化友好。

基元类型：

- 字节、 SByte、 Decimal、 单、 Double、 Int16、 Int32、 Int64、 Uint16、 UInt32 和 UInt64。

- 一个布尔值、 Guid、 字节 []、 TimeSpan、 DateTime、 Uri 和版本。

- Char、 String，XmlDocument。

内置 rehydratable 类型：

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- Ip 地址 MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity，FileSecurity，RegistrySecurity

其他类型：

- SecureString

- 容器 （列表和字典的上述类型）

### <a name="use-securestring-for-sensitive-data-ac06"></a>使用 SecureString 的敏感数据 (AC06)

始终处理敏感数据时使用[System.Security.Securestring](/dotnet/api/System.Security.SecureString)数据类型。 这可能包括参数，以及将敏感数据返回到管道的管道输入。

## <a name="see-also"></a>另请参阅

[所需的开发指导原则](./required-development-guidelines.md)

[强烈建议的开发指导原则](./strongly-encouraged-development-guidelines.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

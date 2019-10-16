---
title: 设计你的 Windows PowerShell 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 962d2ba9fd892c297a633276b9ac07a5fa75ea87
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366806"
---
# <a name="designing-your-windows-powershell-provider"></a>设计 Windows PowerShell 提供程序

如果你的产品或配置公开了一组存储的数据，例如用户要导航或浏览的数据库，则应实现 Windows PowerShell 提供程序。 此外，如果你的产品提供了一个容器，即使它不是多级容器，也有必要实现 Windows PowerShell 提供程序。 例如，如果 cmdlet 谓词的复制、移动、重命名、新增或删除操作对你的产品或配置数据进行操作是有意义的，则你可能想要实现 Windows PowerShell 容器提供程序。

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell 路径标识提供者

Windows PowerShell 运行时使用 Windows PowerShell 路径访问相应的 Windows PowerShell 提供程序。 当某个 cmdlet 指定这些路径之一时，运行时会知道使用哪个提供程序来访问关联的数据存储区。 这些路径包括驱动器限定路径，提供程序限定路径，提供程序-直接路径，以及提供程序内部路径。 每个 Windows PowerShell 提供程序都必须支持其中一个或多个路径。

有关 Windows PowerShell 路径的详细信息，请参阅 Windows PowerShell 的工作原理。

### <a name="defining-a-drive-qualified-path"></a>定义驱动器限定路径

若要允许用户访问物理驱动器上的数据，Windows PowerShell 提供程序必须支持驱动器限定路径。 此路径以驱动器名称开头，后面跟一个冒号（:)，例如 mydrive： \ abc\bar。

### <a name="defining-a-provider-qualified-path"></a>定义提供程序限定的路径

为了允许 Windows PowerShell 运行时对提供程序进行初始化和取消初始化，Windows PowerShell 提供程序必须支持提供程序限定的路径。 例如，FileSystem：： \\ \ uncshare\abc\bar 是 Windows PowerShell 提供的 filesystem 提供程序的提供程序限定路径。

### <a name="defining-a-provider-direct-path"></a>定义提供程序-直接路径

若要允许远程访问你的 Windows PowerShell 提供程序，它应该支持直接传递到 Windows PowerShell 提供程序以获取当前位置的提供程序直接路径。 例如，注册表 Windows PowerShell 提供程序可以使用 \\ \ server\regkeypath 作为提供者直接路径。

### <a name="defining-a-provider-internal-path"></a>定义提供程序内部路径

若要允许提供程序 cmdlet 使用非 Windows PowerShell 应用程序编程接口（Api）访问数据，Windows PowerShell 提供程序应支持提供程序内部路径。 此路径在提供程序限定的路径中的 "：：" 后指示。 例如，filesystem Windows PowerShell 提供程序的提供程序内部路径 \\ \ uncshare\abc\bar。

## <a name="changing-stored-data"></a>更改存储的数据

当重写修改基础数据存储区的方法时，请始终使用该方法更改的项的最新版本调用[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。 提供程序基础结构确定是否需要将项对象传递到管道，例如当用户指定-PassThru 参数时。 如果检索最新项是一项成本高昂的操作（性能方面），则可测试上下文 PassThru 属性以确定是否确实需要写入结果项。

## <a name="choose-a-base-class-for-your-provider"></a>为提供程序选择基类

Windows PowerShell 提供了许多可用于实现自己的 Windows PowerShell 提供程序的基类。 设计提供程序时，请根据您的要求选择此部分中所述的基本类。

每个 Windows PowerShell 提供程序基类都提供一组 cmdlet。 本部分介绍 cmdlet，但不描述它们的参数。

使用会话状态，Windows PowerShell 运行时会使一些位置 cmdlet 可用于某些 Windows PowerShell 提供程序，例如 `Get-Location`、`Set-Location`、`Pop-Location` 和 @no__t 3 cmdlet。 可以使用 @no__t cmdlet 获取有关这些位置 cmdlet 的信息。

### <a name="cmdletprovider-base-class"></a>CmdletProvider 基类

[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类定义基本的 Windows PowerShell 提供程序。 此类支持提供程序声明，并提供可用于所有 Windows PowerShell 提供程序的多个属性和方法。 类由 `Get-PSProvider` cmdlet 调用以列出会话的所有可用提供程序。 此 cmdlet 的实现由会话状态提供。

> [!NOTE]
> Windows PowerShell 提供程序适用于所有 Windows PowerShell 语言范围。

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider 基类

[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类定义 Windows PowerShell 驱动器提供程序，该提供程序支持用于添加新驱动器、删除现有驱动器和初始化默认驱动器的操作。 例如，Windows PowerShell 提供的 FileSystem 提供程序为装入的所有卷（如硬盘驱动器和 CD/DVD 设备驱动器）初始化驱动器。

此类是从[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类派生的。 下表列出了由此类公开的 cmdlet。 除了列出的外，@no__t cmdlet （由会话状态公开）是用于检索可用驱动器的相关 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`New-PSDrive`|为会话创建新的驱动器，并传输驱动信息。|
|`Remove-PSDrive`|从会话中删除驱动器。|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider 基类

[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类定义 Windows PowerShell 项提供程序，该提供程序对数据存储区中的各个项执行操作，并且它不采用任何容器或导航功能。 此类是从[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类派生的。 下表列出了由此类公开的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Clear-Item`|清除指定位置的项的当前内容，并将其替换为提供程序指定的 "clear" 值。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`Get-Item`|检索指定位置中的项，并对生成的对象进行流式处理。|
|`Invoke-Item`|调用指定路径处的项的默认操作。|
|`Set-Item`|使用指示的值在指定位置设置项。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`Resolve-Path`|解析 Windows PowerShell 路径和流路径信息的通配符。|
|`Test-Path`|测试指定的路径，如果该路径 @no__t 存在，则返回 `true`; 否则返回-1。 此 cmdlet 的实现是为了支持[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法的 `IsContainer` 参数。|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider 基类

[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类定义 Windows PowerShell 容器提供程序，该提供程序向用户公开数据存储项的容器。 请注意，只有当一个容器（无嵌套容器）包含项时，才能使用 Windows PowerShell 容器提供程序。 如果有嵌套容器，则必须实现 Windows PowerShell 导航提供程序。

此类是从[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类派生的。 下表定义了此类实现的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Copy-Item`|将项从一个位置复制到另一个位置。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`Get-Childitem`|检索指定位置的子项，并将它们作为对象进行流式处理。|
|`New-Item`|在指定位置创建新项，并对生成的对象进行流式处理。|
|`Remove-Item`|删除指定位置中的项。|
|`Rename-Item`|重命名指定位置的项。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider 基类

[Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类定义 Windows PowerShell 导航提供程序，该提供程序对使用多个容器的项执行操作。 此类是从[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类派生的。 下表列出了由此类公开的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|合并-路径|使用路径之间特定于提供程序的分隔符将两个路径合并为一个路径。 此 cmdlet 流式传输字符串。|
|`Move-Item`|将项移动到指定位置。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|

相关 cmdlet 是 Windows PowerShell 提供的基本分析路径 cmdlet。 此 cmdlet 可用于分析 Windows PowerShell 路径，以支持 @no__t 0 参数。 它流式传输父路径字符串。

## <a name="select-provider-interfaces-to-support"></a>选择要支持的提供程序接口

除了从一个 Windows PowerShell 基类派生，Windows PowerShell 提供程序还可以通过从以下一个或多个提供程序接口派生来支持其他功能。 本部分定义每个接口和支持的 cmdlet。 它不描述接口支持的 cmdlet 的参数。 Cmdlet 参数信息可联机使用 `Get-Command` 和 @no__t cmdlet 提供。

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口定义一个内容提供程序，该提供程序对数据项的内容执行操作。 下表列出了此接口公开的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Add-Content`|将指示的值长度追加到指定项的内容。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`Clear-Content`|将指定项的内容设置为 "clear" 值。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`Get-Content`|检索指定项的内容，并对生成的对象进行流式处理。|
|`Set-Content`|替换指定项的现有内容。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

[Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口定义了 Windows PowerShell 提供程序的属性，该提供程序对数据存储区中的项的属性执行操作。 下表列出了此接口公开的 cmdlet。

> [!NOTE]
> 这些 cmdlet 上的 `Path` 参数指示项的路径，而不是标识属性。

|Cmdlet|定义|
|------------|----------------|
|`Clear-ItemProperty`|将指定项的属性设置为 "clear" 值。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`Get-ItemProperty`|检索指定项中的属性并流式传输生成的对象。|
|`Set-ItemProperty`|设置具有指示值的指定项的属性。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

[Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)接口派生自 Ipropertycmdletprovider，它定义了一个提供程序，该接口指定了它的动态参数[。](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)支持的 cmdlet。 这种类型的提供程序处理可在运行时定义其属性的操作，例如，一个新的属性操作。 不能对具有静态定义的属性的项进行此类操作。 下表列出了此接口公开的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Copy-ItemProperty`|将属性从指定项复制到另一项。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`Move-ItemProperty`|将属性从指定项移动到另一项。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|
|`New-ItemProperty`|在指定项上创建属性，并对生成的对象进行流式处理。|
|`Remove-ItemProperty`|删除指定项的属性。|
|`Rename-ItemProperty`|重命名指定项的属性。 此 cmdlet 不通过管道传递输出对象，除非指定了其 @no__t 参数。|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

[Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider)接口将安全描述符功能添加到提供程序。 此接口允许用户获取并设置数据存储中的项的安全描述符信息。 下表列出了此接口公开的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Get-Acl`|检索访问控制列表（ACL）中包含的信息，该列表是用于保护操作系统资源（例如文件或对象）的安全描述符的一部分。|
|`Set-Acl`|设置 ACL 的信息。 它以 Accesscontrol-namespace 的形式出现在为指定路径指定的项上的[Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity)实例。 如果 Windows PowerShell 提供程序支持安全信息的设置，则此 cmdlet 可以设置有关注册表中的文件、密钥和子项的信息或任何其他提供程序项。|

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 的工作原理](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)
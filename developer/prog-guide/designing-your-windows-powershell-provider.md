---
title: 设计 Windows PowerShell 提供程序 |Microsoft Docs
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
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081812"
---
# <a name="designing-your-windows-powershell-provider"></a>设计 Windows PowerShell 提供程序

如果您的产品或配置公开一组存储数据，如用户会想要在导航或浏览数据库，则应实现一个 Windows PowerShell 提供程序。 此外，如果您的产品提供了一个容器，即使它不是多层次的容器，最好实现 Windows PowerShell 提供程序。 例如，你可能想要实现的 Windows PowerShell 容器提供程序 cmdlet 谓词复制、 移动、 重命名，新的、 或删除作为对您的产品或配置数据的操作会比较有利。

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell 路径标识您的提供程序

Windows PowerShell 运行时使用 Windows PowerShell 路径来访问相应的 Windows PowerShell 提供程序。 当一个 cmdlet 指定两个路径时，运行时知道要使用来访问关联的数据存储区的提供程序。 这些路径包括驱动器限定的路径、 提供程序限定的路径、 提供程序直接路径和提供程序内部的路径。 每个 Windows PowerShell 提供程序必须支持一个或多个这些路径。

有关 Windows PowerShell 路径的详细信息，请参阅 Windows PowerShell 的工作原理。

### <a name="defining-a-drive-qualified-path"></a>定义驱动器限定的路径

若要允许用户访问位于物理驱动器的数据，Windows PowerShell 提供程序必须支持的驱动器限定路径。 此路径的开头使用跟一个冒号 （:），例如，mydrive:\abc\bar 驱动器名称。

### <a name="defining-a-provider-qualified-path"></a>定义提供程序限定的路径

若要允许 Windows PowerShell 运行时初始化和取消初始化提供程序，Windows PowerShell 提供程序必须支持的提供程序限定路径。 例如，文件系统::\\\uncshare\abc\bar 是由 Windows PowerShell filesystem 提供程序的提供程序限定路径。

### <a name="defining-a-provider-direct-path"></a>定义提供程序直接路径

若要允许远程访问 Windows PowerShell 提供程序，它应支持的提供程序直接路径要直接传递到 Windows PowerShell 提供程序为当前的位置。 例如，可以使用注册表的 Windows PowerShell 提供程序\\\server\regkeypath 作为提供程序直接路径。

### <a name="defining-a-provider-internal-path"></a>定义提供程序内部的路径

若要允许使用 Windows PowerShell 应用程序编程接口 (Api) 访问数据的提供程序 cmdlet，Windows PowerShell 提供程序应支持的提供程序内部的路径。 此路径指示后"::"中的提供程序限定路径。 例如，文件系统的 Windows PowerShell 提供程序的提供程序内部路径是\\\uncshare\abc\bar。

## <a name="changing-stored-data"></a>更改存储的数据

重写时修改基础数据存储区的方法，始终调用[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法替换的项的最新版本的更改方法。 提供程序基础结构确定是否需要传递到管道中，例如当用户指定了-PassThru 参数项对象。 如果检索最新项 （极大影响） 为高昂的操作，你可以测试 Context.PassThru 属性，以确定你实际上需要写入生成的项。

## <a name="choose-a-base-class-for-your-provider"></a>为您的提供程序选择的基类

Windows PowerShell 提供了大量可用于实现自己的 Windows PowerShell 提供程序的基类。 在设计时提供程序，选择基类，在本部分中，最适合您的要求中所述。

每个 Windows PowerShell 提供程序基类提供一组 cmdlet。 本部分介绍了这些 cmdlet，但它没有描述其参数。

使用会话状态，Windows PowerShell 运行时向多个位置 cmdlet 提供某些 Windows PowerShell 提供程序，如`Get-Location`， `Set-Location`， `Pop-Location`，和`Push-Location`cmdlet。 可以使用`Get-Help`cmdlet 来获取有关这些位置 cmdlet 的信息。

### <a name="cmdletprovider-base-class"></a>CmdletProvider 基类

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类定义了一个基本的 Windows PowerShell 提供程序。 此类支持的提供程序声明，提供了大量属性和方法可用于所有 Windows PowerShell 提供程序。 通过调用类`Get-PSProvider`cmdlet 可列出所有可用提供程序会话。 此 cmdlet 的实现提供的会话状态。

> [!NOTE]
> Windows PowerShell 提供程序可供所有 Windows PowerShell 语言的作用域。

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider 基类

[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类定义支持的操作添加新的驱动器，删除现有驱动器和初始化默认驱动器的 Windows PowerShell 驱动器提供程序。 例如，提供的 Windows PowerShell FileSystem 提供程序初始化的所有卷的装载，如硬盘驱动器和 CD/DVD 设备驱动器的驱动器。

此类派生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类。 下表列出了通过此类公开的 cmdlet。 除了所列的、 `Get-PSDrive` cmdlet （由会话状态） 是一个相关的 cmdlet 用于检索可用的驱动器。

|Cmdlet|定义|
|------------|----------------|
|`New-PSDrive`|对于会话，请创建新的驱动器和驱动器信息进行流式传输。|
|`Remove-PSDrive`|从会话中删除一个驱动器。|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider 基类

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类定义对数据存储的各个项执行操作的 Windows PowerShell 项提供程序并不会假定任何容器或导航功能。 此类派生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类。 下表列出了通过此类公开的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Clear-Item`|清除项的指定位置的当前内容，并替换与指定提供程序的"清除"值。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`Get-Item`|从指定位置检索项并流式传输结果对象。|
|`Invoke-Item`|调用指定的路径处的项的默认操作。|
|`Set-Item`|用指示值的指定位置设置的项。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`Resolve-Path`|解决了有关 Windows PowerShell 路径和数据流路径信息的通配符。|
|`Test-Path`|测试指定的路径，并返回`true`如果存在和`false`否则为。 此 cmdlet 实现以支持`IsContainer`参数[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider 基类

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类定义的 Windows PowerShell 容器提供程序公开的数据应用商店项目，向用户的容器。 请注意只有在没有一个容器 （没有嵌套的容器） 中它的项时，可以使用 Windows PowerShell 容器提供程序。 如果有嵌套的容器，则必须实现一个 Windows PowerShell 导航提供程序。

此类派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类。 下表定义了此类实现的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Copy-Item`|将项从一个位置复制到另一个。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`Get-Childitem`|检索指定位置的子项，并以对象形式将其流式处理。|
|`New-Item`|在指定位置创建新项并流式传输结果对象。|
|`Remove-Item`|从指定位置移除项。|
|`Rename-Item`|重命名指定位置处的项。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider 基类

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类定义执行操作的项的使用多个容器的 Windows PowerShell 导航提供程序。 此类派生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基类。 下表列出了通过此类公开的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|Combine-Path|将两个路径合并到单个路径，使用特定于提供程序的路径之间的分隔符。 此 cmdlet 将流式传输的字符串。|
|`Move-Item`|将项目移动到指定位置。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|

相关的 cmdlet 是由 Windows PowerShell 的基本分析路径 cmdlet。 此 cmdlet 可用于 Windows PowerShell 路径，以支持分析`Parent`参数。 流式处理的父路径字符串。

## <a name="select-provider-interfaces-to-support"></a>选择支持的提供程序接口

除了从 Windows PowerShell 基础类之一派生，Windows PowerShell 提供程序可以通过从一个或多个以下的提供程序接口派生来支持其他功能。 本部分将定义这些接口和支持的每个 cmdlet。 它没有描述的接口支持的 cmdlet 的参数。 Cmdlet 参数信息，请使用联机`Get-Command`和`Get-Help`cmdlet。

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)接口定义执行操作的内容的数据项的内容提供程序。 下表列出了此接口提供的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Add-Content`|将指示的值长度追加到指定项的内容。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`Clear-Content`|将指定项的内容设置为"清除"的值。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`Get-Content`|检索指定项的内容并流式传输结果对象。|
|`Set-Content`|替换指定项的现有内容。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口定义属性的 Windows PowerShell 提供程序，在数据存储区中执行操作的项的属性。 下表列出了此接口提供的 cmdlet。

> [!NOTE]
> `Path`有关这些 cmdlet 的参数指示的项而不是标识某个属性的路径。

|Cmdlet|定义|
|------------|----------------|
|`Clear-ItemProperty`|将指定项的属性设置为"清除"的值。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`Get-ItemProperty`|从指定的项中检索属性，并流式传输结果对象。|
|`Set-ItemProperty`|设置具有所示值的指定项的属性。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

[System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)接口，派生自[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)，定义指定其支持的 cmdlet 的动态参数的提供程序。 此类型提供程序的处理的操作，在运行时，例如，新的属性操作可以为其定义属性。 此类操作不能以静态方式定义属性的项。 下表列出了此接口提供的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Copy-ItemProperty`|将属性从指定的项复制到另一个项。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`Move-ItemProperty`|将属性从指定的项移动到另一个项。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|
|`New-ItemProperty`|在指定的项上创建属性并流式传输结果对象。|
|`Remove-ItemProperty`|删除指定项的属性。|
|`Rename-ItemProperty`|重命名指定的项的属性。 此 cmdlet 没有通过输出对象通过管道，除非其`PassThru`指定参数。|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

[System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider)接口将安全描述符功能添加到提供程序。 此接口允许用户获取和设置数据存储区中的项的安全描述符信息。 下表列出了此接口提供的 cmdlet。

|Cmdlet|定义|
|------------|----------------|
|`Get-Acl`|检索访问控制列表 (ACL)，这是一个用于防止操作系统资源，例如的安全描述符、 文件或对象的一部分中所包含的信息。|
|`Set-Acl`|设置 ACL 的信息。 它的实例的形式是[System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity)为指定的路径指定的项上。 如果 Windows PowerShell 提供程序支持的安全信息的设置，此 cmdlet 可以在注册表中或任何其他提供程序项，设置有关文件、 项和子项的信息。|

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)
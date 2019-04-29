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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082067"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>创建基础 Windows PowerShell 提供程序

本主题是学习如何创建 Windows PowerShell 提供程序的起始点。 此处所述的基本提供程序提供用于启动和停止提供程序，方法，它虽然此提供程序不提供一种方法来访问数据存储区或要获取或设置数据存储区中的数据，但它不提供所需的基本功能所有提供程序。

如上文所述的基本提供程序在此处实现方法来启动和停止提供程序。 Windows PowerShell 运行时调用这些方法来初始化和取消初始化提供程序。

> [!NOTE]
> 可以通过 Windows PowerShell 提供的 AccessDBSampleProvider01.cs 文件中找到此提供程序的示例。

本主题中的部分如下所示：

- [定义 Windows PowerShell 提供程序类](#Defining-the-Windows-PowerShell-Provider-Class)

- [定义特定于提供程序的状态信息](#Defining-Provider-Specific-State-Information)

- [初始化提供程序](#Initializing-the-Provider)

- [启动动态参数](#Start-Dynamic-Parameters)

- [取消初始化提供程序](#Uninitializing-the-Provider)

- [代码示例](#Code-Sample)

- [测试 Windows PowerShell 提供程序](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>定义 Windows PowerShell 提供程序类

创建 Windows PowerShell 提供程序的第一步是定义其.NET 类。 此基本提供程序定义一个名为类`AccessDBProvider`派生[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类。

建议将放在你提供程序类`Providers`API 命名空间，例如，xxx 的命名空间。PowerShell.Providers。 此提供程序使用`Microsoft.Samples.PowerShell.Provider`命名空间，在其中运行所有 Windows PowerShell 提供程序示例。

> [!NOTE]
> 为 Windows PowerShell 提供程序类必须显式标记为公共。 未标记为公共的类将默认为内部和 Windows PowerShell 运行时将不会找到。

下面是此基本提供程序的类定义：

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

类定义中前, 必须声明[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)具有语法 [CmdletProvider()] 属性。

可以设置属性关键字，以进一步声明类，如有必要。 请注意， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)此处声明的属性包括两个参数。 第一个属性参数指定提供程序，用户可以更高版本修改默认的友好名称。 第二个参数指定的提供程序公开到 Windows PowerShell 运行时在命令处理过程的 Windows PowerShell 定义功能。 定义提供程序功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 由于这是基本提供程序，它支持任何功能。

> [!NOTE]
> Windows PowerShell 提供程序的完全限定的名称包括程序集名称和由 Windows PowerShell 在注册的提供程序的其他属性。

## <a name="defining-provider-specific-state-information"></a>定义特定于提供程序的状态信息

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基类和所有派生的类被视为无状态因为 Windows PowerShell 运行时将创建仅在需要的提供程序实例。 因此，如果您的提供程序需要完全控制和状态维护特定于提供程序的数据，它必须派生一个类从[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)类。 在派生的类应定义需维护状态，以便可以访问特定于提供程序的数据，当 Windows PowerShell 运行时调用的成员[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以初始化访问接口。

Windows PowerShell 提供程序还可以维护基于连接的状态。 有关保持连接状态的详细信息，请参阅[创建一个 PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

## <a name="initializing-the-provider"></a>初始化提供程序

若要初始化的提供程序，Windows PowerShell 运行时调用[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法启动 Windows PowerShell 时。 大多数情况下，您的提供程序可以使用此方法，它只是返回的默认实现[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象，描述您的提供程序。 但是，在你想要添加附加的初始化信息的情况下，则应实现您自己[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法返回的修改的版本[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)传递给您的提供程序的对象。 一般情况下，此方法应返回所提供[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象传递给它或修改过[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)对象包含其他初始化信息。

此基本提供程序不重写此方法。 但是，下面的代码演示此方法的默认实现：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

提供程序可以维护状态的特定于提供程序的信息，如中所述[定义特定于提供程序的数据状态](#Defining-Provider-Specific-State-Information)。 在这种情况下，您的实现必须重写[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法以返回派生的类的实例。

## <a name="start-dynamic-parameters"></a>启动动态参数

在提供程序实现的[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法可能需要其他参数。 在这种情况下，该提供程序应重写[System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法并返回具有属性和字段与分析的对象属性类似于cmdlet 类或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。

此基本提供程序不重写此方法。 但是，下面的代码演示此方法的默认实现：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>取消初始化提供程序

若要释放的 Windows PowerShell 提供程序使用的资源，您的提供程序应实现其自己[System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。 要取消初始化的提供程序在会话的结束位置的 Windows PowerShell 运行时调用此方法。

此基本提供程序不重写此方法。 但是，下面的代码演示此方法的默认实现：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample01 代码示例](./accessdbprovidersample01-code-sample.md)。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

Windows PowerShell 提供程序已注册后使用 Windows PowerShell，可以通过在命令行上运行的受支持的 cmdlet 来测试它。 对于此基本提供程序，运行新的 shell，并使用`Get-PSProvider`cmdlet 检索提供程序的列表，并确保存在 AccessDb 提供程序。

```powershell
Get-PSProvider
```

将显示以下输出：

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

## <a name="see-also"></a>另请参阅

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)
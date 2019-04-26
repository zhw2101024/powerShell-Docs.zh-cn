---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081115"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

此示例演示如何声明直接派生的提供程序类[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类。 仅出于完整性考虑而在此处包含此项。

## <a name="demonstrates"></a>演示

> [!IMPORTANT]
> 提供程序类将很可能从以下类之一派生，并可能实现其他提供程序接口：
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)类。 请参阅[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)类。 请参阅[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)类。 请参阅[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 有关选择哪个提供程序类派生自基于提供程序功能，请参阅详细信息[设计你 Windows PowerShell 提供程序](./provider-types.md)。

此示例将演示如下：

- 声明`CmdletProvider`属性。

- 定义提供程序类直接派生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)类。

## <a name="example"></a>示例

此示例演示如何定义提供程序类以及如何声明`CmdletProvider`属性。

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[设计 Windows PowerShell 提供程序](./provider-types.md)
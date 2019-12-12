---
title: 常见工作流参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366046"
---
# <a name="common-workflow-parameters"></a>常见工作流参数

通过 Windows PowerShell cmdlet 生成的工作流活动定义了许多适用于所有活动的参数。 可以在创作时指定这些参数的子集，使工作流作者可以自定义活动。 调用活动时，用户可以指定这些参数的另一个子集。

常见的工作流参数分为多个类别，如下所示。

## <a name="connectivity-parameters"></a>连接参数

|名称|类型|描述|最终用户是否可以在执行时指定？|在创作时，工作流作者可以指定？|工作流作者是否可以在实例化时指定？|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|string[]|要为其启动作业的计算机名称的列表。|“是”|“是”|“是”|
|PSCredential|[System.web. Automation](/dotnet/api/System.Management.Automation.PSCredential)|用于登录到由 PSComputerName 参数指定的计算机的身份验证凭据。 仅当指定了 PSComputerName 时，此参数才有效。|“是”|“是”|“是”|
|PSPort|UInt32|用于运行工作流的端口。|“是”|“是”|“是”|
|PSUseSSL|布尔|使用安全套接字层（SSL）协议来建立与远程计算机的安全连接，以运行工作流。|“是”|“是”|“是”|
|PSConfigurationName|字符串|用于运行工作流的会话配置。|“是”|“是”|“是”|
|PSApplicationName|字符串|用于执行工作流的连接 URI 的应用程序名称部分。 仅当未使用 ConnectionURI 参数时才使用此参数。|“是”|“是”|“是”|
|PSThrottleLimit|UInt32|可以建立的用于运行工作流的最大并发连接数。|“是”|TBD|“是”|
|PSConnectionURI|string[]|一个完全限定 Uri 的数组，用于指定用于运行工作流的交互式会话的终结点。|“是”|“是”|“是”|
|PSAllowRedirection|布尔|指定是否允许将此连接重定向到备用 URI 以运行工作流。|“是”|“是”|“是”|
|PSSessionOption|["Pssessionoption"。](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|用于运行工作流的会话的高级选项。|“是”|“是”|“是”|
|PSAuthentication|["System.management.automation.runspaces.authenticationmechanism"。](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|一个[system.management.automation.runspaces.authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)枚举值，该值指定用于对用户凭据进行身份验证的身份验证机制。|“是”|“是”|“是”|
|PSCertificateThumbprint|字符串|有权运行工作流的用户帐户的数字公钥证书（X509）。|“是”|“是”|“是”|

### <a name="behavior-parameters"></a>行为参数
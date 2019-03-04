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
ms.openlocfilehash: 2aca4483e500432ef9f52804e85678d2268aa4cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856133"
---
# <a name="common-workflow-parameters"></a>常见工作流参数

从 Windows PowerShell cmdlet 生成的工作流活动定义的所有活动的数量的参数的常见。 在创作时，以便工作流作者可以自定义活动，可以指定这些参数的子集。 调用活动时，用户可以指定这些参数的另一小部分。

按如下所示，将常见的工作流参数分组到多个类别。

## <a name="connectivity-parameters"></a>连接参数

|名称|类型|描述|可以指定在执行时的最终用户？|可以通过工作流编写者在创作时指定？|可以指定在实例化的工作流编写者？|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|string[]|要为其启动作业的计算机名称的列表。|是|是|是|
|PSCredential|[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|要使用的身份验证凭据以登录到由 PSComputerName 参数指定的计算机。 此参数是指定 PSComputerName 时才有效。|是|是|是|
|PSPort|UInt32|要用于运行工作流的端口。|是|是|是|
|PSUseSSL|布尔|使用安全套接字层 (SSL) 协议来建立安全连接到远程计算机以运行工作流。|是|是|是|
|PSConfigurationName|字符串|用于运行工作流的会话配置。|是|是|是|
|PSApplicationName|字符串|工作流执行的连接 URI 的应用程序名称部分。 仅当未使用 ConnectionURI 参数时，请使用此参数。|是|是|是|
|PSThrottleLimit|UInt32|最大并发连接可以建立运行工作流数。|是|TBD|是|
|PSConnectionURI|string[]|为交互式会话用于运行工作流中指定的终结点的完全限定 Uri 的数组。|是|是|是|
|PSAllowRedirection|布尔|指定是否允许此连接到备用 URI 以运行工作流重定向。|是|是|是|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|用于运行工作流会话的高级的选项。|是|是|是|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|值为[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)枚举，用于指定用来对用户的凭据进行身份验证的身份验证机制。|是|是|是|
|PSCertificateThumbprint|字符串|数字公钥证书 (X509) 有权运行工作流的用户帐户。|是|是|是|

### <a name="behavior-parameters"></a>行为参数
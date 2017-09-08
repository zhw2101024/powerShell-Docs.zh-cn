---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Web 访问 cmdlet"
ms.technology: powershell
ms.openlocfilehash: ac8717c2aa97d0482b4d88f1b57d621d7ff47535
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
#  <a name="windows-powershell-web-access-cmdlets"></a>Windows PowerShell Web 访问 Cmdlet

本参考提供所有特定于 Windows PowerShell® Web 访问 cmdlet 的 cmdlet 说明和语法。 本参考按 cmdlet 开头动词的字母顺序列出了这些 cmdlet。

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)

向 Windows PowerShell® Web 访问授权规则集添加新的授权规则。

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)

返回一组 Windows PowerShell Web 访问的授权规则。

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[Install-PswaWebApplication](install-pswawebapplication.md)

在 IIS 中配置 Windows PowerShell Web 访问 Web 应用程序。

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)

从 Windows PowerShell Web 访问删除指定授权规则。

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)

测试授权规则，以验证某个特定用户、计算机或终结点的访问请求是否被授权。

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[Uninstall-PswaWebApplication](uninstall-pswawebapplication.md)

从 IIS 卸载 Windows PowerShell Web 应用程序。

>**注意**：
>
>若要列出所有可用 cmdlet，请使用：
>
> `Get-Command –Module PowerShellWebAccess` cmdlet。

有关其中任何一种 cmdlet 或其语法的详细信息，请使用：  
`Get-Help `&lt;cmdlet 名称&gt;  
其中 &lt;cmdlet name&gt; 是要了解的 cmdlet 的名称。

有关更多详细信息，你可以运行以下任何 cmdlet：

-  `Get-Help `&lt;cmdlet 名称&gt;` -Detailed`
-  `Get-Help `&lt;cmdlet 名称&gt;` -Examples`
-  `Get-Help `&lt;cmdlet 名称&gt;` -Full`

### <a name="more-information"></a>详细信息

有关 PowerShell Web 访问的详细信息，请参阅以下内容：

-   [安装和使用 Windows PowerShell Web 访问](../install-and-use-windows-powershell-web-access.md)


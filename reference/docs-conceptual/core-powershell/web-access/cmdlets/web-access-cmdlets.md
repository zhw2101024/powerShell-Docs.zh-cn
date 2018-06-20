---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: PowerShell Web 访问 Cmdlet
ms.openlocfilehash: 34a7a01f154b2e43416dfe8ea43d4d8e937816d9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188014"
---
# <a name="windows-powershell-web-access-cmdlets"></a>Windows PowerShell Web 访问 Cmdlet

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

若要详细了解任一 cmdlet 或其语法，请使用 `Get-Help `&lt;cmdlet 名称&gt;（其中，&lt;cmdlet 名称&gt; 是要探究的 cmdlet 的名称）。

有关更多详细信息，你可以运行以下任何 cmdlet：

- `Get-Help `&lt;cmdlet 名称&gt;` -Detailed`
- `Get-Help `&lt;cmdlet 名称&gt;` -Examples`
- `Get-Help `&lt;cmdlet 名称&gt;` -Full`

### <a name="more-information"></a>详细信息

有关 PowerShell Web 访问的详细信息，请参阅以下内容：

- [安装和使用 Windows PowerShell Web 访问](../install-and-use-windows-powershell-web-access.md)
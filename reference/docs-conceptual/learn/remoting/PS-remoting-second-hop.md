---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 在 PowerShell 远程处理中形成第二个跃点
ms.openlocfilehash: f4cfde39de8494050c31cfc3181271b968819695
ms.sourcegitcommit: a35450f420dc10a02379f6e6f08a28ad11fe5a6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71692150"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>在 PowerShell 远程处理中形成第二个跃点

“第二个跃点问题”是指如下所示的情况：

1. 已登录到 _ServerA_。
2. 在 _ServerA_ 中，启动远程 PowerShell 会话，以连接到 _ServerB_。
3. 通过 PowerShell 远程处理会话在 _ServerB_ 上运行的命令尝试访问 _ServerC_ 上的资源。
4. 已拒绝访问 _ServerC_ 上的资源，因为用于创建 PowerShell 远程处理会话的凭据未从 _ServerB_ 传递到 _ServerC_。

有几种方法可以解决此问题： 在本主题中，我们将了解第二个跃点问题的几种最受欢迎的解决方案。

## <a name="credssp"></a>CredSSP

可以使用[凭据安全支持提供程序(CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) 进行身份验证。 CredSSP 会将凭据缓存在远程服务器 (_ServerB_) 上，因此使用它会给你带来凭据被盗攻击的风险。 如果远程计算机被攻破，攻击者将有权访问用户的凭据。 默认情况下，CredSSP 在客户端和服务器计算机上都处于禁用状态。 应该仅在最受信任的环境中启用 CredSSP。 例如，连接到域控制器的域管理员，因为域控制器是高度可信任的。

若要详细了解在使用 CredSSP 进行 PowerShell 远程处理时需要注意的安全问题，请参阅[非蓄意破坏：当心 CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp)。

有关凭据被盗攻击的详细信息，请参阅[缓解哈希传递 (PtH) 攻击和其他凭据被盗](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。

有关如何启用和使用 CredSSP 进行 PowerShell 远程处理的示例，请参阅[使用 CredSSP 解决第二个跃点问题](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/)。

### <a name="pros"></a>优点

- 它适用于运行 Windows Server 2008 或更高版本的所有服务器。

### <a name="cons"></a>缺点

- 可能会造成安全漏洞。
- 需要客户端和服务器角色的配置。

## <a name="kerberos-delegation-unconstrained"></a>Kerberos 委派（非约束）

还可以使用 Kerberos 非约束委派来形成第二个跃点。 但是，此方法无法控制使用委派凭据的位置。

>**注意：** 无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户  。 有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和 [Kerberos 身份验证工具和设置](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>优点

- 无需特殊编码。

### <a name="cons"></a>缺点

- 不支持 WinRM 的第二个跃点。
- 无法控制使用凭据的位置，因此产生安全漏洞。

## <a name="kerberos-constrained-delegation"></a>Kerberos 约束委派

可以使用旧的约束委派（而非基于资源的委派）形成第二个跃点。 “使用任何身份验证协议”选项配置 Kerberos 约束委派以允许协议转换。

> [!NOTE]
> 无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户  。 有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和 [Kerberos 身份验证工具和设置](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>优点

- 无需特殊编码

### <a name="cons"></a>缺点

- 不支持 WinRM 的第二个跃点。
- 必须对远程服务器 (ServerB  ) 的 Active Directory 对象进行配置。
- 限于一个域。 不能跨域或林。
- 需要权限才能更新对象和服务主体名称 (SPN)。

## <a name="resource-based-kerberos-constrained-delegation"></a>基于资源的 Kerberos 约束委派

通过使用（Windows Server 2012 中引入的）基于资源的 Kerberos 约束委派，在资源驻留的服务器对象上配置凭据委派。
在上述第二个跃点场景中，配置 _ServerC_ 以指定从何处接受委派凭据。

>**注意：** 无法委派具有“敏感帐户，不能被委派”属性集的 Active Directory 帐户  。 有关详细信息，请参阅[安全聚焦：对特权帐户分析“敏感帐户，不能被委派”](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和 [Kerberos 身份验证工具和设置](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>优点

- 不存储凭据。
- 使用 PowerShell cmdlet 进行配置相对容易 - 无需任何特殊编码。
- 无需特殊域访问权限。
- 可跨域和林使用。
- PowerShell 代码。

### <a name="cons"></a>缺点

- 要求 Windows Server 2012 或更高版本。
- 不支持 WinRM 的第二个跃点。
- 需要权限才能更新对象和服务主体名称 (SPN)。

### <a name="example"></a>示例

让我们看看 PowerShell 示例，该示例在 ServerC  上配置基于资源的约束委派以允许来自 _ServerB_ 的委派凭据。
此示例假定所有服务器都运行 Windows Server 2012 或更高版本，并且任一服务器所属的每个域具有至少一个 Windows Server 2012 域控制器。

在配置约束委派前，必须先添加 `RSAT-AD-PowerShell` 功能以安装 Active Directory PowerShell 模块，然后将该模块导入会话：

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
现在多个可用的 cmdlet 具有 **PrincipalsAllowedToDelegateToAccount** 参数：

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

**PrincipalsAllowedToDelegateToAccount** 参数可设置 Active Directory 对象属性 **msDS AllowedToActOnBehalfOfOtherIdentity**，其中包含一份访问控制列表 (ACL)，指定了哪些帐户有权向关联帐户委派凭据（在本示例中，该帐户为 _Server_ 的计算机帐户）。

现在，我们来设置用于表示服务器的变量：

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

默认情况下，WinRM（由此还有 PowerShell 远程处理）作为计算机帐户运行。 可通过查看 `winrm` 服务的 **StartName** 属性看到：

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

为了 _ServerC_ 允许来自 _ServerB_ 上的 PowerShell 远程处理会话的委派，我们通过将 _ServerC_ 上的 **PrincipalsAllowedToDelegateToAccount** 参数设为 _ServerB_ 的计算机对象来授予权限：

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [密钥分发中心 (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) 缓存拒绝访问尝试（负缓存）长达 15 分钟。 如果 _ServerB_ 先前已尝试访问 _ServerC_，则需要通过调用以下命令清除 _ServerB_ 上的缓存：

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

还可以重启计算机，或等待至少 15 分钟，以清除缓存。

清除缓存之后，可以通过 _ServerB_ 到 _ServerC_成功运行来自 _ServerA_ 的代码：

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

在本示例中，`$using` 变量用于使 `$ServerC` 变量对 _ServerB_ 可见。 有关 `$using` 变量的详细信息，请参阅 [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx)。

若要允许多个服务器向 _ServerC_ 委派凭据，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为数组：

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

如果想要跨域形成第二个跃点，添加 _ServerB_ 所属域的域控制器的完全限定域名 (FQDN)：

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

若要删除向 ServerC 委派凭据的功能，在 _ServerC_ 上将 **PrincipalsAllowedToDelegateToAccount** 参数的值设为 `$null`：

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>基于资源的 Kerberos 约束委派的相关信息

- [Kerberos 身份验证的中的新功能](https://technet.microsoft.com/library/hh831747.aspx)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 1 部分）
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)（Windows Server 2012 如何缓解 Kerberos 约束委派的痛苦，第 2 部分）
- [Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper)（了解 Kerberos 约束委派，以使用集成的 Windows 身份验证进行 Azure Active Directory 应用程序代理部署）
- [[MS-ADA2]：Active Directory 架构属性 M2.210 属性 msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]：Kerberos 协议扩展：用户服务和约束委派协议 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [基于资源的 Kerberos 约束委派](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)（在不使用约束委派的情况下，使用 PrincipalsAllowedToDelegateToAccount 进行远程管理）

## <a name="pssessionconfiguration-using-runas"></a>使用 RunAs 的 PSSessionConfiguration

可以在 _ServerB_ 上创建会话配置并设置其 **RunAsCredential** 参数。

有关使用 PSSessionConfiguration 和 RunAs 解决第二个跃点问题的信息，请参阅 [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/)（多跃点 PowerShell 远程处理的另一种解决方案）。

### <a name="pros"></a>优点

- 兼容任何运行 WMF 3.0 或更高版本的服务器。

### <a name="cons"></a>缺点

- 需要在每个中间服务器 (_ServerB_) 上配置 **PSSessionConfiguration** 和 **RunAs**。
- 使用域 **RunAs** 帐户时要求密码维护

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA 允许限制管理员在 PowerShell 会话期间可以运行的命令。 它可用于解决第二个跃点问题。

有关 JEA 的信息，请参阅 [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview)。

### <a name="pros"></a>优点

- 使用虚拟帐户时无需密码维护。

### <a name="cons"></a>缺点

- 需要 WMF 5.0 或更高版本。
- 需要在每个中间服务器 (_ServerB_) 上进行配置。

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>在 Invoke-Command 脚本块内传递凭据

可以在对 [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet 的调用的 **ScriptBlock** 参数内传递凭据。

### <a name="pros"></a>优点

- 无需特殊服务器配置。
- 适用于任何运行 WMF 2.0 或更高版本的服务器。

### <a name="cons"></a>缺点

- 需要繁琐的代码技术。
- 运行 WMF 2.0 时，需要不同的语法将参数传递到远程会话。

### <a name="example"></a>示例

以下示例演示了如何在 **Invoke-command** 脚本块中传递凭据：

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>另请参阅

[PowerShell 远程处理安全注意事项](WinRMSecurity.md)

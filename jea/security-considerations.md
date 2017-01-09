---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: "JEA 安全注意事项"
ms.technology: powershell
ms.openlocfilehash: 03d34a7c8241aee1578a1cf2e794046578669dce
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="jea-security-considerations"></a>JEA 安全注意事项

> 适用于：Windows PowerShell 5.0

JEA 通过减少计算机上的永久管理员数量来帮助改善安全状况。
为此，它创建了一个新的入口点供用户管理系统（PowerShell 会话配置），该入口点在默认情况下紧密锁定，以防误用。
对于需要某些（但并非不受限制的）计算机访问权限来执行管理任务的用户，可授予对 JEA 终结点的权限。
由于 JEA 允许用户在无需直接拥有管理员权限的情况下运行管理员命令，因此可以将这些用户从高特权安全组删除（使其成为标准用户）。

本主题详细介绍了 JEA 安全模型和最佳做法。

## <a name="run-as-account"></a>运行方式帐户

每个 JEA 终结点都有一个指定的“运行方式”帐户，该帐户是执行连接用户的操作所采用的帐户。
此帐户在[会话配置文件](session-configurations.md)中是可配置的，并且你选择的帐户对终结点的安全性意义重大。

**虚拟帐户**是用于配置运行方式帐户的推荐方法。
虚拟帐户是临时创建的一次性本地帐户，便于连接用户在 JEA 会话期间使用。
一旦用户的会话终止，虚拟帐户将废弃，并且不能再被使用。
连接用户不知道虚拟帐户的凭据，并且无法通过远程桌面或非约束 PowerShell 终结点等其他方式使用虚拟帐户访问系统。

默认情况下，虚拟帐户属于计算机上的本地管理员组。
这将授予他们管理系统中所有内容的全部权限，但这些帐户无权管理网络中的资源。
在与其他计算机进行身份验证时，用户上下文将是本地计算机帐户，而非虚拟帐户。

默认情况下，在 Active Directory 域控制器上，虚拟帐户会获得域管理员特权。
这是由于域控制器上没有任何本地管理员组导致的。
相应地，域控制器上的虚拟帐户为域帐户，可用于其他计算机。
在域控制器上配置 JEA 会话时，必须仔细操作，以避免公开可用于管理网络上的其他计算机的命令。

在这两种情况下，还可以显式定义虚拟帐户应属于哪些安全组。
当要执行的任务无需本地/域管理员权限便可完成时，这是一个很合适的做法。
如果已为管理员定义了安全组，只需向该组授予虚拟帐户成员身份便可授予其所需权限。
虚拟帐户组成员身份仅限于工作站和成员服务器上的本地安全组，但在域控制器上，它们只能是域安全组的成员。
为虚拟帐户指定所属的一个或多个安全组后，该账户将不再属于默认组（本地管理员或域管理员）。

下表总结了虚拟帐户可能的配置选项和生成权限

计算机类型                | 虚拟帐户组配置 | 本地用户上下文                                      | 网络用户上下文
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
域控制器            | 默认值                             | 域用户，“*DOMAIN*\Domain Admins”的成员         | 域用户，“*DOMAIN*\Domain Admins”的成员
域控制器            | 域组 A 和域组 B               | 域用户，“*DOMAIN*\A”、“*DOMAIN*\B”的成员       | 域用户，“*DOMAIN*\A”、“*DOMAIN*\B”的成员
成员服务器或工作站 | 默认值                             | 本地用户、“*BUILTIN*\Administrators”的成员        | 计算机帐户
成员服务器或工作站 | 本地组 C 和 D                | 本地用户、“*COMPUTER*\C”和“*COMPUTER*\D”的成员 | 计算机帐户

查看安全审核事件和应用程序事件日志时，将看到每个 JEA 用户会话都有一个唯一的虚拟帐户。
这有助于将 JEA 终结点中的用户操作追溯到运行该命令的原始用户。
虚拟帐户名称遵循以下格式：“WinRM Virtual Users\\WinRM\_VA\_ACCOUNTNUMBER\_DOMAIN\_sAMAccountName”。例如，当域“Contoso”中的用户“Alice”在 JEA 终结点中重启服务时，与任何服务控制管理器事件关联的用户名将为“WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice”。


**组托管的服务帐户 (gMSA)** 在成员服务器需要对 JEA 会话中的网络资源具有访问权限时十分有用。
这种情况的一个示例用例是 JEA 终结点，它可用于控制对托管在其它计算机上的 REST API 的访问权限。
编写函数对 REST API 执行所需调用很容易，不过若要通过 API 的身份验证，则需要网络标识。
使用组托管服务帐户可实现“第二个跃点”，同时仍控制哪些计算机可使用该帐户。
gMSA 帐户所属的安全组（本地或域）定义 gMSA 的有效权限。

JEA 终结点配置为使用 gMSA 帐户时，所有 JEA 用户的操作将显示来自同一个组托管服务帐户。
将操作追溯到特定用户的唯一方法是标识 PowerShell 会话脚本中运行的命令集。

**传递凭据** 如果未指定运行方式帐户，PowerShell 将使用连接用户的凭据在远程服务器上运行命令。
不推荐 JEA 使用此配置，因为该配置要求向连接用户授予特权管理组的直接访问权限。
如果连接用户已有管理员权限，他们可以完全避免 JEA，并通过其他非约束方式管理系统。
有关详细信息，请参阅下节关于如何使 [JEA 不阻止管理员](#jea-does-not-protect-against-admins)的内容。

**标准运行方式帐户**允许指定整个 PowerShell 会话运行所采用的用户帐户。
这有一个重要的区别，因为设置为（通过 `-RunAsCredential` 参数）使用固定运行方式帐户的会话配置并不了解 JEA。
这意味着角色定义不再按预期正常运行，并且有权访问该终结点的每个用户都会分配相同的角色。

由于将操作追溯到特定用户存在难度并且缺少将用户映射到角色的支持，因此不应该对 JEA 终结点使用 RunAsCredential。

## <a name="winrm-endpoint-acl"></a>WinRM 终结点 ACL

与常规 PowerShell 远程终结点一样，每个 JEA 终结点在 WinRM 配置中都设有单独的访问控制列表 (ACL)，控制哪些用户可以通过 JEA 终结点的身份验证。
如果配置错误，受信任的用户可能无法访问 JEA 终结点和/或不受信任的用户可能获得访问权限。
但是， WinRM ACL 不影响用户到 JEA 角色的映射。
该映射由系统中注册的会话配置文件中的 *RoleDefinitions* 字段控制。

默认情况下，如果使用会话配置文件和一个或多个角色功能注册 JEA 终结点，WinRM ACL 将配置为允许所有用户映射到终结点的一个或多个角色访问权限。
例如，使用以下命令配置的 JEA 会话将授予对 CONTOSO\JEA\_Lev1 和 CONTOSO\JEA\_Lev2 的完全访问权限。

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

可以使用 [Get-pssessionconfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 审核用户权限。

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

若要更改哪些用户具有访问权限，请运行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` 进行交互式提示或运行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` 来更新权限。
用户至少需要调用权限才能访问 JEA 终结点。

如果其他用户获得 JEA 终结点的访问权限，但不属于会话配置文件中定义的任何角色，他们将能够启动 JEA 会话，但只有默认 cmdlet 的访问权限。
可以通过运行 `Get-PSSessionCapability` 来审核 JEA 终结点中的用户权限。
有关审核用户有权访问 JEA 终结点中的哪些命令的详细信息，请查看[有关 JEA 的审核和报告](audit-and-report.md)。

## <a name="least-privilege-roles"></a>最小特权角色

设计 JEA 角色时，务必记住后台运行的虚拟或组托管服务帐户通常具有不受限制的访问权限，以管理本地计算机。
JEA 角色功能通过限制可使用该特权运行上下文的命令和应用程序帮助限制使用该帐户的目的。
设计错误的角色可允许运行危险命令，该命令可能允许用户中断 JEA 边界或获得对敏感信息的访问权限。

例如，考虑以下角色功能事项：

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

此角色功能使用户能够从 Microsoft.PowerShell.Management 模块使用名词“Process”运行任何 PowerShell cmdlet。
用户可能需要访问 `Get-Process` 等 cmdlet，以了解哪些应用程序在系统上运行，以及访问 `Stop-Process` 以终止任何挂起的应用程序。
但是，此项还允许访问 `Start-Process`，以用于启动具有完全管理员权限的任意程序。
该程序无需安装在系统本地，因此攻击者只需启动文件共享上的一个程序，就可授予连接用户本地管理员权限、运行恶意程序等等。”

此相同角色功能的更安全版本如下所示：

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

避免在角色功能中使用通配符，并确保定期[审计有效用户权限](audit-and-report.md#check-effective-rights-for-a-specific-user)可了解用户有权访问哪些命令。

## <a name="jea-does-not-protect-against-admins"></a>JEA 不阻止管理员

JEA 核心原则之一是允许非管理员执行某些管理员任务。
JEA 不阻止已经具有管理员权限的用户。
环境中属于“域管理员”、“本地管理员”或其他高特权组的用户，仍能够通过其他方式登录到计算机获得 JEA 的保护。
例如，他们可以使用 RDP 登录、使用远程 MMC 控制台，或连接到不受约束的 PowerShell 终结点。
系统上的本地管理员还可以修改 JEA 配置以允许其他用户管理系统或更改角色功能，从而扩展其 JEA 会话中用户可以执行的操作范围。
因此必须要评估 JEA 用户的扩展权限，了解是否可以通过其他方式获得对系统的特许访问权限。

一种常见做法是使用 JEA 进行常规的日常维护，并且获得“及时”特许访问权限解决方案，使用户在紧急情况下能够临时成为本地管理员。
这有助于确保用户不会成为系统的永久管理员，只有当且仅当他们完成记录这些权限使用情况的工作流时，才能获得这些权限。
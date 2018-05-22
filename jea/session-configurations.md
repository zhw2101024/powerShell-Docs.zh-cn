---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: JEA 会话配置
ms.openlocfilehash: 3e5a663be8e7aba09a2592c278224cd892c89a20
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="jea-session-configurations"></a>JEA 会话配置

> 适用于：Windows PowerShell 5.0

JEA 终结点通过在系统上采用特定方式创建和注册 PowerShell 会话配置文件进行注册。
会话配置确定可使用 JEA 终结点的*人员*及其有权访问的角色。
它们还定义一些全局设置，这些设置应用于 JEA 会话中任何角色的用户。

本主题介绍如何创建 PowerShell 会话配置文件和注册 JEA 终结点。

## <a name="create-a-session-configuration-file"></a>创建会话配置文件

若要注册 JEA 终结点，需要指定该终结点的配置方式。
此处需考虑很多事项：最重要的是谁应具有访问 JEA 终结点的权限，其将分配有哪些角色，JEA 实际将使用哪个标识，以及 JEA 终结点将采用哪个名称。
这些均可在 PowerShell 会话配置文件中定义，该文件是以 .pssc 扩展名结尾的 PowerShell 数据文件。

若要创建 JEA 终结点的主干会话配置文件，请运行以下命令。

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> 默认情况下，主干文件仅包含最常用的配置选项。
> 使用 `-Full` 切换，在生成的 PSSC 中包含所有适用设置。

可在任意文本编辑器中打开会话配置文件。
`-SessionType RestrictedRemoteServer` 字段指示 JEA 将使用该会话配置进行安全管理。
通过此方式配置的会话将在 [NoLanguage 模式](https://technet.microsoft.com/library/dn433292.aspx)下运行，并且只包含以下 8 个默认命令（和别名）：

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

PowerShell 提供程序均不可用，也不提供任何外部程序（可执行文件、脚本等）。

以下是要为 JEA 会话配置的其他几个字段。
均在以下各节中有所介绍。

### <a name="choose-the-jea-identity"></a>选择 JEA 标识

JEA 在后台运行已连接用户的命令时需要使用标识（即帐户）。
用户决定 JEA 将在会话配置文件中使用哪个标识。

#### <a name="local-virtual-account"></a>本地虚拟帐户

如果此 JEA 终结点支持的角色均用于管理本地计算机，并且本地管理员帐户足以成功运行命令，则应将 JEA 配置为使用本地虚拟帐户。
虚拟帐户是特定用户所独有的临时帐户，仅在 PowerShell 会话的持续时间内有效。
在成员服务器或工作站上，虚拟帐户属于本地计算机的**管理员**组，并且有权访问大多数系统资源。
在 Active Directory 域控制器上，虚拟帐户属于域的**域管理员**组。

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

如果会话配置支持的角色不需要此类广泛特权，可选择性地指定将包含虚拟帐户的安全组。
在成员服务器或工作站上，指定的安全组必须是本地组，而不是来自域的组。

指定一个或多个安全组后，虚拟帐户将不再属于本地或域管理员组。

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>组托管服务帐户


对于需要 JEA 用户访问其他计算机或 Web 服务等网络资源的应用场景，组托管服务帐户 (gMSA) 是更适合使用的标识。
gMSA 帐户提供域标识，可用于向域中任何计算机上的资源进行身份验证。
gMSA 帐户授予你的权限由你当前访问的资源决定。
你在任何计算机或服务上均不会自动拥有管理员权限，除非计算机/服务已显式授予 gMSA 帐户管理员特权。

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

仅在由于多个原因需要访问网络资源时才应使用 gMSA 帐户：

- 使用 gMSA 帐户时，更难跟踪用户的操作，因为每个用户均共享相同的运行方式标识。 你需要参考 PowerShell 会话记录和日志，将用户与其操作进行关联。

- gMSA 帐户可访问连接用户无需访问的多个网络资源。 请始终尽力限制 JEA 会话中的有效权限以符合最低特权原则。

> [!NOTE]
> 组托管服务帐户仅适用于 Windows PowerShell 5.1 或更高版本以及已加入域的计算机。


#### <a name="more-information-about-run-as-users"></a>有关以用户身份运行的详细信息

若要进一步了解运行方式标识及其如何影响 JEA 会话的安全性，可参阅[安全性注意事项](security-considerations.md)文章。

### <a name="session-transcripts"></a>会话脚本

建议将 JEA 会话配置文件配置为自动记录用户会话的脚本。
通过 PowerShell 会话脚本，可查看连接用户、向其分配的运行方式标识以及该用户运行的命令。
对于需要了解谁执行了特定系统更改的审核团队，这些信息非常有用。

若要在会话配置文件中配置自动脚本，请提供应存储脚本的文件夹路径。

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

应将指定的文件夹配置为阻止用户修改或删除其中的任何数据。
脚本由本地系统帐户写入到文件夹中，该帐户需要目录的读取和写入权限。
标准用户不得具有文件夹的访问权限，一组数量有限的安全管理员须具有访问权限来进行脚本审核。

### <a name="user-drive"></a>用户驱动器

如果连接用户需要将文件复制到 JEA 终结点或从中复制文件才可运行命令，可在会话配置文件中启用用户驱动器。
用户驱动器是映射到各连接用户的唯一文件夹的 [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives)。
此文件夹充当将文件复制到系统/从中复制文件的空间，但不提供访问完整文件系统或公开 FileSystem 提供程序的权限。
用户驱动器内容在会话之间持续存在，以便应对网络连接可能中断的情况。

```powershell
MountUserDrive = $true
```

默认情况下，用户驱动器允许每个用户存储最多 50 MB 的数据。
可使用“UserDriveMaximumSize”字段限制用户能使用的数据量。

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

如果不想持久保留用户驱动器中的数据，可在系统上配置计划任务，每晚自动清理文件夹。

> [!NOTE]
> 用户驱动器仅适用于 Windows PowerShell 5.1 或更高版本。

### <a name="role-definitions"></a>角色定义

会话配置文件中的角色定义可定义*用户*到*角色*的映射。
注册时，此字段中包含的所有用户或组都将获得到 JEA 终结点的权限。
每个用户或组仅可在哈希表中以键的形式内附一次，但可向其分配多个角色。
角色功能名称应为角色功能文件的名称，但不带 .psrc 扩展名。

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

如果某用户属于角色定义中的多个组，则其将获得访问每个组角色的权限。
如果两个角色向同一个 cmdlet 授予访问权限，则将向用户授予最宽松的参数集。

在角色定义字段中指定本地用户或组时，请务必在反斜杠前面添加计算机名称（而不是 *localhost* 或 *.*）。
可通过检查 `$env:computername` 变量来查看计算机名称。

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>角色功能搜索顺序
如上例所示，角色功能由角色功能文件的平面名称（不含扩展名的文件名）进行引用。
如果多个角色功能适用于带相同平面名称的系统，PowerShell 将使用隐式搜索顺序选择有效的角色功能文件。
它将**仅**向部分带同一名称的角色功能文件授予访问权限。

JEA 使用 `$env:PSModulePath` 环境变量来确定扫描角色功能文件的路径。
在每个路径中，JEA 将查找包含“RoleCapabilities”子文件夹的有效 PowerShell 模块。
与导入模块一样，与具有相同名称的自定义角色功能相比，JEA 更倾向于 Windows 随附的角色功能。
对于所有其他命名冲突，优先级由 Windows 枚举目录中文件的顺序（不保证按字母顺序排序）决定。
找到的匹配所需名称的第一个角色功能文件将用于连接用户。

当两个或多个角色功能共享同一名称时，角色功能搜索顺序是不确定的，因此**强烈建议**确保角色功能在计算机上具有唯一的名称。

### <a name="conditional-access-rules"></a>条件访问规则

RoleDefinitions 字段中包含的所有用户和组都将自动获得访问 JEA 终结点的权限。
通过条件访问规则，可优化此访问权限并要求用户隶属于其他不会影响其所拥有角色的安全组。
如果想要将 JEA 与“及时”特权访问管理解决方案、智能卡身份验证或其他多重身份验证解决方案进行集成，则此规则十分有用。

条件访问规则在会话配置文件的 RequiredGroups 字段中进行定义。
可在此处提供哈希表（选择性嵌套），利用“And”和“Or”键构造规则。
以下是如何使用此字段的一些示例：

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> 条件访问规则仅适用于 Windows PowerShell 5.1 或更高版本。

### <a name="other-properties"></a>其他属性
会话配置文件还可执行角色功能文件能实现的所有操作，但无法授予连接用户访问不同命令的权限。
如果想要允许所有用户访问特定的 cmdlet、函数或提供程序，可直接在会话配置文件中执行此操作。
有关会话配置文件中受支持属性的完整列表，请运行 `Get-Help New-PSSessionConfigurationFile -Full`。

## <a name="testing-a-session-configuration-file"></a>测试会话配置文件

可使用 [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet 测试会话配置。
如果已使用文本编辑器手动编辑 pssc 文件时，强烈建议测试会话配置文件以确保语法正确。
如果会话配置文件未通过此测试，它将无法在系统上成功注册。

## <a name="sample-session-configuration-file"></a>示例会话配置文件

下面的完整示例演示了如何创建和验证 JEA 的会话配置。
请注意，为了简便和易读，在 `$roles` 变量中创建和存储角色定义。
但并非必须这样做。

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>更新会话配置文件

如果需要更改 JEA 会话配置的属性（包括用户到角色的映射），需要[注销](register-jea.md#unregistering-jea-configurations)和[重新注册](register-jea.md) JEA 会话配置。
重新注册 JEA 会话配置时，使用包含所需更改的更新后的 PowerShell 会话配置文件。

## <a name="next-steps"></a>后续步骤

- [注册 JEA 配置](register-jea.md)
- [创作 JEA 角色](role-capabilities.md)
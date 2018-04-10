---
ms.date: 06/27/2017
keywords: powershell,cmdlet
title: Windows PowerShell Web 访问的授权规则和安全功能
ms.openlocfilehash: 0e765ae90661a054ca9bae71d0f6d449cccb185d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Windows PowerShell Web 访问的授权规则和安全功能

更新时间： 2013年 6 月 24日

适用于：Windows Server 2012 R2、Windows Server 2012

在 Windows Server 2012 R2 和 Windows Server 2012 中的 Windows PowerShell Web 访问具有受限的安全模型。
必须向用户显式授予访问权限，他们才能登录 Windows PowerShell Web 访问网关和使用基于 Web 的 Windows PowerShell 控制台。

## <a name="configuring-authorization-rules-and-site-security"></a>配置授权规则和站点安全

安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。
Windows PowerShell Web 访问的访问控制通过使用下表所述的一组 Windows PowerShell cmdlet 进行管理。
没有相当的 GUI 可用于添加或管理授权规则。
请参阅 [Windows PowerShell Web 访问 Cmdlet](cmdlets/web-access-cmdlets.md)。

管理员可为 Windows PowerShell Web 访问定义 0-*n* 条身份验证规则。
默认的安全性较为严格，而非宽松；零条身份验证规则意味着无用户可访问任何内容。

Windows Server 2012 R2 中的 [Add-PswaAuthorizationRule](cmdlets/add-pswaauthorizationrule.md) 和 [Test-PswaAuthorizationRule](cmdlets/test-pswaauthorizationrule.md) 包含一个 Credential 参数，该参数使你可从远程计算机或在活动的 Windows PowerShell Web 访问会话中添加和测试 Windows PowerShell Web 访问授权规则。
与其他具有 Credential 参数的 Windows PowerShell cmdlet 一样，你可以指定一个 PSCredential 对象作为该参数的值。
若要创建一个包含要传递到远程计算机的凭据的 PSCredential 对象，请运行 [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet。

Windows PowerShell Web 访问身份验证规则是白名单规则。
每条规则定义了用户、目标计算机和特定的 Windows PowerShell [会话配置](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations)（也称作终结点或运行空间）在特定目标计算机上的允许连接。
有关运行空间的说明，请参阅 [Beginning Use of PowerShell Runspaces](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)（PowerShell 运行空间入门）

> **安全说明**
>
> 用户仅需要一条可访问的规则。
如果用户有权从基于 Web 的控制台访问一台具有所有语言访问权限或仅可访问 Windows PowerShell 远程管理 cmdlet 的计算机，用户可登录（或跳到）其他与第一台目标计算机连接的计算机。
配置 Windows PowerShell Web 访问的最安全方法是仅允许用户访问受限制的会话配置，从而可让用户完成他们通常需要远程执行的特定任务。

[Windows PowerShell Web 访问 Cmdlet](cmdlets/web-access-cmdlets.md)中引用的 cmdlet 可用于创建一组访问规则，供授权 Windows PowerShell Web 访问网关上的用户时使用。
规则与目标计算机上的访问控制列表 (ACL) 有所不同，它提高了 Web 访问的安全性。
有关安全性的详细信息如以下部分所述。

如果用户无法通过任一上述的安全层，则会在浏览器窗口中看到一条常规的“拒绝访问”消息。
虽然有关安全性的详细信息记录在网关服务器上，但是最终用户并不获得有关他们通过多少个安全层或无法在哪个安全层登录或身份验证的信息。

有关如何配置授权规则的详细信息，请参阅本主题中的[配置授权规则](#configuring-authorization-rules-and-site-security)。

### <a name="security"></a>安全

Windows PowerShell Web 访问安全模型在基于 Web 控制台的最终用户和目标计算机之间具有四个安全层。
Windows PowerShell Web 访问管理员可通过其它配置在 IIS 管理器控制台中添加安全层。
有关如何确保 IIS 管理器控制台中网站的安全的详细信息，请参阅[配置 Web 服务器安全 (IIS 7)](https://technet.microsoft.com/library/cc731278)。
有关 IIS 最佳做法和阻止拒绝服务攻击的详细信息，请参阅[阻止 DoS/拒绝服务攻击的最佳做法](https://technet.microsoft.com/library/cc750213)。
管理员还可购买和安装其他零售身份验证软件。

下表描述最终用户与目标计算机之间的四个安全层。

|层次|层|
|-|-|
|1|[IIS Web 服务器安全功能](#iis-web-server-security-features)|
|2|[Windows PowerShell Web 访问基于表单的网关身份验证](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows PowerShell Web 访问授权规则](#windows-powershell-web-access-authorization-rules)|
|4|[目标身份验证和授权规则](#target-authentication-and-authorization-rules)|

有关各层的详细信息，可参阅下列标题：

#### <a name="iis-web-server-security-features"></a>IIS Web 服务器安全功能

Windows PowerShell Web 访问用户必须始终提供用户名和密码，以对其在网关上的帐户进行身份验证。
但是，Windows PowerShell Web 访问管理员还可打开或关闭可选的客户端证书身份验证（要了解如何启用测试证书，以及随后如何配置正版证书，请参阅[安装和使用 Windows PowerShell Web 访问](install-and-use-windows-powershell-web-access.md)）。

可选的客户端证书功能要求最终用户除拥有其用户名和密码外，还须持有有效的客户端证书，这是 Web 服务器 (IIS) 配置的一部分。
当启用客户端证书层时，Windows PowerShell Web 访问登录页面将提示用户提供有效的证书，然后再评估用户的登录凭据。
客户端证书身份验证程序自动检查客户端证书。
如果找不到有效的证书，Windows PowerShell Web 访问会通知用户，以便用户提供证书。
如果找到有效的证书，Windows PowerShell Web 访问将为用户打开登录页面，以提供用户名和密码。

这是 IIS Web 服务器提供其他安全设置的示例之一。
有关其他 IIS 安全功能的详细信息，请参阅 [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278)（配置 Web 服务器安全 (IIS 7)）

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell Web 访问基于表单的网关身份验证

Windows PowerShell Web 访问登录页面需要一组凭据（用户名和密码），并向用户提供一个为目标计算机提供其他凭据的选项。
如果用户不提供备用凭据，则照样可使用连接网关时所用的主要用户名和密码，连接目标计算机。

在 Windows PowerShell Web 访问网关上对所需的凭据进行身份验证。
这些凭据必须是本地 Windows PowerShell Web 访问网关服务器或 Active Directory 中有效的用户帐户。

#### <a name="windows-powershell-web-access-authorization-rules"></a>Windows PowerShell Web 访问授权规则

用户在网关上通过身份验证后，Windows PowerShell Web 访问将检查授权规则，以验证用户是否有权访问所需的目标计算机。
成功授权后，用户的凭据将传递到目标计算机。

仅当用户通过网关的身份验证之后，以及用户在目标计算机上通过身份验证之前，评估这些规则。

#### <a name="target-authentication-and-authorization-rules"></a>目标身份验证和授权规则

Windows PowerShell Web 访问的最后安全层是目标计算机自身的安全配置。
用户必须持有在目标计算机上配置的适当访问权限，并且按照 Windows PowerShell Web 访问授权规则，运行通过 Windows PowerShell Web 访问影响目标计算机的 Windows PowerShell 基于 Web 的控制台。

该层提供相同的安全机制；如果用户尝试通过运行 [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Enter-PSSession) 或 [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/new-pssession) cmdlet，为 Windows PowerShell 中的目标计算机创建远程 Windows PowerShell 会话，此类机制将评估连接尝试。

默认情况下，Windows PowerShell Web 访问使用主要用户名和密码，在网关和目标计算机上进行身份验证。
在标题为“可选的连接设置”部分，基于 Web 的登录页面为用户提供一个为目标计算机提供其他凭据的选项（如有必要）。
如果用户不提供备用凭据，则照样可使用连接网关时所用的主要用户名和密码，连接目标计算机。

授权规则可让用户访问特定的会话配置。
可以为 Windows PowerShell Web 访问创建受限的运行空间或会话配置，并可让特定用户在登录到 Windows PowerShell Web 访问时仅连接到特定的会话配置。
可使用访问控制列表 (ACL) 确定哪个用户具有访问特定终结点的权限，并使用本部分中的授权规则进一步限制特定用户组合访问终结点的权限。
有关受限运行空间的详细信息，请参阅 [Creating a constrained runspace](https://msdn.microsoft.com/en-us/library/dn614668)（创建受限运行空间）。

### <a name="configuring-authorization-rules"></a>配置授权规则

管理员可能想对为了进行 Windows PowerShell 远程管理已在其环境中定义的 Windows PowerShell Web 访问用户执行相同的授权规则。
本部分的第一个过程是描述如何添加安全授权规则，此类规则可授予一名用户访问权限，以便用户登录并管理一台计算机，以及处于单个会话配置中。
第二个程序描述如何删除不再需要的授权规则。

如果计划使用自定义会话配置以允许特定用户仅在 Windows PowerShell Web 访问的限制运行空间中运行，则可先创建自定义会话配置，然后再添加参考这些配置的授权规则。
无法使用 Windows PowerShell Web 访问 cmdlet 创建自定义会话配置。
有关创建自定义会话配置的详细信息，请参阅 [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files)。

Windows PowerShell Web 访问 cmdlet 支持只一个通配符，即星号 (\*)。
字符串中的通配符不受支持；根据属性（用户、计算机或会话配置）使用单个星号。

> **注意**
>
> 有关使用授权规则授予用户访问权限以及帮助确保 Windows PowerShell Web 访问环境安全的更多方式，请参阅本主题中的[其他授权规则方案示例](#other-authorization-rule-scenario-examples)。

#### <a name="to-add-a-restrictive-authorization-rule"></a>添加受限的授权规则

1. 使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。

    - 在 Windows 桌面上，右键单击任务栏上的“Windows PowerShell”，然后单击“以管理员身份运行”。

    - 在 Windows“开始”屏幕上，右键单击“Windows PowerShell”，然后单击“以管理员身份运行”。

2. 使用会话配置限制用户访问的可选步骤：

    确保规则中已存在要使用的会话配置。
如果尚未创建这些配置，则使用 [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files) 中用于创建会话配置的说明。

3. 本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见脚本和 cmdlet 需求的特定会话配置的权限。 键入以下命令，然后按**Enter**。

```powershell
Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
```

  - 在以下示例中，_Contoso_ 域中名为 _JSmith_ 的用户获得访问权限，以管理计算机 _Contoso_214_，并使用名为 _NewAdminsOnly_ 的会话配置。

```powershell
Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
```

4. 确保通过运行 **Get-PswaAuthorizationRule** cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt; 创建了该规则。 例如，**Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**。

#### <a name="to-remove-an-authorization-rule"></a>删除授权规则

1. 如果尚未打开 Windows PowerShell 会话，请参阅本部分中[添加受限的授权规则](#to-add-a-restrictive-authorization-rule)的步骤 1。

2. 键入以下内容，然后按 **Enter**，其中的*规则 ID* 代表要删除的规则的唯一 ID 号。

```powershell
Remove-PswaAuthorizationRule -ID <rule ID>
```

或者，如果不知道 ID 号，但知道想要删除的规则的友好名称，则可获取该规则的名称，然后通过管道将其传递给 `Remove-PswaAuthorizationRule` cmdlet，从而删除该规则，如以下示例所示：`Get-PswaAuthorizationRule -RuleName <rule-name> | Remove-PswaAuthorizationRule`。

>**注意**：
>
>系统不会提示你确认是否要删除特定的授权规则；按下 **Enter**，即可删除该规则。 在运行 `Remove-PswaAuthorizationRule` cmdlet 之前，确保你想要删除授权规则。

#### <a name="other-authorization-rule-scenario-examples"></a>其他授权规则方案示例

每个 Windows PowerShell 会话都使用会话配置；如果尚未为会话指定任何会话配置，Windows PowerShell 将使用默认的内置 Windows PowerShell 会话配置（被称为 Microsoft.PowerShell）。 默认的会话配置包括计算机上可用的所有 cmdlet。 管理员可利用受限的运行空间（有限范围内的其最终用户可执行的 cmdlet 和任务）定义会话配置，从而限制对所有计算机的访问权限。 对于有权访问一台具有所有语言访问权限的计算机或仅可访问 Windows PowerShell 远程管理 cmdlet 的用户，可连接到其他与第一台计算机连接的计算机。 定义受限的运行空间可阻止用户从其获准许的 Windows PowerShell 运行空间访问其他计算机，从而改善你的 Windows PowerShell Web 访问环境的安全性。 可（通过使用组策略）将会话配置分配给所有管理员想通过 Windows PowerShell Web 访问进行访问的计算机。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。
以下是本方案的一些示例。

- 管理员创建名为 **PswaEndpoint** 的终结点，其中带有受限的运行空间。 然后管理员创建规则 (**\*,\*,PswaEndpoint**)，并将终结点分配给其他计算机。 规则可让所有用户访问所有带有终结点 **PswaEndpoint** 的计算机。 如果这只是在规则集中定义的授权规则，则不能访问不带有终结点的计算机。

- 管理员创建名为 **PswaEndpoint** 的终结点（其中带有受限的运行空间），并希望限制特定用户的访问权限。 管理员创建一组名为 **Level1Support** 的用户，并定义以下规则：**Level1Support,\*,PswaEndpoint**。 规则可让 **Level1Support** 组中的用户访问所有带有 **PswaEndpoint** 配置的计算机。 类似地，可限制对特定计算机组合的访问权限。

- 有些管理员为某些用户提供的访问权限要比其他用户多。 例如，管理员创建两个用户组，分别是 **Admins** 和 **BasicSupport**。 管理员还创建名为 **PswaEndpoint** 的终结点（其中带有受限的运行空间），并定义以下两条规则：**Admins,\*,\*** 和 **BasicSupport,\*,PswaEndpoint**。 第一条规则为**Admin**组中的所有用户提供访问所有计算机的权限，第二条规则为**BasicSupport**组中的所有用户仅提供访问那些带有**PswaEndpoint**的计算机的权限。

- 管理员已设置专用测试环境，希望可让所有授权的网络用户通过他们经常访问的网络访问所有计算机，并持有对所有他们经常访问的会话配置的访问权限。 因为这是专用测试环境，管理员创建了不安全的授权规则。
  - 管理员运行的 cmdlet `Add-PswaAuthorizationRule * * *`使用通配符 * **\*** 来表示所有用户、所有计算机和所有配置。
  - 此规则与下列各项等效：`Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`。

  >**注意**：
  >
  >此规则不建议在安全的环境中使用，它可绕过 Windows PowerShell Web 访问提供的授权规则安全层。

- 管理员必须允许用户连接到同时包含工作组和域的环境中的目标计算机，其中工作组计算机偶尔用于连接到域中的目标计算机，域中的计算机偶尔用于连接到工作组中的目标计算机。 管理员具有工作组中的网关服务器 *PswaServer*，并且目标计算机 *srv1.contoso.com* 位于域中。 用户 *Chris* 既是工作组网关服务器又是目标计算机上的授权本地用户。 他在工作组服务器上的用户名为 *chrisLocal*，他在目标计算机上的用户名为 *contoso\\chris*。 若要授权 Chris 可访问 srv1.contoso.com，管理员会添加以下规则。

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

上述规则示例会在网关服务器上对 Chris 进行身份验证，然后授权他可以访问 *srv1*。 在登录页面上，Chris 必须在“**可选连接设置**”区域 (*contoso\\chris*) 中提供第二组凭据。 网关服务器使用一组额外的凭据在目标计算机*srv1.contoso.com*上对其进行身份验证。

在上述情景中，Windows PowerShell Web 访问仅在以下操作已成功且至少一个授权规则允许使用以下操作之后才会建立到目标计算机的成功连接。

1. 工作组网关服务器上的身份验证，方法是向授权规则添加采用 *server_name*\\*user_name* 格式的用户名

2. 目标计算机上的身份验证，方法是使用“可选连接设置”区域的登录页面中提供的备用凭据

  >**注意**：
  >
  >如果网关和目标计算机位于不同的工作组或域中，则必须在两个工作组计算机之间、两个域之间或工作组和域之间建立信任关系。 不能使用 Windows PowerShell Web 访问授权规则 cmdlet 配置此关系。 授权规则不会定义计算机之间的信任关系，它们仅可授权用户连接到特定目标计算机和会话配置。 有关如何配置不同域之间信任关系的详细信息，请参阅[创建域和林信任](https://technet.microsoft.com/library/cc794775.aspx")。 有关如何向受信任主机列表中添加工作组计算机的详细信息，请参阅[使用服务器管理器进行远程管理](https://technet.microsoft.com/library/dd759202.aspx)

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>对多个网站使用单一的授权规则集

授权规则存储在 XML 文件中。 默认情况下，XML 文件的路径名为 %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml。

授权规则 XML 文件的路径存储在 **powwa.config** 文件中，可在 _%windir%\\Web\\PowershellWebAccess\\data_ 中找到。 管理员可随时将参考路径更改为 **powwa.config** 中的默认路径，以满足首选项或要求。 允许管理员更改文件的位置，可让多个 Windows PowerShell Web 访问网关在需要此类配置的情况下，使用相同的授权规则。

## <a name="session-management"></a>会话管理

默认情况下，Windows PowerShell Web 访问限制一名用户一次访问三个会话。 可在 IIS 管理器中编辑 Web 应用程序的 web.config 文件，使每名用户可访问不同数目的会话。
web.config 文件的路径是 $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config。

默认情况下，如果编辑了任何设置，则会配置 IIS Web 服务器，以重启应用程序池。 例如，如果对 **web.config** 文件进行更改，则重新启动应用程序池。
>由于 Windows PowerShell Web 访问使用内存中的会话状态，因此重启应用程序池时，登录到 Windows PowerShell Web 访问会话的用户将错过其会话。

### <a name="setting-default-parameters-on-the-sign-in-page"></a>在登录页上设置默认参数

如果您的 Windows PowerShell Web 访问网关在 Windows Server 2012 R2 上运行，您可以配置在 Windows PowerShell Web 访问登录页上显示的设置的默认值。 可以配置上一段所述的 **web.config** 文件中的值。 登录页设置的默认值位于 web.config 文件的 **appSettings** 部分中；以下是 **appSettings** 部分的示例。 其中许多设置的有效值与 Windows PowerShell 中 [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet 的相应参数的有效值相同。
例如，`defaultApplicationName` 键（如以下代码块中所示）是目标计算机上 $PSSessionApplicationName 首选项变量的值。

```xml
    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>超时和计划外断开连接

Windows PowerShell Web 访问会话超时。在 Windows Server 2012 上运行的 Windows PowerShell Web 访问中，会话停止活动 15 分钟后，系统会向登录的用户发出超时消息。 如果用户在超时信息显示后五分钟内无任何回应，则会话结束，用户被注销。你可以在 IIS 管理器的网站设置中，更改会话的超时时间。

在 Windows Server 2012 R2 上运行的 Windows PowerShell Web 访问中，会话停止活动 20 分钟后，会话默认超时。 如果用户从基于 Web 的控制台中的会话断开连接是由于网络错误或其他计划外关机或故障，而不是因为他们自己关闭了会话，Windows PowerShell Web 访问会话将继续运行并连接到目标计算机，直到客户端的超时期结束。 会话在默认的 20 分钟或网关管理员指定的超时期（以时间较短者为准）后断开连接。

如果网关服务器正在运行 Windows Server 2012 R2，Windows PowerShell Web 访问将允许用户稍后重新连接到已保存的会话，但是，如果是网络错误、计划外关机或其他故障导致会话断开连接，用户需在网关管理员指定的超时期过后，才能查看或重新连接到已保存的会话。

## <a name="see-also"></a>另请参阅

- [安装和使用 Windows PowerShell Web 访问](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
- [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
- [Windows PowerShell Web 访问 Cmdlet](cmdlets/web-access-cmdlets.md)
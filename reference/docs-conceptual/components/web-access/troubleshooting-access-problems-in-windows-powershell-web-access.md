---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Windows PowerShell Web 访问中的访问问题疑难解答
ms.openlocfilehash: 314e4a8098988111739705d55b68ff5ed2f5eff3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086589"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Windows PowerShell Web 访问中的访问问题疑难解答

更新时间：2013 年 6 月 24 日（修订时间：2017 年 8 月 23 日）

适用于：Windows Server 2012 R2、Windows Server 2012

下列各部分标识了一些使用 Windows PowerShell Web 访问尝试连接到远程计算机时可能遇到的常见问题，其中包括解决这些问题的建议。

## <a name="sign-in-failure"></a>登录失败

失败可能是由于下列某个原因所至：

- 允许用户访问计算机的授权规则或远程计算机上的特定会话配置并不存在。

  Windows PowerShell Web 访问安全是严谨的；必须使用授权规则明确赋予用户访问远程计算机的权限。

  有关创建授权规则的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

- 用户未获得访问目标计算机的权限。 这是由访问控制列表 (ACL) 来确定的。

  有关详细信息，请参阅[登录到 Windows PowerShell Web 访问](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)或 Windows PowerShell 团队博客。

- 可能无法在目标计算机上启用 Windows PowerShell 远程管理。

  验证用户尝试连接的计算机上是否已启用远程管理。

  有关详细信息，请参阅 [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)（如何配置计算机进行远程处理）。

## <a name="internal-server-error"></a>内部服务器错误

用户尝试在 Internet Explorer 窗口中登录到 Windows PowerShell Web 访问时，系统会向他们显示“内部服务器错误”页面或 Internet Explorer 停止响应。

此问题特定于 Internet Explorer。

### <a name="possible-cause"></a>可能的原因

对于已使用包含中文字符的域名登录的用户或网关服务器名称中包含一个或多个中文字符时会出现此问题。

#### <a name="workaround"></a>解决方法

1. [安装并运行 Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. 将 Internet Explorer“文档模式”设置更改为“IE10 标准”。
   1. 按 F12 打开“开发人员工具”控制台。
   1. 在 Internet Explorer 10 中，单击“浏览器模式”，然后选择“Internet Explorer 10”。
   1. 单击“文档模式”，然后单击“IE10 标准”。
   1. 再次按 **F12** 可关闭“开发人员工具”控制台。
1. 在 Internet Explorer 10 中禁用自动代理配置。
   1. 单击 **“工具”**，然后单击 **“Internet 选项”**。
   1. 在“Internet 选项”对话框中的“连接”选项卡上，单击“LAN 设置”。
   1. 清除“自动检测设置”复选框。 单击“确定”，然后再次单击“确定”可关闭“Internet 选项”对话框。

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>无法连接到远程工作组计算机

如果目标计算机在工作组中，则使用以下语法，提供用户名并登录到计算机：`<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>找不到 Web 服务器 (IIS) 管理工具，即使已安装了角色

如果使用 `Install-WindowsFeature` cmdlet 安装了 Windows PowerShell Web 访问，除非将 `-IncludeManagementTools` 参数添加到 cmdlet，否则不会安装管理工具。

有关示例，请参阅[使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)。

可选择在以网关服务器为目标的“添加角色和功能向导”会话中的工具，添加 IIS Manager 控制台及其他所需的 IIS 管理工具。
“添加角色和功能向导”可从服务器管理器中打开。

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>无法访问 Windows PowerShell Web 访问网站

如果已在 Internet Explorer 中启用了增强的安全配置 (IE ESC)，可将 Windows PowerShell Web 访问网站添加到受信任的站点列表。

出于安全风险考虑，建议禁用 IE ESC。
可在服务器管理器中的“本地服务器”页面上的“属性”磁贴中禁用 IE ESC。

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>授权失败。 请验证你是否被授权连接到目标计算机。

如果网关服务器为目标计算机且也位于工作组中，尝试连接时，会显示上述错误消息。

如果网关服务器也是目标计算机且位于工作组中，指定用户名、计算机名称以及用户组名。
不要使用点 (.) 自行表示计算机名称。

### <a name="scenarios-and-proper-values"></a>方案和适当的值

#### <a name="all-cases"></a>所有情况

参数 | 值
-- | --
UserName | Server\_name\\user\_name<br/>Localhost\\user\_name<br/>.\\user\_name
UserGroup | Server\_name\\user\_group<br/>Localhost\\user\_group<br/>.\\user\_group
ComputerGroup | Server\_name\\computer\_group<br/>Localhost\\computer\_group<br/>.\\computer\_group

#### <a name="gateway-server-is-in-a-domain"></a>网关服务器位于域中

参数 | 值
-- | --
ComputerName | 网关服务器的完全限定名称或 Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>网关服务器位于工作组中

参数 | 值
-- | --
ComputerName | 服务器名称

### <a name="gateway-credentials"></a>Gateway credentials

以目标计算机身份登录到网关服务器，方法是使用以下格式之一的凭据。

- Server\_name\\user\_name
- Localhost\\user\_name
- .\\user\_name

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>授权规则中显示安全标识符 (SID)

在授权规则中显示安全标识符 (SID) 而不是语法 user\_name/computer\_name。

规则不再有效或 Active Directory 域服务查询失败。
如果网关服务器曾一时位于工作组中，但后来加入域中，则这种情形下通常授权规则无效

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>无法使用规则登录为带有域的 IPv6 地址

无法登录到已在授权规则中指定为带有域的 IPv6 地址的目标计算机。

授权规则不支持域名形式的 IPv6 地址。

若要使用 IPv6 地址指定目标计算机，请在授权规则中使用原始 IPv6 地址（包含冒号）。
支持域和数值（带有冒号）IPv6 地址作为 Windows PowerShell Web 访问登录页面而非授权规则中的目标计算机名称。

有关 IPv6 地址的详细信息，请参阅 [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx)（IPv6 的工作原理）。

## <a name="see-also"></a>另请参阅

- [Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
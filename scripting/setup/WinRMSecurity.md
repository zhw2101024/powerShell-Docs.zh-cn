# PowerShell 远程处理安全注意事项

PowerShell 远程处理是管理 Windows 系统的推荐方式。 在 Windows Server 2012 R2 中，默认启用 PowerShell 远程处理。 本文档介绍了使用 PowerShell 远程处理时的安全问题、 
建议以及最佳实践。

## PowerShell 远程处理是什么？

PowerShell 远程处理使用 [Windows 远程管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx)，这是 
[Web 服务管理 (WS-Managment)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) 协议的 Microsoft 实现，允许用户在
远程计算机上运行 PowerShell 命令。 你可以在[运行远程命令](https://technet.microsoft.com/en-us/library/dd819505.aspx)处找到有关使用 PowerShell 远程处理的详细信息。

PowerShell 远程处理不同于使用 cmdlet 的 **ComputerName** 参数在远程计算机上运行它，而是使用远程过程调用 (RPC) 
做为其基础协议。

##  PowerShell 远程处理默认设置

PowerShell 远程处理（和 WinRM）侦听以下端口：

- HTTP：5985
- HTTPS：5986

默认情况下，PowerShell 远程处理仅允许来自管理员组成员的连接。 会话在用户上下文中启动，因此所有
应用到单个用户和组的操作系统访问控件将在通过 PowerShell 远程处理连接时继续应用到它们。

在专用网络上，默认的 PowerShell 远程处理 Windows 防火墙规则接受所有连接。 在公用网络上，默认 Windows 防火墙规则仅允许来自同一子网内的 PowerShell
远程处理连接。 必须明确地更改该规则，以将 PowerShell 远程处理打开到公用网络上的所有连接。

>**警告：**公用网络的防火墙规则旨在保护计算机免于潜在的恶意外部连接尝试。 在删除 
>此规则时务必保持谨慎。

## 进程隔离

PowerShell 远程处理使用 [Windows 远程管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426)来实现计算机之间的通信。 
WinRM 作为网络服务帐户下的服务运行，并生成以用户帐户运行的隔离进程以托管 PowerShell 实例。 作为整体运行的 PowerShell 实例
用户不具有访问以其他用户身份运行 PowerShell 实例的进程的权限。

## PowerShell 远程处理生成的事件日志

FireEye 提供了良好的事件日志和其他由 PowerShell 远程处理会话生成的安全证据的摘要。该摘要在  
[调查 PowerShell 攻击](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)中可用。

## 加密和传输协议

从两个角度考虑 PowerShell 远程处理连接安全的安全性将很有帮助：初始身份验证和正在进行的通信。 

无论使用哪种传输协议（HTTP 或 HTTPS），在使用每会话 AES-256 对称密钥完成初始身份验证后，PowerShell 远程处理将始终加密所有的通信。
    
### 初始身份验证

身份验证确认客户端到服务器（理想情况下，从服务器到客户端）的身份。
    
当客户端连接到使用其计算机名称的域服务器（即：server01 或 server01.contoso.com）时，默认的身份验证协议为 
[Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx)。
Kerberos 保证用户标识和服务器标识，而不发送任何种类的可重用的凭据。

当客户端使用其 IP 地址连接到域服务器，或连接到工作组服务器时，不能进行 Kerberos 身份验证。 在这种情况下，PowerShell
远程处理依赖于 [NTLM 身份验证协议](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx)。 NTLM 身份验证：
保证用户标识，而不发送任何种类的委托证书的协议。 为了证明用户标识，NTLM 协议要求客户端
和服务器从用户的密码计算会话密钥，而无需自行交换密码。 服务器通常不知道用户的密码，因此它与 
知道用户密码的域控制器通信并为服务器计算会话密钥。 
      
但 NTLM 协议不能保证服务器标识。 如同所有使用 NTLM 进行身份验证的协议一样，有权访问计算机帐户（已加入域的计算机）的攻击者
可以调用域控制器来计算 NTLM 会话密钥，从而模拟服务器。

默认禁用基于 NTLM 的身份验证，但是可以通过配置目标服务器上的 SSL 或配置 WinRM TrustedHosts 设置而允许使用。
    
#### 使用 SSL 证书以在基于 NTLM 的连接过程中验证服务器标识

由于 NTLM 身份验证协议不能确保目标服务器的标识（除非它已知道你的密码），你可以配置目标服务器
使用适用于 PowerShell 远程处理的 SSL。 会启用“将 SSL 证书分配到目标服务器（如果由客户端也信任的证书颁发机构颁发）”
确保用户和服务器标识的基于 NTLM 的身份验证。
    
#### 忽略基于 NTLM 的服务器标识错误
      
如果将 SSL 证书部署到用于 NTLM 连接的服务器不可行，则可以通过将服务器添加到 WinRM 
**TrustedHosts** 列表来取消生成的标识错误。 请注意，添加服务器名称到 TrustedHosts 列表不应被视为任何形式的主机本身的可信度陈述，
因为 NTLM 身份验证协议不能确保你实际上正在连接到你想要连接的主机。
相反，应将 TrustedHosts 设置视为你想为其取消因无法验证服务器标识而生成的错误的主机列表。
    
    
### 正在进行的通信

初始身份验证完成后，[PowerShell 远程处理协议](https://msdn.microsoft.com/en-us/library/dd357801.aspx)会使用每会话 AES-256 对称密钥
对所有正在进行的通信进行加密。  


## 形成第二个跃点

默认情况下，PowerShell 远程处理使用 Kerberos（如果可用）或者 NTLM 进行身份验证。 这两种协议对远程计算机进行身份验证而无需向其发送凭据。
这是进行身份验证最安全的方式，但由于远程计算机没有用户的凭据，因此它不能以该用户的名义访问其他计算机和服务。 
这被称为“双跃点”问题。

有几种方法可以避免此问题：

### Kerberos 约束委派

对于高度受信任的服务器，可以启用 [Kerberos 约束委派](https://technet.microsoft.com/en-us/library/cc995228.aspx)。 这允许远程服务器将
经身份验证的用户模拟到指定计算机和服务列表。

### 远程计算机之间的信任

如果你信任远程连接到 *Server1* 的用户访问 *Server2* 上的资源，则可以显式授予 *Server1* 对这些资源的访问权限。

### 访问远程资源时使用显式凭据

通过使用 cmdlet 的 **Credential** 参数，可以将凭据显式传递到远程资源。 例如：

```powershell
$myCredential = Get-Credential
New-PSDrive -Name Tools \\Server2\Shared\Tools -Credential $myCredential 
```

### CredSSP

可以使用[凭据安全支持提供程序(CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) 进行身份验证（通过将“CredSSP”指定为 
对 [New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx) cmdlet 的一个调用的 `Authentication` 参数值。 CredSSP 将凭据以纯文本的形式传递给服务器，
因此，使用它会给你带来凭据被盗攻击的风险。 如果远程计算机被攻破，攻击者将有权访问用户的凭据。 默认情况下，CredSSP 在客户端和 
服务器计算机上都处于禁用状态。 应该仅在最受信任的环境中启用 CredSSP。 例如，连接到域控制器的域管理员，因为域控制器是 
高度受信任的。

有关使用用于 PowerShell 远程处理的 CredSSP 时的安全问题的详细信息，请参阅 
[意外破坏：注意 CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp)。

有关凭据被盗攻击的详细信息，请参阅[缓解哈希传递 (PtH) 攻击和其他凭据被盗](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。










<!--HONumber=Apr16_HO4-->



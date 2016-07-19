---
title: WinRMSecurity
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 67ef350559f9b3d17232f3c93d67634b3e939c60
ms.openlocfilehash: b1addddd50368fadcbb2581673d3ebc7cad8e32a

---

# PowerShell 远程处理安全注意事项

PowerShell 远程处理是管理 Windows 系统的推荐方式。 在 Windows Server 2012 R2 中，默认启用 PowerShell 远程处理。 本文档将介绍与使用 PowerShell 远程处理相关的安全问题、建议和最佳做法。

## PowerShell 远程处理是什么？

PowerShell 远程处理使用 [Windows 远程管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx)（这是 [Web Services for Management (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) 协议的 Microsoft 实现），允许用户在远程计算机上运行 PowerShell 命令。 你可以在[运行远程命令](https://technet.microsoft.com/en-us/library/dd819505.aspx)处找到有关使用 PowerShell 远程处理的详细信息。

PowerShell 远程处理不同于使用 cmdlet 的 **ComputerName** 参数在远程计算机上运行它，后者使用远程过程调用 (RPC) 作为其基础协议。

##  PowerShell 远程处理默认设置

PowerShell 远程处理（和 WinRM）侦听以下端口：

- HTTP：5985
- HTTPS：5986

默认情况下，PowerShell 远程处理仅允许来自管理员组成员的连接。 由于会话是在用户的上下文内启动的，因此所有应用于各个用户和组的操作系统访问控制会在他们通过 PowerShell 远程处理进行连接时继续应用于他们。

在专用网络上，默认的 PowerShell 远程处理 Windows 防火墙规则接受所有连接。 在公用网络上，默认 Windows 防火墙规则仅允许来自同一子网内的 PowerShell 远程处理连接。 必须明确地更改该规则，以将 PowerShell 远程处理打开到公用网络上的所有连接。

>**警告：**公用网络的防火墙规则旨在保护计算机免于潜在的恶意外部连接尝试。 请谨慎删除此规则。

## 进程隔离

PowerShell 远程处理使用 [Windows 远程管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426)来实现计算机之间的通信。 WinRM 作为网络服务帐户下的服务运行，并生成以用户帐户运行的隔离进程以托管 PowerShell 实例。 以一个用户身份运行的 PowerShell 实例无权访问以其他用户身份运行 PowerShell 实例的进程。

## PowerShell 远程处理生成的事件日志

FireEye 提供了良好的事件日志和其他由 PowerShell 远程处理会话生成的安全证据的摘要。该摘要在  
[调查 PowerShell 攻击](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)中可用。

## 加密和传输协议

从以下两个角度来考虑 PowerShell 远程处理连接的安全性会有所帮助：初始身份验证和正在进行的通信。 

无论使用哪种传输协议（HTTP 或 HTTPS），在使用每会话 AES-256 对称密钥完成初始身份验证后，PowerShell 远程处理将始终加密所有的通信。
    
### 初始身份验证

身份验证确认客户端到服务器（理想情况下，从服务器到客户端）的身份。
    
当客户端连接到使用其计算机名称（即 server01 或 server01.contoso.com）的域服务器时，默认身份验证协议为 [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx)。
Kerberos 保证用户标识和服务器标识，而不发送任何种类的可重用的凭据。

当客户端使用其 IP 地址连接到域服务器，或连接到工作组服务器时，不能进行 Kerberos 身份验证。 在这种情况下，PowerShell 远程处理依赖的是 [NTLM 身份验证协议](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx)。 NTLM 身份验证协议可在不发送任何种类的可代理凭据的情况下确保用户标识。 为了证明用户标识，NTLM 协议要求客户端和服务器通过用户的密码计算会话密钥，而不自行交换密码。 由于服务器通常不知道用户的密码，因此它会与域控制器进行通信，域控制器不仅知道用户的密码，还为服务器计算会话密钥。 
      
但 NTLM 协议不能保证服务器标识。 如同所有使用 NTLM 进行身份验证的协议一样，如果攻击者有权访问已加入域的计算机的帐户，则可以调用域控制器来计算 NTLM 会话密钥，从而模拟服务器。

默认禁用基于 NTLM 的身份验证，但是可以通过配置目标服务器上的 SSL 或配置客户端上的 WinRM TrustedHosts 设置而允许使用。
    
#### 使用 SSL 证书以在基于 NTLM 的连接过程中验证服务器标识

由于 NTLM 身份验证协议无法确保目标服务器的标识（除非它已知道你的密码），因此你可以将目标服务器配置为使用适用于 PowerShell 远程处理的 SSL。 将 SSL 证书分配给目标服务器（如果证书是由客户端也信任的证书颁发机构颁发的话）可启用基于 NTLM 的身份验证，从而确保用户标识和服务器标识。
    
#### 忽略基于 NTLM 的服务器标识错误
      
如果无法将 SSL 证书部署到服务器以进行 NTLM 连接，你可以将此服务器添加到 WinRM **TrustedHosts** 列表中，从而取消生成的标识错误。 请注意，将服务器名称添加到 TrustedHosts 列表不得被视为任何形式的主机本身可信度声明，因为 NTLM 身份验证协议无法确保你实际要连接到的主机就是你想要连接到的主机。
相反，应将 TrustedHosts 设置视为你想为其取消因无法验证服务器标识而生成的错误的主机列表。
    
    
### 正在进行的通信

初始身份验证完成后，[PowerShell 远程处理协议](https://msdn.microsoft.com/en-us/library/dd357801.aspx)会使用每会话 AES-256 对称密钥对所有正在进行的通信进行加密。  


## 形成第二个跃点

默认情况下，PowerShell 远程处理使用 Kerberos（如果可用）或者 NTLM 进行身份验证。 这两种协议对远程计算机进行身份验证而无需向其发送凭据。
这是进行身份验证最安全的方式，但由于远程计算机没有用户的凭据，因此它不能以该用户的名义访问其他计算机和服务。 这被称为“双跃点”问题。

有几种方法可以避免此问题：

### Kerberos 约束委派

对于高度受信任的服务器，可以启用 [Kerberos 约束委派](https://technet.microsoft.com/en-us/library/cc995228.aspx)。 这样一来，远程服务器便可以将已通过身份验证的用户模拟到指定的计算机和服务列表中。

### 远程计算机之间的信任

如果你信任远程连接到 *Server1* 的用户访问 *Server2* 上的资源，则可以显式授予 *Server1* 对这些资源的访问权限。

### 访问远程资源时使用显式凭据

通过使用 cmdlet 的 **Credential** 参数，可以将凭据显式传递到远程资源。 例如：

```powershell
$myCredential = Get-Credential
New-PSDrive -Name Tools \\Server2\Shared\Tools -Credential $myCredential 
```

### CredSSP

你可以使用[凭据安全支持提供程序 (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) 进行身份验证，具体方法为将“CredSSP”指定为对 [New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx) cmdlet 的调用的 `Authentication` 参数值。 CredSSP 会将凭据以纯文本的形式传递给服务器，因此会导致你面临遭受凭据被盗攻击的风险。 如果远程计算机被攻破，攻击者将有权访问用户的凭据。 默认情况下，CredSSP 在客户端和服务器计算机上都处于禁用状态。 应该仅在最受信任的环境中启用 CredSSP。 例如，连接到域控制器的域管理员，因为域控制器是高度可信任的。

若要详细了解在使用 CredSSP 进行 PowerShell 远程处理时需要注意的安全问题，请参阅 [Accidental Sabotage: Beware of CredSSP（非蓄意破坏：当心 CredSSP）](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp)。

有关凭据被盗攻击的详细信息，请参阅[缓解哈希传递 (PtH) 攻击和其他凭据被盗](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。











<!--HONumber=Jul16_HO1-->



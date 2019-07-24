---
title: 通过 SSH 进行 PowerShell 远程处理
description: 在 PowerShell Core 中使用 SSH 进行远程处理
ms.date: 08/14/2018
ms.openlocfilehash: d994a3888b9a372b803a65666634775a8905d63a
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372151"
---
# <a name="powershell-remoting-over-ssh"></a>通过 SSH 进行 PowerShell 远程处理

## <a name="overview"></a>概述

PowerShell 远程处理通常使用 WinRM 进行连接协商和数据传输。 SSH 现在可用于 Linux 和 Windows 平台，并允许进行真正的多平台 PowerShell 远程处理。

WinRM 为 PowerShell 远程会话提供可靠的托管模型。 基于 SSH 的远程处理目前不支持远程终结点配置和 JEA (Just Enough Administration)。

通过 SSH 远程处理可以在 Windows 和 Linux 计算机之间执行基础的 PowerShell 会话远程处理。 SSH 远程处理在目标计算机上创建一个 PowerShell 托管进程作为 SSH 子系统。 最终，我们将实现常规托管模型（类似于 WinRM）以支持终结点配置和 JEA。

`New-PSSession`、`Enter-PSSession` 和 `Invoke-Command` cmdlet 现具有新的参数集，以支持这个新的远程处理连接。

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

若要创建远程会话，请使用 `HostName` 参数指定目标计算机并通过 `UserName` 提供用户名。 当以交互方式运行 cmdlet 时，系统会提示输入密码。 还可以通过带有 `KeyFilePath` 参数的私钥文件来使用 SSH 密钥身份验证。

## <a name="general-setup-information"></a>常规安装信息

必须在所有计算机上安装 SSH。 SSH 客户端 (`ssh.exe`) 和服务器 (`sshd.exe`) 皆应安装，以便远程到计算机或从计算机进行远程。 OpenSSH for Windows 现已在 Windows 10 内部版本 1809 和 Windows Server 2019 中可用。 有关详细信息，请参阅 [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview)。 对于 Linux，请安装适用于平台的 SSH（包括 sshd 服务器）。 此外，需要从 GitHub 安装 PowerShell Core 以获取 SSH 远程处理功能。 必须配置 SSH 服务器以创建 SSH 子系统来托管远程计算机上的 PowerShell 进程。 还必须配置启用密码或基于密钥的身份验证。

## <a name="set-up-on-windows-machine"></a>在 Windows 计算机上设置

1. 安装 [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi) 的最新版本

   - 可以通过查看 `New-PSSession` 参数集来判断它是否具有 SSH 远程处理支持

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. 安装最新 Win32 OpenSSH。 有关安装说明，请参阅 [OpenSSH 的安装](/windows-server/administration/openssh/openssh_install_firstuse)。
3. 编辑位于 `$env:ProgramData\ssh` 的 `sshd_config` 文件。

   - 确保已启用密码身份验证

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > OpenSSH for Windows 中存在一个 bug，使空格在子系统可执行路径中无效。 有关详细信息，请参阅[此 GitHub 问题](https://github.com/PowerShell/Win32-OpenSSH/issues/784)。

     一种解决方案是创建不包含空格的 PowerShell 安装目录 symlink：

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     然后将其输入子系统：

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - 启用密钥身份验证（可选）

     ```
     PubkeyAuthentication yes
     ```

4. 重启 sshd 服务

   ```powershell
   Restart-Service sshd
   ```

5. 将 OpenSSH 的安装路径添加到 Path 环境变量。 例如，`C:\Program Files\OpenSSH\`。 通过此条目可找到 ssh.exe。

## <a name="set-up-on-linux-ubuntu-1604-machine"></a>在 Linux (Ubuntu 16.04) 计算机上设置

1. 从 GitHub 安装[适用于 Linux 的 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) 最新版本
2. 按需安装 [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. 编辑 /etc/ssh 位置中的 sshd_config 文件

   - 确保已启用密码身份验证

   ```
   PasswordAuthentication yes
   ```

   - 添加 PowerShell 子系统项

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - 启用密钥身份验证（可选）

   ```
   PubkeyAuthentication yes
   ```

4. 重启 sshd 服务

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>在 MacOS 计算器上设置

1. 安装[适用于 MacOS 的 PowerShell Core](../../install/installing-powershell-core-on-macos.md) 最新版本

   - 按照以下步骤确保已启用 SSH 远程处理：
     - 打开 `System Preferences`
     - 单击 `Sharing`
     - 检查 `Remote Login` - 应为 `Remote Login: On`
     - 允许相应用户访问

2. 编辑 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 文件

   - 使用常用编辑器或者

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - 确保已启用密码身份验证

     ```
     PasswordAuthentication yes
     ```

   - 添加 PowerShell 子系统项

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - 启用密钥身份验证（可选）

     ```
     PubkeyAuthentication yes
     ```

3. 重启 sshd 服务

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>身份验证

通过 SSH 进行 PowerShell 远程处理依赖于 SSH 客户端和 SSH 服务之间的身份验证交换，并且本身不实现任何身份验证方案。 这意味着任何配置的身份验证方案（包括多重身份验证）都由 SSH 处理，并且独立于 PowerShell。 例如，可以将 SSH 服务配置为需要公钥身份验证以及一次性密码，从而增加安全性。 多重身份验证的配置不在本文档的讨论范围。 若要了解如何正确配置多重身份验证，请参阅相关的 SSH 文档，并在尝试将其用于 PowerShell 远程处理之前先在 PowerShell 之外验证它的运行效果。

## <a name="powershell-remoting-example"></a>PowerShell 远程处理示例

测试远程处理最简单的方法是在单个计算机上进行测试。 在本示例中，我们创建返回到同一 Linux 计算机上的远程会话。 我们交互式使用 PowerShell cmdlet，这样我们可看到 SSH 提示我们验证主机计算机并要求提供密码。 可以在 Windows 计算机上执行相同的操作以确保远程处理正常工作。 然后，通过更改主机名在计算机之间进行远程处理。

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a>已知问题

sudo 命令对 Linux 计算机上的远程会话不起作用。

## <a name="see-also"></a>另请参阅

[PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)

[适用于 Linux 的 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[适用于 MacOS 的 PowerShell Core](../../install/installing-powershell-core-on-macos.md)

[OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

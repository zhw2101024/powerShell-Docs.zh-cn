# <a name="powershell-remoting-over-ssh"></a>通过 SSH 进行 PowerShell 远程处理

## <a name="overview"></a>概述

PowerShell 远程处理通常使用 WinRM 进行连接协商和数据传输。
选择 SSH 用于该远程处理实现的原因在于，它在 Linux 和 Windows 平台上皆可使用，并且支持真正的多平台 PowerShell 远程处理。
但是，WinRM 还对 PowerShell 远程会话提供可靠的托管模型，而该实现尚无法做到这点。
这意味着，此实现尚不支持 PowerShell 远程终结点配置和 JEA (Just Enough Administration)。

通过 PowerShell SSH 远程处理可以在 Windows 和 Linux 计算机之间执行基础的 PowerShell 会话远程处理。
其实现方法是在目标计算机上创建一个 PowerShell 托管进程作为 SSH 子系统。
最终，这将更改为更加常规的托管模型，其与 WinRM 支持终结点配置和 JEA 的工作原理相类似。

New-PSSession、Enter-PSSession 和 Invoke-Command cmdlet 现具有新的参数集，有助于实现这个新的远程处理连接

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

此新参数集以后可能会更改，但是现在可用于创建能从命令行交互或者能从其上调用命令和脚本的 SSH PSSession。
使用 HostName 参数指定目标计算机并通过 UserName 提供用户名。
在 PowerShell 命令行以交互方式运行这些 cmdlet 时，系统将提示输入密码。
但是，也可以选择使用 SSH 密钥身份验证方式，并为 KeyFilePath 参数提供一个私钥文件路径。

## <a name="general-setup-information"></a>常规安装信息

需要在所有计算机上安装 SSH。
客户端 (ssh.exe) 和服务器 (sshd.exe) 皆应安装，以便从计算机或对计算机进行远程处理测试。
对于 Windows，需要[从 GitHub 安装 Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)。
对于 Linux，需要安装适用于平台的 SSH（包括 sshd 服务器）。
还需要从 GitHub 中安装具有 SSH 远程处理功能的 PowerShell 新版本或包。
SSH 子系统用于在远程计算机上创建 PowerShell 进程，且 SSH 服务器需要对此作出相应配置。
还需启用密码身份验证或基于密钥的身份验证。

## <a name="setup-on-windows-machine"></a>在 Windows 计算机上安装

1. 安装 [PowerShell Core for Windows] 的最新版本
    - 可以通过查看 New-PSSession 参数集判断它是否具有 SSH 远程处理支持

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. 按照[安装]说明从 GitHub 安装 [Win32 OpenSSH] 最新版本
1. 编辑 Win32 OpenSSH 安装位置中的 sshd_config 文件
    - 确保已启用密码身份验证

    ```
    PasswordAuthentication yes
    ```

    - 添加 PowerShell 子系统项，将 `c:/program files/powershell/6.0.0/pwsh.exe` 替换为所需版本的对应路径

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - 启用密钥身份验证（可选）

    ```
    PubkeyAuthentication yes
    ```

1. 重启 sshd 服务

    ```powershell
    Restart-Service sshd
    ```

1. 将 OpenSSH 的安装路径添加到 Path Env Variable
    - 这应该沿着 `C:\Program Files\OpenSSH\` 行
    - 这样可找到 ssh.exe

## <a name="setup-on-linux-ubuntu-1404-machine"></a>在 Linux (Ubuntu 14.04) 计算机上安装

1. 从 GitHub 安装[适用于 Linux 的 PowerShell] 最新版本
1. 按需安装 [Ubuntu SSH]

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. 编辑 /etc/ssh 位置中的 sshd_config 文件
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

1. 重启 sshd 服务

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>在 MacOS 计算器上安装

1. 安装[适用于 MacOS 的 PowerShell] 最新版本
    - 按照以下步骤确保已启用 SSH 远程处理：
      - 打开 `System Preferences`
      - 单击 `Sharing`
      - 检查 `Remote Login` - 应为 `Remote Login: On`
      - 允许相应用户访问
1. 编辑 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 文件
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

1. 重启 sshd 服务

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>PowerShell 远程处理示例

测试远程处理最简单的方法是在单个计算机上进行测试。
我将在这里创建一个返回 Linux 盒上同一计算机的远程会话。
请注意，我在命令提示符处使用 PowerShell cmdlet，这样我们可看到 SSH 提示我们验证主机计算机和提供密码。
可以在 Windows 计算机上进行相同操作以确保远程处理运行，然后仅通过更改主机名在计算机之间进行远程处理。

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

1. sudo 命令对以 Linux 计算机为目标的远程会话不起作用。

[PowerShell Core for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[安装]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[适用于 Linux 的 PowerShell]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[适用于 MacOS 的 PowerShell]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012

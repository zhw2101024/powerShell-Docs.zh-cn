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
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="a3294-103">通过 SSH 进行 PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="a3294-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="a3294-104">概述</span><span class="sxs-lookup"><span data-stu-id="a3294-104">Overview</span></span>

<span data-ttu-id="a3294-105">PowerShell 远程处理通常使用 WinRM 进行连接协商和数据传输。</span><span class="sxs-lookup"><span data-stu-id="a3294-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="a3294-106">SSH 现在可用于 Linux 和 Windows 平台，并允许进行真正的多平台 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="a3294-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="a3294-107">WinRM 为 PowerShell 远程会话提供可靠的托管模型。</span><span class="sxs-lookup"><span data-stu-id="a3294-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="a3294-108">基于 SSH 的远程处理目前不支持远程终结点配置和 JEA (Just Enough Administration)。</span><span class="sxs-lookup"><span data-stu-id="a3294-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="a3294-109">通过 SSH 远程处理可以在 Windows 和 Linux 计算机之间执行基础的 PowerShell 会话远程处理。</span><span class="sxs-lookup"><span data-stu-id="a3294-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="a3294-110">SSH 远程处理在目标计算机上创建一个 PowerShell 托管进程作为 SSH 子系统。</span><span class="sxs-lookup"><span data-stu-id="a3294-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="a3294-111">最终，我们将实现常规托管模型（类似于 WinRM）以支持终结点配置和 JEA。</span><span class="sxs-lookup"><span data-stu-id="a3294-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="a3294-112">`New-PSSession`、`Enter-PSSession` 和 `Invoke-Command` cmdlet 现具有新的参数集，以支持这个新的远程处理连接。</span><span class="sxs-lookup"><span data-stu-id="a3294-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="a3294-113">若要创建远程会话，请使用 `HostName` 参数指定目标计算机并通过 `UserName` 提供用户名。</span><span class="sxs-lookup"><span data-stu-id="a3294-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="a3294-114">当以交互方式运行 cmdlet 时，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="a3294-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="a3294-115">还可以通过带有 `KeyFilePath` 参数的私钥文件来使用 SSH 密钥身份验证。</span><span class="sxs-lookup"><span data-stu-id="a3294-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="a3294-116">常规安装信息</span><span class="sxs-lookup"><span data-stu-id="a3294-116">General setup information</span></span>

<span data-ttu-id="a3294-117">必须在所有计算机上安装 SSH。</span><span class="sxs-lookup"><span data-stu-id="a3294-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="a3294-118">SSH 客户端 (`ssh.exe`) 和服务器 (`sshd.exe`) 皆应安装，以便远程到计算机或从计算机进行远程。</span><span class="sxs-lookup"><span data-stu-id="a3294-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="a3294-119">OpenSSH for Windows 现已在 Windows 10 内部版本 1809 和 Windows Server 2019 中可用。</span><span class="sxs-lookup"><span data-stu-id="a3294-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="a3294-120">有关详细信息，请参阅 [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview)。</span><span class="sxs-lookup"><span data-stu-id="a3294-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="a3294-121">对于 Linux，请安装适用于平台的 SSH（包括 sshd 服务器）。</span><span class="sxs-lookup"><span data-stu-id="a3294-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="a3294-122">此外，需要从 GitHub 安装 PowerShell Core 以获取 SSH 远程处理功能。</span><span class="sxs-lookup"><span data-stu-id="a3294-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="a3294-123">必须配置 SSH 服务器以创建 SSH 子系统来托管远程计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="a3294-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="a3294-124">还必须配置启用密码或基于密钥的身份验证。</span><span class="sxs-lookup"><span data-stu-id="a3294-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="a3294-125">在 Windows 计算机上设置</span><span class="sxs-lookup"><span data-stu-id="a3294-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="a3294-126">安装 [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi) 的最新版本</span><span class="sxs-lookup"><span data-stu-id="a3294-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="a3294-127">可以通过查看 `New-PSSession` 参数集来判断它是否具有 SSH 远程处理支持</span><span class="sxs-lookup"><span data-stu-id="a3294-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="a3294-128">安装最新 Win32 OpenSSH。</span><span class="sxs-lookup"><span data-stu-id="a3294-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="a3294-129">有关安装说明，请参阅 [OpenSSH 的安装](/windows-server/administration/openssh/openssh_install_firstuse)。</span><span class="sxs-lookup"><span data-stu-id="a3294-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="a3294-130">编辑位于 `$env:ProgramData\ssh` 的 `sshd_config` 文件。</span><span class="sxs-lookup"><span data-stu-id="a3294-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="a3294-131">确保已启用密码身份验证</span><span class="sxs-lookup"><span data-stu-id="a3294-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="a3294-132">OpenSSH for Windows 中存在一个 bug，使空格在子系统可执行路径中无效。</span><span class="sxs-lookup"><span data-stu-id="a3294-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="a3294-133">有关详细信息，请参阅[此 GitHub 问题](https://github.com/PowerShell/Win32-OpenSSH/issues/784)。</span><span class="sxs-lookup"><span data-stu-id="a3294-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="a3294-134">一种解决方案是创建不包含空格的 PowerShell 安装目录 symlink：</span><span class="sxs-lookup"><span data-stu-id="a3294-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="a3294-135">然后将其输入子系统：</span><span class="sxs-lookup"><span data-stu-id="a3294-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="a3294-136">启用密钥身份验证（可选）</span><span class="sxs-lookup"><span data-stu-id="a3294-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="a3294-137">重启 sshd 服务</span><span class="sxs-lookup"><span data-stu-id="a3294-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="a3294-138">将 OpenSSH 的安装路径添加到 Path 环境变量。</span><span class="sxs-lookup"><span data-stu-id="a3294-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="a3294-139">例如，`C:\Program Files\OpenSSH\`。</span><span class="sxs-lookup"><span data-stu-id="a3294-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="a3294-140">通过此条目可找到 ssh.exe。</span><span class="sxs-lookup"><span data-stu-id="a3294-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1604-machine"></a><span data-ttu-id="a3294-141">在 Linux (Ubuntu 16.04) 计算机上设置</span><span class="sxs-lookup"><span data-stu-id="a3294-141">Set up on Linux (Ubuntu 16.04) Machine</span></span>

1. <span data-ttu-id="a3294-142">从 GitHub 安装[适用于 Linux 的 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) 最新版本</span><span class="sxs-lookup"><span data-stu-id="a3294-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) build from GitHub</span></span>
2. <span data-ttu-id="a3294-143">按需安装 [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)</span><span class="sxs-lookup"><span data-stu-id="a3294-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="a3294-144">编辑 /etc/ssh 位置中的 sshd_config 文件</span><span class="sxs-lookup"><span data-stu-id="a3294-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="a3294-145">确保已启用密码身份验证</span><span class="sxs-lookup"><span data-stu-id="a3294-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="a3294-146">添加 PowerShell 子系统项</span><span class="sxs-lookup"><span data-stu-id="a3294-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="a3294-147">启用密钥身份验证（可选）</span><span class="sxs-lookup"><span data-stu-id="a3294-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="a3294-148">重启 sshd 服务</span><span class="sxs-lookup"><span data-stu-id="a3294-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="a3294-149">在 MacOS 计算机上设置</span><span class="sxs-lookup"><span data-stu-id="a3294-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="a3294-150">安装[适用于 MacOS 的 PowerShell Core](../../install/installing-powershell-core-on-macos.md) 最新版本</span><span class="sxs-lookup"><span data-stu-id="a3294-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="a3294-151">按照以下步骤确保已启用 SSH 远程处理：</span><span class="sxs-lookup"><span data-stu-id="a3294-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="a3294-152">打开 `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="a3294-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="a3294-153">单击 `Sharing`</span><span class="sxs-lookup"><span data-stu-id="a3294-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="a3294-154">检查 `Remote Login` - 应为 `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="a3294-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="a3294-155">允许相应用户访问</span><span class="sxs-lookup"><span data-stu-id="a3294-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="a3294-156">编辑 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 文件</span><span class="sxs-lookup"><span data-stu-id="a3294-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="a3294-157">使用常用编辑器或者</span><span class="sxs-lookup"><span data-stu-id="a3294-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="a3294-158">确保已启用密码身份验证</span><span class="sxs-lookup"><span data-stu-id="a3294-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="a3294-159">添加 PowerShell 子系统项</span><span class="sxs-lookup"><span data-stu-id="a3294-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="a3294-160">启用密钥身份验证（可选）</span><span class="sxs-lookup"><span data-stu-id="a3294-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="a3294-161">重启 sshd 服务</span><span class="sxs-lookup"><span data-stu-id="a3294-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="a3294-162">身份验证</span><span class="sxs-lookup"><span data-stu-id="a3294-162">Authentication</span></span>

<span data-ttu-id="a3294-163">通过 SSH 进行 PowerShell 远程处理依赖于 SSH 客户端和 SSH 服务之间的身份验证交换，并且本身不实现任何身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="a3294-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span> <span data-ttu-id="a3294-164">这意味着任何配置的身份验证方案（包括多重身份验证）都由 SSH 处理，并且独立于 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a3294-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="a3294-165">例如，可以将 SSH 服务配置为需要公钥身份验证以及一次性密码，从而增加安全性。</span><span class="sxs-lookup"><span data-stu-id="a3294-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span> <span data-ttu-id="a3294-166">多重身份验证的配置不在本文档的讨论范围。</span><span class="sxs-lookup"><span data-stu-id="a3294-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="a3294-167">若要了解如何正确配置多重身份验证，请参阅相关的 SSH 文档，并在尝试将其用于 PowerShell 远程处理之前先在 PowerShell 之外验证它的运行效果。</span><span class="sxs-lookup"><span data-stu-id="a3294-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="a3294-168">PowerShell 远程处理示例</span><span class="sxs-lookup"><span data-stu-id="a3294-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="a3294-169">测试远程处理最简单的方法是在单个计算机上进行测试。</span><span class="sxs-lookup"><span data-stu-id="a3294-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="a3294-170">在本示例中，我们创建返回到同一 Linux 计算机上的远程会话。</span><span class="sxs-lookup"><span data-stu-id="a3294-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="a3294-171">我们交互式使用 PowerShell cmdlet，这样我们可看到 SSH 提示我们验证主机计算机并要求提供密码。</span><span class="sxs-lookup"><span data-stu-id="a3294-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="a3294-172">可以在 Windows 计算机上执行相同的操作以确保远程处理正常工作。</span><span class="sxs-lookup"><span data-stu-id="a3294-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="a3294-173">然后，通过更改主机名在计算机之间进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="a3294-173">Then remote between machines by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="a3294-174">已知问题</span><span class="sxs-lookup"><span data-stu-id="a3294-174">Known Issues</span></span>

<span data-ttu-id="a3294-175">sudo 命令对 Linux 计算机上的远程会话不起作用。</span><span class="sxs-lookup"><span data-stu-id="a3294-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3294-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3294-176">See Also</span></span>

[<span data-ttu-id="a3294-177">PowerShell Core for Windows</span><span class="sxs-lookup"><span data-stu-id="a3294-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="a3294-178">适用于 Linux 的 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a3294-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="a3294-179">适用于 MacOS 的 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a3294-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="a3294-180">OpenSSH for Windows</span><span class="sxs-lookup"><span data-stu-id="a3294-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="a3294-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="a3294-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

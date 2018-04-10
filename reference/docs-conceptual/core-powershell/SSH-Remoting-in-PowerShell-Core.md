# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="4a560-101">通过 SSH 进行 PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="4a560-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="4a560-102">概述</span><span class="sxs-lookup"><span data-stu-id="4a560-102">Overview</span></span>

<span data-ttu-id="4a560-103">PowerShell 远程处理通常使用 WinRM 进行连接协商和数据传输。</span><span class="sxs-lookup"><span data-stu-id="4a560-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="4a560-104">选择 SSH 用于该远程处理实现的原因在于，它在 Linux 和 Windows 平台上皆可使用，并且支持真正的多平台 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="4a560-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="4a560-105">但是，WinRM 还对 PowerShell 远程会话提供可靠的托管模型，而该实现尚无法做到这点。</span><span class="sxs-lookup"><span data-stu-id="4a560-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="4a560-106">这意味着，此实现尚不支持 PowerShell 远程终结点配置和 JEA (Just Enough Administration)。</span><span class="sxs-lookup"><span data-stu-id="4a560-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="4a560-107">通过 PowerShell SSH 远程处理可以在 Windows 和 Linux 计算机之间执行基础的 PowerShell 会话远程处理。</span><span class="sxs-lookup"><span data-stu-id="4a560-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="4a560-108">其实现方法是在目标计算机上创建一个 PowerShell 托管进程作为 SSH 子系统。</span><span class="sxs-lookup"><span data-stu-id="4a560-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="4a560-109">最终，这将更改为更加常规的托管模型，其与 WinRM 支持终结点配置和 JEA 的工作原理相类似。</span><span class="sxs-lookup"><span data-stu-id="4a560-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="4a560-110">New-PSSession、Enter-PSSession 和 Invoke-Command cmdlet 现具有新的参数集，有助于实现这个新的远程处理连接</span><span class="sxs-lookup"><span data-stu-id="4a560-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="4a560-111">此新参数集以后可能会更改，但是现在可用于创建能从命令行交互或者能从其上调用命令和脚本的 SSH PSSession。</span><span class="sxs-lookup"><span data-stu-id="4a560-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="4a560-112">使用 HostName 参数指定目标计算机并通过 UserName 提供用户名。</span><span class="sxs-lookup"><span data-stu-id="4a560-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="4a560-113">在 PowerShell 命令行以交互方式运行这些 cmdlet 时，系统将提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="4a560-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="4a560-114">但是，也可以选择使用 SSH 密钥身份验证方式，并为 KeyFilePath 参数提供一个私钥文件路径。</span><span class="sxs-lookup"><span data-stu-id="4a560-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="4a560-115">常规安装信息</span><span class="sxs-lookup"><span data-stu-id="4a560-115">General setup information</span></span>

<span data-ttu-id="4a560-116">需要在所有计算机上安装 SSH。</span><span class="sxs-lookup"><span data-stu-id="4a560-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="4a560-117">客户端 (ssh.exe) 和服务器 (sshd.exe) 皆应安装，以便从计算机或对计算机进行远程处理测试。</span><span class="sxs-lookup"><span data-stu-id="4a560-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="4a560-118">对于 Windows，需要[从 GitHub 安装 Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)。</span><span class="sxs-lookup"><span data-stu-id="4a560-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="4a560-119">对于 Linux，需要安装适用于平台的 SSH（包括 sshd 服务器）。</span><span class="sxs-lookup"><span data-stu-id="4a560-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="4a560-120">还需要从 GitHub 中安装具有 SSH 远程处理功能的 PowerShell 新版本或包。</span><span class="sxs-lookup"><span data-stu-id="4a560-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="4a560-121">SSH 子系统用于在远程计算机上创建 PowerShell 进程，且 SSH 服务器需要对此作出相应配置。</span><span class="sxs-lookup"><span data-stu-id="4a560-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="4a560-122">还需启用密码身份验证或基于密钥的身份验证。</span><span class="sxs-lookup"><span data-stu-id="4a560-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="4a560-123">在 Windows 计算机上安装</span><span class="sxs-lookup"><span data-stu-id="4a560-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="4a560-124">[Install the latest version of PowerShell Core for Windows][]</span><span class="sxs-lookup"><span data-stu-id="4a560-124">[Install the latest version of PowerShell Core for Windows][]</span></span>
    - <span data-ttu-id="4a560-125">可以通过查看 New-PSSession 参数集判断它是否具有 SSH 远程处理支持</span><span class="sxs-lookup"><span data-stu-id="4a560-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>
    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```
1. <span data-ttu-id="4a560-126">按照[安装]说明从 GitHub 安装 [Win32 OpenSSH] 最新版本</span><span class="sxs-lookup"><span data-stu-id="4a560-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="4a560-127">编辑 Win32 OpenSSH 安装位置中的 sshd_config 文件</span><span class="sxs-lookup"><span data-stu-id="4a560-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="4a560-128">确保已启用密码身份验证</span><span class="sxs-lookup"><span data-stu-id="4a560-128">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="4a560-129">添加 PowerShell 子系统项，将 `c:/program files/powershell/6.0.0/pwsh.exe` 替换为所需版本的对应路径</span><span class="sxs-lookup"><span data-stu-id="4a560-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>
    ```none
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="4a560-130">启用密钥身份验证（可选）</span><span class="sxs-lookup"><span data-stu-id="4a560-130">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="4a560-131">重启 sshd 服务</span><span class="sxs-lookup"><span data-stu-id="4a560-131">Restart the sshd service</span></span>
    ```powershell
    Restart-Service sshd
    ```
1. <span data-ttu-id="4a560-132">将 OpenSSH 的安装路径添加到 Path Env Variable</span><span class="sxs-lookup"><span data-stu-id="4a560-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="4a560-133">这应该沿着 `C:\Program Files\OpenSSH\` 行</span><span class="sxs-lookup"><span data-stu-id="4a560-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="4a560-134">这样可找到 ssh.exe</span><span class="sxs-lookup"><span data-stu-id="4a560-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="4a560-135">在 Linux (Ubuntu 14.04) 计算机上安装</span><span class="sxs-lookup"><span data-stu-id="4a560-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="4a560-136">从 GitHub 安装[适用于 Linux 的 PowerShell] 最新版本</span><span class="sxs-lookup"><span data-stu-id="4a560-136">Install the latest [PowerShell for Linux] build from GitHub</span></span>
1. <span data-ttu-id="4a560-137">按需安装 [Ubuntu SSH]</span><span class="sxs-lookup"><span data-stu-id="4a560-137">Install [Ubuntu SSH] as needed</span></span>
    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```
1. <span data-ttu-id="4a560-138">编辑 /etc/ssh 位置中的 sshd_config 文件</span><span class="sxs-lookup"><span data-stu-id="4a560-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="4a560-139">确保已启用密码身份验证</span><span class="sxs-lookup"><span data-stu-id="4a560-139">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="4a560-140">添加 PowerShell 子系统项</span><span class="sxs-lookup"><span data-stu-id="4a560-140">Add a PowerShell subsystem entry</span></span>
    ```none
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="4a560-141">启用密钥身份验证（可选）</span><span class="sxs-lookup"><span data-stu-id="4a560-141">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="4a560-142">重启 sshd 服务</span><span class="sxs-lookup"><span data-stu-id="4a560-142">Restart the sshd service</span></span>
    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="4a560-143">在 MacOS 计算器上安装</span><span class="sxs-lookup"><span data-stu-id="4a560-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="4a560-144">安装[适用于 MacOS 的 PowerShell] 最新版本</span><span class="sxs-lookup"><span data-stu-id="4a560-144">Install the latest [PowerShell for MacOS] build</span></span>
    - <span data-ttu-id="4a560-145">按照以下步骤确保已启用 SSH 远程处理：</span><span class="sxs-lookup"><span data-stu-id="4a560-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="4a560-146">打开 `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="4a560-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="4a560-147">单击 `Sharing`</span><span class="sxs-lookup"><span data-stu-id="4a560-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="4a560-148">检查 `Remote Login` - 应为 `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="4a560-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="4a560-149">允许相应用户访问</span><span class="sxs-lookup"><span data-stu-id="4a560-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="4a560-150">编辑 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 文件</span><span class="sxs-lookup"><span data-stu-id="4a560-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="4a560-151">使用常用编辑器或者</span><span class="sxs-lookup"><span data-stu-id="4a560-151">Use your favorite editor or</span></span>
    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```
    - <span data-ttu-id="4a560-152">确保已启用密码身份验证</span><span class="sxs-lookup"><span data-stu-id="4a560-152">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="4a560-153">添加 PowerShell 子系统项</span><span class="sxs-lookup"><span data-stu-id="4a560-153">Add a PowerShell subsystem entry</span></span>
    ```none
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="4a560-154">启用密钥身份验证（可选）</span><span class="sxs-lookup"><span data-stu-id="4a560-154">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="4a560-155">重启 sshd 服务</span><span class="sxs-lookup"><span data-stu-id="4a560-155">Restart the sshd service</span></span>
    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="4a560-156">PowerShell 远程处理示例</span><span class="sxs-lookup"><span data-stu-id="4a560-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="4a560-157">测试远程处理最简单的方法是在单个计算机上进行测试。</span><span class="sxs-lookup"><span data-stu-id="4a560-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="4a560-158">我将在这里创建一个返回 Linux 盒上同一计算机的远程会话。</span><span class="sxs-lookup"><span data-stu-id="4a560-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="4a560-159">请注意，我在命令提示符处使用 PowerShell cmdlet，这样我们可看到 SSH 提示我们验证主机计算机和提供密码。</span><span class="sxs-lookup"><span data-stu-id="4a560-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="4a560-160">可以在 Windows 计算机上进行相同操作以确保远程处理运行，然后仅通过更改主机名在计算机之间进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="4a560-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="4a560-161">已知问题</span><span class="sxs-lookup"><span data-stu-id="4a560-161">Known Issues</span></span>

1. <span data-ttu-id="4a560-162">sudo 命令对以 Linux 计算机为目标的远程会话不起作用。</span><span class="sxs-lookup"><span data-stu-id="4a560-162">sudo command does not work in remote session to Linux machine.</span></span>

[PowerShell for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH
[安装]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[适用于 Linux 的 PowerShell]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[PowerShell for Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[适用于 MacOS 的 PowerShell]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012
[PowerShell for MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012
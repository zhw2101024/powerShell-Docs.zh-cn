---
title: 通过 SSH 进行 PowerShell 远程处理
description: 在 PowerShell Core 中使用 SSH 进行远程处理
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444370"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="c99fc-103">通过 SSH 进行 PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="c99fc-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="c99fc-104">概述</span><span class="sxs-lookup"><span data-stu-id="c99fc-104">Overview</span></span>

<span data-ttu-id="c99fc-105">PowerShell 远程处理通常使用 WinRM 进行连接协商和数据传输。</span><span class="sxs-lookup"><span data-stu-id="c99fc-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="c99fc-106">SSH 现在可用于 Linux 和 Windows 平台，并允许进行真正的多平台 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="c99fc-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="c99fc-107">WinRM 为 PowerShell 远程会话提供可靠的托管模型。</span><span class="sxs-lookup"><span data-stu-id="c99fc-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="c99fc-108">基于 SSH 的远程处理目前不支持远程终结点配置和 Just Enough Administration (JEA)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="c99fc-109">通过 SSH 远程处理可以在 Windows 和 Linux 计算机之间执行基础的 PowerShell 会话远程处理。</span><span class="sxs-lookup"><span data-stu-id="c99fc-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="c99fc-110">SSH 远程处理在目标计算机上创建一个 PowerShell 托管进程作为 SSH 子系统。</span><span class="sxs-lookup"><span data-stu-id="c99fc-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="c99fc-111">最终，我们将实现常规托管模型（类似于 WinRM）以支持终结点配置和 JEA。</span><span class="sxs-lookup"><span data-stu-id="c99fc-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="c99fc-112">`New-PSSession`、`Enter-PSSession` 和 `Invoke-Command` cmdlet 现具有新的参数集，以支持这个新的远程处理连接。</span><span class="sxs-lookup"><span data-stu-id="c99fc-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="c99fc-113">若要创建远程会话，请使用 `HostName` 参数指定目标计算机并通过 `UserName` 提供用户名。</span><span class="sxs-lookup"><span data-stu-id="c99fc-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="c99fc-114">当以交互方式运行 cmdlet 时，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="c99fc-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="c99fc-115">还可以通过带有 `KeyFilePath` 参数的私钥文件来使用 SSH 密钥身份验证。</span><span class="sxs-lookup"><span data-stu-id="c99fc-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="c99fc-116">常规安装信息</span><span class="sxs-lookup"><span data-stu-id="c99fc-116">General setup information</span></span>

<span data-ttu-id="c99fc-117">必须在所有计算机上安装 PowerShell 6 或更高版本，以及 SSH。</span><span class="sxs-lookup"><span data-stu-id="c99fc-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="c99fc-118">安装 SSH 客户端 (`ssh.exe`) 和服务器 (`sshd.exe`)，以便对计算机进行远程处理或从计算机进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="c99fc-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="c99fc-119">OpenSSH for Windows 现已在 Windows 10 内部版本 1809 和 Windows Server 2019 中可用。</span><span class="sxs-lookup"><span data-stu-id="c99fc-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="c99fc-120">有关详细信息，请参阅[使用 OpenSSH 管理 Windows](/windows-server/administration/openssh/openssh_overview)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="c99fc-121">对于 Linux，请安装适用于平台的 SSH（包括 sshd 服务器）。</span><span class="sxs-lookup"><span data-stu-id="c99fc-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="c99fc-122">此外，还需要从 GitHub 安装 PowerShell 以获取 SSH 远程处理功能。</span><span class="sxs-lookup"><span data-stu-id="c99fc-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="c99fc-123">必须配置 SSH 服务器以创建 SSH 子系统来托管远程计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="c99fc-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="c99fc-124">还必须启用**密码**或**基于密钥的**身份验证。</span><span class="sxs-lookup"><span data-stu-id="c99fc-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="c99fc-125">在 Windows 计算机上设置</span><span class="sxs-lookup"><span data-stu-id="c99fc-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="c99fc-126">安装最新版本的 PowerShell，请参阅[在 Windows 上安装 PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="c99fc-127">可通过列出 `New-PSSession` 参数集来确认 PowerShell 具有 SSH 远程处理支持。</span><span class="sxs-lookup"><span data-stu-id="c99fc-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="c99fc-128">你会注意到存在以 **SSH** 开头的参数集名称。</span><span class="sxs-lookup"><span data-stu-id="c99fc-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="c99fc-129">这些参数集包括 **SSH** 参数。</span><span class="sxs-lookup"><span data-stu-id="c99fc-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="c99fc-130">安装最新 Win32 OpenSSH。</span><span class="sxs-lookup"><span data-stu-id="c99fc-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="c99fc-131">有关安装说明，请参阅 [OpenSSH 入门](/windows-server/administration/openssh/openssh_install_firstuse)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="c99fc-132">如果要将 PowerShell 设置为 OpenSSH 的默认 shell，请参阅[为 OpenSSH 配置 Windows](/windows-server/administration/openssh/openssh_server_configuration)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="c99fc-133">编辑位于 `$env:ProgramData\ssh` 的 `sshd_config` 文件。</span><span class="sxs-lookup"><span data-stu-id="c99fc-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="c99fc-134">确保已启用密码身份验证：</span><span class="sxs-lookup"><span data-stu-id="c99fc-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c99fc-135">创建托管远程计算机上的 PowerShell 进程的 SSH 子系统：</span><span class="sxs-lookup"><span data-stu-id="c99fc-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="c99fc-136">对于包含空格的任何文件路径，必须使用 8.3 短名称。</span><span class="sxs-lookup"><span data-stu-id="c99fc-136">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="c99fc-137">OpenSSH for Windows 中存在一个 bug，使空格在子系统可执行路径中无效。</span><span class="sxs-lookup"><span data-stu-id="c99fc-137">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="c99fc-138">有关详细信息，请参阅此 [GitHub 问题](https://github.com/PowerShell/Win32-OpenSSH/issues/784)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-138">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="c99fc-139">Windows 中的 `Program Files` 文件夹的 8.3 短名称通常为 `Progra~1`。</span><span class="sxs-lookup"><span data-stu-id="c99fc-139">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="c99fc-140">但是，可以使用以下命令来确保：</span><span class="sxs-lookup"><span data-stu-id="c99fc-140">However, you can use the following command to make sure:</span></span>
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   <span data-ttu-id="c99fc-141">启用密钥身份验证（可选）：</span><span class="sxs-lookup"><span data-stu-id="c99fc-141">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="c99fc-142">有关详细信息，请参阅[管理 OpenSSH 密钥](/windows-server/administration/openssh/openssh_keymanagement)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-142">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="c99fc-143">重启 **sshd** 服务。</span><span class="sxs-lookup"><span data-stu-id="c99fc-143">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="c99fc-144">将 OpenSSH 的安装路径添加到 Path 环境变量。</span><span class="sxs-lookup"><span data-stu-id="c99fc-144">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="c99fc-145">例如，`C:\Program Files\OpenSSH\`。</span><span class="sxs-lookup"><span data-stu-id="c99fc-145">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="c99fc-146">通过此条目可找到 `ssh.exe`。</span><span class="sxs-lookup"><span data-stu-id="c99fc-146">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="c99fc-147">在 Ubuntu 16.04 Linux 计算机上设置</span><span class="sxs-lookup"><span data-stu-id="c99fc-147">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="c99fc-148">安装最新版本的 PowerShell，请参阅[在 Linux 上安装 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-148">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="c99fc-149">安装 [Ubuntu OpenSSH 服务器](https://help.ubuntu.com/lts/serverguide/openssh-server.html)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-149">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="c99fc-150">编辑 `/etc/ssh` 位置中的 `sshd_config` 文件。</span><span class="sxs-lookup"><span data-stu-id="c99fc-150">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="c99fc-151">确保已启用密码身份验证：</span><span class="sxs-lookup"><span data-stu-id="c99fc-151">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c99fc-152">添加 PowerShell 子系统条目：</span><span class="sxs-lookup"><span data-stu-id="c99fc-152">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="c99fc-153">启用密钥身份验证（可选）：</span><span class="sxs-lookup"><span data-stu-id="c99fc-153">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="c99fc-154">重启 **sshd** 服务。</span><span class="sxs-lookup"><span data-stu-id="c99fc-154">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="c99fc-155">在 macOS 计算机上设置</span><span class="sxs-lookup"><span data-stu-id="c99fc-155">Set up on a macOS computer</span></span>

1. <span data-ttu-id="c99fc-156">安装最新版本的 PowerShell，请参阅[在 macOS 上安装 PowerShell Core](../../install/installing-powershell-core-on-macos.md)。</span><span class="sxs-lookup"><span data-stu-id="c99fc-156">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="c99fc-157">按照以下步骤确保已启用 SSH 远程处理：</span><span class="sxs-lookup"><span data-stu-id="c99fc-157">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="c99fc-158">打开 `System Preferences`。</span><span class="sxs-lookup"><span data-stu-id="c99fc-158">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="c99fc-159">单击 `Sharing`。</span><span class="sxs-lookup"><span data-stu-id="c99fc-159">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="c99fc-160">选中 `Remote Login` 以设置 `Remote Login: On`。</span><span class="sxs-lookup"><span data-stu-id="c99fc-160">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="c99fc-161">允许相应用户访问。</span><span class="sxs-lookup"><span data-stu-id="c99fc-161">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="c99fc-162">编辑 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 文件。</span><span class="sxs-lookup"><span data-stu-id="c99fc-162">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="c99fc-163">打开文本编辑器，例如 **nano**：</span><span class="sxs-lookup"><span data-stu-id="c99fc-163">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="c99fc-164">确保已启用密码身份验证：</span><span class="sxs-lookup"><span data-stu-id="c99fc-164">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c99fc-165">添加 PowerShell 子系统条目：</span><span class="sxs-lookup"><span data-stu-id="c99fc-165">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="c99fc-166">启用密钥身份验证（可选）：</span><span class="sxs-lookup"><span data-stu-id="c99fc-166">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="c99fc-167">重启 **sshd** 服务。</span><span class="sxs-lookup"><span data-stu-id="c99fc-167">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="c99fc-168">身份验证</span><span class="sxs-lookup"><span data-stu-id="c99fc-168">Authentication</span></span>

<span data-ttu-id="c99fc-169">通过 SSH 进行 PowerShell 远程处理依赖于 SSH 客户端和 SSH 服务之间的身份验证交换，并且本身不实现任何身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="c99fc-169">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="c99fc-170">这使得任何配置的身份验证方案（包括多重身份验证）都由 SSH 处理，并且独立于 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c99fc-170">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="c99fc-171">例如，可以将 SSH 服务配置为需要公钥身份验证以及一次性密码，从而增加安全性。</span><span class="sxs-lookup"><span data-stu-id="c99fc-171">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="c99fc-172">多重身份验证的配置不在本文档的讨论范围。</span><span class="sxs-lookup"><span data-stu-id="c99fc-172">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="c99fc-173">若要了解如何正确配置多重身份验证，请参阅相关的 SSH 文档，并在尝试将其用于 PowerShell 远程处理之前先在 PowerShell 之外验证它的运行效果。</span><span class="sxs-lookup"><span data-stu-id="c99fc-173">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="c99fc-174">PowerShell 远程处理示例</span><span class="sxs-lookup"><span data-stu-id="c99fc-174">PowerShell remoting example</span></span>

<span data-ttu-id="c99fc-175">测试远程处理最简单的方法是在单个计算机上进行测试。</span><span class="sxs-lookup"><span data-stu-id="c99fc-175">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="c99fc-176">在本示例中，我们创建返回到同一 Linux 计算机上的远程会话。</span><span class="sxs-lookup"><span data-stu-id="c99fc-176">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="c99fc-177">我们交互式使用 PowerShell cmdlet，这样我们可看到 SSH 提示我们验证主机计算机并要求提供密码。</span><span class="sxs-lookup"><span data-stu-id="c99fc-177">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="c99fc-178">可以在 Windows 计算机上执行相同的操作以确保远程处理正常工作。</span><span class="sxs-lookup"><span data-stu-id="c99fc-178">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="c99fc-179">然后，通过更改主机名在计算机之间进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="c99fc-179">Then, remote between computers by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
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

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
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

### <a name="known-issues"></a><span data-ttu-id="c99fc-180">已知问题</span><span class="sxs-lookup"><span data-stu-id="c99fc-180">Known issues</span></span>

<span data-ttu-id="c99fc-181">**sudo** 命令对 Linux 计算机上的远程会话不起作用。</span><span class="sxs-lookup"><span data-stu-id="c99fc-181">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="c99fc-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c99fc-182">See also</span></span>

[<span data-ttu-id="c99fc-183">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c99fc-183">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="c99fc-184">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c99fc-184">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="c99fc-185">在 Windows 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c99fc-185">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="c99fc-186">使用 OpenSSH 管理 Windows</span><span class="sxs-lookup"><span data-stu-id="c99fc-186">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="c99fc-187">管理 OpenSSH 密钥</span><span class="sxs-lookup"><span data-stu-id="c99fc-187">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="c99fc-188">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="c99fc-188">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

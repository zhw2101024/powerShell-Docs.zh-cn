---
title: 在 Windows 上安装 PowerShell Core
description: 介绍如何在 Windows 上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293004"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="9e529-103">在 Windows 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9e529-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="9e529-104">有多种方法可以在 Windows 中安装 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="9e529-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e529-105">必备条件</span><span class="sxs-lookup"><span data-stu-id="9e529-105">Prerequisites</span></span>

<span data-ttu-id="9e529-106">若要通过 WSMan 启用 PowerShell 远程处理，需要满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="9e529-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="9e529-107">在 Windows 10 之前的 Windows 版本上安装[通用 C 运行时](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="9e529-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="9e529-108">可通过直接下载或 Windows 更新进行安装。</span><span class="sxs-lookup"><span data-stu-id="9e529-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="9e529-109">经完全修补（含可选包）且受支持的系统中已安装有通用 C 运行时。</span><span class="sxs-lookup"><span data-stu-id="9e529-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="9e529-110">在 Windows 7 和 Windows Server 2008 R2 上安装 Windows Management Framework (WMF) 4.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="9e529-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="9e529-111"><a id="msi" />安装 MSI 包</span><span class="sxs-lookup"><span data-stu-id="9e529-111"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="9e529-112">若要在 Windows 客户端或 Windows Server（适用于 Windows 7 SP1、Server 2008 R2 以及更高版本）上安装 PowerShell，请从 GitHub [版本][] 页面下载 MSI 包。</span><span class="sxs-lookup"><span data-stu-id="9e529-112">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="9e529-113">向下滚动到要安装的版本的“资产”部分。</span><span class="sxs-lookup"><span data-stu-id="9e529-113">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="9e529-114">“资产”部分可能处于折叠状态，因此可能需要单击使其展开。</span><span class="sxs-lookup"><span data-stu-id="9e529-114">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="9e529-115">MSI 文件类似于 -</span><span class="sxs-lookup"><span data-stu-id="9e529-115">The MSI file looks like this -</span></span> `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="9e529-116">下载后，双击安装程序并按照提示进行操作。</span><span class="sxs-lookup"><span data-stu-id="9e529-116">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="9e529-117">安装程序在 Windows“开始”菜单中创建一个快捷方式。</span><span class="sxs-lookup"><span data-stu-id="9e529-117">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="9e529-118">默认情况下，包安装位置为</span><span class="sxs-lookup"><span data-stu-id="9e529-118">By default the package is installed to</span></span> `$env:ProgramFiles\PowerShell\<version>`
- <span data-ttu-id="9e529-119">可以通过“开始”菜单启动 PowerShell 或</span><span class="sxs-lookup"><span data-stu-id="9e529-119">You can launch PowerShell via the Start Menu or</span></span> `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="9e529-120">通过命令行进行管理安装</span><span class="sxs-lookup"><span data-stu-id="9e529-120">Administrative install from the command line</span></span>

<span data-ttu-id="9e529-121">可以通过命令行安装 MSI 包。</span><span class="sxs-lookup"><span data-stu-id="9e529-121">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="9e529-122">这样，管理员可以部署包而无需用户交互。</span><span class="sxs-lookup"><span data-stu-id="9e529-122">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="9e529-123">适用于 PowerShell 的 MSI 包包含下列属性以控制安装选项：</span><span class="sxs-lookup"><span data-stu-id="9e529-123">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="9e529-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此属性控制向 Windows 资源管理器中的上下文菜单添加“打开 PowerShell”项的选项。</span><span class="sxs-lookup"><span data-stu-id="9e529-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="9e529-125">**ENABLE_PSREMOTING** - 此属性控制用于在安装过程中启用 PowerShell 远程处理的选项。</span><span class="sxs-lookup"><span data-stu-id="9e529-125">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="9e529-126">**REGISTER_MANIFEST** - 此属性控制用于注册 Windows 事件日志记录清单的选项。</span><span class="sxs-lookup"><span data-stu-id="9e529-126">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="9e529-127">下面的示例演示如何在启用所有安装选项的情况下以无提示方式安装 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="9e529-127">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="9e529-128">有关 Msiexec.exe 命令行选项的完整列表，请参阅[命令行选项](/windows/desktop/Msi/command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="9e529-128">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="9e529-129"><a id="zip" />安装 ZIP 包</span><span class="sxs-lookup"><span data-stu-id="9e529-129"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="9e529-130">提供有 PowerShell 二进制 ZIP 存档，从而支持高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="9e529-130">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="9e529-131">请注意，使用 ZIP 存档时，不同于使用 MSI，你无法获取 MSI 先决条件检查。</span><span class="sxs-lookup"><span data-stu-id="9e529-131">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="9e529-132">要使通过 WSMan 的远程处理正常工作，请确保满足[先决条件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="9e529-132">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="9e529-133">在 Windows IoT 上部署</span><span class="sxs-lookup"><span data-stu-id="9e529-133">Deploying on Windows IoT</span></span>

<span data-ttu-id="9e529-134">Windows IoT 已经附带了 Windows PowerShell，我们将使用它来部署 PowerShell Core 6。</span><span class="sxs-lookup"><span data-stu-id="9e529-134">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="9e529-135">在目标设备中创建 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="9e529-135">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="9e529-136">将 ZIP 包复制到设备</span><span class="sxs-lookup"><span data-stu-id="9e529-136">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="9e529-137">连接到设备并展开存档</span><span class="sxs-lookup"><span data-stu-id="9e529-137">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="9e529-138">在 PowerShell Core 6 中设置远程处理</span><span class="sxs-lookup"><span data-stu-id="9e529-138">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="9e529-139">连接到设备上的 PowerShell Core 6 终结点</span><span class="sxs-lookup"><span data-stu-id="9e529-139">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="9e529-140">在 Nano Server 上进行部署</span><span class="sxs-lookup"><span data-stu-id="9e529-140">Deploying on Nano Server</span></span>

<span data-ttu-id="9e529-141">这些说明假定某个 PowerShell 版本已在 Nano Server 映像上运行，并且其已经由 [Nano Server 映像生成器](/windows-server/get-started/deploy-nano-server)生成。</span><span class="sxs-lookup"><span data-stu-id="9e529-141">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="9e529-142">Nano Server 是“无外设”OS。</span><span class="sxs-lookup"><span data-stu-id="9e529-142">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="9e529-143">可以使用两种不同的方法部署核心二进制文件。</span><span class="sxs-lookup"><span data-stu-id="9e529-143">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="9e529-144">脱机 - 安装 Nano Server VHD，并将 zip 文件的内容解压到安装映像中的所选位置。</span><span class="sxs-lookup"><span data-stu-id="9e529-144">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="9e529-145">联机 - 通过 PowerShell 会话传输 zip 文件，并在所需位置中将其解压。</span><span class="sxs-lookup"><span data-stu-id="9e529-145">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="9e529-146">这两种情况下皆需要 Windows 10 x64 ZIP 发布包，且需要在“管理员”PowerShell 实例中运行命令。</span><span class="sxs-lookup"><span data-stu-id="9e529-146">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="9e529-147">PowerShell Core 脱机部署</span><span class="sxs-lookup"><span data-stu-id="9e529-147">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="9e529-148">使用常用 zip 实用工具将包解压到已安装的 Nano Server 映像中的目录。</span><span class="sxs-lookup"><span data-stu-id="9e529-148">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="9e529-149">卸载映像并启动。</span><span class="sxs-lookup"><span data-stu-id="9e529-149">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="9e529-150">连接到 Windows PowerShell 的收件箱实例。</span><span class="sxs-lookup"><span data-stu-id="9e529-150">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="9e529-151">按照说明使用[“另一种实例技术”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="9e529-151">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="9e529-152">PowerShell Core 联机部署</span><span class="sxs-lookup"><span data-stu-id="9e529-152">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="9e529-153">以下步骤将指导你向 Nano Server 运行实例部署 PowerShell Core，并配置其远程终结点。</span><span class="sxs-lookup"><span data-stu-id="9e529-153">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="9e529-154">连接到 Windows PowerShell 的收件箱实例</span><span class="sxs-lookup"><span data-stu-id="9e529-154">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="9e529-155">将文件复制到 Nano Server 实例</span><span class="sxs-lookup"><span data-stu-id="9e529-155">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="9e529-156">输入会话</span><span class="sxs-lookup"><span data-stu-id="9e529-156">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="9e529-157">提取 ZIP 文件</span><span class="sxs-lookup"><span data-stu-id="9e529-157">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="9e529-158">如果需要基于 WSMan 的远程处理，请按照说明使用[“另一种实例技术”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="9e529-158">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="9e529-159">如何创建远程处理终结点</span><span class="sxs-lookup"><span data-stu-id="9e529-159">How to create a remoting endpoint</span></span>

<span data-ttu-id="9e529-160">PowerShell Core 同时支持采用 WSMan 和 SSH 的 PowerShell 远程处理协议 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="9e529-160">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="9e529-161">有关更多信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="9e529-161">For more information, see:</span></span>

- <span data-ttu-id="9e529-162">[SSH Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="9e529-162">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="9e529-163">[PowerShell Core 中的 WSMan 远程处理][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="9e529-163">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
<span data-ttu-id="9e529-164">[版本]： https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span><span class="sxs-lookup"><span data-stu-id="9e529-164">[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span></span>

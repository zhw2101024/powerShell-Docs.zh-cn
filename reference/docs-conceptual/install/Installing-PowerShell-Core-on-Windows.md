---
title: 在 Windows 上安装 PowerShell Core
description: 介绍如何在 Windows 上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748955"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="bc9aa-103">在 Windows 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="bc9aa-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="bc9aa-104">MSI</span><span class="sxs-lookup"><span data-stu-id="bc9aa-104">MSI</span></span>

<span data-ttu-id="bc9aa-105">若要在 Windows 客户端或 Windows Server（适用于 Windows 7 SP1、Server 2008 R2 以及更高版本）上安装 PowerShell，请从 GitHub [版本][]页面下载 MSI 包。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="bc9aa-106">向下滚动到要安装的版本的“资产”部分。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="bc9aa-107">“资产”部分可能处于折叠状态，因此可能需要单击使其展开。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="bc9aa-108">MSI 文件类似于 `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="bc9aa-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="bc9aa-109">下载后，双击安装程序并按照提示进行操作。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="bc9aa-110">安装后会向“开始”菜单添加快捷方式。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="bc9aa-111">默认情况下，包安装位置为 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="bc9aa-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="bc9aa-112">可以通过“开始”菜单或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 启动 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc9aa-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="bc9aa-113">必备条件</span><span class="sxs-lookup"><span data-stu-id="bc9aa-113">Prerequisites</span></span>

<span data-ttu-id="bc9aa-114">若要通过 WSMan 启用 PowerShell 远程处理，需要满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="bc9aa-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="bc9aa-115">在 Windows 10 之前的 Windows 版本上安装[通用 C 运行时](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="bc9aa-116">可通过直接下载或 Windows 更新进行安装。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="bc9aa-117">经完全修补（含可选包）且受支持的系统中已安装有通用 C 运行时。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="bc9aa-118">在 Windows 7 和 Windows Server 2008 R2 上安装 Windows Management Framework (WMF) 4.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="bc9aa-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="bc9aa-119">ZIP</span></span>

<span data-ttu-id="bc9aa-120">提供有 PowerShell 二进制 ZIP 存档，从而支持高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="bc9aa-121">请注意，使用 ZIP 存档时，不同于使用 MSI，你无法获取 MSI 先决条件检查。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="bc9aa-122">因此，为使通过 WSMan 进行的远程处理可在低于 Windows 10 的 Windows 版本上正常运行，则需确保满足[先决条件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="bc9aa-123">在 Windows IoT 上部署</span><span class="sxs-lookup"><span data-stu-id="bc9aa-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="bc9aa-124">Windows IoT 已经附带了 Windows PowerShell，我们将使用它来部署 PowerShell Core 6。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="bc9aa-125">在目标设备中创建 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="bc9aa-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="bc9aa-126">将 ZIP 包复制到设备</span><span class="sxs-lookup"><span data-stu-id="bc9aa-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="bc9aa-127">连接到设备并展开存档</span><span class="sxs-lookup"><span data-stu-id="bc9aa-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="bc9aa-128">在 PowerShell Core 6 中设置远程处理</span><span class="sxs-lookup"><span data-stu-id="bc9aa-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="bc9aa-129">连接到设备上的 PowerShell Core 6 终结点</span><span class="sxs-lookup"><span data-stu-id="bc9aa-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="bc9aa-130">在 Nano Server 上进行部署</span><span class="sxs-lookup"><span data-stu-id="bc9aa-130">Deploying on Nano Server</span></span>

<span data-ttu-id="bc9aa-131">这些说明假定某个 PowerShell 版本已在 Nano Server 映像上运行，并且其已经由 [Nano Server 映像生成器](/windows-server/get-started/deploy-nano-server)生成。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="bc9aa-132">Nano Server 是“无外设”OS。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="bc9aa-133">可以使用两种不同的方法部署核心二进制文件。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="bc9aa-134">脱机 - 安装 Nano Server VHD，并将 zip 文件的内容解压到安装映像中的所选位置。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="bc9aa-135">联机 - 通过 PowerShell 会话传输 zip 文件，并在所需位置中将其解压。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="bc9aa-136">这两种情况下皆需要 Windows 10 x64 ZIP 发布包，且需要在“管理员”PowerShell 实例中运行命令。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="bc9aa-137">PowerShell Core 脱机部署</span><span class="sxs-lookup"><span data-stu-id="bc9aa-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="bc9aa-138">使用常用 zip 实用工具将包解压到已安装的 Nano Server 映像中的目录。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="bc9aa-139">卸载映像并启动。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="bc9aa-140">连接到 Windows PowerShell 的收件箱实例。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="bc9aa-141">按照说明使用[“另一种实例技术”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="bc9aa-142">PowerShell Core 联机部署</span><span class="sxs-lookup"><span data-stu-id="bc9aa-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="bc9aa-143">以下步骤将指导你向 Nano Server 运行实例部署 PowerShell Core，并配置其远程终结点。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="bc9aa-144">连接到 Windows PowerShell 的收件箱实例</span><span class="sxs-lookup"><span data-stu-id="bc9aa-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="bc9aa-145">将文件复制到 Nano Server 实例</span><span class="sxs-lookup"><span data-stu-id="bc9aa-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="bc9aa-146">输入会话</span><span class="sxs-lookup"><span data-stu-id="bc9aa-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="bc9aa-147">提取 ZIP 文件</span><span class="sxs-lookup"><span data-stu-id="bc9aa-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="bc9aa-148">如果需要基于 WSMan 的远程处理，请按照说明使用[“另一种实例技术”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="bc9aa-149">有关创建远程处理终结点的说明</span><span class="sxs-lookup"><span data-stu-id="bc9aa-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="bc9aa-150">PowerShell Core 同时支持采用 WSMan 和 SSH 的 PowerShell 远程处理协议 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="bc9aa-151">有关更多信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="bc9aa-151">For more information, see:</span></span>

- <span data-ttu-id="bc9aa-152">[在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="bc9aa-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="bc9aa-153">[在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="bc9aa-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="bc9aa-154">项目安装说明</span><span class="sxs-lookup"><span data-stu-id="bc9aa-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="bc9aa-155">我们使用 [AppVeyor][] 在每个 CI 版本上发布具有 CoreCLR 位的存档。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="bc9aa-156">若要从 CoreCLR 项目中安装 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="bc9aa-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="bc9aa-157">从特定版本的“项目”选项卡下载 ZIP 包。</span><span class="sxs-lookup"><span data-stu-id="bc9aa-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="bc9aa-158">解除阻止 ZIP 文件：右键单击“文件资源管理器”->“属性”->“选中‘解除阻止’框”->“应用”</span><span class="sxs-lookup"><span data-stu-id="bc9aa-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="bc9aa-159">将 zip 文件解压到 `bin` 目录</span><span class="sxs-lookup"><span data-stu-id="bc9aa-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[版本]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell

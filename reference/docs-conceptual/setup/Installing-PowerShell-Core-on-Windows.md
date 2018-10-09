---
title: 在 Windows 上安装 PowerShell Core
description: 介绍如何在 Windows 上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2b21908c38796117308f2ac1219db00ff9086408
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850973"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="1c788-103">在 Windows 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="1c788-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="1c788-104">MSI</span><span class="sxs-lookup"><span data-stu-id="1c788-104">MSI</span></span>

<span data-ttu-id="1c788-105">若要在 Windows 客户端或 Windows Server（适用于 Windows 7 SP1、Server 2008 R2 以及更高版本）上安装 PowerShell，请从 GitHub [版本][]页面下载 MSI 包。</span><span class="sxs-lookup"><span data-stu-id="1c788-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="1c788-106">MSI 文件类似于 `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="1c788-106">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="1c788-107">下载后，双击安装程序并按照提示进行操作。</span><span class="sxs-lookup"><span data-stu-id="1c788-107">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="1c788-108">安装后会向“开始”菜单添加快捷方式。</span><span class="sxs-lookup"><span data-stu-id="1c788-108">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="1c788-109">默认情况下，包安装位置为 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="1c788-109">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="1c788-110">可以通过“开始”菜单或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 启动 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c788-110">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1c788-111">必备条件</span><span class="sxs-lookup"><span data-stu-id="1c788-111">Prerequisites</span></span>

<span data-ttu-id="1c788-112">若要通过 WSMan 启用 PowerShell 远程处理，需要满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="1c788-112">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="1c788-113">在 Windows 10 之前的 Windows 版本上安装[通用 C 运行时](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="1c788-113">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="1c788-114">可通过直接下载或 Windows 更新进行安装。</span><span class="sxs-lookup"><span data-stu-id="1c788-114">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="1c788-115">经完全修补（含可选包）且受支持的系统中已安装有通用 C 运行时。</span><span class="sxs-lookup"><span data-stu-id="1c788-115">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="1c788-116">在 Windows 7 和 Windows Server 2008 R2 上安装 Windows Management Framework (WMF) 4.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="1c788-116">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="1c788-117">ZIP</span><span class="sxs-lookup"><span data-stu-id="1c788-117">ZIP</span></span>

<span data-ttu-id="1c788-118">提供有 PowerShell 二进制 ZIP 存档，从而支持高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="1c788-118">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="1c788-119">请注意，使用 ZIP 存档时，不同于使用 MSI，你无法获取 MSI 先决条件检查。</span><span class="sxs-lookup"><span data-stu-id="1c788-119">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="1c788-120">因此，为使通过 WSMan 进行的远程处理可在低于 Windows 10 的 Windows 版本上正常运行，则需确保满足[先决条件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="1c788-120">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="1c788-121">在 Windows IoT 上部署</span><span class="sxs-lookup"><span data-stu-id="1c788-121">Deploying on Windows IoT</span></span>

<span data-ttu-id="1c788-122">Windows IoT 已经附带了 Windows PowerShell，我们将使用它来部署 PowerShell Core 6。</span><span class="sxs-lookup"><span data-stu-id="1c788-122">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="1c788-123">在目标设备中创建 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="1c788-123">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="1c788-124">将 ZIP 包复制到设备</span><span class="sxs-lookup"><span data-stu-id="1c788-124">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="1c788-125">连接到设备并展开存档</span><span class="sxs-lookup"><span data-stu-id="1c788-125">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. <span data-ttu-id="1c788-126">在 PowerShell Core 6 中设置远程处理</span><span class="sxs-lookup"><span data-stu-id="1c788-126">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="1c788-127">连接到设备上的 PowerShell Core 6 终结点</span><span class="sxs-lookup"><span data-stu-id="1c788-127">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="1c788-128">在 Nano Server 上进行部署</span><span class="sxs-lookup"><span data-stu-id="1c788-128">Deploying on Nano Server</span></span>

<span data-ttu-id="1c788-129">这些说明假定某个 PowerShell 版本已在 Nano Server 映像上运行，并且其已经由 [Nano Server 映像生成器](/windows-server/get-started/deploy-nano-server)生成。</span><span class="sxs-lookup"><span data-stu-id="1c788-129">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="1c788-130">Nano Server 是“无外设”OS。</span><span class="sxs-lookup"><span data-stu-id="1c788-130">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="1c788-131">可以使用两种不同的方法部署核心二进制文件。</span><span class="sxs-lookup"><span data-stu-id="1c788-131">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="1c788-132">脱机 - 安装 Nano Server VHD，并将 zip 文件的内容解压到安装映像中的所选位置。</span><span class="sxs-lookup"><span data-stu-id="1c788-132">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="1c788-133">联机 - 通过 PowerShell 会话传输 zip 文件，并在所需位置中将其解压。</span><span class="sxs-lookup"><span data-stu-id="1c788-133">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="1c788-134">这两种情况下皆需要 Windows 10 x64 ZIP 发布包，且需要在“管理员”PowerShell 实例中运行命令。</span><span class="sxs-lookup"><span data-stu-id="1c788-134">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="1c788-135">PowerShell Core 脱机部署</span><span class="sxs-lookup"><span data-stu-id="1c788-135">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="1c788-136">使用常用 zip 实用工具将包解压到已安装的 Nano Server 映像中的目录。</span><span class="sxs-lookup"><span data-stu-id="1c788-136">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="1c788-137">卸载映像并启动。</span><span class="sxs-lookup"><span data-stu-id="1c788-137">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="1c788-138">连接到 Windows PowerShell 的收件箱实例。</span><span class="sxs-lookup"><span data-stu-id="1c788-138">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="1c788-139">按照说明使用[“另一种实例技术”](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="1c788-139">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="1c788-140">PowerShell Core 联机部署</span><span class="sxs-lookup"><span data-stu-id="1c788-140">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="1c788-141">以下步骤将指导你向 Nano Server 运行实例部署 PowerShell Core，并配置其远程终结点。</span><span class="sxs-lookup"><span data-stu-id="1c788-141">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="1c788-142">连接到 Windows PowerShell 的收件箱实例</span><span class="sxs-lookup"><span data-stu-id="1c788-142">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="1c788-143">将文件复制到 Nano Server 实例</span><span class="sxs-lookup"><span data-stu-id="1c788-143">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="1c788-144">输入会话</span><span class="sxs-lookup"><span data-stu-id="1c788-144">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="1c788-145">提取 ZIP 文件</span><span class="sxs-lookup"><span data-stu-id="1c788-145">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="1c788-146">如果需要基于 WSMan 的远程处理，请按照说明使用[“另一种实例技术”](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="1c788-146">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="1c788-147">有关创建远程处理终结点的说明</span><span class="sxs-lookup"><span data-stu-id="1c788-147">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="1c788-148">PowerShell Core 同时支持采用 WSMan 和 SSH 的 PowerShell 远程处理协议 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="1c788-148">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="1c788-149">有关更多信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="1c788-149">For more information, see:</span></span>

- <span data-ttu-id="1c788-150">[在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="1c788-150">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="1c788-151">[在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="1c788-151">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="1c788-152">项目安装说明</span><span class="sxs-lookup"><span data-stu-id="1c788-152">Artifact Installation Instructions</span></span>

<span data-ttu-id="1c788-153">我们使用 [AppVeyor][] 在每个 CI 版本上发布具有 CoreCLR 位的存档。</span><span class="sxs-lookup"><span data-stu-id="1c788-153">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="1c788-154">若要从 CoreCLR 项目中安装 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="1c788-154">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="1c788-155">从特定版本的“项目”选项卡下载 ZIP 包。</span><span class="sxs-lookup"><span data-stu-id="1c788-155">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="1c788-156">解除阻止 ZIP 文件：右键单击“文件资源管理器”->“属性”->“选中‘解除阻止’框”->“应用”</span><span class="sxs-lookup"><span data-stu-id="1c788-156">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="1c788-157">将 zip 文件解压到 `bin` 目录</span><span class="sxs-lookup"><span data-stu-id="1c788-157">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[版本]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell

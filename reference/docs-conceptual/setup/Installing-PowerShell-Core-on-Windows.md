# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="952d4-101">在 Windows 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="952d4-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="952d4-102">MSI</span><span class="sxs-lookup"><span data-stu-id="952d4-102">MSI</span></span>

<span data-ttu-id="952d4-103">若要在 Windows 客户端或 Windows Server（适用于 Windows 7 SP1、Server 2008 R2 以及更高版本）上安装 PowerShell，请从 GitHub [版本][]页面下载 MSI 包。</span><span class="sxs-lookup"><span data-stu-id="952d4-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="952d4-104">MSI 文件类似于 `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="952d4-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="952d4-105">下载后，双击安装程序并按照提示进行操作。</span><span class="sxs-lookup"><span data-stu-id="952d4-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="952d4-106">安装后会向“开始”菜单添加快捷方式。</span><span class="sxs-lookup"><span data-stu-id="952d4-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="952d4-107">默认情况下，包安装位置为 `$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="952d4-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="952d4-108">可以通过“开始”菜单或 `$env:ProgramFiles\PowerShell\pwsh.exe` 启动 PowerShell</span><span class="sxs-lookup"><span data-stu-id="952d4-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="952d4-109">必备条件</span><span class="sxs-lookup"><span data-stu-id="952d4-109">Prerequisites</span></span>

<span data-ttu-id="952d4-110">若要通过 WSMan 启用 PowerShell 远程处理，需要满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="952d4-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="952d4-111">在 Windows 10 之前的 Windows 版本上安装[通用 C 运行时](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="952d4-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="952d4-112">可通过直接下载或 Windows 更新进行安装。</span><span class="sxs-lookup"><span data-stu-id="952d4-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="952d4-113">经完全修补（含可选包）且受支持的系统中已安装有通用 C 运行时。</span><span class="sxs-lookup"><span data-stu-id="952d4-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="952d4-114">在 Windows 7 和 Windows Server 2008 R2 上安装 Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) 或更高版本([5.1](https://www.microsoft.com/download/details.aspx?id=54616))。</span><span class="sxs-lookup"><span data-stu-id="952d4-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="952d4-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="952d4-115">ZIP</span></span>

<span data-ttu-id="952d4-116">提供有 PowerShell 二进制 ZIP 存档，从而支持高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="952d4-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="952d4-117">请注意，使用 ZIP 存档时，不同于使用 MSI，你无法获取 MSI 先决条件检查。</span><span class="sxs-lookup"><span data-stu-id="952d4-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="952d4-118">因此，为使通过 WSMan 进行的远程处理可在低于 Windows 10 的 Windows 版本上正常运行，则需确保满足[先决条件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="952d4-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="952d4-119">在 Nano Server 上进行部署</span><span class="sxs-lookup"><span data-stu-id="952d4-119">Deploying on Nano Server</span></span>

<span data-ttu-id="952d4-120">这些说明假定某个 PowerShell 版本已在 Nano Server 映像上运行，并且其已经由 [Nano Server 映像生成器](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server)生成。</span><span class="sxs-lookup"><span data-stu-id="952d4-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="952d4-121">Nano Server 是“无外设”操作系统，PowerShell Core 二进制文件部署可以两种不同的方式进行：</span><span class="sxs-lookup"><span data-stu-id="952d4-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="952d4-122">脱机 - 安装 Nano Server VHD，并将 zip 文件的内容解压到安装映像中的所选位置。</span><span class="sxs-lookup"><span data-stu-id="952d4-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="952d4-123">联机 - 通过 PowerShell 会话传输 zip 文件，并在所需位置中将其解压。</span><span class="sxs-lookup"><span data-stu-id="952d4-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="952d4-124">这两种情况下皆需要 Windows 10 x64 Zip 发布包，且需要在“管理员”PowerShell 实例中运行命令。</span><span class="sxs-lookup"><span data-stu-id="952d4-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="952d4-125">PowerShell Core 脱机部署</span><span class="sxs-lookup"><span data-stu-id="952d4-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="952d4-126">使用常用 zip 实用工具将包解压到已安装的 Nano Server 映像中的目录。</span><span class="sxs-lookup"><span data-stu-id="952d4-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="952d4-127">卸载映像并启动。</span><span class="sxs-lookup"><span data-stu-id="952d4-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="952d4-128">连接到 Windows PowerShell 的收件箱实例。</span><span class="sxs-lookup"><span data-stu-id="952d4-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="952d4-129">按照说明使用[另一种实例技术](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="952d4-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="952d4-130">PowerShell Core 联机部署</span><span class="sxs-lookup"><span data-stu-id="952d4-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="952d4-131">以下步骤将指导将 PowerShell Core 部署到 Nano Server 运行的实例及其远程终结点的配置。</span><span class="sxs-lookup"><span data-stu-id="952d4-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="952d4-132">连接到 Windows PowerShell 的收件箱实例</span><span class="sxs-lookup"><span data-stu-id="952d4-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="952d4-133">将文件复制到 Nano Server 实例</span><span class="sxs-lookup"><span data-stu-id="952d4-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="952d4-134">输入会话</span><span class="sxs-lookup"><span data-stu-id="952d4-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="952d4-135">提取 Zip 文件</span><span class="sxs-lookup"><span data-stu-id="952d4-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="952d4-136">如果需要基于 WSMan 的远程处理，请按照说明使用[另一种实例技术](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="952d4-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="952d4-137">有关创建远程处理终结点的说明</span><span class="sxs-lookup"><span data-stu-id="952d4-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="952d4-138">PowerShell Core 同时支持采用 WSMan 和 SSH 的 PowerShell 远程处理协议 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="952d4-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="952d4-139">有关更多信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="952d4-139">For more information, see:</span></span>

* <span data-ttu-id="952d4-140">[在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="952d4-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="952d4-141">[在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="952d4-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="952d4-142">项目安装说明</span><span class="sxs-lookup"><span data-stu-id="952d4-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="952d4-143">我们使用 [AppVeyor][] 在每个 CI 版本上发布具有 CoreCLR 位的存档。</span><span class="sxs-lookup"><span data-stu-id="952d4-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="952d4-144">CoreCLR 项目</span><span class="sxs-lookup"><span data-stu-id="952d4-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="952d4-145">从特定版本的“项目”选项卡下载 zip 包。</span><span class="sxs-lookup"><span data-stu-id="952d4-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="952d4-146">解除阻止 zip 文件：右键单击“文件资源管理器”->“属性”->“检查‘解除阻止’框”->“应用”</span><span class="sxs-lookup"><span data-stu-id="952d4-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="952d4-147">将 zip 文件解压到 `bin` 目录</span><span class="sxs-lookup"><span data-stu-id="952d4-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[版本]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
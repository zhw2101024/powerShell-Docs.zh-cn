---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 Desired State Configuration (DSC) 入门
ms.openlocfilehash: a18b226d4b2d8b8e1ba8b4168ec6ad8f73c73c42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079684"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="f8264-103">适用于 Linux 的 Desired State Configuration (DSC) 入门</span><span class="sxs-lookup"><span data-stu-id="f8264-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="f8264-104">本主题说明如何开始使用适用于 Linux 的 PowerShell Desired State Configuration (DSC)。</span><span class="sxs-lookup"><span data-stu-id="f8264-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="f8264-105">有关 DSC 的常规信息，请参阅 [Windows PowerShell Desired State Configuration 入门](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f8264-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="f8264-106">支持的 Linux 操作系统版本</span><span class="sxs-lookup"><span data-stu-id="f8264-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="f8264-107">适用于 Linux 的 DSC 支持以下 Linux 操作系统版本。</span><span class="sxs-lookup"><span data-stu-id="f8264-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="f8264-108">CentOS 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="f8264-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="f8264-109">Debian GNU/Linux 6、7 和 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="f8264-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="f8264-110">Oracle Linux 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="f8264-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="f8264-111">Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="f8264-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="f8264-112">SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="f8264-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="f8264-113">Ubuntu Server 12.04 LTS、14.04 LTS 和 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="f8264-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="f8264-114">下表说明了适用于 Linux 的 DSC 所需的程序包依赖项。</span><span class="sxs-lookup"><span data-stu-id="f8264-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="f8264-115">所需程序包</span><span class="sxs-lookup"><span data-stu-id="f8264-115">Required package</span></span> |  <span data-ttu-id="f8264-116">说明</span><span class="sxs-lookup"><span data-stu-id="f8264-116">Description</span></span> |  <span data-ttu-id="f8264-117">最低版本</span><span class="sxs-lookup"><span data-stu-id="f8264-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="f8264-118">glibc</span><span class="sxs-lookup"><span data-stu-id="f8264-118">glibc</span></span>| <span data-ttu-id="f8264-119">GNU 库</span><span class="sxs-lookup"><span data-stu-id="f8264-119">GNU Library</span></span>| <span data-ttu-id="f8264-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="f8264-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="f8264-121">python</span><span class="sxs-lookup"><span data-stu-id="f8264-121">python</span></span>| <span data-ttu-id="f8264-122">Python</span><span class="sxs-lookup"><span data-stu-id="f8264-122">Python</span></span>| <span data-ttu-id="f8264-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="f8264-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="f8264-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="f8264-124">omiserver</span></span>| <span data-ttu-id="f8264-125">开放式管理基础结构</span><span class="sxs-lookup"><span data-stu-id="f8264-125">Open Management Infrastructure</span></span>| <span data-ttu-id="f8264-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="f8264-126">1.0.8.1</span></span>|
| <span data-ttu-id="f8264-127">openssl</span><span class="sxs-lookup"><span data-stu-id="f8264-127">openssl</span></span>| <span data-ttu-id="f8264-128">OpenSSL 库</span><span class="sxs-lookup"><span data-stu-id="f8264-128">OpenSSL Libraries</span></span>| <span data-ttu-id="f8264-129">0.9.8 或 1.0</span><span class="sxs-lookup"><span data-stu-id="f8264-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="f8264-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="f8264-130">ctypes</span></span>| <span data-ttu-id="f8264-131">Python CTypes 库</span><span class="sxs-lookup"><span data-stu-id="f8264-131">Python CTypes library</span></span>| <span data-ttu-id="f8264-132">必须与 Python 版本匹配</span><span class="sxs-lookup"><span data-stu-id="f8264-132">Must match Python version</span></span>|
| <span data-ttu-id="f8264-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="f8264-133">libcurl</span></span>| <span data-ttu-id="f8264-134">cURL http 客户端库</span><span class="sxs-lookup"><span data-stu-id="f8264-134">cURL http client library</span></span>| <span data-ttu-id="f8264-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="f8264-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="f8264-136">安装适用于 Linux 的 DSC</span><span class="sxs-lookup"><span data-stu-id="f8264-136">Installing DSC for Linux</span></span>

<span data-ttu-id="f8264-137">必须先安装[开放式管理基础结构 (OMI)](https://github.com/Microsoft/omi)，才能安装适用于 Linux 的 DSC。</span><span class="sxs-lookup"><span data-stu-id="f8264-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="f8264-138">安装 OMI</span><span class="sxs-lookup"><span data-stu-id="f8264-138">Installing OMI</span></span>

<span data-ttu-id="f8264-139">适用于 Linux 的 Desired State Configuration 需要开放式管理基础结构 (OMI) CIM 服务器版本 1.0.8.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f8264-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="f8264-140">可以从国际开放标准组织下载 OMI：[开放式管理基础结构 (OMI)](https://github.com/Microsoft/omi)。</span><span class="sxs-lookup"><span data-stu-id="f8264-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="f8264-141">若要安装 OMI，请安装适用于 Linux 系统（.rpm 或.deb）和 OpenSSL 版本（ssl_098 或 ssl_100）以及体系结构 (x64/x86) 的程序包。</span><span class="sxs-lookup"><span data-stu-id="f8264-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="f8264-142">RPM 程序包适用于 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="f8264-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="f8264-143">DEB 程序包适用于 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="f8264-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="f8264-144">ssl_098 程序包适用于安装了 OpenSSL 0.9.8 的计算机，而 ssl_100 程序包适用于安装了 OpenSSL 1.0 的计算机。</span><span class="sxs-lookup"><span data-stu-id="f8264-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="f8264-145">若要确定安装的 OpenSSL 版本，请运行 `openssl version` 命令。</span><span class="sxs-lookup"><span data-stu-id="f8264-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="f8264-146">运行以下命令以在 CentOS 7 x64 系统上安装 OMI。</span><span class="sxs-lookup"><span data-stu-id="f8264-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="f8264-147">安装 DSC</span><span class="sxs-lookup"><span data-stu-id="f8264-147">Installing DSC</span></span>

<span data-ttu-id="f8264-148">适用于 Linux 的 DSC 可在[此处](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294)下载。</span><span class="sxs-lookup"><span data-stu-id="f8264-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="f8264-149">若要安装 DSC，请安装适用于 Linux 系统（.rpm 或.deb）和 OpenSSL 版本（ssl_098 或 ssl_100）以及体系结构 (x64/x86) 的程序包。</span><span class="sxs-lookup"><span data-stu-id="f8264-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="f8264-150">RPM 程序包适用于 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="f8264-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="f8264-151">DEB 程序包适用于 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="f8264-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="f8264-152">ssl_098 程序包适用于安装了 OpenSSL 0.9.8 的计算机，而 ssl_100 程序包适用于安装了 OpenSSL 1.0 的计算机。</span><span class="sxs-lookup"><span data-stu-id="f8264-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="f8264-153">若要确定安装的 OpenSSL 版本，请运行 openssl version 命令。</span><span class="sxs-lookup"><span data-stu-id="f8264-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="f8264-154">运行以下命令以在 CentOS 7 x64 系统上安装 DSC。</span><span class="sxs-lookup"><span data-stu-id="f8264-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="f8264-155">使用适用于 Linux 的 DSC</span><span class="sxs-lookup"><span data-stu-id="f8264-155">Using DSC for Linux</span></span>

<span data-ttu-id="f8264-156">以下章节说明了如何在 Linux 计算机上创建和运行 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="f8264-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="f8264-157">创建配置 MOF 文档</span><span class="sxs-lookup"><span data-stu-id="f8264-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="f8264-158">使用 Windows PowerShell Configuration 关键字为 Linux 计算机创建配置，与为 Windows 计算机创建配置类似。</span><span class="sxs-lookup"><span data-stu-id="f8264-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="f8264-159">以下步骤描述了如何使用 Windows PowerShell 为 Linux 计算机创建配置文档。</span><span class="sxs-lookup"><span data-stu-id="f8264-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="f8264-160">导入 nx 模块。</span><span class="sxs-lookup"><span data-stu-id="f8264-160">Import the nx module.</span></span> <span data-ttu-id="f8264-161">此 nx Windows PowerShell 模块包含适用于 Linux 的 DSC 内置资源的架构，必须将其安装到本地计算机上并导入到配置中。</span><span class="sxs-lookup"><span data-stu-id="f8264-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="f8264-162">若要安装 nx 模块，请将 nx 模块目录复制到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules` 中。</span><span class="sxs-lookup"><span data-stu-id="f8264-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="f8264-163">该 nx 模块包含在适用于 Linux 的 DSC 安装包中。</span><span class="sxs-lookup"><span data-stu-id="f8264-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="f8264-164">若要在配置中导入 nx 模块，请使用 `Import-DSCResource` 命令：</span><span class="sxs-lookup"><span data-stu-id="f8264-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="f8264-165">定义配置并生成配置文档：</span><span class="sxs-lookup"><span data-stu-id="f8264-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="f8264-166">将配置推送到 Linux 计算机</span><span class="sxs-lookup"><span data-stu-id="f8264-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="f8264-167">可使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将配置文档（MOF 文件）推送到 Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="f8264-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="f8264-168">若要将此 cmdlet 和 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) 或 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlet 远程运用到 Linux 计算机，必须使用 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="f8264-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="f8264-169">使用 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet 将 CIMSession 创建到 Linux 计算机中。</span><span class="sxs-lookup"><span data-stu-id="f8264-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="f8264-170">以下代码表明了如何创建适用于 Linux 的 DSC CIMSession。</span><span class="sxs-lookup"><span data-stu-id="f8264-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="f8264-171">对于“推送”模式，用户凭据必须是 Linux 计算机上的根用户。</span><span class="sxs-lookup"><span data-stu-id="f8264-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="f8264-172">适用于 Linux 的 DSC 仅支持 SSL/TLS 连接，使用 `New-CimSession` 时必须将 –UseSSL 参数设置为 $true。</span><span class="sxs-lookup"><span data-stu-id="f8264-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="f8264-173">在 `/opt/omi/etc/omiserver.conf` 文件中通过 pemfile 和 keyfile 属性指定（DSC 的）OMI 使用的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="f8264-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="f8264-174">如果 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet 运行于的 Windows 计算机不信任此证书，你可以通过以下 CIMSession 选项选择忽略证书验证：`-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`。</span><span class="sxs-lookup"><span data-stu-id="f8264-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="f8264-175">运行以下命令以将 DSC 配置推送到 Linux 节点。</span><span class="sxs-lookup"><span data-stu-id="f8264-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="f8264-176">使用请求服务器分发配置</span><span class="sxs-lookup"><span data-stu-id="f8264-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="f8264-177">可使用请求服务器将配置分发到 Linux 计算机，与分发到 Windows 计算机类似。</span><span class="sxs-lookup"><span data-stu-id="f8264-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="f8264-178">有关使用请求服务器的指南，请参阅 [Windows PowerShell Desired State Configuration 请求服务器](../pull-server/pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="f8264-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="f8264-179">有关通过请求服务器使用 Linux 计算机其他信息和限制条件，请参阅“适用于 Linux 的 Desired State Configuration 发行说明”。</span><span class="sxs-lookup"><span data-stu-id="f8264-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="f8264-180">从本地进行配置</span><span class="sxs-lookup"><span data-stu-id="f8264-180">Working with configurations locally</span></span>

<span data-ttu-id="f8264-181">适用于 Linux 的 DSC 包括用于从本地 Linux 计算机进行配置的脚本。</span><span class="sxs-lookup"><span data-stu-id="f8264-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="f8264-182">这些脚本位于 `/opt/microsoft/dsc/Scripts` 中，包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="f8264-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="f8264-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="f8264-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="f8264-184">返回应用于此计算机的当前配置。</span><span class="sxs-lookup"><span data-stu-id="f8264-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="f8264-185">与使用 Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet 类似。</span><span class="sxs-lookup"><span data-stu-id="f8264-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="f8264-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="f8264-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="f8264-187">返回应用于此计算机的当前元配置。</span><span class="sxs-lookup"><span data-stu-id="f8264-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="f8264-188">与 cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet 类似。</span><span class="sxs-lookup"><span data-stu-id="f8264-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="f8264-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="f8264-189">InstallModule.py</span></span>

<span data-ttu-id="f8264-190">安装自定义 DSC 资源模块。</span><span class="sxs-lookup"><span data-stu-id="f8264-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="f8264-191">需要包含模块共享对象库和架构 MOF 文件的 .zip 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="f8264-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="f8264-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="f8264-192">RemoveModule.py</span></span>

<span data-ttu-id="f8264-193">删除自定义 DSC 资源模块。</span><span class="sxs-lookup"><span data-stu-id="f8264-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="f8264-194">需要待删除模块的名称。</span><span class="sxs-lookup"><span data-stu-id="f8264-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="f8264-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="f8264-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="f8264-196">将配置 MOF 文件应用于计算机。</span><span class="sxs-lookup"><span data-stu-id="f8264-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="f8264-197">与 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 类似。</span><span class="sxs-lookup"><span data-stu-id="f8264-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="f8264-198">需要待应用的配置 MOF 的路径。</span><span class="sxs-lookup"><span data-stu-id="f8264-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="f8264-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="f8264-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="f8264-200">将元配置 MOF 文件应用于计算机。</span><span class="sxs-lookup"><span data-stu-id="f8264-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="f8264-201">与 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet 类似。</span><span class="sxs-lookup"><span data-stu-id="f8264-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="f8264-202">需要待应用的元配置 MOF 的路径。</span><span class="sxs-lookup"><span data-stu-id="f8264-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="f8264-203">适用于 Linux 的 PowerShell Desired State Configuration 日志文件</span><span class="sxs-lookup"><span data-stu-id="f8264-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="f8264-204">为适用于 Linux 的.DSC 生成了以下日志文件。</span><span class="sxs-lookup"><span data-stu-id="f8264-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="f8264-205">日志文件</span><span class="sxs-lookup"><span data-stu-id="f8264-205">Log file</span></span>|<span data-ttu-id="f8264-206">Directory</span><span class="sxs-lookup"><span data-stu-id="f8264-206">Directory</span></span>|<span data-ttu-id="f8264-207">说明</span><span class="sxs-lookup"><span data-stu-id="f8264-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="f8264-208">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="f8264-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="f8264-209">与 OMI CIM 服务器操作相关的消息。</span><span class="sxs-lookup"><span data-stu-id="f8264-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="f8264-210">dsc.log</span><span class="sxs-lookup"><span data-stu-id="f8264-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="f8264-211">与本地配置管理器 (LCM) 操作和 DSC 资源操作相关的消息。</span><span class="sxs-lookup"><span data-stu-id="f8264-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|

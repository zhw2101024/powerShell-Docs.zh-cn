---
title: 在 macOS 上安装 PowerShell Core
description: 介绍如何在 macOS 上安装 PowerShell Core
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998497"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="cb360-103">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="cb360-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="cb360-104">PowerShell Core 支持 macOS 10.12 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="cb360-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="cb360-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="cb360-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="cb360-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="cb360-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="cb360-107">关于 Brew</span><span class="sxs-lookup"><span data-stu-id="cb360-107">About Brew</span></span>

<span data-ttu-id="cb360-108">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="cb360-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="cb360-109">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="cb360-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cb360-110">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的稳定版本</span><span class="sxs-lookup"><span data-stu-id="cb360-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cb360-111">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="cb360-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cb360-112">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cb360-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="cb360-113">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="cb360-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="cb360-114">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cb360-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="cb360-115">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="cb360-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cb360-116">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的预览版</span><span class="sxs-lookup"><span data-stu-id="cb360-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cb360-117">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="cb360-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cb360-118">安装 Homebrew 后，安装 PowerShell 就变得很容易。</span><span class="sxs-lookup"><span data-stu-id="cb360-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="cb360-119">首先，安装 [Cask-Versions ][cask-versions]，通过它可安装替代版本的 cask 包：</span><span class="sxs-lookup"><span data-stu-id="cb360-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="cb360-120">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cb360-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="cb360-121">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="cb360-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="cb360-122">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cb360-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="cb360-123">可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。</span><span class="sxs-lookup"><span data-stu-id="cb360-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="cb360-124">然后刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="cb360-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="cb360-125">通过直接下载安装</span><span class="sxs-lookup"><span data-stu-id="cb360-125">Installation via Direct Download</span></span>

<span data-ttu-id="cb360-126">下载 PKG 包`powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="cb360-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="cb360-127">（从[版本][]页下载）到 macOS 计算机上。</span><span class="sxs-lookup"><span data-stu-id="cb360-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="cb360-128">可以双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="cb360-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="cb360-129">安装 [OpenSSL](#install-openssl)，因为这是执行 PowerShell 远程处理和 CIM 操作所必需的。</span><span class="sxs-lookup"><span data-stu-id="cb360-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="cb360-130">二进制存档</span><span class="sxs-lookup"><span data-stu-id="cb360-130">Binary Archives</span></span>

<span data-ttu-id="cb360-131">已对 macOS 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="cb360-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="cb360-132">在 macOS 上安装二进制存档</span><span class="sxs-lookup"><span data-stu-id="cb360-132">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="cb360-133">安装 [OpenSSL](#install-openssl)，因为这是执行 PowerShell 远程处理和 CIM 操作所必需的。</span><span class="sxs-lookup"><span data-stu-id="cb360-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="cb360-134">安装依赖关系</span><span class="sxs-lookup"><span data-stu-id="cb360-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="cb360-135">安装 XCode 命令行工具</span><span class="sxs-lookup"><span data-stu-id="cb360-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="cb360-136">安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cb360-136">Install OpenSSL</span></span>

<span data-ttu-id="cb360-137">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="cb360-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="cb360-138">可以通过 MacPorts 或 Brew 进行安装。</span><span class="sxs-lookup"><span data-stu-id="cb360-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="cb360-139">通过 Brew 安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cb360-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="cb360-140">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="cb360-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cb360-141">运行 `brew install openssl` 以安装 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="cb360-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="cb360-142">通过 MacPorts 安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cb360-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="cb360-143">安装 [XCode 命令行工具](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="cb360-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="cb360-144">安装 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="cb360-144">Install MacPorts.</span></span>
   <span data-ttu-id="cb360-145">如需说明，请参阅[安装指南](https://guide.macports.org/chunked/installing.macports.html)。</span><span class="sxs-lookup"><span data-stu-id="cb360-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="cb360-146">通过运行 `sudo port selfupdate` 更新 MacPorts</span><span class="sxs-lookup"><span data-stu-id="cb360-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="cb360-147">通过运行 `sudo port upgrade outdated` 升级 MacPorts 包</span><span class="sxs-lookup"><span data-stu-id="cb360-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="cb360-148">通过运行 `sudo port instal openssl` 安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cb360-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="cb360-149">链接库，以便 PowerShell 可以使用它。</span><span class="sxs-lookup"><span data-stu-id="cb360-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="cb360-150">卸载 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="cb360-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="cb360-151">如果使用 Homebrew 安装 PowerShell，则卸载很简单：</span><span class="sxs-lookup"><span data-stu-id="cb360-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="cb360-152">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cb360-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="cb360-153">若要删除其他 PowerShell 路径，请参阅本文档的[路径](#paths)一节，并使用 `sudo rm` 删除所需路径。</span><span class="sxs-lookup"><span data-stu-id="cb360-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="cb360-154">如果使用 Homebrew 安装，则此步骤并非必要步骤。</span><span class="sxs-lookup"><span data-stu-id="cb360-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="cb360-155">路径</span><span class="sxs-lookup"><span data-stu-id="cb360-155">Paths</span></span>

* <span data-ttu-id="cb360-156">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="cb360-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="cb360-157">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="cb360-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="cb360-158">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="cb360-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="cb360-159">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="cb360-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cb360-160">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="cb360-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cb360-161">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="cb360-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="cb360-162">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="cb360-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cb360-163">配置文件采用 PowerShell 的每个主机配置。</span><span class="sxs-lookup"><span data-stu-id="cb360-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="cb360-164">因此特定于主机的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="cb360-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cb360-165">PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="cb360-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="cb360-166">由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="cb360-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="cb360-167">因此，`$PSHOME` 为 `/usr/local/microsoft/powershell/6.1.0/`，且符号链接位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="cb360-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cb360-168">其他资源</span><span class="sxs-lookup"><span data-stu-id="cb360-168">Additional Resources</span></span>

* <span data-ttu-id="cb360-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="cb360-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="cb360-170">[Homebrew Github 存储库][GitHub]</span><span class="sxs-lookup"><span data-stu-id="cb360-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="cb360-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="cb360-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

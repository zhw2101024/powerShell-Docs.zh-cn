---
title: 在 macOS 上安装 PowerShell Core
description: 介绍如何在 macOS 上安装 PowerShell Core
ms.date: 12/12/2018
ms.openlocfilehash: 70f5d64aa8a697a9011d07fbcb2bb821463827e1
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229739"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="80c3e-103">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="80c3e-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="80c3e-104">PowerShell Core 支持 macOS 10.12 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="80c3e-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="80c3e-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="80c3e-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="80c3e-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="80c3e-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="80c3e-107">关于 Brew</span><span class="sxs-lookup"><span data-stu-id="80c3e-107">About Brew</span></span>

<span data-ttu-id="80c3e-108">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="80c3e-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="80c3e-109">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="80c3e-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="80c3e-110">或者，可通过[直接下载](#installation-via-direct-download)或从[二进制存档](#binary-archives)安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="80c3e-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="80c3e-111">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的稳定版本</span><span class="sxs-lookup"><span data-stu-id="80c3e-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="80c3e-112">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="80c3e-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="80c3e-113">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="80c3e-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="80c3e-114">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="80c3e-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="80c3e-115">PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="80c3e-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="80c3e-116">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 `$PSVersionTable` 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="80c3e-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="80c3e-117">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的预览版</span><span class="sxs-lookup"><span data-stu-id="80c3e-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="80c3e-118">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="80c3e-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="80c3e-119">安装 Homebrew 后，可以安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="80c3e-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="80c3e-120">首先，安装 [Cask-Versions ][cask-versions] 包，通过它可安装替代版本的 cask 包：</span><span class="sxs-lookup"><span data-stu-id="80c3e-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="80c3e-121">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="80c3e-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="80c3e-122">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="80c3e-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="80c3e-123">PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="80c3e-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="80c3e-124">可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。</span><span class="sxs-lookup"><span data-stu-id="80c3e-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="80c3e-125">然后刷新 `$PSVersionTable` 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="80c3e-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="80c3e-126">通过直接下载安装</span><span class="sxs-lookup"><span data-stu-id="80c3e-126">Installation via Direct Download</span></span>

<span data-ttu-id="80c3e-127">下载 PKG 包`powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="80c3e-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="80c3e-128">（从[版本][]页下载）到 macOS 计算机上。</span><span class="sxs-lookup"><span data-stu-id="80c3e-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="80c3e-129">可以双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="80c3e-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="80c3e-130">安装 [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="80c3e-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="80c3e-131">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="80c3e-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="80c3e-132">二进制存档</span><span class="sxs-lookup"><span data-stu-id="80c3e-132">Binary Archives</span></span>

<span data-ttu-id="80c3e-133">已对 macOS 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="80c3e-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="80c3e-134">在 macOS 上安装二进制存档</span><span class="sxs-lookup"><span data-stu-id="80c3e-134">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="80c3e-135">安装 [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="80c3e-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="80c3e-136">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="80c3e-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="80c3e-137">安装依赖关系</span><span class="sxs-lookup"><span data-stu-id="80c3e-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="80c3e-138">安装 XCode 命令行工具</span><span class="sxs-lookup"><span data-stu-id="80c3e-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="80c3e-139">安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="80c3e-139">Install OpenSSL</span></span>

<span data-ttu-id="80c3e-140">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="80c3e-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="80c3e-141">可以通过 MacPorts 或 Brew 进行安装。</span><span class="sxs-lookup"><span data-stu-id="80c3e-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="80c3e-142">通过 Brew 安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="80c3e-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="80c3e-143">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="80c3e-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="80c3e-144">若要安装 OpenSSL，请运行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="80c3e-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="80c3e-145">通过 MacPorts 安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="80c3e-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="80c3e-146">安装 [XCode 命令行工具](#install-xcode-command-line-tools)。</span><span class="sxs-lookup"><span data-stu-id="80c3e-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="80c3e-147">安装 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="80c3e-147">Install MacPorts.</span></span>
   <span data-ttu-id="80c3e-148">如需说明，请参阅[安装指南](https://guide.macports.org/chunked/installing.macports.html)。</span><span class="sxs-lookup"><span data-stu-id="80c3e-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="80c3e-149">通过运行 `sudo port selfupdate` 更新 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="80c3e-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="80c3e-150">通过运行 `sudo port upgrade outdated` 升级 MacPorts 包。</span><span class="sxs-lookup"><span data-stu-id="80c3e-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="80c3e-151">通过运行 `sudo port install openssl` 安装 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="80c3e-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="80c3e-152">链接库，使其可供 PowerShell 使用：</span><span class="sxs-lookup"><span data-stu-id="80c3e-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="80c3e-153">卸载 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="80c3e-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="80c3e-154">如果使用 Homebrew 安装 PowerShell，请使用以下命令进行卸载：</span><span class="sxs-lookup"><span data-stu-id="80c3e-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="80c3e-155">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="80c3e-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="80c3e-156">若要删除其他 PowerShell 路径，请参阅本文档的[路径](#paths)一节，并使用 `sudo rm` 删除路径。</span><span class="sxs-lookup"><span data-stu-id="80c3e-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="80c3e-157">如果使用 Homebrew 安装，则此步骤并非必要步骤。</span><span class="sxs-lookup"><span data-stu-id="80c3e-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="80c3e-158">路径</span><span class="sxs-lookup"><span data-stu-id="80c3e-158">Paths</span></span>

* <span data-ttu-id="80c3e-159">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="80c3e-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="80c3e-160">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="80c3e-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="80c3e-161">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="80c3e-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="80c3e-162">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="80c3e-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="80c3e-163">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="80c3e-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="80c3e-164">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="80c3e-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="80c3e-165">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="80c3e-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="80c3e-166">配置文件采用 PowerShell 的每个主机配置。</span><span class="sxs-lookup"><span data-stu-id="80c3e-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="80c3e-167">因此主机特定的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="80c3e-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="80c3e-168">PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="80c3e-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="80c3e-169">由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="80c3e-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="80c3e-170">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.2.0/`，且符号链接位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="80c3e-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="80c3e-171">其他资源</span><span class="sxs-lookup"><span data-stu-id="80c3e-171">Additional Resources</span></span>

* <span data-ttu-id="80c3e-172">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="80c3e-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="80c3e-173">[Homebrew Github 存储库][GitHub]</span><span class="sxs-lookup"><span data-stu-id="80c3e-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="80c3e-174">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="80c3e-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

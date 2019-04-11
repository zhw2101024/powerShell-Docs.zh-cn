---
title: 在 macOS 上安装 PowerShell Core
description: 介绍如何在 macOS 上安装 PowerShell Core
ms.date: 12/12/2018
ms.openlocfilehash: 7db8ca0cb6d13db8ce7f11b4a4b03b7d3f9b6feb
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293395"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="cdc21-103">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="cdc21-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="cdc21-104">PowerShell Core 支持 macOS 10.12 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="cdc21-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="cdc21-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="cdc21-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="cdc21-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="cdc21-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="cdc21-107">关于 Brew</span><span class="sxs-lookup"><span data-stu-id="cdc21-107">About Brew</span></span>

<span data-ttu-id="cdc21-108">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="cdc21-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="cdc21-109">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="cdc21-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cdc21-110">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的稳定版本</span><span class="sxs-lookup"><span data-stu-id="cdc21-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cdc21-111">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="cdc21-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cdc21-112">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cdc21-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="cdc21-113">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="cdc21-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="cdc21-114">PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cdc21-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="cdc21-115">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 `$PSVersionTable` 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="cdc21-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cdc21-116">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的预览版</span><span class="sxs-lookup"><span data-stu-id="cdc21-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cdc21-117">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="cdc21-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cdc21-118">安装 Homebrew 后，可以安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cdc21-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="cdc21-119">首先，安装 [Cask-Versions ][cask-versions] 包，通过它可安装替代版本的 cask 包：</span><span class="sxs-lookup"><span data-stu-id="cdc21-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="cdc21-120">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cdc21-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="cdc21-121">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="cdc21-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="cdc21-122">PowerShell 新版本发布后，更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cdc21-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="cdc21-123">可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。</span><span class="sxs-lookup"><span data-stu-id="cdc21-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="cdc21-124">然后刷新 `$PSVersionTable` 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="cdc21-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="cdc21-125">通过直接下载安装</span><span class="sxs-lookup"><span data-stu-id="cdc21-125">Installation via Direct Download</span></span>

<span data-ttu-id="cdc21-126">下载 PKG 包</span><span class="sxs-lookup"><span data-stu-id="cdc21-126">Download the PKG package</span></span>
`powershell-6.2.0-osx-x64.pkg`
<span data-ttu-id="cdc21-127">（从[版本][]页下载）到 macOS 计算机上。</span><span class="sxs-lookup"><span data-stu-id="cdc21-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="cdc21-128">可以双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="cdc21-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="cdc21-129">安装 [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="cdc21-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="cdc21-130">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="cdc21-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="cdc21-131">二进制存档</span><span class="sxs-lookup"><span data-stu-id="cdc21-131">Binary Archives</span></span>

<span data-ttu-id="cdc21-132">已对 macOS 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="cdc21-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="cdc21-133">在 macOS 上安装二进制存档</span><span class="sxs-lookup"><span data-stu-id="cdc21-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="cdc21-134">安装 [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="cdc21-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="cdc21-135">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="cdc21-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="cdc21-136">安装依赖关系</span><span class="sxs-lookup"><span data-stu-id="cdc21-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="cdc21-137">安装 XCode 命令行工具</span><span class="sxs-lookup"><span data-stu-id="cdc21-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="cdc21-138">安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cdc21-138">Install OpenSSL</span></span>

<span data-ttu-id="cdc21-139">PowerShell 远程处理和 CIM 操作均需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="cdc21-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="cdc21-140">可以通过 MacPorts 或 Brew 进行安装。</span><span class="sxs-lookup"><span data-stu-id="cdc21-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="cdc21-141">通过 Brew 安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cdc21-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="cdc21-142">有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="cdc21-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cdc21-143">若要安装 OpenSSL，请运行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="cdc21-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="cdc21-144">通过 MacPorts 安装 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cdc21-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="cdc21-145">安装 [XCode 命令行工具](#install-xcode-command-line-tools)。</span><span class="sxs-lookup"><span data-stu-id="cdc21-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="cdc21-146">安装 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="cdc21-146">Install MacPorts.</span></span>
   <span data-ttu-id="cdc21-147">如需说明，请参阅[安装指南](https://guide.macports.org/chunked/installing.macports.html)。</span><span class="sxs-lookup"><span data-stu-id="cdc21-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="cdc21-148">通过运行 `sudo port selfupdate` 更新 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="cdc21-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="cdc21-149">通过运行 `sudo port upgrade outdated` 升级 MacPorts 包。</span><span class="sxs-lookup"><span data-stu-id="cdc21-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="cdc21-150">通过运行 `sudo port install openssl` 安装 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="cdc21-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="cdc21-151">链接库，使其可供 PowerShell 使用：</span><span class="sxs-lookup"><span data-stu-id="cdc21-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="cdc21-152">卸载 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="cdc21-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="cdc21-153">如果使用 Homebrew 安装 PowerShell，请使用以下命令进行卸载：</span><span class="sxs-lookup"><span data-stu-id="cdc21-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="cdc21-154">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cdc21-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="cdc21-155">若要删除其他 PowerShell 路径，请参阅本文档的[路径](#paths)一节，并使用 `sudo rm` 删除路径。</span><span class="sxs-lookup"><span data-stu-id="cdc21-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="cdc21-156">如果使用 Homebrew 安装，则此步骤并非必要步骤。</span><span class="sxs-lookup"><span data-stu-id="cdc21-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="cdc21-157">路径</span><span class="sxs-lookup"><span data-stu-id="cdc21-157">Paths</span></span>

* `$PSHOME` <span data-ttu-id="cdc21-158">是</span><span class="sxs-lookup"><span data-stu-id="cdc21-158">is</span></span> `/usr/local/microsoft/powershell/6.2.0/`
* <span data-ttu-id="cdc21-159">将从以下位置读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="cdc21-159">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="cdc21-160">将从以下位置读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="cdc21-160">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="cdc21-161">将从以下位置读取用户模块</span><span class="sxs-lookup"><span data-stu-id="cdc21-161">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="cdc21-162">将从以下位置读取共享模块</span><span class="sxs-lookup"><span data-stu-id="cdc21-162">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="cdc21-163">将从以下位置读取默认模块</span><span class="sxs-lookup"><span data-stu-id="cdc21-163">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="cdc21-164">PSReadline 历史记录将记录到</span><span class="sxs-lookup"><span data-stu-id="cdc21-164">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="cdc21-165">配置文件采用 PowerShell 的每个主机配置。</span><span class="sxs-lookup"><span data-stu-id="cdc21-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="cdc21-166">因此主机特定的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="cdc21-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cdc21-167">PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="cdc21-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="cdc21-168">由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="cdc21-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="cdc21-169">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.2.0/`，且符号链接位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="cdc21-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cdc21-170">其他资源</span><span class="sxs-lookup"><span data-stu-id="cdc21-170">Additional Resources</span></span>

* <span data-ttu-id="cdc21-171">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="cdc21-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="cdc21-172">[Homebrew Github 存储库][GitHub]</span><span class="sxs-lookup"><span data-stu-id="cdc21-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="cdc21-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="cdc21-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[<span data-ttu-id="cdc21-174">版本</span><span class="sxs-lookup"><span data-stu-id="cdc21-174">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

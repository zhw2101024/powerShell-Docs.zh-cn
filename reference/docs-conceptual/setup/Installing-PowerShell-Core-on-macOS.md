---
title: 在 macOS 上安装 PowerShell Core
description: 介绍如何在 macOS 上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611481"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="a4706-103">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a4706-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="a4706-104">PowerShell Core 支持 macOS 10.12 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="a4706-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="a4706-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="a4706-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="a4706-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="a4706-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="a4706-107">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的稳定版本</span><span class="sxs-lookup"><span data-stu-id="a4706-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="a4706-108">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="a4706-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="a4706-109">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="a4706-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="a4706-110">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a4706-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="a4706-111">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="a4706-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="a4706-112">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a4706-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="a4706-113">可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。</span><span class="sxs-lookup"><span data-stu-id="a4706-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="a4706-114">然后刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="a4706-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="a4706-115">通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的预览版</span><span class="sxs-lookup"><span data-stu-id="a4706-115">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="a4706-116">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="a4706-116">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="a4706-117">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="a4706-117">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="a4706-118">安装 Homebrew 后，安装 PowerShell 就变得很容易。</span><span class="sxs-lookup"><span data-stu-id="a4706-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="a4706-119">首先，安装 [Cask-Versions ][cask-versions]，通过它可安装替代版本的 cask 包：</span><span class="sxs-lookup"><span data-stu-id="a4706-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="a4706-120">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a4706-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="a4706-121">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="a4706-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="a4706-122">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a4706-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="a4706-123">可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。</span><span class="sxs-lookup"><span data-stu-id="a4706-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="a4706-124">然后刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="a4706-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="a4706-125">通过直接下载安装</span><span class="sxs-lookup"><span data-stu-id="a4706-125">Installation via Direct Download</span></span>

<span data-ttu-id="a4706-126">下载 PKG 包`powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="a4706-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="a4706-127">（从[版本][]页下载）到 macOS 计算机上。</span><span class="sxs-lookup"><span data-stu-id="a4706-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="a4706-128">可以双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="a4706-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="a4706-129">二进制存档</span><span class="sxs-lookup"><span data-stu-id="a4706-129">Binary Archives</span></span>

<span data-ttu-id="a4706-130">已对 macOS 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="a4706-130">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="a4706-131">在 macOS 上安装二进制存档</span><span class="sxs-lookup"><span data-stu-id="a4706-131">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="a4706-132">卸载 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a4706-132">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="a4706-133">如果使用 Homebrew 安装 PowerShell，则卸载很简单：</span><span class="sxs-lookup"><span data-stu-id="a4706-133">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="a4706-134">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a4706-134">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="a4706-135">若要删除其他 PowerShell 路径，请参阅本文档的[路径](#paths)一节，并使用 `sudo rm` 删除所需路径。</span><span class="sxs-lookup"><span data-stu-id="a4706-135">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="a4706-136">如果使用 Homebrew 安装，则此步骤并非必要步骤。</span><span class="sxs-lookup"><span data-stu-id="a4706-136">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="a4706-137">路径</span><span class="sxs-lookup"><span data-stu-id="a4706-137">Paths</span></span>

* <span data-ttu-id="a4706-138">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="a4706-138">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="a4706-139">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="a4706-139">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="a4706-140">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="a4706-140">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="a4706-141">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="a4706-141">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a4706-142">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="a4706-142">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a4706-143">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="a4706-143">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="a4706-144">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a4706-144">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="a4706-145">配置文件采用 PowerShell 的每个主机配置。</span><span class="sxs-lookup"><span data-stu-id="a4706-145">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="a4706-146">因此特定于主机的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="a4706-146">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="a4706-147">PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="a4706-147">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="a4706-148">由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="a4706-148">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="a4706-149">因此，`$PSHOME` 为 `/usr/local/microsoft/powershell/6.1.0/`，且 symlink 位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="a4706-149">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a4706-150">其他资源</span><span class="sxs-lookup"><span data-stu-id="a4706-150">Additional Resources</span></span>

* <span data-ttu-id="a4706-151">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="a4706-151">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="a4706-152">[Homebrew Github 存储库][GitHub]</span><span class="sxs-lookup"><span data-stu-id="a4706-152">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="a4706-153">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="a4706-153">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

---
title: 在 macOS 上安装 PowerShell Core
description: 介绍如何在 macOS 上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587459"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="0ecad-103">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0ecad-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="0ecad-104">PowerShell Core 支持 macOS 10.12 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="0ecad-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="0ecad-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="0ecad-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0ecad-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="0ecad-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="0ecad-107">在 macOS 10.12+ 上通过 Homebrew 安装</span><span class="sxs-lookup"><span data-stu-id="0ecad-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="0ecad-108">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="0ecad-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="0ecad-109">在终端窗口中，键入 `brew` 运行 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="0ecad-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="0ecad-110">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="0ecad-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="0ecad-111">如果以前安装过 Homebrew，建议运行“brew update-reset”和“brew update”。</span><span class="sxs-lookup"><span data-stu-id="0ecad-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="0ecad-112">较旧版本的 Homebrew 使用点击“caskroom/cask”，此功能已被弃用，并已被迁移到“homebrew/cask”。</span><span class="sxs-lookup"><span data-stu-id="0ecad-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="0ecad-113">可在 [Homebrew-cask][cask] 中找到更为详细的信息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="0ecad-114">使用“brew tap”命令列出你的当前点击。</span><span class="sxs-lookup"><span data-stu-id="0ecad-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="0ecad-115">如果看到“caskroom/cask”，可以使用“brew update”让 Homebrew 来迁移点击。</span><span class="sxs-lookup"><span data-stu-id="0ecad-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="0ecad-116">安装/更新 Homebrew 后，安装 PowerShell 就变得很容易。</span><span class="sxs-lookup"><span data-stu-id="0ecad-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="0ecad-117">若要安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0ecad-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="0ecad-118">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="0ecad-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="0ecad-119">若要退出 PowerShell 并返回 bash，请使用“exit”命令。</span><span class="sxs-lookup"><span data-stu-id="0ecad-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="0ecad-120">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0ecad-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="0ecad-121">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="0ecad-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="0ecad-122">在 macOS 10.12+ 上通过 Homebrew 安装预览版</span><span class="sxs-lookup"><span data-stu-id="0ecad-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="0ecad-123">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="0ecad-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="0ecad-124">在终端窗口中，键入 `brew` 运行 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="0ecad-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="0ecad-125">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="0ecad-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="0ecad-126">如果以前安装过 Homebrew，建议运行“brew update-reset”和“brew update”。</span><span class="sxs-lookup"><span data-stu-id="0ecad-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="0ecad-127">然后，必须点击 `versions` casks 存储库来获取预览包：</span><span class="sxs-lookup"><span data-stu-id="0ecad-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="0ecad-128">若要安装 PowerShell 预览版：</span><span class="sxs-lookup"><span data-stu-id="0ecad-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="0ecad-129">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="0ecad-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="0ecad-130">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell 预览版：</span><span class="sxs-lookup"><span data-stu-id="0ecad-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="0ecad-131">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="0ecad-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="0ecad-132">通过直接下载安装</span><span class="sxs-lookup"><span data-stu-id="0ecad-132">Installation via Direct Download</span></span>

<span data-ttu-id="0ecad-133">请从[版本][]页中将 PKG 包 `powershell-6.0.2-osx.10.12-x64.pkg` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="0ecad-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="0ecad-134">可以双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="0ecad-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="0ecad-135">二进制存档</span><span class="sxs-lookup"><span data-stu-id="0ecad-135">Binary Archives</span></span>

<span data-ttu-id="0ecad-136">已对 macOS 和 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="0ecad-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="0ecad-137">在 macOS 上安装二进制存档</span><span class="sxs-lookup"><span data-stu-id="0ecad-137">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="0ecad-138">卸载 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0ecad-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="0ecad-139">如果使用 Homebrew 安装 PowerShell，则卸载很简单：</span><span class="sxs-lookup"><span data-stu-id="0ecad-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="0ecad-140">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0ecad-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="0ecad-141">若要删除其他 PowerShell 路径，请参阅本文档的[路径][]一节，并使用 `sudo rm` 删除所需路径。</span><span class="sxs-lookup"><span data-stu-id="0ecad-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="0ecad-142">如果使用 Homebrew 安装，则此步骤并非必要步骤。</span><span class="sxs-lookup"><span data-stu-id="0ecad-142">This is not necessary if you installed with Homebrew.</span></span>

[路径]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="0ecad-144">路径</span><span class="sxs-lookup"><span data-stu-id="0ecad-144">Paths</span></span>

* <span data-ttu-id="0ecad-145">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="0ecad-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="0ecad-146">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="0ecad-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0ecad-147">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="0ecad-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0ecad-148">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="0ecad-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0ecad-149">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="0ecad-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0ecad-150">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="0ecad-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0ecad-151">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0ecad-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0ecad-152">配置文件采用 PowerShell 的每个主机配置。</span><span class="sxs-lookup"><span data-stu-id="0ecad-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="0ecad-153">因此特定于主机的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="0ecad-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0ecad-154">PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="0ecad-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="0ecad-155">由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="0ecad-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="0ecad-156">因此，`$PSHOME` 为 `/usr/local/microsoft/powershell/6.0.2/`，且 symlink 位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="0ecad-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0ecad-157">其他资源</span><span class="sxs-lookup"><span data-stu-id="0ecad-157">Additional Resources</span></span>

* <span data-ttu-id="0ecad-158">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="0ecad-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="0ecad-159">[Homebrew Github 存储库][GitHub]</span><span class="sxs-lookup"><span data-stu-id="0ecad-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="0ecad-160">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="0ecad-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

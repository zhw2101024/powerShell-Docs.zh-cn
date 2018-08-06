# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="f21c0-101">在 macOS 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f21c0-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="f21c0-102">PowerShell Core 支持 macOS 10.12 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="f21c0-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="f21c0-103">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="f21c0-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="f21c0-104">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="f21c0-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="f21c0-105">在 macOS 10.12+ 上通过 Homebrew 安装</span><span class="sxs-lookup"><span data-stu-id="f21c0-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="f21c0-106">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="f21c0-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="f21c0-107">在终端窗口中，键入 `brew` 运行 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="f21c0-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="f21c0-108">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="f21c0-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="f21c0-109">如果以前安装过 Homebrew，建议运行“brew update-reset”和“brew update”。</span><span class="sxs-lookup"><span data-stu-id="f21c0-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="f21c0-110">较旧版本的 Homebrew 使用点击“caskroom/cask”，此功能已被弃用，并已被迁移到“homebrew/cask”。</span><span class="sxs-lookup"><span data-stu-id="f21c0-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="f21c0-111">可在 [Homebrew-cask][cask] 中找到更为详细的信息。</span><span class="sxs-lookup"><span data-stu-id="f21c0-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="f21c0-112">使用“brew tap”命令列出你的当前点击。</span><span class="sxs-lookup"><span data-stu-id="f21c0-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="f21c0-113">如果看到“caskroom/cask”，可以使用“brew update”让 Homebrew 来迁移点击。</span><span class="sxs-lookup"><span data-stu-id="f21c0-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="f21c0-114">安装/更新 Homebrew 后，安装 PowerShell 就变得很容易。</span><span class="sxs-lookup"><span data-stu-id="f21c0-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="f21c0-115">若要安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="f21c0-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="f21c0-116">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="f21c0-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="f21c0-117">若要退出 PowerShell 并返回 bash，请使用“exit”命令。</span><span class="sxs-lookup"><span data-stu-id="f21c0-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="f21c0-118">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="f21c0-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="f21c0-119">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="f21c0-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="f21c0-120">在 macOS 10.12+ 上通过 Homebrew 安装预览版</span><span class="sxs-lookup"><span data-stu-id="f21c0-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="f21c0-121">[Homebrew][brew] 是 macOS 的首选包管理器。</span><span class="sxs-lookup"><span data-stu-id="f21c0-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="f21c0-122">在终端窗口中，键入 `brew` 运行 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="f21c0-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="f21c0-123">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="f21c0-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="f21c0-124">如果以前安装过 Homebrew，建议运行“brew update-reset”和“brew update”。</span><span class="sxs-lookup"><span data-stu-id="f21c0-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="f21c0-125">然后，必须点击 `versions` casks 存储库来获取预览包：</span><span class="sxs-lookup"><span data-stu-id="f21c0-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="f21c0-126">若要安装 PowerShell 预览版：</span><span class="sxs-lookup"><span data-stu-id="f21c0-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="f21c0-127">最后，验证安装是否正常运行：</span><span class="sxs-lookup"><span data-stu-id="f21c0-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="f21c0-128">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell 预览版：</span><span class="sxs-lookup"><span data-stu-id="f21c0-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="f21c0-129">可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="f21c0-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="f21c0-130">通过直接下载安装</span><span class="sxs-lookup"><span data-stu-id="f21c0-130">Installation via Direct Download</span></span>

<span data-ttu-id="f21c0-131">请从[版本][]页中将 PKG 包 `powershell-6.0.2-osx.10.12-x64.pkg` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="f21c0-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="f21c0-132">可以双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="f21c0-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="f21c0-133">二进制存档</span><span class="sxs-lookup"><span data-stu-id="f21c0-133">Binary Archives</span></span>

<span data-ttu-id="f21c0-134">已对 macOS 和 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="f21c0-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="f21c0-135">在 macOS 上安装二进制存档</span><span class="sxs-lookup"><span data-stu-id="f21c0-135">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="f21c0-136">卸载 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f21c0-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="f21c0-137">如果使用 Homebrew 安装 PowerShell，则卸载很简单：</span><span class="sxs-lookup"><span data-stu-id="f21c0-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="f21c0-138">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="f21c0-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="f21c0-139">若要删除其他 PowerShell 路径，请参阅本文档的[路径][]一节，并使用 `sudo rm` 删除所需路径。</span><span class="sxs-lookup"><span data-stu-id="f21c0-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="f21c0-140">如果使用 Homebrew 安装，则此步骤并非必要步骤。</span><span class="sxs-lookup"><span data-stu-id="f21c0-140">This is not necessary if you installed with Homebrew.</span></span>

[路径]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="f21c0-142">路径</span><span class="sxs-lookup"><span data-stu-id="f21c0-142">Paths</span></span>

* <span data-ttu-id="f21c0-143">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="f21c0-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="f21c0-144">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="f21c0-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="f21c0-145">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="f21c0-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="f21c0-146">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="f21c0-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="f21c0-147">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="f21c0-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="f21c0-148">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="f21c0-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="f21c0-149">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="f21c0-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="f21c0-150">配置文件采用 PowerShell 的每个主机配置。</span><span class="sxs-lookup"><span data-stu-id="f21c0-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="f21c0-151">因此特定于主机的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="f21c0-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="f21c0-152">PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="f21c0-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="f21c0-153">由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="f21c0-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="f21c0-154">因此，`$PSHOME` 为 `/usr/local/microsoft/powershell/6.0.2/`，且 symlink 位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="f21c0-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f21c0-155">其他资源</span><span class="sxs-lookup"><span data-stu-id="f21c0-155">Additional Resources</span></span>

* <span data-ttu-id="f21c0-156">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="f21c0-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="f21c0-157">[Homebrew Github 存储库][GitHub]</span><span class="sxs-lookup"><span data-stu-id="f21c0-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="f21c0-158">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="f21c0-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="3a0c4-101">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3a0c4-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="3a0c4-102">支持 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.10][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="3a0c4-103">对于不受正式支持的 Linux 分发版，可以尝试使用 [PowerShell AppImage][lai]。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="3a0c4-104">还可以尝试直接使用 Linux [`tar.gz` archive][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置所需的依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="3a0c4-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="3a0c4-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="3a0c4-107">安装预览版本</span><span class="sxs-lookup"><span data-stu-id="3a0c4-107">Installing Preview Releases</span></span>

<span data-ttu-id="3a0c4-108">通过包存储库安装适用于 Linux 的 PowerShell Core 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="3a0c4-109">直接下载安装不会更改包名称（文件名除外）。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="3a0c4-110">下面是使用各种包管理器安装稳定包和预览包的命令表：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="3a0c4-111">Distrobution</span><span class="sxs-lookup"><span data-stu-id="3a0c4-111">Distrobution(s)</span></span>|<span data-ttu-id="3a0c4-112">稳定包命令</span><span class="sxs-lookup"><span data-stu-id="3a0c4-112">Stable Command</span></span> | <span data-ttu-id="3a0c4-113">预览包命令</span><span class="sxs-lookup"><span data-stu-id="3a0c4-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="3a0c4-114">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="3a0c4-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="3a0c4-115">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="3a0c4-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="3a0c4-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="3a0c4-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="3a0c4-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="3a0c4-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="3a0c4-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="3a0c4-119">通过包存储库安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="3a0c4-120">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3a0c4-121">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-121">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-122">以超级用户身份注册 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="3a0c4-123">此后，只需使用 `sudo apt-get upgrade powershell` 来更新安装。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="3a0c4-124">通过直接下载进行安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="3a0c4-125">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3a0c4-126">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3a0c4-127">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3a0c4-128">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="3a0c4-129">卸载 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="3a0c4-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="3a0c4-131">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="3a0c4-132">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3a0c4-133">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-133">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-134">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="3a0c4-135">通过 Direct Download 的安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="3a0c4-136">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3a0c4-137">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3a0c4-138">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3a0c4-139">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="3a0c4-140">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="3a0c4-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3a0c4-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-142">`6.1.0-preview.2` 后添加了对 Ubuntu 17.04 的支持</span><span class="sxs-lookup"><span data-stu-id="3a0c4-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="3a0c4-143">通过包存储库安装 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3a0c4-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="3a0c4-144">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3a0c4-145">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-146">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="3a0c4-147">通过直接下载进行安装 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3a0c4-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="3a0c4-148">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3a0c4-149">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3a0c4-150">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3a0c4-151">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="3a0c4-152">卸载 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3a0c4-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="3a0c4-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-154">`6.1.0-preview.2` 后添加了对 Ubuntu 18.04 的支持</span><span class="sxs-lookup"><span data-stu-id="3a0c4-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="3a0c4-155">通过包存储库安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="3a0c4-156">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3a0c4-157">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-158">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="3a0c4-159">通过直接下载安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="3a0c4-160">从[版本][]页中将 Debian 包 `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3a0c4-161">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3a0c4-162">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3a0c4-163">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="3a0c4-164">卸载 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3a0c4-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="3a0c4-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3a0c4-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="3a0c4-166">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="3a0c4-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="3a0c4-167">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3a0c4-168">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-168">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-169">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="3a0c4-170">通过直接下载进行安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="3a0c4-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="3a0c4-171">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.8_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3a0c4-172">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3a0c4-173">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3a0c4-174">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="3a0c4-175">卸载 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="3a0c4-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="3a0c4-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3a0c4-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="3a0c4-177">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3a0c4-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="3a0c4-178">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3a0c4-179">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-179">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-180">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="3a0c4-181">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3a0c4-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="3a0c4-182">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.9_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3a0c4-183">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="3a0c4-184">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3a0c4-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="3a0c4-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-186">此包也可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="3a0c4-187">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="3a0c4-188">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-189">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="3a0c4-190">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="3a0c4-191">使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="3a0c4-192">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3a0c4-193">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="3a0c4-194">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3a0c4-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3a0c4-197">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3a0c4-198">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3a0c4-199">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3a0c4-200">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3a0c4-201">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="3a0c4-202">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3a0c4-203">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3a0c4-204">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="3a0c4-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3a0c4-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="3a0c4-206">安装 PowerShell Core 时，`zypper` 可能报告以下错误：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="3a0c4-207">在这种情况下，通过检查以下命令将 `libcurl4` 包显示为已安装来验证存在兼容的 `libcurl` 库：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="3a0c4-208">然后在安装 PowerShell 包时选择 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解决方案。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="3a0c4-209">通过包存储库安装（首选）- OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3a0c4-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="3a0c4-210">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="3a0c4-211">通过直接下载进行安装 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3a0c4-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="3a0c4-212">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 OpenSUSE 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3a0c4-213">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="3a0c4-214">卸载 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3a0c4-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="3a0c4-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="3a0c4-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-216">Fedora 28 仅在 PowerShell Core 6.1 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="3a0c4-217">通过包存储库安装（首选）- Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3a0c4-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3a0c4-218">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="3a0c4-219">通过直接下载进行安装 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3a0c4-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3a0c4-220">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="3a0c4-221">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3a0c4-222">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="3a0c4-223">卸载 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3a0c4-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="3a0c4-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3a0c4-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-225">Arch 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-225">Arch support is experimental.</span></span>

<span data-ttu-id="3a0c4-226">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="3a0c4-227">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="3a0c4-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="3a0c4-228">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="3a0c4-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="3a0c4-229">可以使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="3a0c4-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="3a0c4-230">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="3a0c4-231">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="3a0c4-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="3a0c4-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-234">AppImage 支持是实验性的</span><span class="sxs-lookup"><span data-stu-id="3a0c4-234">AppImage support is experimental</span></span>

<span data-ttu-id="3a0c4-235">使用新的 Linux 分发版时，请从[版本][]页中将 AppImage `powershell-6.0.1-x86_64.AppImage`下载到 Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="3a0c4-236">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3a0c4-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="3a0c4-237">通过 [AppImage][] 无需安装即可运行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="3a0c4-238">此款可移植应用程序将 PowerShell 及其依赖项（包括 .NET Core 的系统依赖项）捆绑到一个统一包中。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="3a0c4-239">此包为单个二进制文件，独立于用户的 Linux 分发版运行。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="3a0c4-241">Kali</span><span class="sxs-lookup"><span data-stu-id="3a0c4-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-242">Kali 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="3a0c4-243">安装</span><span class="sxs-lookup"><span data-stu-id="3a0c4-243">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="3a0c4-244">在最新版 Kali (Kali GNU/Linux Rolling) 中无需安装即可运行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a0c4-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="3a0c4-245">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="3a0c4-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="3a0c4-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3a0c4-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="3a0c4-247">Raspbian 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="3a0c4-248">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="3a0c4-249">此外 CoreCLR（和 PowerShell Core）仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="3a0c4-250">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="3a0c4-251">安装</span><span class="sxs-lookup"><span data-stu-id="3a0c4-251">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="3a0c4-252">或者可以创建能够启动 PowerShell 的符号链接，而无需指定到“pwsh”二进制文件的路径</span><span class="sxs-lookup"><span data-stu-id="3a0c4-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="3a0c4-253">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="3a0c4-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="3a0c4-254">二进制存档</span><span class="sxs-lookup"><span data-stu-id="3a0c4-254">Binary Archives</span></span>

<span data-ttu-id="3a0c4-255">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="3a0c4-256">依赖关系</span><span class="sxs-lookup"><span data-stu-id="3a0c4-256">Dependencies</span></span>

<span data-ttu-id="3a0c4-257">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="3a0c4-258">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，因此 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="3a0c4-259">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="3a0c4-260">操作系统</span><span class="sxs-lookup"><span data-stu-id="3a0c4-260">OS</span></span>                 | <span data-ttu-id="3a0c4-261">依赖关系</span><span class="sxs-lookup"><span data-stu-id="3a0c4-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="3a0c4-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="3a0c4-263">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3a0c4-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3a0c4-264">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="3a0c4-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3a0c4-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="3a0c4-266">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3a0c4-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3a0c4-267">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="3a0c4-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="3a0c4-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3a0c4-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="3a0c4-269">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3a0c4-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3a0c4-270">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="3a0c4-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="3a0c4-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3a0c4-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="3a0c4-272">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3a0c4-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3a0c4-273">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="3a0c4-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="3a0c4-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="3a0c4-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="3a0c4-275">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3a0c4-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3a0c4-276">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="3a0c4-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3a0c4-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="3a0c4-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="3a0c4-278">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3a0c4-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3a0c4-279">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="3a0c4-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="3a0c4-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-280">CentOS 7</span></span> <br> <span data-ttu-id="3a0c4-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="3a0c4-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="3a0c4-282">RHEL 7</span></span> <br> <span data-ttu-id="3a0c4-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3a0c4-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="3a0c4-284">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="3a0c4-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="3a0c4-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="3a0c4-285">Fedora 27</span></span> <br> <span data-ttu-id="3a0c4-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3a0c4-286">Fedora 28</span></span> | <span data-ttu-id="3a0c4-287">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="3a0c4-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="3a0c4-288">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="3a0c4-289">例如，[Amazon Linux dockerfile][amazon-dockerfile] 应先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="3a0c4-290">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="3a0c4-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="3a0c4-291">Linux</span><span class="sxs-lookup"><span data-stu-id="3a0c4-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="3a0c4-292">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="3a0c4-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="3a0c4-293">路径</span><span class="sxs-lookup"><span data-stu-id="3a0c4-293">Paths</span></span>

* <span data-ttu-id="3a0c4-294">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="3a0c4-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="3a0c4-295">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="3a0c4-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="3a0c4-296">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="3a0c4-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="3a0c4-297">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="3a0c4-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3a0c4-298">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="3a0c4-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3a0c4-299">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="3a0c4-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="3a0c4-300">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="3a0c4-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3a0c4-301">配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3a0c4-302">PowerShell 采用 Linux 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="3a0c4-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

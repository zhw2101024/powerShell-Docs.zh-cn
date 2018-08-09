---
title: 在 Linux 上安装 PowerShell Core
description: 介绍如何在各种 Linux 分发上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587442"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="3f569-103">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3f569-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="3f569-104">支持 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 18.10][u18]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.3][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="3f569-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="3f569-105">对于未获得官方支持的 Linux 分发，可尝试使用 [PowerShell Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="3f569-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="3f569-106">还可以尝试直接使用 Linux [`tar.gz` archive][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置所需的依赖项。</span><span class="sxs-lookup"><span data-stu-id="3f569-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="3f569-107">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="3f569-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="3f569-108">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="3f569-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="3f569-109">安装预览版本</span><span class="sxs-lookup"><span data-stu-id="3f569-109">Installing Preview Releases</span></span>

<span data-ttu-id="3f569-110">通过包存储库安装适用于 Linux 的 PowerShell Core 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="3f569-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="3f569-111">直接下载安装不会更改包名称（文件名除外）。</span><span class="sxs-lookup"><span data-stu-id="3f569-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="3f569-112">下面是使用各种包管理器安装稳定包和预览包的命令表：</span><span class="sxs-lookup"><span data-stu-id="3f569-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="3f569-113">分配</span><span class="sxs-lookup"><span data-stu-id="3f569-113">Distribution(s)</span></span>|<span data-ttu-id="3f569-114">稳定包命令</span><span class="sxs-lookup"><span data-stu-id="3f569-114">Stable Command</span></span> | <span data-ttu-id="3f569-115">预览包命令</span><span class="sxs-lookup"><span data-stu-id="3f569-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="3f569-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="3f569-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="3f569-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="3f569-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="3f569-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="3f569-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="3f569-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="3f569-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="3f569-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3f569-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="3f569-121">通过包存储库安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3f569-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="3f569-122">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3f569-123">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3f569-123">This is the preferred method.</span></span>

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

<span data-ttu-id="3f569-124">以超级用户身份注册 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="3f569-125">此后，只需使用 `sudo apt-get upgrade powershell` 来更新安装。</span><span class="sxs-lookup"><span data-stu-id="3f569-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="3f569-126">通过直接下载进行安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3f569-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="3f569-127">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-127">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3f569-128">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3f569-129">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3f569-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3f569-130">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3f569-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="3f569-131">卸载 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3f569-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="3f569-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3f569-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="3f569-133">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3f569-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="3f569-134">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3f569-135">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3f569-135">This is the preferred method.</span></span>

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

<span data-ttu-id="3f569-136">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3f569-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="3f569-137">通过 Direct Download 的安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3f569-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="3f569-138">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-138">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3f569-139">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-139">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3f569-140">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3f569-140">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3f569-141">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3f569-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="3f569-142">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3f569-142">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="3f569-143">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3f569-143">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-144">`6.1.0-preview.2` 后添加了对 Ubuntu 18.04 的支持</span><span class="sxs-lookup"><span data-stu-id="3f569-144">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="3f569-145">通过包存储库安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3f569-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="3f569-146">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3f569-147">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3f569-147">This is the preferred method.</span></span>

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
pwsh-preview
```

<span data-ttu-id="3f569-148">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3f569-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="3f569-149">通过直接下载安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3f569-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="3f569-150">从[版本][]页中将 Debian 包 `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-150">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3f569-151">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-151">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3f569-152">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3f569-152">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3f569-153">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3f569-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="3f569-154">卸载 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3f569-154">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="3f569-155">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="3f569-155">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-156">自 `6.1.0-preview.3` 起添加了对 Ubuntu 18.10 的支持。</span><span class="sxs-lookup"><span data-stu-id="3f569-156">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="3f569-157">18.10 是一个每日内部版本，因此它仅可用于社区。</span><span class="sxs-lookup"><span data-stu-id="3f569-157">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="3f569-158">支持通过 `snapd` 按 18.10 版上进行安装。</span><span class="sxs-lookup"><span data-stu-id="3f569-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="3f569-159">有关完整说明，请参阅 [Snap 包][snap]；</span><span class="sxs-lookup"><span data-stu-id="3f569-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="3f569-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3f569-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="3f569-161">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="3f569-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="3f569-162">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3f569-163">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3f569-163">This is the preferred method.</span></span>

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

<span data-ttu-id="3f569-164">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3f569-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="3f569-165">通过直接下载进行安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="3f569-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="3f569-166">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.8_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-166">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3f569-167">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-167">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3f569-168">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="3f569-168">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3f569-169">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="3f569-169">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="3f569-170">卸载 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="3f569-170">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="3f569-171">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3f569-171">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="3f569-172">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3f569-172">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="3f569-173">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-173">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3f569-174">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3f569-174">This is the preferred method.</span></span>

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

<span data-ttu-id="3f569-175">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="3f569-175">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="3f569-176">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3f569-176">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="3f569-177">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.9_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-177">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3f569-178">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-178">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="3f569-179">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3f569-179">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="3f569-180">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3f569-180">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-181">此包也可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="3f569-181">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="3f569-182">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3f569-182">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="3f569-183">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-183">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3f569-184">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="3f569-184">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="3f569-185">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3f569-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="3f569-186">使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-186">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="3f569-187">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-187">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3f569-188">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3f569-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="3f569-189">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3f569-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3f569-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3f569-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3f569-192">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3f569-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3f569-193">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3f569-194">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="3f569-194">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3f569-195">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3f569-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3f569-196">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-196">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="3f569-197">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-197">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3f569-198">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3f569-198">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3f569-199">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3f569-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="3f569-200">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3f569-200">OpenSUSE 42.3</span></span>

<span data-ttu-id="3f569-201">安装 PowerShell Core 时，`zypper` 可能报告以下错误：</span><span class="sxs-lookup"><span data-stu-id="3f569-201">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="3f569-202">在这种情况下，通过检查以下命令将 `libcurl4` 包显示为已安装来验证存在兼容的 `libcurl` 库：</span><span class="sxs-lookup"><span data-stu-id="3f569-202">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="3f569-203">然后在安装 PowerShell 包时选择 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解决方案。</span><span class="sxs-lookup"><span data-stu-id="3f569-203">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="3f569-204">通过包存储库安装（首选）- OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3f569-204">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="3f569-205">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="3f569-206">通过直接下载进行安装 - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3f569-206">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="3f569-207">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 OpenSUSE 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3f569-208">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3f569-208">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="3f569-209">卸载 - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3f569-209">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="3f569-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="3f569-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-211">Fedora 28 仅在 PowerShell Core 6.1 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="3f569-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="3f569-212">通过包存储库安装（首选）- Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3f569-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3f569-213">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="3f569-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="3f569-214">通过直接下载进行安装 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3f569-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3f569-215">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-215">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="3f569-216">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-216">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3f569-217">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="3f569-217">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="3f569-218">卸载 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3f569-218">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="3f569-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3f569-219">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-220">Arch 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="3f569-220">Arch support is experimental.</span></span>

<span data-ttu-id="3f569-221">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3f569-221">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="3f569-222">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="3f569-222">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="3f569-223">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="3f569-223">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="3f569-224">可以使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="3f569-224">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="3f569-225">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="3f569-225">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="3f569-226">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="3f569-226">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="3f569-228">Snap 包</span><span class="sxs-lookup"><span data-stu-id="3f569-228">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="3f569-229">获取 snapd</span><span class="sxs-lookup"><span data-stu-id="3f569-229">Getting snapd</span></span>

<span data-ttu-id="3f569-230">需具备 `snapd` 才能运行 Snap。</span><span class="sxs-lookup"><span data-stu-id="3f569-230">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="3f569-231">按照[这些说明](https://docs.snapcraft.io/core/install)确保你已安装 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="3f569-231">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="3f569-232">通过 Snap 进行安装</span><span class="sxs-lookup"><span data-stu-id="3f569-232">Installation via Snap</span></span>

<span data-ttu-id="3f569-233">为简化安装（和更新），已向 [Snap 存储](https://snapcraft.io/store)发布 PowerShell Core for Linux。</span><span class="sxs-lookup"><span data-stu-id="3f569-233">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="3f569-234">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="3f569-234">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="3f569-235">安装 Snap 后将自动升级，但你可使用 `sudo snap refresh powershell-preview` 触发升级。</span><span class="sxs-lookup"><span data-stu-id="3f569-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="3f569-236">卸载</span><span class="sxs-lookup"><span data-stu-id="3f569-236">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="3f569-237">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="3f569-237">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-238">AppImage 支持是实验性的</span><span class="sxs-lookup"><span data-stu-id="3f569-238">AppImage support is experimental</span></span>

<span data-ttu-id="3f569-239">使用新的 Linux 分发版时，请从[版本][]页中将 AppImage `powershell-6.0.1-x86_64.AppImage`下载到 Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="3f569-239">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="3f569-240">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3f569-240">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="3f569-241">通过 [AppImage][] 无需安装即可运行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3f569-241">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="3f569-242">此款可移植应用程序将 PowerShell 及其依赖项（包括 .NET Core 的系统依赖项）捆绑到一个统一包中。</span><span class="sxs-lookup"><span data-stu-id="3f569-242">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="3f569-243">此包为单个二进制文件，独立于用户的 Linux 分发版运行。</span><span class="sxs-lookup"><span data-stu-id="3f569-243">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="3f569-245">Kali</span><span class="sxs-lookup"><span data-stu-id="3f569-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-246">Kali 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="3f569-246">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="3f569-247">安装</span><span class="sxs-lookup"><span data-stu-id="3f569-247">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="3f569-248">在最新版 Kali (Kali GNU/Linux Rolling) 中无需安装即可运行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f569-248">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="3f569-249">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="3f569-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="3f569-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3f569-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="3f569-251">Raspbian 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="3f569-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="3f569-252">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3f569-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="3f569-253">此外 CoreCLR（和 PowerShell Core）仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="3f569-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="3f569-254">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="3f569-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="3f569-255">安装</span><span class="sxs-lookup"><span data-stu-id="3f569-255">Installation</span></span>

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

<span data-ttu-id="3f569-256">或者可以创建能够启动 PowerShell 的符号链接，而无需指定到“pwsh”二进制文件的路径</span><span class="sxs-lookup"><span data-stu-id="3f569-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="3f569-257">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="3f569-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="3f569-258">二进制存档</span><span class="sxs-lookup"><span data-stu-id="3f569-258">Binary Archives</span></span>

<span data-ttu-id="3f569-259">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="3f569-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="3f569-260">依赖关系</span><span class="sxs-lookup"><span data-stu-id="3f569-260">Dependencies</span></span>

<span data-ttu-id="3f569-261">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="3f569-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="3f569-262">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，因此 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="3f569-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="3f569-263">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="3f569-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="3f569-264">操作系统</span><span class="sxs-lookup"><span data-stu-id="3f569-264">OS</span></span>                 | <span data-ttu-id="3f569-265">依赖关系</span><span class="sxs-lookup"><span data-stu-id="3f569-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="3f569-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3f569-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="3f569-267">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3f569-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3f569-268">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="3f569-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3f569-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3f569-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="3f569-270">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3f569-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3f569-271">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="3f569-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="3f569-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3f569-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="3f569-273">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3f569-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3f569-274">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="3f569-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="3f569-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3f569-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="3f569-276">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3f569-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3f569-277">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="3f569-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="3f569-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="3f569-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="3f569-279">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3f569-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3f569-280">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="3f569-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3f569-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="3f569-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="3f569-282">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3f569-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3f569-283">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="3f569-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="3f569-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3f569-284">CentOS 7</span></span> <br> <span data-ttu-id="3f569-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3f569-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="3f569-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="3f569-286">RHEL 7</span></span> <br> <span data-ttu-id="3f569-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3f569-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="3f569-288">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="3f569-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="3f569-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="3f569-289">Fedora 27</span></span> <br> <span data-ttu-id="3f569-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3f569-290">Fedora 28</span></span> | <span data-ttu-id="3f569-291">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="3f569-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="3f569-292">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="3f569-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="3f569-293">例如，[Amazon Linux dockerfile][amazon-dockerfile] 应先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="3f569-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="3f569-294">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="3f569-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="3f569-295">Linux</span><span class="sxs-lookup"><span data-stu-id="3f569-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="3f569-296">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="3f569-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="3f569-297">路径</span><span class="sxs-lookup"><span data-stu-id="3f569-297">Paths</span></span>

* <span data-ttu-id="3f569-298">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="3f569-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="3f569-299">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="3f569-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="3f569-300">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="3f569-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="3f569-301">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="3f569-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3f569-302">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="3f569-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3f569-303">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="3f569-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="3f569-304">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="3f569-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3f569-305">配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="3f569-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3f569-306">PowerShell 采用 Linux 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="3f569-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

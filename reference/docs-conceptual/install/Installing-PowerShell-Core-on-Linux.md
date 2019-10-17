---
title: 在 Linux 上安装 PowerShell Core
description: 介绍如何在各种 Linux 分发上安装 PowerShell Core
ms.date: 07/19/2019
ms.openlocfilehash: fc5a278f0fc10733a0d60fb856d0400332ba2719
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350195"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="11812-103">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="11812-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="11812-104">支持 [Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Ubuntu 19.04][u1904]、[Debian 8][deb8]、[Debian 9][deb9][CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="11812-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="11812-105">对于未获得官方支持的 Linux 分发，可尝试使用 [PowerShell Snap 包][snap]安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="11812-106">还可尝试直接使用 Linux [`tar.gz`存档][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置必要的依赖项。</span><span class="sxs-lookup"><span data-stu-id="11812-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="11812-107">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="11812-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="11812-108">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="11812-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="11812-109">若已安装 [预览版](#installing-preview-releases)，请运行 `pwsh-preview`。</span><span class="sxs-lookup"><span data-stu-id="11812-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="11812-110">安装预览版本</span><span class="sxs-lookup"><span data-stu-id="11812-110">Installing Preview Releases</span></span>

<span data-ttu-id="11812-111">通过包存储库安装适用于 Linux 的 PowerShell Core 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="11812-111">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="11812-112">直接下载安装不会更改包名称（文件名除外）。</span><span class="sxs-lookup"><span data-stu-id="11812-112">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="11812-113">下表包含使用各种包管理器安装稳定包和预览包的命令：</span><span class="sxs-lookup"><span data-stu-id="11812-113">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="11812-114">分配</span><span class="sxs-lookup"><span data-stu-id="11812-114">Distribution(s)</span></span>|<span data-ttu-id="11812-115">稳定包命令</span><span class="sxs-lookup"><span data-stu-id="11812-115">Stable Command</span></span> | <span data-ttu-id="11812-116">预览包命令</span><span class="sxs-lookup"><span data-stu-id="11812-116">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="11812-117">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="11812-117">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="11812-118">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="11812-118">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="11812-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="11812-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="11812-120">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="11812-120">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="11812-121">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="11812-121">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="11812-122">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="11812-122">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11812-123">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="11812-123">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="11812-124">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="11812-124">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11812-125">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-125">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="11812-126">通过直接下载进行安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="11812-126">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="11812-127">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-127">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="11812-128">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-128">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="11812-129">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="11812-129">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="11812-130">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="11812-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="11812-131">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="11812-131">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="11812-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="11812-132">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="11812-133">通过包存储库安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="11812-133">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="11812-134">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="11812-134">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11812-135">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="11812-135">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="11812-136">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="11812-136">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11812-137">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-137">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="11812-138">通过直接下载安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="11812-138">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="11812-139">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-139">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="11812-140">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-140">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="11812-141">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="11812-141">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="11812-142">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="11812-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="11812-143">卸载 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="11812-143">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="11812-144">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="11812-144">Ubuntu 18.10</span></span>

<span data-ttu-id="11812-145">安装是通过 `snapd` 受到支持。</span><span class="sxs-lookup"><span data-stu-id="11812-145">Installation is supported via `snapd`.</span></span> <span data-ttu-id="11812-146">有关说明，请参阅 [Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="11812-146">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="11812-147">Ubuntu 18.10 是[支持社区](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。</span><span class="sxs-lookup"><span data-stu-id="11812-147">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="11812-148">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="11812-148">Ubuntu 19.04</span></span>

<span data-ttu-id="11812-149">安装是通过 `snapd` 受到支持。</span><span class="sxs-lookup"><span data-stu-id="11812-149">Installation is supported via `snapd`.</span></span> <span data-ttu-id="11812-150">有关说明，请参阅 [Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="11812-150">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="11812-151">Ubuntu 19.04 是[社区支持](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。</span><span class="sxs-lookup"><span data-stu-id="11812-151">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="11812-152">Debian 8</span><span class="sxs-lookup"><span data-stu-id="11812-152">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="11812-153">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="11812-153">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="11812-154">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="11812-154">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11812-155">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="11812-155">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

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

<span data-ttu-id="11812-156">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="11812-156">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11812-157">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-157">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="11812-158">Debian 9</span><span class="sxs-lookup"><span data-stu-id="11812-158">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="11812-159">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="11812-159">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="11812-160">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="11812-160">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11812-161">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="11812-161">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

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

<span data-ttu-id="11812-162">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="11812-162">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11812-163">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-163">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="11812-164">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="11812-164">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="11812-165">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.debian.9_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-165">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="11812-166">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-166">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="11812-167">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="11812-167">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="11812-168">Debian 10</span><span class="sxs-lookup"><span data-stu-id="11812-168">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="11812-169">Debian 10 仅在 PowerShell 7.0 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="11812-169">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="11812-170">通过直接下载进行安装 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="11812-170">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="11812-171">从[版本][]页中将 tar.gz 包 `powershell_7.0.0-preview-7-linux-x64.tar.gz` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-171">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="11812-172">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-172">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="11812-173">Alpine 3.9 和 Alpine 3.10</span><span class="sxs-lookup"><span data-stu-id="11812-173">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="11812-174">Alpine 3.9 和 Alpine 3.10 仅在 PowerShell 7.0 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="11812-174">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="11812-175">通过直接下载进行安装 - Alpine 3.9 和 3.10</span><span class="sxs-lookup"><span data-stu-id="11812-175">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="11812-176">从[版本][]页中将 tar.gz 包 `powershell_7.0.0-preview-7-linux-x64.tar.gz` 下载到 Alpine 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-176">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="11812-177">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-177">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="centos-7"></a><span data-ttu-id="11812-178">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11812-178">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="11812-179">此包可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="11812-179">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="11812-180">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11812-180">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="11812-181">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="11812-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="11812-182">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="11812-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11812-183">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="11812-184">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11812-184">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="11812-185">使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-185">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="11812-186">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="11812-187">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="11812-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="11812-188">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11812-188">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11812-190">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11812-190">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11812-191">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11812-191">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="11812-192">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="11812-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="11812-193">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="11812-193">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11812-194">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-194">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11812-195">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11812-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="11812-196">从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-196">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="11812-197">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-197">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="11812-198">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="11812-198">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11812-199">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11812-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="11812-200">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="11812-200">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="11812-201">安装 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="11812-201">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="11812-202">安装 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="11812-202">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="11812-203">卸载 - OpenSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="11812-203">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="11812-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="11812-204">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="11812-205">Fedora 28 仅在 PowerShell Core 6.1 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="11812-205">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="11812-206">Fedora 29 和 Fedora 30 仅在 PowerShell 7.0 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="11812-206">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="11812-207">通过包存储库安装（首选）- Fedora 28、Fedora 29 和 Fedora 30</span><span class="sxs-lookup"><span data-stu-id="11812-207">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="11812-208">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="11812-208">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="11812-209">通过直接下载进行安装 - Fedora 28、Fedora 29 和 Fedora 30</span><span class="sxs-lookup"><span data-stu-id="11812-209">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="11812-210">从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。</span><span class="sxs-lookup"><span data-stu-id="11812-210">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="11812-211">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="11812-211">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="11812-212">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="11812-212">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="11812-213">卸载 - Fedora 28、Fedora 29 和 Fedora 30</span><span class="sxs-lookup"><span data-stu-id="11812-213">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="11812-214">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="11812-214">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="11812-215">Arch 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="11812-215">Arch support is experimental.</span></span>

<span data-ttu-id="11812-216">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-216">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="11812-217">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="11812-217">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="11812-218">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="11812-218">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="11812-219">可使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="11812-219">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="11812-220">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="11812-220">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="11812-221">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="11812-221">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="11812-223">Snap 包</span><span class="sxs-lookup"><span data-stu-id="11812-223">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="11812-224">获取 snapd</span><span class="sxs-lookup"><span data-stu-id="11812-224">Getting snapd</span></span>

<span data-ttu-id="11812-225">需具备 `snapd` 才能运行 Snap。</span><span class="sxs-lookup"><span data-stu-id="11812-225">`snapd` is required to run snaps.</span></span> <span data-ttu-id="11812-226">按照[这些说明](https://docs.snapcraft.io/core/install)确保你已安装 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="11812-226">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="11812-227">通过 Snap 进行安装</span><span class="sxs-lookup"><span data-stu-id="11812-227">Installation via Snap</span></span>

<span data-ttu-id="11812-228">为简化安装和更新，已向 [Snap 存储](https://snapcraft.io/store)发布 PowerShell Core for Linux。</span><span class="sxs-lookup"><span data-stu-id="11812-228">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="11812-229">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="11812-229">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="11812-230">若要安装预览版本，请使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="11812-230">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="11812-231">安装完成后，Snap 将自动升级。</span><span class="sxs-lookup"><span data-stu-id="11812-231">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="11812-232">可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 触发升级。</span><span class="sxs-lookup"><span data-stu-id="11812-232">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="11812-233">卸载</span><span class="sxs-lookup"><span data-stu-id="11812-233">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="11812-234">或</span><span class="sxs-lookup"><span data-stu-id="11812-234">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="11812-235">Kali</span><span class="sxs-lookup"><span data-stu-id="11812-235">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="11812-236">安装 - Kali</span><span class="sxs-lookup"><span data-stu-id="11812-236">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="11812-237">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="11812-237">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="11812-238">Raspbian</span><span class="sxs-lookup"><span data-stu-id="11812-238">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="11812-239">Raspbian 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="11812-239">Raspbian support is experimental.</span></span>

<span data-ttu-id="11812-240">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="11812-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="11812-241">CoreCLR 和 PowerShell Core 仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="11812-241">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="11812-242">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="11812-242">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="11812-243">安装 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="11812-243">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="11812-244">或者，可以创建可启动 PowerShell 的符号链接，而无需指定到 `pwsh` 二进制文件的路径。</span><span class="sxs-lookup"><span data-stu-id="11812-244">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="11812-245">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="11812-245">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="11812-246">二进制存档</span><span class="sxs-lookup"><span data-stu-id="11812-246">Binary Archives</span></span>

<span data-ttu-id="11812-247">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="11812-247">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="11812-248">依赖项</span><span class="sxs-lookup"><span data-stu-id="11812-248">Dependencies</span></span>

<span data-ttu-id="11812-249">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="11812-249">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="11812-250">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，并且 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="11812-250">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="11812-251">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="11812-251">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="11812-252">操作系统</span><span class="sxs-lookup"><span data-stu-id="11812-252">OS</span></span>                 | <span data-ttu-id="11812-253">依赖项</span><span class="sxs-lookup"><span data-stu-id="11812-253">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="11812-254">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="11812-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="11812-255">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="11812-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11812-256">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="11812-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="11812-257">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="11812-257">Ubuntu 17.10</span></span>       | <span data-ttu-id="11812-258">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="11812-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11812-259">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="11812-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="11812-260">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="11812-260">Ubuntu 18.04</span></span>       | <span data-ttu-id="11812-261">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="11812-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11812-262">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="11812-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="11812-263">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="11812-263">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="11812-264">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="11812-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11812-265">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="11812-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="11812-266">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="11812-266">Debian 9 (Stretch)</span></span> | <span data-ttu-id="11812-267">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="11812-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11812-268">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="11812-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="11812-269">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11812-269">CentOS 7</span></span> <br> <span data-ttu-id="11812-270">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="11812-270">Oracle Linux 7</span></span> <br> <span data-ttu-id="11812-271">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="11812-271">RHEL 7</span></span> | <span data-ttu-id="11812-272">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="11812-272">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="11812-273">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="11812-273">openSUSE 42.3</span></span> | <span data-ttu-id="11812-274">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="11812-274">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="11812-275">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="11812-275">openSUSE Leap 15</span></span> | <span data-ttu-id="11812-276">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="11812-276">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="11812-277">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="11812-277">Fedora 27</span></span> <br> <span data-ttu-id="11812-278">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="11812-278">Fedora 28</span></span> | <span data-ttu-id="11812-279">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="11812-279">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="11812-280">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="11812-280">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="11812-281">例如，[Amazon Linux dockerfile][amazon-dockerfile] 先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="11812-281">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="11812-282">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="11812-282">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="11812-283">Linux</span><span class="sxs-lookup"><span data-stu-id="11812-283">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="11812-284">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="11812-284">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="11812-285">路径</span><span class="sxs-lookup"><span data-stu-id="11812-285">Paths</span></span>

* <span data-ttu-id="11812-286">`$PSHOME` 是 `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="11812-286">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="11812-287">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="11812-287">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="11812-288">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="11812-288">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="11812-289">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="11812-289">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="11812-290">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="11812-290">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="11812-291">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="11812-291">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="11812-292">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="11812-292">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="11812-293">配置文件采用 PowerShell 的按主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="11812-293">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="11812-294">PowerShell 采用 Linux 上的 [XDG 基目录规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="11812-294">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

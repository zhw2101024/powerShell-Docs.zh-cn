---
title: 在 Linux 上安装 PowerShell Core
description: 介绍如何在各种 Linux 分发上安装 PowerShell Core
ms.date: 07/19/2019
ms.openlocfilehash: 7d7c9a9f915f0a6e735a7baec1ec56e9c205a155
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848187"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="45f3e-103">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="45f3e-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="45f3e-104">支持 [Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Ubuntu 19.04][u1904]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="45f3e-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="45f3e-105">对于未获得官方支持的 Linux 分发，可尝试使用 [PowerShell Snap 包][snap]安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="45f3e-106">还可尝试直接使用 Linux [`tar.gz`存档][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置必要的依赖项。</span><span class="sxs-lookup"><span data-stu-id="45f3e-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="45f3e-107">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="45f3e-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="45f3e-108">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="45f3e-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="45f3e-109">安装预览版本</span><span class="sxs-lookup"><span data-stu-id="45f3e-109">Installing Preview Releases</span></span>

<span data-ttu-id="45f3e-110">通过包存储库安装适用于 Linux 的 PowerShell Core 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="45f3e-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="45f3e-111">直接下载安装不会更改包名称（文件名除外）。</span><span class="sxs-lookup"><span data-stu-id="45f3e-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="45f3e-112">下表包含使用各种包管理器安装稳定包和预览包的命令：</span><span class="sxs-lookup"><span data-stu-id="45f3e-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="45f3e-113">分配</span><span class="sxs-lookup"><span data-stu-id="45f3e-113">Distribution(s)</span></span>|<span data-ttu-id="45f3e-114">稳定包命令</span><span class="sxs-lookup"><span data-stu-id="45f3e-114">Stable Command</span></span> | <span data-ttu-id="45f3e-115">预览包命令</span><span class="sxs-lookup"><span data-stu-id="45f3e-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="45f3e-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="45f3e-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="45f3e-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="45f3e-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="45f3e-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="45f3e-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="45f3e-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="45f3e-120">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="45f3e-121">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="45f3e-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="45f3e-122">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="45f3e-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="45f3e-123">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="45f3e-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="45f3e-124">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="45f3e-125">通过直接下载进行安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="45f3e-126">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="45f3e-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="45f3e-127">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="45f3e-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="45f3e-128">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="45f3e-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="45f3e-129">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="45f3e-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="45f3e-130">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="45f3e-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="45f3e-132">通过包存储库安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="45f3e-133">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="45f3e-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="45f3e-134">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="45f3e-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="45f3e-135">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="45f3e-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="45f3e-136">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="45f3e-137">通过直接下载安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="45f3e-138">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="45f3e-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="45f3e-139">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="45f3e-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="45f3e-140">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="45f3e-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="45f3e-141">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="45f3e-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="45f3e-142">卸载 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="45f3e-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="45f3e-143">Ubuntu 18.10</span></span>

<span data-ttu-id="45f3e-144">安装是通过 `snapd` 受到支持。</span><span class="sxs-lookup"><span data-stu-id="45f3e-144">Installation is supported via `snapd`.</span></span> <span data-ttu-id="45f3e-145">有关说明，请参阅 [Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="45f3e-145">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="45f3e-146">Ubuntu 18.10 是[支持社区](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。</span><span class="sxs-lookup"><span data-stu-id="45f3e-146">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="45f3e-147">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-147">Ubuntu 19.04</span></span>

<span data-ttu-id="45f3e-148">安装是通过 `snapd` 受到支持。</span><span class="sxs-lookup"><span data-stu-id="45f3e-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="45f3e-149">有关说明，请参阅 [Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="45f3e-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="45f3e-150">Ubuntu 19.04 是[社区支持](../powershell-support-lifecycle.md)的[过渡版本](https://www.ubuntu.com/about/release-cycle)。</span><span class="sxs-lookup"><span data-stu-id="45f3e-150">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="45f3e-151">Debian 8</span><span class="sxs-lookup"><span data-stu-id="45f3e-151">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="45f3e-152">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="45f3e-152">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="45f3e-153">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="45f3e-153">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="45f3e-154">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="45f3e-154">The preferred method is as follows:</span></span>

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

<span data-ttu-id="45f3e-155">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="45f3e-155">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="45f3e-156">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-156">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="45f3e-157">Debian 9</span><span class="sxs-lookup"><span data-stu-id="45f3e-157">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="45f3e-158">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="45f3e-158">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="45f3e-159">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="45f3e-159">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="45f3e-160">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="45f3e-160">The preferred method is as follows:</span></span>

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

<span data-ttu-id="45f3e-161">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="45f3e-161">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="45f3e-162">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-162">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="45f3e-163">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="45f3e-163">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="45f3e-164">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.debian.9_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="45f3e-164">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="45f3e-165">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="45f3e-165">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="45f3e-166">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="45f3e-166">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="45f3e-167">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-167">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="45f3e-168">此包可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="45f3e-168">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="45f3e-169">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-169">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="45f3e-170">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="45f3e-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="45f3e-171">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="45f3e-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="45f3e-172">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-172">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="45f3e-173">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-173">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="45f3e-174">使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="45f3e-174">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="45f3e-175">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="45f3e-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="45f3e-176">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="45f3e-176">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="45f3e-177">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-177">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="45f3e-179">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-179">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="45f3e-180">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-180">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="45f3e-181">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="45f3e-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="45f3e-182">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="45f3e-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="45f3e-183">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="45f3e-184">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-184">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="45f3e-185">从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="45f3e-185">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="45f3e-186">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="45f3e-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="45f3e-187">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="45f3e-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="45f3e-188">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-188">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="45f3e-189">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="45f3e-189">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="45f3e-190">安装 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="45f3e-190">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="45f3e-191">安装 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="45f3e-191">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="45f3e-192">卸载 - OpenSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="45f3e-192">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="45f3e-193">Fedora</span><span class="sxs-lookup"><span data-stu-id="45f3e-193">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="45f3e-194">Fedora 28 仅在 PowerShell Core 6.1 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="45f3e-194">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="45f3e-195">通过包存储库安装（首选）- Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="45f3e-195">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="45f3e-196">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="45f3e-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="45f3e-197">通过直接下载进行安装 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="45f3e-197">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="45f3e-198">从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。</span><span class="sxs-lookup"><span data-stu-id="45f3e-198">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="45f3e-199">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="45f3e-199">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="45f3e-200">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="45f3e-200">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="45f3e-201">卸载 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="45f3e-201">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="45f3e-202">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="45f3e-202">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="45f3e-203">Arch 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="45f3e-203">Arch support is experimental.</span></span>

<span data-ttu-id="45f3e-204">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="45f3e-205">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="45f3e-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="45f3e-206">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="45f3e-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="45f3e-207">可使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="45f3e-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="45f3e-208">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="45f3e-208">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="45f3e-209">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="45f3e-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="45f3e-211">Snap 包</span><span class="sxs-lookup"><span data-stu-id="45f3e-211">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="45f3e-212">获取 snapd</span><span class="sxs-lookup"><span data-stu-id="45f3e-212">Getting snapd</span></span>

<span data-ttu-id="45f3e-213">需具备 `snapd` 才能运行 Snap。</span><span class="sxs-lookup"><span data-stu-id="45f3e-213">`snapd` is required to run snaps.</span></span> <span data-ttu-id="45f3e-214">按照[这些说明](https://docs.snapcraft.io/core/install)确保你已安装 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="45f3e-214">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="45f3e-215">通过 Snap 进行安装</span><span class="sxs-lookup"><span data-stu-id="45f3e-215">Installation via Snap</span></span>

<span data-ttu-id="45f3e-216">为简化安装和更新，已向 [Snap 存储](https://snapcraft.io/store)发布 PowerShell Core for Linux。</span><span class="sxs-lookup"><span data-stu-id="45f3e-216">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="45f3e-217">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="45f3e-217">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="45f3e-218">若要安装预览版本，请使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="45f3e-218">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="45f3e-219">安装完成后，Snap 将自动升级。</span><span class="sxs-lookup"><span data-stu-id="45f3e-219">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="45f3e-220">可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 触发升级。</span><span class="sxs-lookup"><span data-stu-id="45f3e-220">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="45f3e-221">卸载</span><span class="sxs-lookup"><span data-stu-id="45f3e-221">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="45f3e-222">或</span><span class="sxs-lookup"><span data-stu-id="45f3e-222">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="45f3e-223">Kali</span><span class="sxs-lookup"><span data-stu-id="45f3e-223">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="45f3e-224">安装 - Kali</span><span class="sxs-lookup"><span data-stu-id="45f3e-224">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="45f3e-225">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="45f3e-225">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="45f3e-226">Raspbian</span><span class="sxs-lookup"><span data-stu-id="45f3e-226">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="45f3e-227">Raspbian 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="45f3e-227">Raspbian support is experimental.</span></span>

<span data-ttu-id="45f3e-228">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45f3e-228">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="45f3e-229">CoreCLR 和 PowerShell Core 仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="45f3e-229">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="45f3e-230">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="45f3e-230">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="45f3e-231">安装 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="45f3e-231">Installation - Raspbian</span></span>

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

<span data-ttu-id="45f3e-232">或者，可以创建可启动 PowerShell 的符号链接，而无需指定到 `pwsh` 二进制文件的路径。</span><span class="sxs-lookup"><span data-stu-id="45f3e-232">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="45f3e-233">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="45f3e-233">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="45f3e-234">二进制存档</span><span class="sxs-lookup"><span data-stu-id="45f3e-234">Binary Archives</span></span>

<span data-ttu-id="45f3e-235">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="45f3e-235">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="45f3e-236">依赖项</span><span class="sxs-lookup"><span data-stu-id="45f3e-236">Dependencies</span></span>

<span data-ttu-id="45f3e-237">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="45f3e-237">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="45f3e-238">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，并且 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="45f3e-238">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="45f3e-239">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="45f3e-239">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="45f3e-240">操作系统</span><span class="sxs-lookup"><span data-stu-id="45f3e-240">OS</span></span>                 | <span data-ttu-id="45f3e-241">依赖项</span><span class="sxs-lookup"><span data-stu-id="45f3e-241">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="45f3e-242">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-242">Ubuntu 16.04</span></span>       | <span data-ttu-id="45f3e-243">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="45f3e-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="45f3e-244">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="45f3e-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="45f3e-245">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="45f3e-245">Ubuntu 17.10</span></span>       | <span data-ttu-id="45f3e-246">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="45f3e-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="45f3e-247">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="45f3e-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="45f3e-248">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="45f3e-248">Ubuntu 18.04</span></span>       | <span data-ttu-id="45f3e-249">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="45f3e-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="45f3e-250">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="45f3e-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="45f3e-251">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="45f3e-251">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="45f3e-252">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="45f3e-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="45f3e-253">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="45f3e-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="45f3e-254">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="45f3e-254">Debian 9 (Stretch)</span></span> | <span data-ttu-id="45f3e-255">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="45f3e-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="45f3e-256">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="45f3e-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="45f3e-257">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-257">CentOS 7</span></span> <br> <span data-ttu-id="45f3e-258">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-258">Oracle Linux 7</span></span> <br> <span data-ttu-id="45f3e-259">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="45f3e-259">RHEL 7</span></span> | <span data-ttu-id="45f3e-260">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="45f3e-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="45f3e-261">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="45f3e-261">openSUSE 42.3</span></span> | <span data-ttu-id="45f3e-262">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="45f3e-262">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="45f3e-263">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="45f3e-263">openSUSE Leap 15</span></span> | <span data-ttu-id="45f3e-264">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="45f3e-264">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="45f3e-265">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="45f3e-265">Fedora 27</span></span> <br> <span data-ttu-id="45f3e-266">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="45f3e-266">Fedora 28</span></span> | <span data-ttu-id="45f3e-267">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="45f3e-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="45f3e-268">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="45f3e-268">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="45f3e-269">例如，[Amazon Linux dockerfile][amazon-dockerfile] 先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="45f3e-269">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="45f3e-270">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="45f3e-270">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="45f3e-271">Linux</span><span class="sxs-lookup"><span data-stu-id="45f3e-271">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="45f3e-272">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="45f3e-272">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="45f3e-273">路径</span><span class="sxs-lookup"><span data-stu-id="45f3e-273">Paths</span></span>

* <span data-ttu-id="45f3e-274">`$PSHOME` 是 `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="45f3e-274">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="45f3e-275">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="45f3e-275">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="45f3e-276">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="45f3e-276">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="45f3e-277">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="45f3e-277">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="45f3e-278">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="45f3e-278">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="45f3e-279">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="45f3e-279">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="45f3e-280">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="45f3e-280">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="45f3e-281">配置文件采用 PowerShell 的按主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="45f3e-281">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="45f3e-282">PowerShell 采用 Linux 上的 [XDG 基目录规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="45f3e-282">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

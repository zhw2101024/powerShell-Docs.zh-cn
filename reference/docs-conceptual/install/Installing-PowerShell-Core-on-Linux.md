---
title: 在 Linux 上安装 PowerShell Core
description: 介绍如何在各种 Linux 分发上安装 PowerShell Core
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372194"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="26773-103">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="26773-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="26773-104">支持 [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Debian 9][deb9],
 [CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse], [Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="26773-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="26773-105">对于未获得官方支持的 Linux 分发，可尝试使用 [PowerShell Snap 包][snap]安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="26773-106">还可尝试直接使用 Linux [`tar.gz` archive][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置必要的依赖项。</span><span class="sxs-lookup"><span data-stu-id="26773-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="26773-107">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="26773-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="26773-108">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="26773-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="26773-109">安装预览版本</span><span class="sxs-lookup"><span data-stu-id="26773-109">Installing Preview Releases</span></span>

<span data-ttu-id="26773-110">通过包存储库安装适用于 Linux 的 PowerShell Core 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="26773-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="26773-111">直接下载安装不会更改包名称（文件名除外）。</span><span class="sxs-lookup"><span data-stu-id="26773-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="26773-112">下表包含使用各种包管理器安装稳定包和预览包的命令：</span><span class="sxs-lookup"><span data-stu-id="26773-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="26773-113">分配</span><span class="sxs-lookup"><span data-stu-id="26773-113">Distribution(s)</span></span>|<span data-ttu-id="26773-114">稳定包命令</span><span class="sxs-lookup"><span data-stu-id="26773-114">Stable Command</span></span> | <span data-ttu-id="26773-115">预览包命令</span><span class="sxs-lookup"><span data-stu-id="26773-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="26773-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="26773-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="26773-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="26773-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="26773-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="26773-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="26773-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="26773-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="26773-120">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="26773-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="26773-121">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="26773-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="26773-122">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="26773-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="26773-123">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="26773-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="26773-124">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="26773-125">通过 Direct Download 的安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="26773-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="26773-126">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="26773-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="26773-127">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26773-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="26773-128">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="26773-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="26773-129">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="26773-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="26773-130">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="26773-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="26773-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="26773-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="26773-132">通过包存储库安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="26773-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="26773-133">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="26773-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="26773-134">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="26773-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="26773-135">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="26773-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="26773-136">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="26773-137">通过直接下载安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="26773-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="26773-138">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="26773-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="26773-139">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26773-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="26773-140">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="26773-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="26773-141">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="26773-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="26773-142">卸载 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="26773-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="26773-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="26773-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="26773-144">因为 18.10 是[过渡版本](https://www.ubuntu.com/about/release-cycle)，所以它仅[支持社区](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="26773-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="26773-145">支持通过 `snapd` 按 18.10 版上进行安装。</span><span class="sxs-lookup"><span data-stu-id="26773-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="26773-146">有关完整说明，请参阅 [Snap 包][snap]；</span><span class="sxs-lookup"><span data-stu-id="26773-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="26773-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="26773-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="26773-148">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="26773-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="26773-149">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="26773-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="26773-150">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="26773-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="26773-151">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="26773-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="26773-152">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="26773-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="26773-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="26773-154">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="26773-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="26773-155">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="26773-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="26773-156">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="26773-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="26773-157">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="26773-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="26773-158">注册后，可以通过 `sudo apt-get upgrade powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="26773-159">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="26773-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="26773-160">从[版本][]页中将 Debian 包 `powershell_6.2.0-1.debian.9_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="26773-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="26773-161">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26773-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="26773-162">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="26773-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="26773-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="26773-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="26773-164">此包可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="26773-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="26773-165">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="26773-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="26773-166">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="26773-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="26773-167">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="26773-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="26773-168">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="26773-169">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="26773-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="26773-170">使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="26773-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="26773-171">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26773-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="26773-172">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="26773-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="26773-173">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="26773-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="26773-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="26773-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="26773-176">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="26773-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="26773-177">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="26773-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="26773-178">以超级用户身份注册 Microsoft 存储库一次。</span><span class="sxs-lookup"><span data-stu-id="26773-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="26773-179">注册后，可以通过 `sudo yum update powershell` 更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="26773-180">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="26773-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="26773-181">从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="26773-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="26773-182">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26773-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="26773-183">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="26773-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="26773-184">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="26773-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="26773-185">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="26773-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="26773-186">安装 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="26773-186">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="26773-187">安装 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="26773-187">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="26773-188">卸载 - OpenSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="26773-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="26773-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="26773-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="26773-190">Fedora 28 仅在 PowerShell Core 6.1 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="26773-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="26773-191">通过包存储库安装（首选）- Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="26773-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="26773-192">为简化安装和更新，已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="26773-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="26773-193">通过直接下载进行安装 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="26773-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="26773-194">从[版本][]页中将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。</span><span class="sxs-lookup"><span data-stu-id="26773-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="26773-195">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="26773-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="26773-196">无需该中间下载步骤即可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="26773-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="26773-197">卸载 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="26773-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="26773-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="26773-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="26773-199">Arch 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="26773-199">Arch support is experimental.</span></span>

<span data-ttu-id="26773-200">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="26773-201">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="26773-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="26773-202">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="26773-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="26773-203">可使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="26773-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="26773-204">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="26773-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="26773-205">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="26773-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="26773-207">Snap 包</span><span class="sxs-lookup"><span data-stu-id="26773-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="26773-208">获取 snapd</span><span class="sxs-lookup"><span data-stu-id="26773-208">Getting snapd</span></span>

<span data-ttu-id="26773-209">需具备 `snapd` 才能运行 Snap。</span><span class="sxs-lookup"><span data-stu-id="26773-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="26773-210">按照[这些说明](https://docs.snapcraft.io/core/install)确保你已安装 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="26773-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="26773-211">通过 Snap 进行安装</span><span class="sxs-lookup"><span data-stu-id="26773-211">Installation via Snap</span></span>

<span data-ttu-id="26773-212">为简化安装和更新，已向 [Snap 存储](https://snapcraft.io/store)发布 PowerShell Core for Linux。</span><span class="sxs-lookup"><span data-stu-id="26773-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="26773-213">首选方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="26773-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="26773-214">若要安装预览版本，请使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="26773-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="26773-215">安装完成后，Snap 将自动升级。</span><span class="sxs-lookup"><span data-stu-id="26773-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="26773-216">可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 触发升级。</span><span class="sxs-lookup"><span data-stu-id="26773-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="26773-217">卸载</span><span class="sxs-lookup"><span data-stu-id="26773-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="26773-218">或</span><span class="sxs-lookup"><span data-stu-id="26773-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="26773-219">Kali</span><span class="sxs-lookup"><span data-stu-id="26773-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="26773-220">安装 - Kali</span><span class="sxs-lookup"><span data-stu-id="26773-220">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="26773-221">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="26773-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="26773-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="26773-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="26773-223">Raspbian 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="26773-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="26773-224">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="26773-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="26773-225">CoreCLR 和 PowerShell Core 仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="26773-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="26773-226">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="26773-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="26773-227">安装 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="26773-227">Installation - Raspbian</span></span>

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

<span data-ttu-id="26773-228">或者，可以创建可启动 PowerShell 的符号链接，而无需指定到 `pwsh` 二进制文件的路径。</span><span class="sxs-lookup"><span data-stu-id="26773-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="26773-229">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="26773-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="26773-230">二进制存档</span><span class="sxs-lookup"><span data-stu-id="26773-230">Binary Archives</span></span>

<span data-ttu-id="26773-231">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="26773-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="26773-232">依赖关系</span><span class="sxs-lookup"><span data-stu-id="26773-232">Dependencies</span></span>

<span data-ttu-id="26773-233">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="26773-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="26773-234">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，并且 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="26773-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="26773-235">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="26773-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="26773-236">操作系统</span><span class="sxs-lookup"><span data-stu-id="26773-236">OS</span></span>                 | <span data-ttu-id="26773-237">依赖关系</span><span class="sxs-lookup"><span data-stu-id="26773-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="26773-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="26773-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="26773-239">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="26773-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="26773-240">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="26773-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="26773-241">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="26773-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="26773-242">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="26773-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="26773-243">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="26773-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="26773-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="26773-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="26773-245">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="26773-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="26773-246">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="26773-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="26773-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="26773-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="26773-248">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="26773-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="26773-249">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="26773-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="26773-250">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="26773-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="26773-251">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="26773-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="26773-252">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="26773-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="26773-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="26773-253">CentOS 7</span></span> <br> <span data-ttu-id="26773-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="26773-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="26773-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="26773-255">RHEL 7</span></span> | <span data-ttu-id="26773-256">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="26773-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="26773-257">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="26773-257">openSUSE 42.3</span></span> | <span data-ttu-id="26773-258">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="26773-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="26773-259">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="26773-259">openSUSE Leap 15</span></span> | <span data-ttu-id="26773-260">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="26773-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="26773-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="26773-261">Fedora 27</span></span> <br> <span data-ttu-id="26773-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="26773-262">Fedora 28</span></span> | <span data-ttu-id="26773-263">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="26773-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="26773-264">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="26773-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="26773-265">例如，[Amazon Linux dockerfile][amazon-dockerfile] 先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="26773-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="26773-266">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="26773-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="26773-267">Linux</span><span class="sxs-lookup"><span data-stu-id="26773-267">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="26773-268">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="26773-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="26773-269">路径</span><span class="sxs-lookup"><span data-stu-id="26773-269">Paths</span></span>

* <span data-ttu-id="26773-270">`$PSHOME` 是 `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="26773-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="26773-271">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="26773-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="26773-272">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="26773-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="26773-273">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="26773-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="26773-274">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="26773-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="26773-275">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="26773-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="26773-276">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="26773-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="26773-277">配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="26773-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="26773-278">PowerShell 采用 Linux 上的 [XDG 基目录规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="26773-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

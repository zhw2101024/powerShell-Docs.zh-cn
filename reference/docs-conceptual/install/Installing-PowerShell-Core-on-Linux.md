---
title: 在 Linux 上安装 PowerShell Core
description: 介绍如何在各种 Linux 分发上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 32d6c0e718ca798af2f6a5d796c3ca362e7befd9
ms.sourcegitcommit: 13e170e8bff29d3d5f854c874de88f53c5e5ef20
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67829441"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="133f0-103">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="133f0-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="133f0-104">支持 [Ubuntu 14.04][u14], [Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810],  [Debian 9][deb9],
[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse],
[Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="133f0-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9],
[CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse],
[Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="133f0-105">对于未获得官方支持的 Linux 分发，可尝试使用 [PowerShell Snap 包][snap]。</span><span class="sxs-lookup"><span data-stu-id="133f0-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="133f0-106">还可尝试直接使用 Linux [`tar.gz` archive][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置必要的依赖项。</span><span class="sxs-lookup"><span data-stu-id="133f0-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="133f0-107">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="133f0-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="133f0-108">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="133f0-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
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

## <a name="installing-preview-releases"></a><span data-ttu-id="133f0-109">安装预览版本</span><span class="sxs-lookup"><span data-stu-id="133f0-109">Installing Preview Releases</span></span>

<span data-ttu-id="133f0-110">通过包存储库安装适用于 Linux 的 PowerShell Core 预览版本时，包名称从 `powershell` 更改为 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="133f0-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="133f0-111">直接下载安装不会更改包名称（文件名除外）。</span><span class="sxs-lookup"><span data-stu-id="133f0-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="133f0-112">下面是使用各种包管理器安装稳定包和预览包的命令表：</span><span class="sxs-lookup"><span data-stu-id="133f0-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="133f0-113">分配</span><span class="sxs-lookup"><span data-stu-id="133f0-113">Distribution(s)</span></span>|<span data-ttu-id="133f0-114">稳定包命令</span><span class="sxs-lookup"><span data-stu-id="133f0-114">Stable Command</span></span> | <span data-ttu-id="133f0-115">预览包命令</span><span class="sxs-lookup"><span data-stu-id="133f0-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="133f0-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="133f0-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="133f0-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="133f0-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="133f0-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="133f0-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="133f0-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="133f0-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="133f0-120">通过包存储库安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="133f0-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="133f0-121">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="133f0-122">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="133f0-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="133f0-123">以超级用户身份注册 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="133f0-124">此后，只需使用 `sudo apt-get upgrade powershell` 来更新安装。</span><span class="sxs-lookup"><span data-stu-id="133f0-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="133f0-125">通过直接下载进行安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="133f0-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="133f0-126">从以下位置将 Debian 包 `powershell_6.2.0-1.ubuntu.14.04_amd64.deb` 下载到 Debian 计算机：</span><span class="sxs-lookup"><span data-stu-id="133f0-126">Download the Debian package `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="133f0-127">[版本][]页。</span><span class="sxs-lookup"><span data-stu-id="133f0-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="133f0-128">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="133f0-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="133f0-129">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="133f0-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="133f0-130">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="133f0-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="133f0-131">卸载 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="133f0-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="133f0-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="133f0-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="133f0-133">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="133f0-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="133f0-134">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="133f0-135">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="133f0-135">This is the preferred method.</span></span>

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

<span data-ttu-id="133f0-136">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="133f0-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="133f0-137">通过 Direct Download 的安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="133f0-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="133f0-138">从以下位置将 Debian 包 `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` 下载到 Debian 计算机：</span><span class="sxs-lookup"><span data-stu-id="133f0-138">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="133f0-139">[版本][]页。</span><span class="sxs-lookup"><span data-stu-id="133f0-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="133f0-140">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="133f0-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="133f0-141">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="133f0-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="133f0-142">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="133f0-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="133f0-143">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="133f0-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="133f0-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="133f0-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="133f0-145">通过包存储库安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="133f0-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="133f0-146">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="133f0-147">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="133f0-147">This is the preferred method.</span></span>

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

<span data-ttu-id="133f0-148">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="133f0-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="133f0-149">通过直接下载安装 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="133f0-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="133f0-150">从以下位置将 Debian 包 `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` 下载到 Debian 计算机：</span><span class="sxs-lookup"><span data-stu-id="133f0-150">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="133f0-151">[版本][]页。</span><span class="sxs-lookup"><span data-stu-id="133f0-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="133f0-152">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="133f0-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="133f0-153">`dpkg -i` 命令失败，未满足依赖项。</span><span class="sxs-lookup"><span data-stu-id="133f0-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="133f0-154">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="133f0-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="133f0-155">卸载 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="133f0-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="133f0-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="133f0-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="133f0-157">因为 18.10 是[过渡版本](https://www.ubuntu.com/about/release-cycle)，所以它仅[支持社区](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="133f0-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="133f0-158">支持通过 `snapd` 按 18.10 版上进行安装。</span><span class="sxs-lookup"><span data-stu-id="133f0-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="133f0-159">有关完整说明，请参阅 [Snap 包][snap]；</span><span class="sxs-lookup"><span data-stu-id="133f0-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="133f0-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="133f0-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="133f0-161">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="133f0-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="133f0-162">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="133f0-163">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="133f0-163">This is the preferred method.</span></span>

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

<span data-ttu-id="133f0-164">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="133f0-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="133f0-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="133f0-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="133f0-166">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="133f0-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="133f0-167">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="133f0-168">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="133f0-168">This is the preferred method.</span></span>

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

<span data-ttu-id="133f0-169">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="133f0-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="133f0-170">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="133f0-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="133f0-171">从以下位置将 Debian 包 `powershell_6.2.0-1.debian.9_amd64.deb` 下载到 Debian 计算机：</span><span class="sxs-lookup"><span data-stu-id="133f0-171">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="133f0-172">[版本][]页。</span><span class="sxs-lookup"><span data-stu-id="133f0-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="133f0-173">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="133f0-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="133f0-174">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="133f0-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="133f0-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="133f0-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="133f0-176">此包也可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="133f0-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="133f0-177">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="133f0-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="133f0-178">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="133f0-179">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="133f0-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="133f0-180">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="133f0-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="133f0-181">使用 [CentOS 7][] 从以下位置将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机：</span><span class="sxs-lookup"><span data-stu-id="133f0-181">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="133f0-182">[版本][]页。</span><span class="sxs-lookup"><span data-stu-id="133f0-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="133f0-183">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="133f0-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="133f0-184">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="133f0-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="133f0-185">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="133f0-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="133f0-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="133f0-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="133f0-188">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="133f0-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="133f0-189">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="133f0-190">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="133f0-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="133f0-191">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="133f0-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="133f0-192">从以下位置将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机：</span><span class="sxs-lookup"><span data-stu-id="133f0-192">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="133f0-193">[版本][]页。</span><span class="sxs-lookup"><span data-stu-id="133f0-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="133f0-194">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="133f0-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="133f0-195">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="133f0-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="133f0-196">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="133f0-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="133f0-197">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="133f0-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="133f0-198">安装 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="133f0-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="133f0-199">安装 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="133f0-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="133f0-200">卸载 - OpenSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="133f0-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="133f0-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="133f0-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="133f0-202">Fedora 28 仅在 PowerShell Core 6.1 以及更新版本中受到支持。</span><span class="sxs-lookup"><span data-stu-id="133f0-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="133f0-203">通过包存储库安装（首选）- Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="133f0-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="133f0-204">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="133f0-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="133f0-205">通过直接下载进行安装 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="133f0-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="133f0-206">从以下位置将 RPM 包 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机：</span><span class="sxs-lookup"><span data-stu-id="133f0-206">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="133f0-207">[版本][]页。</span><span class="sxs-lookup"><span data-stu-id="133f0-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="133f0-208">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="133f0-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="133f0-209">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="133f0-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="133f0-210">卸载 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="133f0-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="133f0-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="133f0-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="133f0-212">Arch 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="133f0-212">Arch support is experimental.</span></span>

<span data-ttu-id="133f0-213">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="133f0-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="133f0-214">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="133f0-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="133f0-215">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="133f0-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="133f0-216">可使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="133f0-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="133f0-217">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="133f0-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="133f0-218">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="133f0-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="133f0-220">Snap 包</span><span class="sxs-lookup"><span data-stu-id="133f0-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="133f0-221">获取 snapd</span><span class="sxs-lookup"><span data-stu-id="133f0-221">Getting snapd</span></span>

<span data-ttu-id="133f0-222">需具备 `snapd` 才能运行 Snap。</span><span class="sxs-lookup"><span data-stu-id="133f0-222">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="133f0-223">按照[这些说明](https://docs.snapcraft.io/core/install)确保你已安装 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="133f0-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="133f0-224">通过 Snap 进行安装</span><span class="sxs-lookup"><span data-stu-id="133f0-224">Installation via Snap</span></span>

<span data-ttu-id="133f0-225">为简化安装（和更新），已向 [Snap 存储](https://snapcraft.io/store)发布 PowerShell Core for Linux。</span><span class="sxs-lookup"><span data-stu-id="133f0-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="133f0-226">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="133f0-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="133f0-227">如果想要安装预览版本，请使用以下方法。</span><span class="sxs-lookup"><span data-stu-id="133f0-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="133f0-228">安装 Snap 后将自动升级，但可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 来触发升级。</span><span class="sxs-lookup"><span data-stu-id="133f0-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="133f0-229">卸载</span><span class="sxs-lookup"><span data-stu-id="133f0-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="133f0-230">或</span><span class="sxs-lookup"><span data-stu-id="133f0-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="133f0-231">Kali</span><span class="sxs-lookup"><span data-stu-id="133f0-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="133f0-232">安装 - Kali</span><span class="sxs-lookup"><span data-stu-id="133f0-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="133f0-233">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="133f0-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="133f0-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="133f0-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="133f0-235">Raspbian 支持是实验性的。</span><span class="sxs-lookup"><span data-stu-id="133f0-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="133f0-236">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="133f0-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="133f0-237">此外 CoreCLR（和 PowerShell Core）仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="133f0-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="133f0-238">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="133f0-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="133f0-239">安装 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="133f0-239">Installation - Raspbian</span></span>

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

<span data-ttu-id="133f0-240">或者可以创建能够启动 PowerShell 的符号链接，而无需指定到“pwsh”二进制文件的路径</span><span class="sxs-lookup"><span data-stu-id="133f0-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="133f0-241">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="133f0-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="133f0-242">二进制存档</span><span class="sxs-lookup"><span data-stu-id="133f0-242">Binary Archives</span></span>

<span data-ttu-id="133f0-243">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="133f0-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="133f0-244">依赖关系</span><span class="sxs-lookup"><span data-stu-id="133f0-244">Dependencies</span></span>

<span data-ttu-id="133f0-245">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="133f0-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="133f0-246">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，因此 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="133f0-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="133f0-247">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="133f0-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="133f0-248">操作系统</span><span class="sxs-lookup"><span data-stu-id="133f0-248">OS</span></span>                 | <span data-ttu-id="133f0-249">依赖关系</span><span class="sxs-lookup"><span data-stu-id="133f0-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="133f0-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="133f0-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="133f0-251">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="133f0-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="133f0-252">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="133f0-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="133f0-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="133f0-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="133f0-254">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="133f0-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="133f0-255">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="133f0-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="133f0-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="133f0-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="133f0-257">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="133f0-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="133f0-258">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="133f0-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="133f0-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="133f0-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="133f0-260">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="133f0-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="133f0-261">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="133f0-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="133f0-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="133f0-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="133f0-263">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="133f0-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="133f0-264">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="133f0-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="133f0-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="133f0-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="133f0-266">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="133f0-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="133f0-267">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="133f0-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="133f0-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="133f0-268">CentOS 7</span></span> <br> <span data-ttu-id="133f0-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="133f0-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="133f0-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="133f0-270">RHEL 7</span></span> | <span data-ttu-id="133f0-271">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="133f0-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="133f0-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="133f0-272">openSUSE 42.3</span></span> | <span data-ttu-id="133f0-273">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="133f0-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="133f0-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="133f0-274">openSUSE Leap 15</span></span> | <span data-ttu-id="133f0-275">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="133f0-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="133f0-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="133f0-276">Fedora 27</span></span> <br> <span data-ttu-id="133f0-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="133f0-277">Fedora 28</span></span> | <span data-ttu-id="133f0-278">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="133f0-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="133f0-279">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="133f0-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="133f0-280">例如，[Amazon Linux dockerfile][amazon-dockerfile] 先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="133f0-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="133f0-281">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="133f0-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="133f0-282">Linux</span><span class="sxs-lookup"><span data-stu-id="133f0-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="133f0-283">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="133f0-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="133f0-284">路径</span><span class="sxs-lookup"><span data-stu-id="133f0-284">Paths</span></span>

* <span data-ttu-id="133f0-285">`$PSHOME` 是 `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="133f0-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="133f0-286">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="133f0-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="133f0-287">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="133f0-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="133f0-288">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="133f0-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="133f0-289">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="133f0-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="133f0-290">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="133f0-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="133f0-291">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="133f0-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="133f0-292">配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="133f0-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="133f0-293">PowerShell 采用 Linux 上的 [XDG 基目录规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="133f0-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

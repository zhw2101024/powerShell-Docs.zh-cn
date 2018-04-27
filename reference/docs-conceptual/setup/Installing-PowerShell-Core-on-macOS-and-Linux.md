# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="77b70-101">在 macOS 和 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="77b70-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="77b70-102">支持 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 25][fed25]、[Fedora 26][fed26]、[Arch Linux][arch] 和 [macOS 10.12][mac]。</span><span class="sxs-lookup"><span data-stu-id="77b70-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="77b70-103">对于不受正式支持的 Linux 分发版，可以尝试使用 [PowerShell AppImage][lai]。</span><span class="sxs-lookup"><span data-stu-id="77b70-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="77b70-104">还可以尝试直接使用 Linux [`tar.gz` archive][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置所需的依赖项。</span><span class="sxs-lookup"><span data-stu-id="77b70-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="77b70-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="77b70-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="77b70-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="77b70-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="77b70-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="77b70-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="77b70-108">通过包存储库安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="77b70-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="77b70-109">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="77b70-110">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="77b70-110">This is the preferred method.</span></span>

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

<span data-ttu-id="77b70-111">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="77b70-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="77b70-112">通过直接下载进行安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="77b70-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="77b70-113">从[版本][]页中将 Debian 包 `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="77b70-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="77b70-114">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="77b70-115">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="77b70-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="77b70-116">卸载 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="77b70-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="77b70-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="77b70-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="77b70-118">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="77b70-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="77b70-119">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="77b70-120">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="77b70-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="77b70-121">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="77b70-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="77b70-122">通过 Direct Download 的安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="77b70-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="77b70-123">从[版本][]页中将 Debian 包 `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="77b70-124">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="77b70-125">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="77b70-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="77b70-126">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="77b70-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="77b70-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="77b70-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="77b70-128">通过 Package Repository 的安装 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="77b70-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="77b70-129">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="77b70-130">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="77b70-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="77b70-131">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="77b70-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="77b70-132">通过直接下载进行安装 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="77b70-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="77b70-133">从[版本][]页中将 Debian 包 `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` 下载到 Ubuntu 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="77b70-134">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="77b70-135">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="77b70-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="77b70-136">卸载 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="77b70-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="77b70-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="77b70-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="77b70-138">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="77b70-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="77b70-139">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="77b70-140">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="77b70-140">This is the preferred method.</span></span>

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

<span data-ttu-id="77b70-141">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="77b70-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="77b70-142">通过直接下载进行安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="77b70-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="77b70-143">从[版本][]页中将 Debian 包 `powershell_6.0.0-1.debian.8_amd64.deb` 下载到 Debian 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="77b70-144">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="77b70-145">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="77b70-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="77b70-146">卸载 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="77b70-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="77b70-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="77b70-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="77b70-148">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="77b70-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="77b70-149">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="77b70-150">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="77b70-150">This is the preferred method.</span></span>

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

<span data-ttu-id="77b70-151">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="77b70-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="77b70-152">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="77b70-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="77b70-153">从[版本][]页中将 Debian 包 `powershell_6.0.0-1.debian.9_amd64.deb` 下载到 Debian 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="77b70-154">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="77b70-155">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="77b70-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="77b70-156">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="77b70-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="77b70-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="77b70-157">CentOS 7</span></span>

> <span data-ttu-id="77b70-158">此包也可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="77b70-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="77b70-159">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="77b70-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="77b70-160">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="77b70-161">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="77b70-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="77b70-162">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="77b70-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="77b70-163">使用 [CentOS 7][] 时，请从[版本][]页中将 RPM 包 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-164">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-165">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="77b70-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="77b70-166">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="77b70-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="77b70-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="77b70-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="77b70-169">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="77b70-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="77b70-170">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="77b70-171">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="77b70-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="77b70-172">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="77b70-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="77b70-173">从[版本][]页中将 RPM 包 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="77b70-174">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-175">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="77b70-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="77b70-176">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="77b70-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="77b70-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="77b70-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="77b70-178">**请注意：**安装 PowerShell Core 时，`zypper` 可能报告以下错误：</span><span class="sxs-lookup"><span data-stu-id="77b70-178">**Note:** When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="77b70-179">在这种情况下，通过检查以下命令将 `libcurl4` 包显示为已安装来验证存在兼容的 `libcurl` 库：</span><span class="sxs-lookup"><span data-stu-id="77b70-179">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="77b70-180">然后在安装 `powershell` 包时选择 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解决方案。</span><span class="sxs-lookup"><span data-stu-id="77b70-180">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the `powershell` package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="77b70-181">通过包存储库安装（首选）- OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="77b70-181">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="77b70-182">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="77b70-183">通过直接下载进行安装 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="77b70-183">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="77b70-184">从[版本][]页中将 RPM 包 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下载到 OpenSUSE 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-184">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-185">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="77b70-185">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="77b70-186">卸载 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="77b70-186">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="77b70-187">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="77b70-187">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="77b70-188">通过包存储库安装（首选）- Fedora 25</span><span class="sxs-lookup"><span data-stu-id="77b70-188">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="77b70-189">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="77b70-190">通过直接下载进行安装 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="77b70-190">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="77b70-191">从[版本][]页中将 RPM 包 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-191">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-192">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-192">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-193">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="77b70-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="77b70-194">卸载 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="77b70-194">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="77b70-195">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="77b70-195">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="77b70-196">通过包存储库安装（首选）- Fedora 26</span><span class="sxs-lookup"><span data-stu-id="77b70-196">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="77b70-197">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="77b70-197">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="77b70-198">通过直接下载进行安装 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="77b70-198">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="77b70-199">从[版本][]页中将 RPM 包 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机：</span><span class="sxs-lookup"><span data-stu-id="77b70-199">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-200">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-200">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="77b70-201">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="77b70-201">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="77b70-202">卸载 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="77b70-202">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="77b70-203">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="77b70-203">Arch Linux</span></span>

<span data-ttu-id="77b70-204">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77b70-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="77b70-205">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="77b70-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="77b70-206">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="77b70-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="77b70-207">可以使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="77b70-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="77b70-208">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="77b70-208">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="77b70-209">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="77b70-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="77b70-211">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="77b70-211">Linux AppImage</span></span>

<span data-ttu-id="77b70-212">使用新的 Linux 分发版时，请从[版本][]页中将 AppImage `powershell-6.0.0-x86_64.AppImage`下载到 Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="77b70-212">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="77b70-213">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="77b70-213">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="77b70-214">通过 [AppImage][] 无需安装即可运行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77b70-214">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="77b70-215">此款可移植应用程序将 PowerShell 及其依赖项（包括 .NET Core 的系统依赖项）捆绑到一个统一包中。</span><span class="sxs-lookup"><span data-stu-id="77b70-215">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="77b70-216">此包独立于用户的 Linux 分发版之外运行，且为单个二进制文件。</span><span class="sxs-lookup"><span data-stu-id="77b70-216">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="77b70-218">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="77b70-218">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="77b70-219">通过 Homebrew 安装（首选）的- macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="77b70-219">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="77b70-220">[Homebrew][brew] 是 macOS 的缺失包管理器。</span><span class="sxs-lookup"><span data-stu-id="77b70-220">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="77b70-221">如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="77b70-221">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="77b70-222">安装 Homebrew 后，安装 PowerShell 就变得很容易。</span><span class="sxs-lookup"><span data-stu-id="77b70-222">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="77b70-223">首先，安装 [Homebrew-Cask][cask]，这样可安装更多包：</span><span class="sxs-lookup"><span data-stu-id="77b70-223">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="77b70-224">现在，可以开始安装 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="77b70-224">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="77b70-225">PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="77b70-225">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> <span data-ttu-id="77b70-226">注意：可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新进入以完成升级，并刷新 $PSVersionTable 中显示的值。</span><span class="sxs-lookup"><span data-stu-id="77b70-226">Note: The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and re-entered to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="77b70-227">通过直接下载安装 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="77b70-227">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="77b70-228">使用 macOS 10.12 时，请从[版本][]页中将 PKG 包 `powershell-6.0.0-osx.10.12-x64.pkg` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="77b70-228">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="77b70-229">双击文件并按照提示操作，或者从终端安装：</span><span class="sxs-lookup"><span data-stu-id="77b70-229">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="77b70-230">卸载 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="77b70-230">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="77b70-231">如果使用 Homebrew 安装 PowerShell，则卸载很简单：</span><span class="sxs-lookup"><span data-stu-id="77b70-231">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="77b70-232">如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="77b70-232">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="77b70-233">若要卸载其他 PowerShell 路径（例如用户配置文件路径），请参阅本文档后面的[路径][paths]一节，并使用 `sudo rm` 删除所需路径。</span><span class="sxs-lookup"><span data-stu-id="77b70-233">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="77b70-234">（请注意：如果使用 Homebrew 安装，则此步骤并非必要步骤。）</span><span class="sxs-lookup"><span data-stu-id="77b70-234">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="77b70-235">Kali</span><span class="sxs-lookup"><span data-stu-id="77b70-235">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="77b70-236">安装</span><span class="sxs-lookup"><span data-stu-id="77b70-236">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="77b70-237">在最新版 Kali (Kali GNU/Linux Rolling) 中无需安装即可运行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="77b70-237">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="77b70-238">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="77b70-238">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="77b70-239">Raspbian</span><span class="sxs-lookup"><span data-stu-id="77b70-239">Raspbian</span></span>

<span data-ttu-id="77b70-240">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77b70-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="77b70-241">安装</span><span class="sxs-lookup"><span data-stu-id="77b70-241">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="77b70-242">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="77b70-242">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="77b70-243">二进制存档</span><span class="sxs-lookup"><span data-stu-id="77b70-243">Binary Archives</span></span>

<span data-ttu-id="77b70-244">已对 macOS 和 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="77b70-244">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="77b70-245">依赖关系</span><span class="sxs-lookup"><span data-stu-id="77b70-245">Dependencies</span></span>

<span data-ttu-id="77b70-246">对于 Linux，PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="77b70-246">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="77b70-247">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，因此 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="77b70-247">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="77b70-248">下表列出了正式支持的不同 Linux 分发版的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="77b70-248">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="77b70-249">操作系统</span><span class="sxs-lookup"><span data-stu-id="77b70-249">OS</span></span>                 | <span data-ttu-id="77b70-250">依赖关系</span><span class="sxs-lookup"><span data-stu-id="77b70-250">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="77b70-251">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="77b70-251">Ubuntu 14.04</span></span>       | <span data-ttu-id="77b70-252">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="77b70-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="77b70-253">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="77b70-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="77b70-254">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="77b70-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="77b70-255">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="77b70-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="77b70-256">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="77b70-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="77b70-257">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="77b70-257">Ubuntu 17.04</span></span>       | <span data-ttu-id="77b70-258">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="77b70-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="77b70-259">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="77b70-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="77b70-260">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="77b70-260">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="77b70-261">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="77b70-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="77b70-262">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="77b70-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="77b70-263">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="77b70-263">Debian 9 (Stretch)</span></span> | <span data-ttu-id="77b70-264">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="77b70-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="77b70-265">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="77b70-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="77b70-266">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="77b70-266">CentOS 7</span></span> <br> <span data-ttu-id="77b70-267">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="77b70-267">Oracle Linux 7</span></span> <br> <span data-ttu-id="77b70-268">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="77b70-268">RHEL 7</span></span> <br> <span data-ttu-id="77b70-269">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="77b70-269">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="77b70-270">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="77b70-270">Fedora 25</span></span> | <span data-ttu-id="77b70-271">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="77b70-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="77b70-272">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="77b70-272">Fedora 26</span></span>          | <span data-ttu-id="77b70-273">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="77b70-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="77b70-274">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需为在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="77b70-274">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="77b70-275">例如，[Amazon Linux dockerfile][amazon-dockerfile] 应先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="77b70-275">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="77b70-276">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="77b70-276">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="77b70-277">Linux</span><span class="sxs-lookup"><span data-stu-id="77b70-277">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="77b70-278">macOS</span><span class="sxs-lookup"><span data-stu-id="77b70-278">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="77b70-279">卸载 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="77b70-279">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="77b70-280">Linux</span><span class="sxs-lookup"><span data-stu-id="77b70-280">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="77b70-281">macOS</span><span class="sxs-lookup"><span data-stu-id="77b70-281">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="77b70-282">路径</span><span class="sxs-lookup"><span data-stu-id="77b70-282">Paths</span></span>

* <span data-ttu-id="77b70-283">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="77b70-283">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="77b70-284">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="77b70-284">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="77b70-285">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="77b70-285">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="77b70-286">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="77b70-286">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="77b70-287">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="77b70-287">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="77b70-288">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="77b70-288">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="77b70-289">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="77b70-289">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="77b70-290">配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="77b70-290">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="77b70-291">Linux 和 macOS 上采用 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="77b70-291">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="77b70-292">注意，由于 macOS 派生自 BSD，因此前缀为 `/usr/local` 而不是 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="77b70-292">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="77b70-293">因此，`$PSHOME` 为 `/usr/local/microsoft/powershell/6.0.0/`，且 symlink 位于 `/usr/local/bin/pwsh` 中。</span><span class="sxs-lookup"><span data-stu-id="77b70-293">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="ec97f-101">在 Linux 上安装 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="ec97f-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="ec97f-102">支持 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="ec97f-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="ec97f-103">对于不受正式支持的 Linux 分发版，可以尝试使用 [PowerShell AppImage][lai]。</span><span class="sxs-lookup"><span data-stu-id="ec97f-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="ec97f-104">还可以尝试直接使用 Linux [`tar.gz` archive][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置所需的依赖项。</span><span class="sxs-lookup"><span data-stu-id="ec97f-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="ec97f-105">GitHub [版本][]页面上提供有所有可用包。</span><span class="sxs-lookup"><span data-stu-id="ec97f-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="ec97f-106">安装包以后，从终端运行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="ec97f-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="ec97f-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="ec97f-108">通过包存储库安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="ec97f-109">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec97f-110">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="ec97f-110">This is the preferred method.</span></span>

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

<span data-ttu-id="ec97f-111">以超级用户身份注册 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="ec97f-112">此后，只需使用 `sudo apt-get upgrade powershell` 来更新安装。</span><span class="sxs-lookup"><span data-stu-id="ec97f-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="ec97f-113">通过直接下载进行安装 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="ec97f-114">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec97f-115">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="ec97f-116">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="ec97f-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="ec97f-117">卸载 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="ec97f-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="ec97f-119">通过包存储库安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="ec97f-120">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec97f-121">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="ec97f-121">This is the preferred method.</span></span>

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

<span data-ttu-id="ec97f-122">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="ec97f-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="ec97f-123">通过 Direct Download 的安装 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="ec97f-124">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec97f-125">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="ec97f-126">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="ec97f-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="ec97f-127">卸载 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="ec97f-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="ec97f-129">通过 Package Repository 的安装 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="ec97f-130">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec97f-131">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="ec97f-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec97f-132">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="ec97f-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="ec97f-133">通过直接下载进行安装 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="ec97f-134">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` 下载到 Ubuntu 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec97f-135">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="ec97f-136">请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="ec97f-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="ec97f-137">卸载 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="ec97f-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec97f-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="ec97f-139">通过包存储库安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec97f-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="ec97f-140">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec97f-141">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="ec97f-141">This is the preferred method.</span></span>

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

<span data-ttu-id="ec97f-142">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="ec97f-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="ec97f-143">通过直接下载进行安装 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec97f-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="ec97f-144">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.8_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ec97f-145">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec97f-146">请注意，`dpkg -i` 对于 unmet 依赖项无效。</span><span class="sxs-lookup"><span data-stu-id="ec97f-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="ec97f-147">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="ec97f-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="ec97f-148">卸载 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec97f-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="ec97f-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec97f-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="ec97f-150">通过包存储库安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec97f-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="ec97f-151">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec97f-152">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="ec97f-152">This is the preferred method.</span></span>

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

<span data-ttu-id="ec97f-153">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。</span><span class="sxs-lookup"><span data-stu-id="ec97f-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="ec97f-154">通过直接下载进行安装 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec97f-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="ec97f-155">从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.9_amd64.deb` 下载到 Debian 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ec97f-156">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec97f-157">请注意，`dpkg -i` 对于 unmet 依赖项无效。</span><span class="sxs-lookup"><span data-stu-id="ec97f-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="ec97f-158">下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。</span><span class="sxs-lookup"><span data-stu-id="ec97f-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="ec97f-159">卸载 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec97f-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="ec97f-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-160">CentOS 7</span></span>

> <span data-ttu-id="ec97f-161">此包也可以在 Oracle Linux 7 上运行。</span><span class="sxs-lookup"><span data-stu-id="ec97f-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="ec97f-162">通过包存储库安装（首选）- CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="ec97f-163">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec97f-164">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="ec97f-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="ec97f-165">通过直接下载进行安装 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="ec97f-166">使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="ec97f-167">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec97f-168">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="ec97f-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="ec97f-169">卸载 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec97f-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec97f-172">通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ec97f-173">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec97f-174">作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。</span><span class="sxs-lookup"><span data-stu-id="ec97f-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec97f-175">通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ec97f-176">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="ec97f-177">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec97f-178">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="ec97f-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec97f-179">卸载 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="ec97f-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="ec97f-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="ec97f-181">安装 PowerShell Core 时，`zypper` 可能报告以下错误：</span><span class="sxs-lookup"><span data-stu-id="ec97f-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="ec97f-182">在这种情况下，通过检查以下命令将 `libcurl4` 包显示为已安装来验证存在兼容的 `libcurl` 库：</span><span class="sxs-lookup"><span data-stu-id="ec97f-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="ec97f-183">然后在安装 PowerShell 包时选择 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解决方案。</span><span class="sxs-lookup"><span data-stu-id="ec97f-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="ec97f-184">通过包存储库安装（首选）- OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="ec97f-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="ec97f-185">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="ec97f-186">通过直接下载进行安装 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="ec97f-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="ec97f-187">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 OpenSUSE 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec97f-188">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="ec97f-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="ec97f-189">卸载 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="ec97f-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="ec97f-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="ec97f-190">Fedora</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="ec97f-191">通过包存储库安装（首选）- Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec97f-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ec97f-192">为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。</span><span class="sxs-lookup"><span data-stu-id="ec97f-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="ec97f-193">通过直接下载进行安装 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec97f-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ec97f-194">从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="ec97f-195">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec97f-196">无需该中间下载步骤也可安装 RPM：</span><span class="sxs-lookup"><span data-stu-id="ec97f-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="ec97f-197">卸载 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec97f-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="ec97f-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="ec97f-198">Arch Linux</span></span>

<span data-ttu-id="ec97f-199">[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ec97f-199">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="ec97f-200">可使用[最新标记版本][arch-release]对其进行编译</span><span class="sxs-lookup"><span data-stu-id="ec97f-200">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="ec97f-201">可使用[最新 commit to master][arch-git] 对其进行编译</span><span class="sxs-lookup"><span data-stu-id="ec97f-201">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="ec97f-202">可以使用[最新版本二进制文件][arch-bin]进行安装</span><span class="sxs-lookup"><span data-stu-id="ec97f-202">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="ec97f-203">AUR 中的包由社区维护，并无正式支持。</span><span class="sxs-lookup"><span data-stu-id="ec97f-203">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="ec97f-204">有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。</span><span class="sxs-lookup"><span data-stu-id="ec97f-204">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="ec97f-206">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="ec97f-206">Linux AppImage</span></span>

<span data-ttu-id="ec97f-207">使用新的 Linux 分发版时，请从[版本][]页中将 AppImage `powershell-6.0.1-x86_64.AppImage`下载到 Linux 计算机。</span><span class="sxs-lookup"><span data-stu-id="ec97f-207">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="ec97f-208">然后在终端中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec97f-208">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="ec97f-209">通过 [AppImage][] 无需安装即可运行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ec97f-209">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="ec97f-210">此款可移植应用程序将 PowerShell 及其依赖项（包括 .NET Core 的系统依赖项）捆绑到一个统一包中。</span><span class="sxs-lookup"><span data-stu-id="ec97f-210">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="ec97f-211">此包为单个二进制文件，独立于用户的 Linux 分发版运行。</span><span class="sxs-lookup"><span data-stu-id="ec97f-211">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="ec97f-213">Kali</span><span class="sxs-lookup"><span data-stu-id="ec97f-213">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="ec97f-214">安装</span><span class="sxs-lookup"><span data-stu-id="ec97f-214">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="ec97f-215">在最新版 Kali (Kali GNU/Linux Rolling) 中无需安装即可运行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec97f-215">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="ec97f-216">卸载 - Kali</span><span class="sxs-lookup"><span data-stu-id="ec97f-216">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="ec97f-217">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec97f-217">Raspbian</span></span>

<span data-ttu-id="ec97f-218">当前仅 Raspbian Stretch 支持 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ec97f-218">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="ec97f-219">此外 CoreCLR（和 PowerShell Core）仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。</span><span class="sxs-lookup"><span data-stu-id="ec97f-219">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="ec97f-220">下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。</span><span class="sxs-lookup"><span data-stu-id="ec97f-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="ec97f-221">安装</span><span class="sxs-lookup"><span data-stu-id="ec97f-221">Installation</span></span>

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

<span data-ttu-id="ec97f-222">或者可以创建能够启动 PowerShell 的符号链接，而无需指定到“pwsh”二进制文件的路径</span><span class="sxs-lookup"><span data-stu-id="ec97f-222">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="ec97f-223">卸载 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec97f-223">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="ec97f-224">二进制存档</span><span class="sxs-lookup"><span data-stu-id="ec97f-224">Binary Archives</span></span>

<span data-ttu-id="ec97f-225">已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。</span><span class="sxs-lookup"><span data-stu-id="ec97f-225">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="ec97f-226">依赖关系</span><span class="sxs-lookup"><span data-stu-id="ec97f-226">Dependencies</span></span>

<span data-ttu-id="ec97f-227">PowerShell 为所有 Linux 分发版生成可移植二进制文件。</span><span class="sxs-lookup"><span data-stu-id="ec97f-227">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="ec97f-228">但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，因此 PowerShell 也有相同要求。</span><span class="sxs-lookup"><span data-stu-id="ec97f-228">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="ec97f-229">下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。</span><span class="sxs-lookup"><span data-stu-id="ec97f-229">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="ec97f-230">操作系统</span><span class="sxs-lookup"><span data-stu-id="ec97f-230">OS</span></span>                 | <span data-ttu-id="ec97f-231">依赖关系</span><span class="sxs-lookup"><span data-stu-id="ec97f-231">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="ec97f-232">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-232">Ubuntu 14.04</span></span>       | <span data-ttu-id="ec97f-233">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="ec97f-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec97f-234">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="ec97f-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ec97f-235">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-235">Ubuntu 16.04</span></span>       | <span data-ttu-id="ec97f-236">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="ec97f-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec97f-237">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="ec97f-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="ec97f-238">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="ec97f-238">Ubuntu 17.04</span></span>       | <span data-ttu-id="ec97f-239">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="ec97f-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec97f-240">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="ec97f-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="ec97f-241">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="ec97f-241">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="ec97f-242">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="ec97f-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec97f-243">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="ec97f-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ec97f-244">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="ec97f-244">Debian 9 (Stretch)</span></span> | <span data-ttu-id="ec97f-245">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="ec97f-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec97f-246">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="ec97f-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="ec97f-247">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-247">CentOS 7</span></span> <br> <span data-ttu-id="ec97f-248">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-248">Oracle Linux 7</span></span> <br> <span data-ttu-id="ec97f-249">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="ec97f-249">RHEL 7</span></span> <br> <span data-ttu-id="ec97f-250">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="ec97f-250">OpenSUSE 42.2</span></span> | <span data-ttu-id="ec97f-251">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="ec97f-251">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="ec97f-252">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ec97f-252">Fedora 27</span></span> <br> <span data-ttu-id="ec97f-253">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec97f-253">Fedora 28</span></span> | <span data-ttu-id="ec97f-254">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="ec97f-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="ec97f-255">若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。</span><span class="sxs-lookup"><span data-stu-id="ec97f-255">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="ec97f-256">例如，[Amazon Linux dockerfile][amazon-dockerfile] 应先安装依赖项，然后提取 Linux `tar.gz` 存档。</span><span class="sxs-lookup"><span data-stu-id="ec97f-256">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="ec97f-257">安装 - 二进制存档</span><span class="sxs-lookup"><span data-stu-id="ec97f-257">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="ec97f-258">Linux</span><span class="sxs-lookup"><span data-stu-id="ec97f-258">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="ec97f-259">卸载二进制存档</span><span class="sxs-lookup"><span data-stu-id="ec97f-259">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="ec97f-260">路径</span><span class="sxs-lookup"><span data-stu-id="ec97f-260">Paths</span></span>

* <span data-ttu-id="ec97f-261">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="ec97f-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="ec97f-262">将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件</span><span class="sxs-lookup"><span data-stu-id="ec97f-262">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="ec97f-263">将从 `$PSHOME/profile.ps1` 中读取默认配置文件</span><span class="sxs-lookup"><span data-stu-id="ec97f-263">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="ec97f-264">将从 `~/.local/share/powershell/Modules` 中读取用户模块</span><span class="sxs-lookup"><span data-stu-id="ec97f-264">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ec97f-265">将从 `/usr/local/share/powershell/Modules` 中读取共享模块</span><span class="sxs-lookup"><span data-stu-id="ec97f-265">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ec97f-266">将从 `$PSHOME/Modules` 中读取默认模块</span><span class="sxs-lookup"><span data-stu-id="ec97f-266">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="ec97f-267">PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="ec97f-267">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ec97f-268">配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。</span><span class="sxs-lookup"><span data-stu-id="ec97f-268">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ec97f-269">PowerShell 采用 Linux 上的 [XDG Base Directory 规范][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="ec97f-269">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

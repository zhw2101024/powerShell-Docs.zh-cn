# <a name="installing-powershell-core-on-macos-and-linux"></a>在 macOS 和 Linux 上安装 PowerShell Core

支持 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 25][fed25]、[Fedora 26][fed26]、[Arch Linux][arch] 和 [macOS 10.12][mac]。

对于不受正式支持的 Linux 分发版，可以尝试使用 [PowerShell AppImage][lai]。
还可以尝试直接使用 Linux [`tar.gz` archive][tar] 部署 PowerShell 二进制文件，但是需要在各个步骤中基于 OS 设置所需的依赖项。

GitHub [版本][]页面上提供有所有可用包。
安装包以后，从终端运行 `pwsh`。

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

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>通过包存储库安装 - Ubuntu 14.04

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。
这是首选方法。

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

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。

### <a name="installation-via-direct-download---ubuntu-1404"></a>通过直接下载进行安装 - Ubuntu 14.04

从[版本][]页中将 Debian 包 `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> 请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---ubuntu-1404"></a>卸载 - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>通过包存储库安装 - Ubuntu 16.04

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。
这是首选方法。

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

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。

### <a name="installation-via-direct-download---ubuntu-1604"></a>通过 Direct Download 的安装 - Ubuntu 16.04

从[版本][]页中将 Debian 包 `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> 请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---ubuntu-1604"></a>卸载 - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>通过 Package Repository 的安装 - Ubuntu 17.04

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。
这是首选方法。

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

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。

### <a name="installation-via-direct-download---ubuntu-1704"></a>通过直接下载进行安装 - Ubuntu 17.04

从[版本][]页中将 Debian 包 `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> 请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---ubuntu-1704"></a>卸载 - Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>通过包存储库安装 - Debian 8

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。
这是首选方法。

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

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。

### <a name="installation-via-direct-download---debian-8"></a>通过直接下载进行安装 - Debian 8

从[版本][]页中将 Debian 包 `powershell_6.0.0-rc-1.debian.8_amd64.deb` 下载到 Debian 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.8_amd64.deb
sudo apt-get install -f
```

> 请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---debian-8"></a>卸载 - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>通过包存储库安装 - Debian 9

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到包存储库。
这是首选方法。

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

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。

### <a name="installation-via-direct-download---debian-9"></a>通过直接下载进行安装 - Debian 9

从[版本][]页中将 Debian 包 `powershell_6.0.0-rc-1.debian.9_amd64.deb` 下载到 Debian 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.9_amd64.deb
sudo apt-get install -f
```

> 请注意，`dpkg -i` 对于 unmet 依赖项无效；下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

### <a name="uninstallation---debian-9"></a>卸载 - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> 此包也可以在 Oracle Linux 7 上运行。

### <a name="installation-via-package-repository-preferred---centos-7"></a>通过包存储库安装（首选）- CentOS 7

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。

### <a name="installation-via-direct-download---centos-7"></a>通过直接下载进行安装 - CentOS 7

使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。

然后在终端中执行以下命令：

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>卸载 - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>通过包存储库安装（首选）- Red Hat Enterprise Linux (RHEL) 7

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo yum update powershell` 更新 PowerShell 即可。

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>通过直接下载进行安装 - Red Hat Enterprise Linux (RHEL) 7

从[版本][]页中将 RPM 包 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。

然后在终端中执行以下命令：

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>卸载 - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **注意：**安装 PowerShell Core 时，OpenSUSE 可能报告没有提供 `libcurl`。
`libcurl` 可能已安装在受支持的 OpenSUSE 版本上。
运行 `zypper search libcurl` 以确定。
该错误会显示 2 个“解决方案”。 选择“解决方案 2”继续安装 PowerShell Core。

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>通过包存储库安装（首选）- OpenSUSE 42.2

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。

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

### <a name="installation-via-direct-download---opensuse-422"></a>通过直接下载进行安装 - OpenSUSE 42.2

从[版本][]页中将 RPM 包 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` 下载到 OpenSUSE 计算机。

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>卸载 - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>通过包存储库安装（首选）- Fedora 25

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。

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

### <a name="installation-via-direct-download---fedora-25"></a>通过直接下载进行安装 - Fedora 25

从[版本][]页中将 RPM 包 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。

然后在终端中执行以下命令：

```sh
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>卸载 - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>通过包存储库安装（首选）- Fedora 26

为简化安装（和更新），已将适用于 Linux 的 PowerShell Core 发布到正式的 Microsoft 存储库。

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

### <a name="installation-via-direct-download---fedora-26"></a>通过直接下载进行安装 - Fedora 26

从[版本][]页中将 RPM 包 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。

然后在终端中执行以下命令：

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>卸载 - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

[Arch Linux][] 用户存储库 (AUR) 中提供有 PowerShell。

* 可使用[最新标记版本][arch-release]对其进行编译
* 可使用[最新 commit to master][arch-git] 对其进行编译
* 可以使用[最新版本二进制文件][arch-bin]进行安装

AUR 中的包由社区维护，并无正式支持。

有关从 AUR 安装包的详细信息，请参阅 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 社区。

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

使用新的 Linux 分发版时，请从[版本][]页中将 AppImage `powershell-6.0.0-rc-x86_64.AppImage`下载到 Linux 计算机。

然后在终端中执行以下命令：

```bash
chmod a+x powershell-6.0.0-rc-x86_64.AppImage
./powershell-6.0.0-rc-x86_64.AppImage
```

通过 [AppImage][] 无需安装即可运行 PowerShell。
此款可移植应用程序将 PowerShell 及其依赖项（包括 .NET Core 的系统依赖项）捆绑到一个统一包中。
此包独立于用户的 Linux 分发版之外运行，且为单个二进制文件。

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>通过 Homebrew 安装（首选）的- macOS 10.12

[Homebrew][brew] 是 macOS 的缺失包管理器。
如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。

安装 Homebrew 后，安装 PowerShell 就变得很容易。
首先，安装 [Homebrew-Cask][cask]，这样可安装更多包：

```sh
brew tap caskroom/cask
```

现在，可以开始安装 PowerShell：

```sh
brew cask install powershell
```

PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：

```sh
brew update
brew cask reinstall powershell
```

> 注意：由于 [Cask 中的此问题](https://github.com/caskroom/homebrew-cask/issues/29301)，当前需要重新安装才能升级。

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>通过直接下载安装 - macOS 10.12

使用 macOS 10.12 时，请从[版本][]页中将 PKG 包 `powershell-6.0.0-rc-osx.10.12-x64.pkg` 下载到 CentOS 计算机。

双击文件并按照提示操作，或者从终端安装：

```sh
sudo installer -pkg powershell-6.0.0-rc-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>卸载 - macOS 10.12

如果使用 Homebrew 安装 PowerShell，则卸载很简单：

```sh
brew cask uninstall powershell
```

如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

若要卸载其他 PowerShell 路径（例如用户配置文件路径），请参阅本文档后面的[路径][paths]一节，并使用 `sudo rm` 删除所需路径。
（请注意：如果使用 Homebrew 安装，则此步骤并非必要步骤。）

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>安装

```sh
# Install prerequisites
apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>在最新版 Kali (Kali GNU/Linux Rolling) 中无需安装即可运行 PowerShell

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-rc-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-rc-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>卸载 - Kali

```sh
dpkg -r powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

当前仅 Raspbian Stretch 支持 PowerShell。

### <a name="installation"></a>安装

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-rc-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>卸载 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>二进制存档

已对 macOS 和 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。

### <a name="dependencies"></a>依赖关系

对于 Linux，PowerShell 为所有 Linux 分发版生成可移植二进制文件。
但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，因此 PowerShell 也有相同要求。

下表列出了正式支持的不同 Linux 分发版的 .NET Core 2.0 依赖项。

| 操作系统                 | 依赖关系 |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Ubuntu 16.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55 |
| Ubuntu 17.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57 |
| Debian 8 (Jessie)  | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Debian 9 (Stretch) | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind、libcurl、openssl-libs、libicu |
| Fedora 26          | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需为在各个步骤中安装目标 OS 的必要依赖项。
例如，[Amazon Linux dockerfile][amazon-dockerfile] 应先安装依赖项，然后提取 Linux `tar.gz` 存档。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>安装 - 二进制存档

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0-rc/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0-rc/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>卸载 - 二进制存档

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>路径

* `$PSHOME` 是 `/opt/microsoft/powershell/6.0.0-rc/`
* 将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件
* 将从 `$PSHOME/profile.ps1` 中读取默认配置文件
* 将从 `~/.local/share/powershell/Modules` 中读取用户模块
* 将从 `/usr/local/share/powershell/Modules` 中读取共享模块
* 将从 `$PSHOME/Modules` 中读取默认模块
* PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。

Linux 和 macOS 上采用 [XDG Base Directory 规范][xdg-bds]。

注意，由于 macOS 派生自 BSD，因此前缀为 `/usr/local` 而不是 `/opt`。
因此，`$PSHOME` 为 `/usr/local/microsoft/powershell/6.0.0-rc/`，且 symlink 位于 `/usr/local/bin/pwsh` 中。

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

# <a name="installing-powershell-core-on-linux"></a>在 Linux 上安装 PowerShell Core

支持 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 和 [Arch Linux][arch]。

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
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
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

以超级用户身份注册 Microsoft 存储库。
此后，只需使用 `sudo apt-get upgrade powershell` 来更新安装。

### <a name="installation-via-direct-download---ubuntu-1404"></a>通过直接下载进行安装 - Ubuntu 14.04

从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。

### <a name="installation-via-direct-download---ubuntu-1604"></a>通过 Direct Download 的安装 - Ubuntu 16.04

从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

作为超级用户注册 Microsoft 存储库一次后，仅需使用 `sudo apt-get upgrade powershell` 将其更新即可。

### <a name="installation-via-direct-download---ubuntu-1704"></a>通过直接下载进行安装 - Ubuntu 17.04

从[版本][]页中将 Debian 包 `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` 下载到 Ubuntu 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
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

从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.8_amd64.deb` 下载到 Debian 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> 请注意，`dpkg -i` 对于 unmet 依赖项无效。
> 下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

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

从[版本][]页中将 Debian 包 `powershell_6.0.2-1.debian.9_amd64.deb` 下载到 Debian 计算机。

然后在终端中执行以下命令：

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> 请注意，`dpkg -i` 对于 unmet 依赖项无效。
> 下一命令 `apt-get install -f` 解决此类问题，然后完成 PowerShell 包配置。

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

使用 [CentOS 7][]时，请从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 CentOS 计算机。

然后在终端中执行以下命令：

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Red Hat Enterprise Linux 计算机。

然后在终端中执行以下命令：

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>卸载 - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> [!NOTE]
> 安装 PowerShell Core 时，`zypper` 可能报告以下错误：
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> 在这种情况下，通过检查以下命令将 `libcurl4` 包显示为已安装来验证存在兼容的 `libcurl` 库：
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> 然后在安装 PowerShell 包时选择 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解决方案。

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

从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 OpenSUSE 计算机。

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>卸载 - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>通过包存储库安装（首选）- Fedora 27、Fedora 28

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>通过直接下载进行安装 - Fedora 27、Fedora 28

从[版本][]页中将 RPM 包 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下载到 Fedora 计算机。

然后在终端中执行以下命令：

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

无需该中间下载步骤也可安装 RPM：

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>卸载 - Fedora 27、Fedora 28

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

使用新的 Linux 分发版时，请从[版本][]页中将 AppImage `powershell-6.0.1-x86_64.AppImage`下载到 Linux 计算机。

然后在终端中执行以下命令：

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

通过 [AppImage][] 无需安装即可运行 PowerShell。
此款可移植应用程序将 PowerShell 及其依赖项（包括 .NET Core 的系统依赖项）捆绑到一个统一包中。
此包为单个二进制文件，独立于用户的 Linux 分发版运行。

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

### <a name="installation"></a>安装

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>在最新版 Kali (Kali GNU/Linux Rolling) 中无需安装即可运行 PowerShell

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>卸载 - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

当前仅 Raspbian Stretch 支持 PowerShell。

此外 CoreCLR（和 PowerShell Core）仅适用于 Pi 2 和 Pi 3 设备，因为其他设备（如 [Pi 0](https://github.com/dotnet/coreclr/issues/10605)）有不受支持的处理器。

下载 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 并按照[安装说明](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)操作，将其安装在你的 Pi 上。

### <a name="installation"></a>安装

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

或者可以创建能够启动 PowerShell 的符号链接，而无需指定到“pwsh”二进制文件的路径

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>卸载 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>二进制存档

已对 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。

### <a name="dependencies"></a>依赖关系

PowerShell 为所有 Linux 分发版生成可移植二进制文件。
但是对于不同的分发版，.NET Core 运行时需要不同的依赖项，因此 PowerShell 也有相同要求。

下表列出了在不同 Linux 分发版上正式支持的 .NET Core 2.0 依赖项。

| 操作系统                 | 依赖关系 |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Ubuntu 16.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55 |
| Ubuntu 17.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57 |
| Debian 8 (Jessie)  | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Debian 9 (Stretch) | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 | libunwind、libcurl、openssl-libs、libicu |
| Fedora 27 <br> Fedora 28 | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

若要在不受正式支持的 Linux 分发版上部署 PowerShell 二进制文件，则需在各个步骤中安装目标 OS 的必要依赖项。
例如，[Amazon Linux dockerfile][amazon-dockerfile] 应先安装依赖项，然后提取 Linux `tar.gz` 存档。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>安装 - 二进制存档

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>卸载二进制存档

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>路径

* `$PSHOME` 是 `/opt/microsoft/powershell/6.0.2/`
* 将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件
* 将从 `$PSHOME/profile.ps1` 中读取默认配置文件
* 将从 `~/.local/share/powershell/Modules` 中读取用户模块
* 将从 `/usr/local/share/powershell/Modules` 中读取共享模块
* 将从 `$PSHOME/Modules` 中读取默认模块
* PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

配置文件采用 PowerShell 的每个主机配置，所以默认主机特定配置文件位于相同位置下的 `Microsoft.PowerShell_profile.ps1` 中。

PowerShell 采用 Linux 上的 [XDG Base Directory 规范][xdg-bds]。

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

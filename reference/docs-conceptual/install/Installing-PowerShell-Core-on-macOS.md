---
title: 在 macOS 上安装 PowerShell Core
description: 介绍如何在 macOS 上安装 PowerShell Core
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400460"
---
# <a name="installing-powershell-core-on-macos"></a>在 macOS 上安装 PowerShell Core

PowerShell Core 支持 macOS 10.12 和更高版本。
GitHub [版本][]页面上提供有所有可用包。
安装此包后，运行`pwsh`从终端。

## <a name="about-brew"></a>关于 Brew

[Homebrew][brew] 是 macOS 的首选包管理器。
如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的稳定版本

有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。

现在，可以开始安装 PowerShell：

```sh
brew cask install powershell
```

最后，验证安装是否正常运行：

```sh
pwsh
```

当发布新版本的 PowerShell 时，更新 Homebrew 的公式并升级 PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> 上面的命令可以从调用 PowerShell (pwsh) 主机，但 PowerShell shell 必须退出并重新启动才能完成升级和刷新中显示的值然后`$PSVersionTable`。

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>通过 Homebrew 在 macOS 10.12 或更高版本上安装最新的预览版

有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。

已安装 Homebrew 后，可以安装 PowerShell。
首先，安装[Cask 版本][ cask-versions]可让你安装的 cask 包的替代版本的包：

```sh
brew tap homebrew/cask-versions
```

现在，可以开始安装 PowerShell：

```sh
brew cask install powershell-preview
```

最后，验证安装是否正常运行：

```sh
pwsh-preview
```

当发布新版本的 PowerShell 时，更新 Homebrew 的公式并升级 PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> 可能会从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重新启动以完成升级。
> 刷新中显示的值和`$PSVersionTable`。

## <a name="installation-via-direct-download"></a>通过直接下载安装

下载 PKG 包`powershell-6.1.0-osx-x64.pkg`
（从[版本][]页下载）到 macOS 计算机上。

可以双击文件并按照提示操作，或者从终端安装：

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

安装 [OpenSSL](#install-openssl). PowerShell 远程处理和 CIM 操作均需要 OpenSSL。

## <a name="binary-archives"></a>二进制存档

已对 macOS 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。

### <a name="installing-binary-archives-on-macos"></a>在 macOS 上安装二进制存档

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

安装 [OpenSSL](#install-openssl). PowerShell 远程处理和 CIM 操作均需要 OpenSSL。

## <a name="installing-dependencies"></a>安装依赖关系

### <a name="install-xcode-command-line-tools"></a>安装 XCode 命令行工具

```sh
xcode-select --install
```

### <a name="install-openssl"></a>安装 OpenSSL

PowerShell 远程处理和 CIM 操作均需要 OpenSSL。 可以通过 MacPorts 或 Brew 进行安装。

#### <a name="install-openssl-via-brew"></a>通过 Brew 安装 OpenSSL

有关 Brew 的信息，请参阅[关于 Brew](#about-brew)。

若要安装 OpenSSL，请运行`brew install openssl`。

#### <a name="install-openssl-via-macports"></a>通过 MacPorts 安装 OpenSSL

1. 安装[XCode 命令行工具](#install-xcode-command-line-tools)。
1. 安装 MacPorts。
   如果需要说明，请参阅[安装指南](https://guide.macports.org/chunked/installing.macports.html)。
1. 通过运行 `sudo port selfupdate` 更新 MacPorts。
1. 通过运行 `sudo port upgrade outdated` 升级 MacPorts 包。
1. 通过运行安装 OpenSSL `sudo port install openssl`。
1. 链接的库，以使其可供 PowerShell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>卸载 PowerShell Core

如果使用 Homebrew 安装 PowerShell，使用以下命令卸载：

```sh
brew cask uninstall powershell
```

如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

若要删除其他 PowerShell 路径，请参阅[路径](#paths)本文档中部分，并删除使用路径`sudo rm`。

> [!NOTE]
> 如果使用 Homebrew 安装，则此步骤并非必要步骤。

## <a name="paths"></a>路径

* `$PSHOME` 是 `/usr/local/microsoft/powershell/6.1.0/`
* 将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件
* 将从 `$PSHOME/profile.ps1` 中读取默认配置文件
* 将从 `~/.local/share/powershell/Modules` 中读取用户模块
* 将从 `/usr/local/share/powershell/Modules` 中读取共享模块
* 将从 `$PSHOME/Modules` 中读取默认模块
* PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

配置文件采用 PowerShell 的每个主机配置。
因此默认特定于宿主的配置文件位于`Microsoft.PowerShell_profile.ps1`所在的位置。

PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。

由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。
因此，`$PSHOME`是`/usr/local/microsoft/powershell/6.1.0/`，和符号链接放置在`/usr/local/bin/pwsh`。

## <a name="additional-resources"></a>其他资源

* [Homebrew Web][brew]
* [Homebrew Github 存储库][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

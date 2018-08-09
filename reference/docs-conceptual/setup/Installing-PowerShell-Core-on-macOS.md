---
title: 在 macOS 上安装 PowerShell Core
description: 介绍如何在 macOS 上安装 PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587459"
---
# <a name="installing-powershell-core-on-macos"></a>在 macOS 上安装 PowerShell Core

PowerShell Core 支持 macOS 10.12 和更高版本。
GitHub [版本][]页面上提供有所有可用包。
安装包以后，从终端运行 `pwsh`。

### <a name="installation-via-homebrew-on-macos-1012"></a>在 macOS 10.12+ 上通过 Homebrew 安装

[Homebrew][brew] 是 macOS 的首选包管理器。
在终端窗口中，键入 `brew` 运行 Homebrew。  如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。

> [!NOTE]
> 如果以前安装过 Homebrew，建议运行“brew update-reset”和“brew update”。
```sh
brew update-reset
brew update
```

> 较旧版本的 Homebrew 使用点击“caskroom/cask”，此功能已被弃用，并已被迁移到“homebrew/cask”。  可在 [Homebrew-cask][cask] 中找到更为详细的信息。 使用“brew tap”命令列出你的当前点击。  如果看到“caskroom/cask”，可以使用“brew update”让 Homebrew 来迁移点击。

```sh
brew tap
brew update
```

安装/更新 Homebrew 后，安装 PowerShell 就变得很容易。

若要安装 PowerShell：

```sh
brew cask install powershell
```

最后，验证安装是否正常运行：

```sh
pwsh
```

若要退出 PowerShell 并返回 bash，请使用“exit”命令。
```sh
exit
```

PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell：

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> 可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 $PSVersionTable 中显示的值。

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>在 macOS 10.12+ 上通过 Homebrew 安装预览版

[Homebrew][brew] 是 macOS 的首选包管理器。
在终端窗口中，键入 `brew` 运行 Homebrew。  如果未找到 `brew` 命令，则需要按照[说明][brew]安装 Homebrew。

> [!NOTE]
> 如果以前安装过 Homebrew，建议运行“brew update-reset”和“brew update”。
```sh
brew update-reset
brew update
```

然后，必须点击 `versions` casks 存储库来获取预览包：

```sh
brew tap homebrew/cask-versions
```

若要安装 PowerShell 预览版：

```sh
brew cask install powershell-preview
```

最后，验证安装是否正常运行：

```sh
pwsh-preview
```

PowerShell 新版本发布后，只需更新 Homebrew 公式并升级 PowerShell 预览版：

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> 可从 PowerShell (pwsh) 主机调用上面的命令，但是调用后必须退出 PowerShell 并重启以完成升级，并刷新 $PSVersionTable 中显示的值。

### <a name="installation-via-direct-download"></a>通过直接下载安装

请从[版本][]页中将 PKG 包 `powershell-6.0.2-osx.10.12-x64.pkg` 下载到 CentOS 计算机。

可以双击文件并按照提示操作，或者从终端安装：

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>二进制存档

已对 macOS 和 Linux 平台提供 PowerShell 二进制 `tar.gz` 存档，以启用高级部署方案。

### <a name="installing-binary-archives-on-macos"></a>在 macOS 上安装二进制存档

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>卸载 PowerShell Core

如果使用 Homebrew 安装 PowerShell，则卸载很简单：

```sh
brew cask uninstall powershell
```

如果通过直接下载安装 PowerShell，则必须手动删除 PowerShell：

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

若要删除其他 PowerShell 路径，请参阅本文档的[路径][]一节，并使用 `sudo rm` 删除所需路径。

> [!NOTE]
> 如果使用 Homebrew 安装，则此步骤并非必要步骤。

[路径]:#paths

## <a name="paths"></a>路径

* `$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.2/`
* 将从 `~/.config/powershell/profile.ps1` 中读取用户配置文件
* 将从 `$PSHOME/profile.ps1` 中读取默认配置文件
* 将从 `~/.local/share/powershell/Modules` 中读取用户模块
* 将从 `/usr/local/share/powershell/Modules` 中读取共享模块
* 将从 `$PSHOME/Modules` 中读取默认模块
* PSReadline 历史记录将记录到 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

配置文件采用 PowerShell 的每个主机配置。
因此特定于主机的默认配置文件位于相同位置的 `Microsoft.PowerShell_profile.ps1`。

PowerShell 采用 macOS 上的 [XDG Base Directory 规范][xdg-bds]。

由于 macOS 派生自 BSD，因此前缀为 `/usr/local`而不是 `/opt`。
因此，`$PSHOME` 为 `/usr/local/microsoft/powershell/6.0.2/`，且 symlink 位于 `/usr/local/bin/pwsh` 中。

## <a name="additional-resources"></a>其他资源

* [Homebrew Web][brew]
* [Homebrew Github 存储库][GitHub]
* [Homebrew-Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

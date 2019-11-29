---
title: PowerShell Core 支持生命周期
description: 用于管理 PowerShell Core 支持的策略
ms.date: 08/06/2018
ms.openlocfilehash: 27738514fc84105a0339eafcdbb540b7d3790052
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416302"
---
# <a name="powershell-core-support-lifecycle"></a>PowerShell Core 支持生命周期

PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。 因此，PowerShell Core 不包括在 Windows 7/8.1/10 或 Windows Server 许可协议中。

不过，PowerShell Core 受传统 Microsoft 支持协议支持，包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。
还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。

## <a name="community-support"></a>社区支持

我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。
此外，你还可以从 Microsoft [PowerShell 技术社区][]或 [PowerShell][pshub] 中心页的社区部分列出的任何论坛中获得社区其他成员的帮助。 我们不能确保社区能够及时解决问题。 如果问题需要立即解决，应使用传统的付费支持选项。

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core 生命周期

PowerShell Core 即将采用 [Microsoft 新式生命周期策略][modern]。 此支持生命周期旨在使客户随时知悉最新版本。

PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。

> [!IMPORTANT]
> 必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。

例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。

> [!IMPORTANT]
> 必须在每个新修补程序版本发布后的 30 天之内进行更新，然后方可继续获取支持。

例如，若要运行 PowerShell Core 6.1，且 6.1.3 已于 2019 年 2 月 19 日发布，应在发布后的 30 天之内（即 2019 年 3 月 21 日前）更新到 PowerShell Core 6.1.3，更新后方可继续获取支持。 如果发现需要任何修补程序，则将在下一次累积更新中发布修补程序。

新式生命周期策略还要求，在中止对某产品（即 PowerShell Core）提供支持前的 12 个月内，Microsoft 需向客户持续提供通知。

最终，我们预计 PowerShell Core 将采用长期服务方法。 在此服务方法中，只需服务和安全更新即可获取有关 6.x 特定分支/版本的支持。

## <a name="supported-platforms"></a>支持平台

若要确认你的 PowerShell Core 平台和版本是否受到官方支持，请参阅下表。

我们的社区也为一些平台提供了包，但它们不受官方支持。 这些包在表中标记为 `Community`。

列为 `Experimental` 的平台不受官方支持，但可用于实验和反馈。

| 平台                                          |      6.2      |    7.0    |
|---------------------------------------------------|:-------------:|:---------:|
| Windows 7、8.1 和 10                            |   支持   | 支持 |
| Windows Server 2008 R2、2012 R2、2016             |   支持   | 支持 |
| [Windows Server 半年频道][semi-annual] |   支持   | 支持 |
| Ubuntu 16.04 和 18.04                            |   支持   | 支持 |
| Ubuntu 18.10（使用 Snap 包）                   |   社区   | 社区 |
| Ubuntu 19.04（通过 Snap 包）                   |   社区   | 社区 |
| Debian 9                                          |   支持   | 支持 |
| Debian 10                                         | 不受支持 | 支持 |
| CentOS 7                                          |   支持   | 支持 |
| Red Hat Enterprise Linux 7                        |   支持   | 支持 |
| openSUSE 42.3                                     |   支持   | 支持 |
| Fedora 28                                         |   支持   | 支持 |
| Fedora 29、Fedora 30                                     | 不受支持 | 支持 |
| Alpine 3.8                                        |   请参阅备注    | 请参阅备注  |
| Alpine 3.9 和 Alpine 3.10                               | 不受支持 | 请参阅备注  |
| macOS 10.12+                                      |   支持   | 支持 |
| Arch                                              |   社区   | 社区 |
| Raspbian                                          |   社区   | 社区 |
| Kali                                              |   社区   | 社区 |
| AppImage（可在多个 Linux 平台上运行）      |   社区   | 社区 |
| [Snap 包](https://snapcraft.io/powershell)   |   查看注释    | 查看注释  |

> [!NOTE]
> Snap 包与正在运行此包的发行版受到相同的支持。

> [!NOTE]
> Alpine 不支持 CIM、PowerShell 远程处理和 DSC。

## <a name="powershell-releases-end-of-life"></a>PowerShell 版本生命周期终止日期

根据 [PowerShell Core 生命周期](#lifecycle-of-powershell-core)，下表列出了各个版本不再受支持的日期。

| 版本 | 生命周期终止日期                   |
|---------|-------------------------------|
| 6.0     | 2019 年 2 月 13 日             |
| 6.1     | 2019 年 9 月 28 日            |
| 6.2     | 7 发布后的 6 个月后     |

## <a name="unsupported-platforms"></a>不支持的平台

如果某个平台版本已到达平台所有者定义的生命周期终止日期，PowerShell Core 也会停止支持相应平台版本。 以前发布的包对需要访问的客户仍可用，但将不再提供任何种类的正式支持和更新。

因此，发行版所有者不再支持以下版本，它们不受支持。

| 平台 | 版本 | 生命周期终止                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [2017 年 8 月](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [2017 年 12 月](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [2018 年 5 月](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| OpenSUSE | 42.1    | [2017 年 5 月](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| OpenSUSE | 42.2    | [2018 年 1 月](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [2017 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [2018 年 1 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [2018 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [2018 年 6 月](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [2018 年 11 月](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [2019 年 4 月](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>有关许可的说明

PowerShell Core 在 [MIT 许可][] 下发布。 根据此许可规定，如果没有付费支持协议，那么用户只能获得[社区支持][]。 对于社区支持，Microsoft 无法保证及时作出响应或进行修复。

## <a name="windows-powershell-module"></a>Windows PowerShell 模块

对 PowerShell Core 的支持不包括产品模块，除非这些模块显式支持 PowerShell Core。 例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。

不过，在某些情况下，不显式支持 PowerShell Core 的模块可能是兼容的。 通过安装 [WindowsPSModulePath][] 模块，可以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core `PSModulePath`。

首先，安装来自 PowerShell 库的 WindowsPSModulePath  模块：

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>实验性功能

[实验性功能][]只能获得[社区支持](#community-support)。

[顶级]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[社区支持]: https://github.com/powershell/powershell/issues
[pshub]: https://docs.microsoft.com/powershell
[PowerShell 技术社区]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[辅助支持]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 许可]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[实验性功能]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures

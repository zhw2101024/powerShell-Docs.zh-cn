---
title: PowerShell Core 支持生命周期
description: 用于管理 PowerShell Core 支持的策略
ms.date: 03/09/2020
ms.openlocfilehash: c1e91aa193dd4a6353098e16ae18301c0753ea85
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082413"
---
# <a name="powershell-support-lifecycle"></a>PowerShell 支持生命周期

PowerShell 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。 PowerShell 不包含在 Windows 许可协议中。

PowerShell 受传统 Microsoft 支持协议支持，包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。
还可通过针对相应问题填写支持请求，从而付费获取有关 PowerShell 的[辅助支持][]。

## <a name="community-support"></a>社区支持

我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。
此外，你还可以从 Microsoft [PowerShell 技术社区][]或 [PowerShell][pshub] 中心页的社区部分列出的任何论坛中获得社区其他成员的帮助。 我们不能确保社区能够及时解决问题。 如果问题需要立即解决，应使用传统的付费支持选项。

## <a name="lifecycle-of-powershell-7"></a>PowerShell 7 生命周期

发布 PowerShell 7 后，PowerShell 继续受 [Microsoft 新式生命周期策略][modern]支持，但支持日期链接到 [.NET Core 的支持生命周期][Long-Term]。 在此服务方法中，客户可以选择长期支持 (LTS) 版本或当前版本。 PowerShell 7.0 是一个 LTS 版本。 结束对 .NET Core 3.1 的支持。 下一个 LTS 版本遵循下一个 .NET Core LTS 版本。 有关当前结束支持日期的信息，请参阅 [PowerShell 版本生命周期结束表](#powershell-releases-end-of-life)。 LTS 版本更新仅包含关键安全和服务更新，以及旨在避免或最大程度地减小对现有工作负荷的影响的修补程序。

当前版本是在 LTS 版本之间出现的版本。 当前版本可以包含关键修补程序、创新和新功能。 当前版本在后续的当前版本或 LTS 版本发布后的三个月内受支持。

> [!IMPORTANT]
> 必须安装最新的修补程序更新才能获得支持。 例如，如果你运行的是 PowerShell 7.0，并且已发布 7.0.1，则必须更新到 7.0.1 才能获得支持。

## <a name="lifecycle-of-powershell-core-6x"></a>PowerShell Core 6.x 生命周期

PowerShell Core 使用 [Microsoft 新式生命周期策略][modern]。 此支持生命周期旨在使客户随时知悉最新版本。

PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。 但是，在发布 PowerShell 7 后，不会再有 6.x 的次要版本。 PowerShell 6.2.x 仍受支持时将继续接收服务更新。

> [!IMPORTANT]
> 必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。

例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。

> [!IMPORTANT]
> 必须在每个新修补程序版本发布后的 30 天之内进行更新，然后方可继续获取支持。

例如，若要运行 PowerShell Core 6.1，且 6.1.3 已于 2019 年 2 月 19 日发布，应在发布后的 30 天之内（即 2019 年 3 月 21 日前）更新到 PowerShell Core 6.1.3，更新后方可继续获取支持。 如果发现需要任何修补程序，则将在下一次累积更新中发布修补程序。

新式生命周期策略还要求，在中止对某产品（即 PowerShell Core）提供支持前的 12 个月内，Microsoft 需向客户持续提供通知。

## <a name="supported-platforms"></a>支持的平台

若要确认你的 PowerShell Core 平台和版本是否受到官方支持，请参阅下表。

我们的社区也为一些平台提供了包，但它们不受官方支持。 这些包在表中标记为 `Community`。

列为 `Experimental` 的平台不受官方支持，但可用于实验和反馈。

| 平台                                          |      6.2      |    7.0    |
| ------------------------------------------------- | :-----------: | :-------: |
| Windows 8.1 和 10                               |   支持   | 支持 |
| Windows Server 2012 R2、2016                      |   支持   | 支持 |
| [Windows Server 半年频道][semi-annual] |   支持   | 支持 |
| Ubuntu 16.04 和 18.04                            |   支持   | 支持 |
| Ubuntu 19.10（通过 Snap 包）                   |   社区   | 社区 |
| Ubuntu 20.04（通过 Snap 包）                   |   社区   | 社区 |
| Debian 9                                          |   支持   | 支持 |
| Debian 10                                         | 不支持 | 支持 |
| CentOS 7                                          |   支持   | 支持 |
| CentOS 8                                          | 不支持 | 支持 |
| Red Hat Enterprise Linux 7                        |   支持   | 支持 |
| Red Hat Enterprise Linux 8                        | 不支持 | 支持 |
| Fedora 30                                         | 不支持 | 支持 |
| Alpine 3.8                                        |   请参阅备注    | 请参阅备注  |
| Alpine 3.9 和 Alpine 3.10                               | 不支持 | 请参阅备注  |
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

## <a name="powershell-releases-end-of-life"></a>PowerShell 版本生命周期结束

根据 [PowerShell 生命周期](#lifecycle-of-powershell-7)，下表列出了各个版本不再受支持的日期。

| 版本 |    生命周期终止日期     |
| :-----: | ------------------ |
|   7.0   | 2022 年 12 月 3 日   |
|   6.2   | 2020 年 9 月 4 日  |
|   6.1   | 2019 年 9 月 28 日 |
|   6.0   | 2019 年 2 月 13 日  |

## <a name="unsupported-platforms"></a>不支持的平台

如果某个平台版本已到达平台所有者定义的生命周期终止日期，PowerShell Core 也会停止支持相应平台版本。 以前发布的包对需要访问的客户仍可用，但将不再提供任何种类的正式支持和更新。

因此，发行版所有者不再支持以下版本，它们不受支持。

|    平台    | 版本 |                                                         生命周期终止                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [2018 年 6 月](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [2017 年 8 月](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [2017 年 12 月](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [2018 年 5 月](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [2018 年 11 月](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [2019 年 5 月](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| OpenSUSE       |  42.1   | [2017 年 5 月](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| OpenSUSE       |  42.2   | [2018 年 1 月](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| OpenSUSE       |  42.3   | [2019 年 7 月](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14.04  | [2019 年 4 月](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16.10  | [2017 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17.04  | [2018 年 1 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17.1  | [2018 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [2020 年 1 月](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [2020 年 1 月](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>有关许可的说明

PowerShell Core 在 [MIT 许可][] 下发布。 根据此许可规定，如果没有付费支持协议，那么用户只能获得[社区支持][]。 对于社区支持，Microsoft 无法保证及时作出响应或进行修复。

## <a name="windows-powershell-compatibility"></a>Windows PowerShell 兼容性

PowerShell 的支持生命周期不包含 PowerShell 7 发布包之外提供的模块。 例如，使用 Windows Server 随附的 `ActiveDirectory` 模块受 [Windows 支持生命周期][]支持。

PowerShell 7 改进了与为 Windows PowerShell 编写的现有 PowerShell 模块的兼容性。
有关详细信息，请参阅 [about_Windows_Compatibility][] 文章和[模块兼容性列表][]。

> [!NOTE]
> PowerShell 7 中不再需要也不再支持 [WindowsPSModulePath](https://www.powershellgallery.com/packages/WindowsPSModulePath) 模块。

## <a name="experimental-features"></a>实验性功能

[实验性功能][]只能获得[社区支持](#community-support)。

## <a name="release-history"></a>版本历史记录

下表包含 PowerShell 主要版本的时间线。 此表仅供历史参考。 它不用于确定支持生命周期。

|       版本        | 发布日期 |                                                                     注意                                                                      |
| -------------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| PowerShell 7.0 (LTS) |   2020 年 3 月   | 基于 .NET Core 3.1 (LTS) 生成                                                                                                                  |
| PowerShell 6.0       |   2018 年 1 月   | 第一版，基于 .NET Core 2.1 生成。 可在 Windows、Linux 和 macOS 上安装。                                                              |
| PowerShell 5.1       |   2016 年 8 月   | 在 Windows 10 周年更新和 Windows Server 2016 中发布                                                                             |
| PowerShell 5.0       |   2016 年 2 月   | 在 Windows Management Framework (WMF) 5.0 中发布                                                                                            |
| PowerShell 4.0       |   2013 年 10 月   | 在 Windows 8.1 中与 Windows Server 2012 R2 集成。 可在 Windows 7 SP1、Windows Server 2008 R2 SP1 和 Windows Server 2012 上安装。 |
| PowerShell 3.0       |   2012 年 10 月   | 在 Windows 8 中与 Windows Server 2012 集成。 可在 Windows 7 SP1、Windows Server 2008 SP1 和 Windows Server 2008 R2 SP1 上安装。  |
| PowerShell 2.0       |   2009 年 7 月   | 在 Windows 7 中与 Windows Server 2008 R2 集成。 可在 Windows XP SP3、Windows Server 2003 SP2 和 Windows Vista SP1 上安装。            |
| PowerShell 1.0       |   2006 年 11 月   | 可在 Windows XP SP2、Windows Server 2003 SP1 和 Windows Vista 上安装。 Windows Server 2008 的可选组件。                          |

<!-- hyperlink references -->
[顶级]: https://www.microsoft.com/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[社区支持]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell 技术社区]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[辅助支持]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[MIT 许可]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[about_Windows_Compatibility]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Windows 支持生命周期]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[模块兼容性列表]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[实验性功能]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures

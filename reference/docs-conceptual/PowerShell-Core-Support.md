# <a name="powershell-core-support-lifecycle"></a>PowerShell Core 支持生命周期

PowerShell Core 是独特的工具和组件集，该集从 Windows PowerShell 单独传输、安装和配置。
因此，PowerShell Core 不包括在 Windows 7/8.1/10 或 Windows Server 许可协议中。

但是，PowerShell Core 受传统 Microsoft 支持协议支持，此类协议包括[顶级][]、[Microsoft 企业协议][enterprise-agreement]和 [Microsoft 软件保障][assurance]。
还可通过就相应问题填写支持请求，从而付费获取有关 PowerShell Core 的[辅助支持][]。

我们还在 GitHub 上提供[社区支持][]，你可在其中提交问题、bug 或功能请求。
或者，可以从常规 [Microsoft 社区][]或 Microsoft [PowerShell 技术社区][] 的其他成员获取帮助。
我们不能确保问题能够及时解决。
如果问题需要立即解决，应使用传统的付费支持选项。

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core 生命周期

PowerShell Core 采用 [Microsoft 新式声明周期策略][modern]。
此支持生命周期旨在使客户随时知悉最新版本。

PowerShell Core 的版本 6.x 分支（例如 6.0、6.1、6.2 等）大约每六个月更新一次。

> [!IMPORTANT]
> 必须在每个新次要版本发布后的六个月时间之内进行更新，然后方可继续获取支持。

例如，如果 PowerShell Core 6.1 发布于 2018 年 7 月 1 日，则应在 2019 年 1 月 1 日前更新到 PowerShell Core 6.1，更新后方可继续获取支持。

![PowerShell Core 分支生命周期][lifecycle-chart]

新式生命周期策略还要求在中止对某产品（例如 PowerShell Core）提供支持前的 12 个月内， Microsoft 需向客户持续提供通知。

最终，我们希望 PowerShell Core 采取“长期服务”方法，从而只需服务和安全更新即可获取有关 6.x 特定分支/版本的支持。

## <a name="supported-platforms"></a>支持平台

PowerShell Core 在以下平台上受到正式支持：

* Windows 7、8.1 和 10
* Windows Server 2008 R2、2012 R2、2016
* [Windows Server 半年频道][semi-annual]
* Ubuntu 14.04、16.04 和 17.04
* Debian 8.7+ 和 9
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42.2
* Fedora 25、26
* macOS 10.12+

我们社区也为以下平台提供包，但是它们不受正式支持：

* Arch Linux
* Kali Linux
* AppImage（可在多个 Linux 平台上运行）

## <a name="notes-on-licensing"></a>有关许可的说明

PowerShell Core 在 [MIT 许可][] 下发布。
根据此许可规定，如果缺失付费支持协议，则用户仅限于获取[社区支持][]。
对于社区支持，Microsoft 无法保证及时作出响应或进行修复。

## <a name="windows-powershell-module"></a>Windows PowerShell 模块

对 PowerShell Core 的支持不扩展到其他产品模块，除非那些产品模块显式支持 PowerShell Core。
例如，使用 Windows Server 随附的 `ActiveDirectory` 模块是不受支持的方案。

但是，不显式支持 PowerShell Core 的模块在某些情况下可能兼容。
通过安装 [`WindowsPSModulePath`][] 模块，可以将 Windows PowerShell `PSModulePath` 追加到 PowerShell Core `PSModulePath`。

首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[顶级]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[社区支持]: https://github.com/powershell/powershell/issues
[Microsoft 社区]: https://answers.microsoft.com/
[PowerShell 技术社区]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[辅助支持]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 许可]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/

# <a name="the-powershell-gallery"></a>PowerShell 库

PowerShell 库是 PowerShell 内容的中心存储库。 你可以在库中找到新的 PowerShell 命令或 Desired State Configuration (DSC) 资源。

# <a name="powershellget-overview"></a>PowerShellGet 概述

PowerShellGet 模块包含用于发现、安装、更新和发布来自 https://www.PowerShellGallery.com 和其他专用存储库的模块、DSC 资源、角色功能和脚本等 PowerShell 项目的 cmdlet。

## <a name="getting-started-with-the-gallery"></a>库入门

从库安装项需要最新版本的 PowerShellGet 模块，Windows 10、Windows Management Framework (WMF) 5.0 或基于 MSI 的安装程序（适用于 PowerShell 3 和 4）中提供此模块。

- [**获取 Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)、
- [**获取 WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175)，或
- [**获取 MSI 安装程序**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

使用最新 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模块，你可以进行以下操作：

-   使用 [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 搜索库中的项
-   使用 [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 将库中的项保存到系统
-   使用 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 安装库中的项
-   使用 [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 将项上传到库
-   使用 [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 添加你自己的自定义存储库

有关如何在库中使用 PowerShellGet 命令的详细信息，请参阅[入门](psgallery/psgallery_gettingstarted.md)页面。 你也可运行 *Update-Help -Module PowerShellGet* 安装这些命令的本地帮助。

## <a name="supported-operating-systems"></a>受支持的操作系统

**PowerShellGet** 模块需要 **PowerShell 3.0 或更高版本**。

因此，**PowerShellGet** 需要以下操作系统之一：

- Windows 10
- Windows 8.1 专业版
- Windows 8.1 企业版
- Windows 7 SP1
- Windows Server 2016 TP5
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** 也需要 .NET Framework 4.5 或更高版本。 你可从[此处](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。


## <a name="got-a-question-have-feedback"></a>遇到问题？ 有反馈？

可在[入门](psgallery/psgallery_gettingstarted.md)页面找到有关 PowerShell 库和 PowerShellGet 的详细信息。 请使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供反馈和报告问题。


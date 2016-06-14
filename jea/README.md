# Just Enough Administration
Just Enough Administration (JEA) 是一项安全技术，委派的管理员可通过它执行可通过 PowerShell 处理的任意操作。
使用 JEA，你可以：
- 通过利用代表普通用户执行特权操作的虚拟帐户，**减少你计算机上的管理员数量**。
- 通过指定用户可运行的 cmdlet、函数和外部命令，**限制用户可执行的操作**。
- 使用准确显示用户在会话中所执行命令的“即时权限提升”脚本，**更好地了解你的用户进行的操作**。

为什么这很重要？
请考虑这样的常见场景，即你的 DNS 服务器与 Active Directory 域控制器位于同一位置。
你的 DNS 管理员需要拥有本地管理员特权才能解决有关 DNS 服务器的问题，但是为了实现这一点，必须使其成为拥有高度特权的“域管理员”组的成员。
这将有效地给予其对整个域的控制全以及对该计算机上所有资源的访问权。

而有了 JEA，你就可以为 DNS 管理员配置角色，使其能够并且仅能够访问完成工作所需的所有命令。
这意味着他们可以轻松修复中毒的 DNS 缓存，而无权访问 Active Directory、浏览文件系统或运行潜在危险脚本。
更棒的是，将 JEA 会话配置为使用具有一次性特权的虚拟帐户时，你的 DNS 管理员可以使用*无特权*凭据连接到服务器并仍可运行特权命令。

## 入门

### 安装
JEA 正与即将发布的 Windows Server 2016 版共同开发，并可通过 Windows Management Framework 更新在旧版 Windows 上使用。
当前版本的 JEA 在以下平台上可用：

**Windows Server**
- Windows Server 2016 Technical Preview 4 及更高版本
- \*安装了[ Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows Server 2012 R2、2012 和 2008 R2

**Windows 客户端**
- 安装了 11 月更新 (1511) 的 Windows 10
- \*安装了[ Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows 8.1、8 和 7

\* Windows Server 2008 R2 或 Windows 7 上目前不支持在 JEA 会话中使用虚拟帐户。


### 核心概念
**JEA 具体是什么？**

JEA 是 PowerShell [受约束的终结点](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)的扩展，它添加了角色定义、虚拟帐户和多项其他改进，让你能够更轻松地锁定管理终结点。
JEA 终结点由一个 PowerShell 会话配置文件和一个或多个角色功能文件组成。

**会话配置文件和角色功能文件是什么？**

PowerShell 会话配置文件 (.pssc) 定义可连接到 PowerShell 终结点的*人员*及其配置*方式*。
在该文件中，你可以将用户和安全组映射到特定管理角色，并配置虚拟帐户和脚本策略等全局设置。
会话配置文件特定于每台计算机，让你能够根据需要按计算机控制访问权限。

PowerShell 角色功能文件 (.psrc) 定义属于某个角色的用户能够在系统上执行的*操作*。
在该文件中，你可以限制用户在其 JEA 会话中使用的 cmdlet、函数、提供程序和外部提供程序。
角色功能文件对于身为服务对象的角色（DNS 域、1 级技术支持人员、只读清单审核等）常是通用的，这些文件属于 PowerShell 模块，让你能够在你的环境中以及与他人进行共享。

**JEA 如何利用虚拟帐户？**

在 PowerShell 会话配置文件中，你可以将 JEA 会话配置为使用虚拟的“运行方式”帐户。
虚拟帐户是一次性特权帐户，在执行用户命令的上下文中，针对特定会话中的特定连接用户而生成。
默认情况下，虚拟帐户属于本地“管理员”安全组，但可以选择将其配置为仅属于你指定的安全组。

### 浏览体验指南
准备好创建你的第一个 JEA 终结点了吗？
请参阅 [JEA 体验指南](./JEA Guide.md)了解如何创作、部署和使用你自己的 JEA 终结点。
该指南允许你使用预构建的 JEA 终结点快速开始，让你大概了解最终用户体验；然后引导你从头重新创建终结点，以帮助解释会话配置和角色功能。

### 开始创作你自己的 JEA 终结点
创作 JEA 终结点很容易 -- 仅需启用了 JEA 的系统和文件编辑器（如 PowerShell ISE）。
对于开始使用很有帮助的一个提示是，使用不带任何其他参数的 `New-PSRoleCapabilityFile -Path <path>` 和 `New-PSSessionCapabilityFile -Path <Path>` 创建主干文件。
这些主干文件包含所有适用的配置字段，以及解释每个字段用途的有益注释。 

若要更轻松地创作 JEA 终结点，请参阅 [JEA 工具包帮助程序](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)，它提供可以用于创作会话配置文件和角色功能文件的 GUI。
它甚至支持生成基于 PowerShell 日志的角色功能，直接为你提供你的用户定期运行完成其工作的命令。


<!--HONumber=Jun16_HO1-->



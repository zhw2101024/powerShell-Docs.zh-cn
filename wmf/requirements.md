# 系统要求

- 先安装最新 Windows 更新，再安装 WMF 5.0 RTM。
- 你仅可以在以下操作系统上安装 WMF 5.0 RTM：

    | 操作系统       | 版本         | 系统必备组件        |  包链接 |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | 除 IA64 之外的所有版本 | 已安装 [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) 和 [.NET Framework 4.5](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) 或更高版本| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | 专业版、企业版 | | **x64:**  [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:**  [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | 所有版本 | 已安装 [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) 和 [.NET Framework 4.5 或更高版本](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) | **x64:**  [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:**  [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# 安装说明

### 从 Windows 资源管理器（或文件资源管理器）安装 WMF 5.0：

1. 导航到在其中下载了 MSU 文件的文件夹。

2. 双击 MSU 以运行它。

### 从“命令提示符”安装 WMF 5.0：

1. 下载适用于计算机体系结构的正确程序包后，使用提升的用户权限（以管理员身份运行）打开“命令提示符”窗口。 在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的服务器核心安装选项上，命令提示符默认使用提升的用户权限打开。

2. 将目录更改为向其中下载或复制 WMF 5.0 安装包的文件夹。

3. 运行下列命令之一：
    - 在正在运行 Windows Server 2012 R2 或 Windows 8.1 x64 的计算机上，运行 **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**。
    - 在正在运行 Windows Server 2012 的计算机上，运行 **W2K12-KB3134759-x64.msu /quiet**。
    - 在正在运行 Windows Server 2008 R2 SP1 或 Windows 7 SP1 x64 的计算机上，运行 **Win7AndW2K8R2-KB3134760-x64.msu /quiet**。
    - 在正在运行 Windows 8.1 x86 的计算机上，运行 **Win8.1-KB3134758-x86.msu /quiet**。
    - 在正在运行 Windows 7 SP1 x86 的计算机上，运行 **Win7-KB3134760-x86.msu /quiet**。

### Windows Server 2008 R2 SP1 和 Windows 7 SP1 的其他安装说明：

确保已满足以下必备条件：
- 已安装最新服务包。
- 已安装 [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)。
- 已安装 [NET framework 4.5 或更高版本](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)。

**WMF 4.0 依赖关系**

Windows Server 2008 R2 SP1 和 Windows 7 SP1 系统内置了 PowerShell 2.0、WinRM 和 WMI。 在发布 Windows Server 2008 R2 SP1 和 Windows 7 SP1 之后，发布了更新这些内置组件的 WMF 3.0 和 WMF 4.0 程序包。 安装/卸载 WMF 3.0 和 WMF 4.0 程序包在以下升级路径中发现了一些问题：

- 内置 --> WMF 4.0。
- 内置 --> WMF 3.0 --> WMF4.0。 

我们在 WMF 4.0 程序包中修复了这些问题。 因此，对于在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上安装 WMF 5.0，WMF 4.0 是先决条件。 下面是如果在升级到 WMF 5.0 之前未安装 WMF 4.0，可能会遇到的特定问题：

- 在 Windows 7 SP1 和 Windows Server 2008 R2 SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)) 中卸载 WMF 3.0 或 WMF 5.0（未安装先决条件 WMF 4.0）之后，已转发事件日志不可用，且 EventCollector 日志不会显示在事件查看器中 。
- 在 Windows 7 SP1 和 Windows Server 2008 R2 SP1 中进行以下升级时，对 *PSModulePath* 环境变量进行的自定义会重置为默认值：直接从内置 PowerShell 2.0 升级到 WMF 5.0 ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) 或从 WMF 3.0 升级到 WMF 5.0 ([KB2872047](https://support.microsoft.com/en-us/kb/2872047))。

**WinRM 依赖关系**

Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。 在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上默认不启用 WinRM。 若要启用 WinRM，请在 Windows PowerShell 提升的会话中运行 **Set-WSManQuickConfig**。

# 卸载说明

### 使用命令提示符

1.  打开“命令提示符”。

2.  运行 [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307)，如下所示：

在 Windows Server 2012 R2 和 Windows 8.1 上：
```powershell
wusa /uninstall /kb:3134758
```
在 Windows Server 2012 上：
```powershell
wusa /uninstall /kb:3134759
```
在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上：
```powershell
wusa /uninstall /kb:3134760
```

### 使用控制面板。

1.  打开“控制面板”。

2.  打开“程序”，然后打开“卸载程序”。

3.  单击“查看已安装的更新”。

4.  从已安装的更新列表中选择“Windows Management Framework 5.0”。 这对应于 *KB3134758*、*KB3134759* 或 *KB3134760*。 单击“卸载”。


<!--HONumber=Mar16_HO4-->



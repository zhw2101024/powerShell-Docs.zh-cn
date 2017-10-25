---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
contributor: keithb
title: "安装和配置 WMF 5.1"
ms.openlocfilehash: ea9b2fb184f2dd9a8e7a09c3a36278087f795172
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2017
---
# <a name="install-and-configure-wmf-51"></a>安装和配置 WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>下载和安装 WMF 5.1 包

下载适用于要在其中进行安装的操作系统和体系结构的 WMF 5.1 包：

| 操作系统       | 必备条件       | 包链接             |
|------------------------|---------------------|---------------------------|
| Windows Server 2012 R2 | | [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516)|
| Windows Server 2012    | | [W2K12-KB3191565-x64.msu](https://go.microsoft.com/fwlink/?linkid=839513)|
| Windows Server 2008 R2 | [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) | 
| Windows 8.1            |  | **x64：**[Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516) </br> **x86：**[Win8.1-KB3191564-x86.msu](https://go.microsoft.com/fwlink/?linkid=839521) |
| Windows 7 SP1          | [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | **x64：**[Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) </br> **x86：**[Win7-KB3191566-x86.ZIP](https://go.microsoft.com/fwlink/?linkid=839522)



## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>安装适用于 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1

> **注意：**针对 Windows Server 2008 R2 和 Windows 7 的安装说明发生变化，不同于其他包的安装说明。 下文中介绍了针对 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安装说明。

**在 Windows Server 2008 R2 和 Windows 7 上安装 WMF 5.1**

1. 转到在其中下载了 ZIP 文件的文件夹。 

2. 右键单击 ZIP 文件，然后选择“全部提取...”。 ZIP 文件中包含 2 个文件：MSU 和 Install-WMF5.1.PS1 脚本文件。 解压缩 ZIP 文件后，便可以将内容复制到运行 Windows 7 或 Windows Server 2008 R2 的任何一台计算机上。  

3. 提取 ZIP 文件内容后，以管理员身份打开 PowerShell，然后转到包含  
ZIP 文件内容的文件夹。 

4. 在此文件夹中运行 Install-Wmf5.1.ps1 脚本，然后按说明操作。 此脚本会在本地计算机上检查系统必备，如果系统必备已满足，则会安装 WMF 5.1。 下文中列出了系统必备。 

Install-WMF5.1.ps1 采用以下参数，以简化在 Windows Server 2008 R2 和 Windows 7 上自动执行安装：

- AcceptEula：如果包含此参数，将会自动接受但不显示 EULA。
- AllowRestart：只有在指定 AcceptEula 后，才能使用此参数。 如果包含此参数，并且在安装 WMF 5.1 后需要重启，将在安装完成后不发出提示就立即重启计算机。 

**Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 系统必备**

若要在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安装 WMF 5.1，必须先安装以下各项：
- 必须安装最新 Service Pack。
- **不得**安装 WMF 3.0。 安装 WMF 5.1 来替代 WMF 3.0 会导致 PSModulePath 丢失，进而可能会导致其他应用程序无法正常运行。 安装 WMF 5.1 前，要么必须先卸载 WMF 3.0，要么必须先保存 PSModulePath，然后在 WMF 5.1 安装完成后进行手动还原。 
- WMF 5.1 至少需要 [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642)。可按下载位置提供的说明操作，安装 Microsoft .NET Framework 4.5.2。

**WinRM 依赖关系** 

Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。 若要启用 WinRM，在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>安装适用于 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1
**在 Windows 资源管理器（或 Windows Server 2012 R2 或 Windows 8.1 中的文件资源管理器）中安装**

1. 导航到在其中下载了 MSU 文件的文件夹。

2. 双击 MSU 以运行它。

**通过命令提示符进行安装**

1. 下载适用于计算机体系结构的正确程序包后，使用提升的用户权限（以管理员身份运行）打开“命令提示符”窗口。 在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的服务器核心安装选项上，命令提示符默认使用提升的用户权限打开。

2. 将目录更改为向其中下载或复制 WMF 5.1 安装包的文件夹。

3. 运行下列命令之一：
    - 在运行 Windows Server 2012 R2 或 Windows 8.1 x64 的计算机上，运行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`。
    - 在运行 Windows Server 2012 的计算机上，运行 `W2K12-KB3191565-x64.msu /quiet`。
    - 在运行 Windows 8.1 x86 的计算机上，运行 `Win8.1-KB3191564-x86.msu /quiet`。
    

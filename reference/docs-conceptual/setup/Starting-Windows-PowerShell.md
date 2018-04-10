---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 启动 Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="starting-windows-powershell"></a>启动 Windows PowerShell
PowerShell 是一个脚本引擎 dll，嵌入到多个主机中。  启动的最常见主机是交互式命令行 PowerShell.exe 和交互式脚本环境 PowerShell_ISE.exe。

若要在 Windows Server® 2012 R2、Windows® 8.1、Windows Server 2012 和 Windows 8 上启动 Windows PowerShell®，请参阅[常见管理任务和导航](http://technet.microsoft.com/library/hh831491.aspx)。

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>如何在早期版本的 Windows 上启动 Windows PowerShell

本部分介绍了如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 上启动 Windows PowerShell 和 Windows PowerShell 集成脚本环境 (ISE)。 还介绍了如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中启用 Windows PowerShell ISE 的可选功能。

使用以下任一方法来启动已安装的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本（如果适用）。

#### <a name="from-the-start-menu"></a>在“开始”菜单中

- 单击“开始”，键入 **PowerShell**，然后单击“Windows PowerShell”。
- 在“开始”菜单中，依次单击“开始”、“所有程序”、“附件”、“Windows PowerShell”文件夹，然后单击“Windows PowerShell”。

#### <a name="at-the-command-prompt"></a>在命令提示符处

在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：

```
PowerShell
```

你还可以使用 PowerShell.exe 程序的参数来自定义会话。 有关详细信息，请参阅 [PowerShell.exe 命令行帮助](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用管理权限（“以管理员身份运行”）

单击“**开始**”，键入 **PowerShell**，右键单击“**Windows PowerShell**”，然后单击“**以管理员身份运行**”。

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在早期版本的 Windows 上启动 Windows PowerShell ISE

使用以下任一方法启动 Windows PowerShell ISE。

#### <a name="from-the-start-menu"></a>在“开始”菜单中

- 单击“开始”，键入 **ISE**，然后单击“Windows PowerShell ISE”。
- 在“开始”菜单中，依次单击“开始”、“所有程序”、“附件”、“Windows PowerShell”文件夹，然后单击“Windows PowerShell ISE”。

#### <a name="at-the-command-prompt"></a>在命令提示符处

在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：

```
PowerShell_ISE
```

或

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用管理权限（“以管理员身份运行”）

单击“**开始**”，键入 **ISE**，右键单击“**Windows PowerShell ISE**”，然后单击“**以管理员身份运行**”。

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在早期版本的 Windows 上启用 Windows PowerShell ISE

在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，默认情况下，所有版本的 Windows 上都启用 Windows PowerShell ISE。 如果尚未启用，则 Windows Management Framework 4.0 或 Windows Management Framework 3.0 会启用它。

在 Windows PowerShell 2.0 中，默认情况下，在 Windows 7 上启用 Windows PowerShell ISE。 但是，在 Windows Server 2008 R2 和 Windows Server 2008 上，它是一项可选功能。

若要启用 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中的 Windows PowerShell ISE，请使用以下过程。

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>启用 Windows PowerShell 集成脚本环境 (ISE)

1. 启动“服务器管理器”。
2. 单击“功能”，然后单击“添加功能”。
3. 在“选择功能”中，单击“Windows PowerShell 集成脚本环境 (ISE)”

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>启动 32 位版本的 Windows PowerShell

在 64 位计算机 (**Windows PowerShell (x86)**) 上安装 Windows PowerShell 时，除 64 位版之外，还将安装 32 位版本的 Windows PowerShell。 运行 Windows PowerShell 时，默认运行 64 位版。

但是，有时可能需要运行 **Windows PowerShell (x86)**，例如使用需要 32 位版的模块时，或者远程连接到 32 位计算机时。

若要启动 32 位版本的 Windows PowerShell，请使用以下任何过程。

#### <a name="in-windows-server-2012-r2"></a>在 Windows Server® 2012 R2 中

- 在“开始”屏幕上，键入 **Windows PowerShell (x86)**。 单击“Windows PowerShell x86”磁贴。
- 在“服务器管理器”中，从“工具”菜单中选择“Windows PowerShell (x86)”。
- 在桌面上，将光标移动到右上角，单击“搜索”，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>在 Windows Server® 2012 中

- 在“开始”屏幕上，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”。
- 在“服务器管理器”中，从“工具”菜单中选择“Windows PowerShell (x86)”。
- 在桌面上，将光标移动到右上角，单击“搜索”，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>在 Windows® 8.1 中

- 在“开始”屏幕上，键入 **Windows PowerShell (x86)**。 单击“Windows PowerShell x86”磁贴。
- 如果你正在运行 Windows 8.1 的[远程服务器管理工具](http://go.microsoft.com/fwlink/?LinkID=304145)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86。
  选择“Windows PowerShell (x86)”。
- 在桌面上，将光标移动到右上角，单击“搜索”，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>在 Windows® 8 中

- 在“开始”屏幕上，将光标移动到右上角，依次单击“设置”、“磁贴”，然后将“显示管理工具”滑块移动到“是”。 然后，键入 **PowerShell**，单击“Windows PowerShell (x86)”。
- 如果你正在运行 Windows 8 的[远程服务器管理工具](http://www.microsoft.com/download/details.aspx?id=28972)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86。 选择“Windows PowerShell (x86)”。
- 在“开始”屏幕或桌面上，键入 **PowerShell (x86)**，然后单击“Windows PowerShell (x86)”。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
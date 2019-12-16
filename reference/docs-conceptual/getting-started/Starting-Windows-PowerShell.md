---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: 启动 Windows PowerShell
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953817"
---
# <a name="starting-windows-powershell"></a>启动 Windows PowerShell

Windows PowerShell 是一个嵌入到多个主机中的脚本引擎 `.DLL`。 启动的最常见主机是交互式命令行 powershell.exe 和交互式脚本环境 powershell_ise.exe   。

若要在 Windows Server® 2012 R2、Windows® 8.1、Windows Server 2012 和 Windows 8 上启动 Windows PowerShell®，请参阅 [Windows 中的常见管理任务和导航](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11))。

## <a name="powershell-core-has-renamed-binary"></a>PowerShell Core 已重命名二进制文件

PowerShell Core（称为 PowerShell）为第 6 版及更高版本，采用开源代码并使用 .NET Core。 受支持的版本在 Windows、macOS 和 Linux 上可用。

自 PowerShell 6 起，PowerShell 二进制文件已分别重命名为 pwsh.exe（适用于 Windows）和 pwsh（适用于 macOS 和 Linux）   。 可以使用 pwsh-preview 启动 PowerShell 预览版  。 有关详细信息，请参阅 [PowerShell Core 6.0 中的新增功能](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe)和[关于 pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7)。

若要查找 PowerShell 7 的 cmdlet 参考文档和安装文档，请使用以下链接：

| 文档 | 链接 |
| ----- | ----- |
| Cmdlet 参考 | [PowerShell 模块浏览器](/powershell/module/?view=powershell-7) |
| Windows 安装 | [在 Windows 上安装 PowerShell Core](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| macOS 安装 | [在 macOS 上安装 PowerShell Core](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| Linux 安装 | [在 Linux 上安装 PowerShell Core](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

若要查看其他 PowerShell 版本的相关内容，请参阅[如何使用 PowerShell 文档](../how-to-use-docs.md)。

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>如何在早期版本的 Windows 上启动 Windows PowerShell

本部分介绍了如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 上启动 Windows PowerShell 和 Windows PowerShell 集成脚本环境 (ISE)。 还介绍了如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中启用 Windows PowerShell ISE 的可选功能。

使用以下任一方法来启动已安装的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本（如果适用）。

#### <a name="from-the-start-menu"></a>在“开始”菜单中

- 单击“开始”  ，键入 **PowerShell**，然后单击“Windows PowerShell”  。
- 在“开始”  菜单中，依次单击“开始”  、“所有程序”  、“附件”  、“Windows PowerShell”  文件夹，然后单击“Windows PowerShell”  。

#### <a name="at-the-command-prompt"></a>在命令提示符处

在 cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入  ：

```
PowerShell
```

你还可以使用 powershell.exe 程序的参数来自定义会话  。 有关详细信息，请参阅 [PowerShell.exe 命令行帮助](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用管理权限（以管理员身份运行）

单击“**开始**”，键入 **PowerShell**，右键单击“**Windows PowerShell**”，然后单击“**以管理员身份运行**”。

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在早期版本的 Windows 上启动 Windows PowerShell ISE

使用以下任一方法启动 Windows PowerShell ISE。

#### <a name="from-the-start-menu"></a>在“开始”菜单中

- 单击“开始”  ，键入 **ISE**，然后单击“Windows PowerShell ISE”  。
- 在“开始”  菜单中，依次单击“开始”  、“所有程序”  、“附件”  、“Windows PowerShell”  文件夹，然后单击“Windows PowerShell ISE”  。

#### <a name="at-the-command-prompt"></a>在命令提示符处

在 cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入  ：

```
PowerShell_ISE
```

或

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用管理权限（以管理员身份运行）

单击“**开始**”，键入 **ISE**，右键单击“**Windows PowerShell ISE**”，然后单击“**以管理员身份运行**”。

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在早期版本的 Windows 上启用 Windows PowerShell ISE

在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，默认情况下，所有版本的 Windows 上都启用 Windows PowerShell ISE。 如果尚未启用，则 Windows Management Framework 4.0 或 Windows Management Framework 3.0 会启用它。

在 Windows PowerShell 2.0 中，默认情况下，在 Windows 7 上启用 Windows PowerShell ISE。 但是，在 Windows Server 2008 R2 和 Windows Server 2008 上，它是一项可选功能。

若要启用 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中的 Windows PowerShell ISE，请使用以下过程。

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>启用 Windows PowerShell 集成脚本环境 (ISE)

1. 启动“服务器管理器”。
2. 单击“功能”  ，然后单击“添加功能”  。
3. 在“选择功能”中，单击“Windows PowerShell 集成脚本环境 (ISE)”

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>启动 32 位版本的 Windows PowerShell

在 64 位计算机 (**Windows PowerShell (x86)** ) 上安装 Windows PowerShell 时，除 64 位版之外，还将安装 32 位版本的 Windows PowerShell。 运行 Windows PowerShell 时，默认运行 64 位版。

但是，有时可能需要运行 Windows PowerShell (x86)，例如使用需要 32 位版本的模块时，或者远程连接到 32 位计算机时  。

若要启动 32 位版本的 Windows PowerShell，请使用以下任何过程。

#### <a name="in-windows-server-2012-r2"></a>在 Windows Server® 2012 R2 中

- 在“开始”  屏幕上，键入 **Windows PowerShell (x86)** 。 单击“Windows PowerShell x86”  磁贴。
- 在“服务器管理器”  中，从“工具”  菜单中选择“Windows PowerShell (x86)”  。
- 在桌面上，将光标移动到右上角，单击“搜索”  ，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”  。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>在 Windows Server® 2012 中

- 在“开始”  屏幕上，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”  。
- 在“服务器管理器”  中，从“工具”  菜单中选择“Windows PowerShell (x86)”  。
- 在桌面上，将光标移动到右上角，单击“搜索”  ，键入 **PowerShell**，然后单击“Windows PowerShell (x86)”  。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>在 Windows® 8.1 中

- 在“开始”  屏幕上，键入 **Windows PowerShell (x86)** 。 单击“Windows PowerShell x86”  磁贴。
- 如果你正在运行 Windows 8.1 的[远程服务器管理工具](https://go.microsoft.com/fwlink/?LinkID=304145)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86  。 选择“Windows PowerShell (x86)”  。
- 在桌面上，将光标移动到右上角，单击“搜索”  ，键入**PowerShell x86**，然后单击“Windows PowerShell (x86)”  。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>在 Windows® 8 中

- 在“开始”屏幕上，将光标移动到右上角，依次单击“设置”、“磁贴”，然后将“显示管理工具”滑块移动到“是”      。 然后，键入 **PowerShell**，单击“Windows PowerShell (x86)”  。
- 如果你正在运行 Windows 8 的[远程服务器管理工具](https://www.microsoft.com/download/details.aspx?id=28972)，则也可从“服务器管理器工具”菜单中打开 Windows PowerShell x86  。 选择“Windows PowerShell (x86)”  。
- 在“开始”  屏幕或桌面上，键入 **PowerShell (x86)** ，然后单击“Windows PowerShell (x86)”  。
- 通过命令行，输入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

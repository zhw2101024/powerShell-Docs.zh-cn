---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: PowerShell 脚本调试中的改进
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147807"
---
# <a name="improvements-in-powershell-script-debugging"></a>PowerShell 脚本调试中的改进

PowerShell 5.0 包括用于增强调试体验的多项改进。

## <a name="break-all"></a>全部中断

PowerShell 控制台和 PowerShell ISE 现在可以中断调试器，而运行脚本。 这在本地和远程会话中很有效。

在控制台中，按 <kbd>Ctrl</kbd>+<kbd>Break</kbd>。

在 ISE 中，按 <kbd>Ctrl</kbd>+<kbd>B</kbd>，或使用“调试”->“全部中断”  菜单命令。

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>PowerShell ISE 中的远程调试和远程文件编辑

PowerShell ISE 现在可以通过运行 PSEdit 命令，在远程会话中打开并编辑文件。
例如，你可以在远程会话中打开文件并从命令行进行编辑，如下所示：

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

此外，你现在还可以在远程文件中编辑并保存更改，远程文件是你命中断点时在 PowerShell ISE 中自动打开的文件。 现在，你可以调试在远程计算机上运行的脚本文件，编辑该文件以修复错误，然后重新运行修改后的脚本。

## <a name="advanced-script-debugging"></a>高级脚本调试

新的高级调试功能使你能够附加到已加载 PowerShell 的任何本地计算机进程，并在该进程中调试任意运行空间。

### <a name="runspace-debugging"></a>运行空间调试

已添加的新 cmdlet 使你能够列出某个进程中的当前运行空间，并将 PowerShell 控制台或 PowerShell ISE 调试器附加到该运行空间进行脚本调试：

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>附加到承载 PowerShell 的进程

你现在可以附加到已加载 PowerShell 的任何计算机进程。 可通过输入与主机进程交互的会话执行此操作。 有关更多信息，请参阅：

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)

# PowerShell 脚本调试中的改进

在 PowerShell 5.0 中已进行了大量改进来增强调试体验：

## 全部中断

PowerShell 控制台和 Windows PowerShell ISE 现在可以中断调试器，而运行脚本。 这在本地和远程会话中很有效。

在控制台中，按 **Ctrl+Break**。

在 ISE 中，按 **Ctrl+B**，或使用“调试”->“全部中断”****菜单命令。

## Windows PowerShell ISE 中的远程调试和远程文件编辑

Windows PowerShell ISE 现在可以通过运行 PSEdit 命令，在远程会话中打开并编辑文件。
例如，你可以在远程会话中打开文件并从命令行进行编辑，如下所示：

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

此外，你现在还可以在远程文件中编辑并保存更改，远程文件是你命中断点时在 Windows PowerShell ISE 中自动打开的文件。
现在，你可以调试在远程计算机上运行的脚本文件，编辑该文件以修复错误，然后重新运行修改后的脚本。

## 高级脚本调试

新的高级调试功能使你能够附加到已加载 Windows PowerShell 的任何本地计算机进程，并在该进程中调试任意运行空间。

### 运行空间调试

已添加的新 cmdlet 使你能够列出某个进程中的当前运行空间，并将 Windows PowerShell 控制台或 ISE 调试器附加到该运行空间进行脚本调试：

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### 附加到承载 PowerShell 的进程

你现在可以附加到已加载 Windows PowerShell 的任何计算机进程。 可通过输入与该进程交互的会话执行此操作，类似于你通过运行 Enter-PSSession cmdlet 输入交互式远程会话的操作方式。

-   Enter-PSHostProcess
-   Exit-PSHostProcess<!--HONumber=Mar16_HO2-->

# <a name="using-visual-studio-code-for-powershell-development"></a>使用 Visual Studio Code 进行 PowerShell 开发

除 [PowerShell ISE][ise] 外，PowerShell 还高度支持 Visual Studio Code。
此外，PowerShell Core 不支持 ISE，但是 Visual Studio Code 在所有平台上（Windows、macOS 和 Linux）均支持 PowerShell Core

通过使用 Windows 10 或安装适用于低版本 Windows OS（例如 Windows 8.1 等）的 [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395)，可在 Windows 上结合使用 Visual Studio Code 和 PowerShell 版本 5.

开始前，请确保系统上安装有 PowerShell。
有关 Windows、macOS 和 Linux 上的新式工作负荷，请参阅：

- [在 Linux 上安装 PowerShell Core][install-pscore-linux]
- [在 macOS 上安装 PowerShell Core][install-pscore-macos]
- [在 Windows 上安装 PowerShell Core][install-pscore-windows]

有关传统 Windows PowerShell 工作负荷，请参阅[安装 Windows PowerShell][install-winps]。

## <a name="editing-with-visual-studio-code"></a>使用 Visual Studio Code 进行编辑

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1.安装 Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**：请按照[在 Linux 上运行 VS Code](https://code.visualstudio.com/docs/setup/linux) 页面上的安装说明进行操作

- **macOS**：请按照[在 macOS 上运行 VS Code](https://code.visualstudio.com/docs/setup/mac) 页面上的安装说明进行操作

  > [!IMPORTANT]
  > 在 macOS 上，必须安装 OpenSSL 后 PowerShell 扩展方可正常运行。
  > 实现此要求的最简单方法是安装 [Homebrew](http://brew.sh/)，然后运行 `brew install openssl`。
  > VS Code 现可成功加载 PowerShell 扩展。

- **Windows**：按照[在 Windows 上运行 VS Code](https://code.visualstudio.com/docs/setup/windows) 页面上的安装说明进行操作

### <a name="2-installing-powershell-extension"></a>2.安装 PowerShell 扩展

- 按照如下方式启动 Visual Studio Code 应用：
  - **Windows**：在 PowerShell 会话中键入 `code`
  - **Linux**：在终端中键入 `code`
  - **macOS**：在终端中键入 `code`

- 通过按 Ctrl+P（Mac 上为 Cmd+P）启动“Quick Open”。
- 在“Quick Open”中，键入 `ext install powershell` 并按 Enter。
- “扩展”视图随即在侧边栏上打开。 从 Microsoft 中选择 PowerShell 扩展。
  应看到如下内容：

  ![VSCode](../../images/vscode.png)

- 在 Microsoft 下单击 PowerShell 扩展上的“安装”按钮。
- 安装后，“安装”按钮将变为“重载”。
  单击“重载”。
- 重载 Visual Studio Code 后即可开始编辑。

例如，若要创建新文件，请单击“文件”->“新建”。
若要保存，请单击“文件”->“保存”，然后提供一个文件名，例如 `HelloWorld.ps1`。
若要关闭文件，则单击文件名旁的“x”。
若要退出 Visual Studio Code，请单击“文件”->“退出”。

#### <a name="using-a-specific-installed-version-of-powershell"></a>使用 PowerShell 特定安装版

如果要通过 Visual Studio Code 使用 PowerShell 的特定安装版，则需要将新的变量添加到用户设置文件。

1. 单击“文件”->“首选项”->“设置”
2. 此时会出现两个编辑器窗格。
   在最右侧窗格 (`settings.json`) 中，将对应于以下 OS 的设置插入到花括号（`{` 和 `}`）之间的某处，并将 <version> 替换为安装的 PowerShell 版本：

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

3. 将设置替换为所需 PowerShell 可执行文件的路径
4. 保存设置文件并重启 Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code 的配置设置

按照上一段落中的步骤可在 `settings.json` 中添加配置设置。

我们建议对 Visual Studio Code 添加以下配置设置：

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>使用 Visual Studio Code 进行调试

### <a name="no-workspace-debugging"></a>无工作区调试

从 Visual Studio Code 版本 1.9 开始，无需打开包含 PowerShell 脚本的文件夹即可调试 PowerShell 脚本。
只需单击“文件”->“打开文件...”打开 PowerShell 脚本文件，在行上设一个断点（按 F9），然后按 F5 即可开始调试。
此时应出现“调试”操作窗格，通过该窗格可以中断调试器、执行、继续和停止调试。

### <a name="workspace-debugging"></a>工作区调试

工作区调试是指文件夹上下文中的调试，该文件夹是使用“文件”菜单的“打开文件夹...”在 Visual Studio Code 中打开的。
打开的文件夹通常是 PowerShell 项目文件夹和/或 Git 存储库的根文件夹。

即使在此模式下，按 F5 也可开始调试当前所选的 PowerShell 脚本。
但是，通过工作区调试可以定义多个调试配置，而不是只调试当前打开的文件。
例如，可通过添加配置执行以下操作：

- 在调试器中启动 Pester 测试
- 使用调试器中的参数启动特定文件
- 在调试器中启动交互会话
- 将调试器附加到 PowerShell 主机进程

  按照以下步骤创建调试配置文件：

  1. 按 Ctrl+Shift+D（Mac 上为 Cmd+Shift+D）打开“调试”视图。
  2. 按工具栏中的“配置”齿轮图标。
  3. Visual Studio Code 将提示“选择环境”。
  选择“PowerShell”。

  执行此操作时，Visual Studio Code 会在工作区文件夹的根中创建一个目录和一个“.vscode\launch.json”文件。
  这是调试配置的存储位置。 如果文件位于 Git 存储库中，则通常需要提交 launch.json 文件。
  launch.json 文件的内容为：

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  这表示常见调试方案。
  但是，在编辑器中打开此文件时，会显示“添加配置...”按钮。
  按此按钮可添加更多 PowerShell 调试配置。 其中可添加的一个便捷配置是“PowerShell: Launch Script”。
  通过此配置，可以使用可选参数指定特定文件，无论编辑器中哪个文件处于活动状态，无论何时按 F5 时，此文件都会启动。

  调试配置建立后，可以在“调试”视图工具栏中的调试配置下拉列表中选择要在调试会话中使用的配置。

  以下博客可能提供有关将 PowerShell 扩展用于 Visual Studio Code 的有用帮助

Visual Studio Code：

- [PowerShell 扩展插件][ps-extension]
- [在 Visual Studio Code 中编写和调试 PowerShell 脚本][debug]
- [Visual Studio Code 调试指南][vscode-guide]
- [在 Visual Studio Code 中调试 PowerShell][ps-vscode]
- [在 Visual Studio Code 中进行 PowerShell 开发][getting-started]
- [适用于 PowerShell 开发的 Visual Studio Code 编辑功能 – 第 1 部分][editing-part1]
- [适用于 PowerShell 开发的 Visual Studio Code 编辑功能 – 第 2 部分][editing-part2]
- [在 Visual Studio Code 中调试 PowerShell 脚本 – 第 1 部分][debugging-part1]
- [在 Visual Studio Code 中调试 PowerShell 脚本 – 第 2 部分][debugging-part2]

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>适用于 Visual Studio Code 的 PowerShell 扩展

可以在 [GitHub](https://github.com/PowerShell/vscode-powershell) 上找到 PowerShell 扩展的源代码。
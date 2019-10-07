---
title: 使用 Visual Studio Code 进行 PowerShell 开发
description: 使用 Visual Studio Code 进行 PowerShell 开发
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325233"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>使用 Visual Studio Code 进行 PowerShell 开发

除 [PowerShell ISE][ise] 外，PowerShell 还在 Visual Studio Code (VSCode) 中受到高度支持。 此外，PowerShell Core 不支持 ISE，但 VSCode 在所有平台（Windows、macOS 和 Linux）上均受到 PowerShell Core 支持

通过使用 Windows 10 或安装适用于低版本 Windows OS（例如 Windows 8.1 等）的 [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/)，可在 Windows 上结合使用 VSCode 和 PowerShell 版本 5。

开始前，请确保系统上安装有 PowerShell。 有关 Windows、macOS 和 Linux 上的新式工作负荷，请参阅：

- [在 Linux 上安装 PowerShell Core][install-pscore-linux]
- [在 macOS 上安装 PowerShell Core][install-pscore-macos]
- [在 Windows 上安装 PowerShell Core][install-pscore-windows]

有关传统 Windows PowerShell 工作负载，请参阅[安装 Windows PowerShell][install-winps]。

## <a name="editing-with-vscode"></a>使用 VSCode 进行编辑

1. [安装 VSCode](https://code.visualstudio.com/Docs/setup/setup-overview)

   - **Linux**：请按照[在 Linux 上运行 VSCode](https://code.visualstudio.com/docs/setup/linux) 页上的安装说明进行操作
   - **macOS**：请按照[在 macOS 上运行 VSCode](https://code.visualstudio.com/docs/setup/mac) 页上的安装说明进行操作

     > [!IMPORTANT]
     > 在 macOS 上，必须安装 OpenSSL 后 PowerShell 扩展方可正常运行。 实现此要求的最简单方法是安装 [Homebrew](https://brew.sh/)，然后运行 `brew install openssl`。 VSCode 现可成功加载 PowerShell 扩展。

   - **Windows**：请按照[在 Windows 上运行 VSCode](https://code.visualstudio.com/docs/setup/windows) 页上的安装说明进行操作

2. 安装 PowerShell 扩展

   - 通过以下方式启动 VSCode 应用：
     - **Windows**：在 PowerShell 会话中键入 `code`
     - **Linux**：在终端中键入 `code`
     - **macOS**：在终端中键入 `code`
   - 通过按 <kbd>Ctrl</kbd>+<kbd>P</kbd>（Mac 上为 <kbd>Cmd</kbd>+<kbd>P</kbd>）启动“Quick Open”  。
   - 在“Quick Open”中，键入 `ext install powershell` 并按 Enter  。
   - “扩展”视图随即在侧边栏上打开  。 从 Microsoft 中选择 PowerShell 扩展。
     应看到如下内容：

     ![VSCode](../../images/using-vscode/vscode.png)

   - 在 Microsoft 下单击 PowerShell 扩展上的“安装”按钮  。
   - 安装后，“安装”按钮将变为“重载”   。 单击“重载”  。
   - 重载 VSCode 后即可开始编辑。

例如，若要创建新文件，请单击“文件”->“新建”  。 若要保存，请单击“文件”->“保存”，然后提供一个文件名，例如 `HelloWorld.ps1`  。 若要关闭文件，则单击文件名旁的“x”。 若要退出 VSCode，请单击“文件”->“退出”  。

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>在受限制的系统上安装 PowerShell 扩展

有些系统的设置要求检查所有代码签名，因此需要手动批准 PowerShell 编辑器服务才能在系统上运行。 如果已经安装 PowerShell 扩展，但出现以下错误，那么更改执行策略的组策略更新可能是原因之一：

```
Language server startup failed.
```

若要手动批准 PowerShell 编辑器服务，则适用于 VSCode 的 PowerShell 扩展打开 PowerShell 提示符并运行：

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

系统会提示你“是否要运行来自此不可信发布者的软件？” 键入 `R` 以运行该文件。 然后打开 VSCode，并检查 PowerShell 扩展是否正常工作。 如果在开始使用时仍有问题，请在 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) 上告诉我们。

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>选择要与扩展一起使用的 PowerShell 版本

将 PowerShell Core 与 Windows PowerShell 并行安装后，现在可以将特定版本的 PowerShell 与 PowerShell 扩展一起使用。 使用以下步骤选择版本：

1. 打开命令托盘（在 Windows 和 Linux 上为 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，在 macOS 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>）。
1. 搜索“会话”。
1. 单击“PowerShell:显示会话菜单”。
1. 选择要从列表中使用的 PowerShell 版本 - 例如，“PowerShell Core”。

> [!IMPORTANT]
> 此功能通过不同操作系统上的几个已知路径来发现 PowerShell 的安装位置。 如果已将 PowerShell 安装到非典型位置，则最初可能不会显示在会话菜单中。 可以按如下所述[添加你自己的自定义路径](#adding-your-own-powershell-paths-to-the-session-menu)来扩展会话菜单。

>[!NOTE]
> 还有一种方法可以获取会话菜单。 当 PowerShell 文件在编辑器中打开时，你会看到右下角的绿色版本号。 单击此版本号将为你提供会话菜单。

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>将你自己的 PowerShell 路径添加到会话菜单

可以通过 VSCode 设置将其他 PowerShell 可执行文件路径添加到会话菜单。

向列表 `powershell.powerShellAdditionalExePaths` 添加项或创建该列表（如果它不存在于 `settings.json` 中）：

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

每个项必须具有：

* `exePath`：`pwsh` 或 `powershell` 可执行文件的路径。
* `versionName`：将显示在会话菜单中的文本。

可以将默认 PowerShell 版本设置为使用 `powershell.powerShellDefaultVersion` 设置，方法是将其设置为显示在会话菜单中的文本（也称为最后一个设置中的 `versionName`）：

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

进行此设置后，重启 VSCode 或使用“开发人员:重载窗口”命令托盘操作来重载当前的 VSCode 窗口。

如果打开会话菜单，你现在会看到其他 PowerShell 版本！

> [!NOTE]
> 如果从源生成 PowerShell，则这是测试 PowerShell 的本地生成的好办法。

#### <a name="configuration-settings-for-vscode"></a>VSCode 的配置设置

按照上一段落中的步骤可在 `settings.json` 中添加配置设置。

我们建议对 VSCode 进行以下配置设置：

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

如果不希望这些设置影响所有文件类型，则 VSCode 还允许按语言进行配置。 通过将设置置于 `[<language-name>]` 字段，创建语言特定的设置。 例如：

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

有关 VSCode 中文件编码的详细信息，请参阅[了解文件编码](understanding-file-encoding.md)。

## <a name="debugging-with-vscode"></a>使用 VSCode 进行调试

### <a name="no-workspace-debugging"></a>无工作区调试

从 VSCode 版本 1.9 开始，无需打开包含 PowerShell 脚本的文件夹即可调试 PowerShell 脚本。 单击“文件”->“打开文件...”来打开 PowerShell 脚本文件，在行上设一个断点（按 <kbd>F9</kbd>），然后按 <kbd>F5</kbd> 即可开始调试  。 此时应出现“调试”操作窗格，通过该窗格可以中断调试器、执行、继续和停止调试。

### <a name="workspace-debugging"></a>工作区调试

工作区调试是指文件夹上下文中的调试，该文件夹是使用“文件”菜单的“打开文件夹...”在 Visual Studio Code 中打开的   。 打开的文件夹通常是 PowerShell 项目文件夹和/或 Git 存储库的根文件夹。

即使在此模式下，按 <kbd>F5</kbd> 也可开始调试当前所选的 PowerShell 脚本。 但是，通过工作区调试可以定义多个调试配置，而不是只调试当前打开的文件。 例如，可通过添加配置执行以下操作：

- 在调试器中启动 Pester 测试
- 使用调试器中的参数启动特定文件
- 在调试器中启动交互会话
- 将调试器附加到 PowerShell 主机进程

按照以下步骤创建调试配置文件：

  1. 按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>（Mac 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>）打开“调试”视图  。
  2. 单击工具栏中的“配置”齿轮图标  。
  3. VSCode 将提示“选择环境”  。 选择“PowerShell”  。

  执行此操作时，VSCode 会在工作区文件夹的根目录中创建一个目录和一个“.vscode\launch.json”文件。 这是调试配置的存储位置。 如果文件位于 Git 存储库中，则通常需要提交 launch.json 文件。 launch.json 文件的内容为：

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

  这表示常见调试方案。 但是，在编辑器中打开此文件时，会显示“添加配置...”按钮  。 单击此按钮可添加更多 PowerShell 调试配置。 其中可添加的一个便捷配置是“PowerShell:**Launch Script**。 通过此配置，可以使用可选参数指定特定文件，无论编辑器中哪个文件处于活动状态，无论何时按 <kbd>F5</kbd>，此文件都会启动。

  调试配置建立后，可以在“调试”视图工具栏中的调试配置下拉列表中选择要在调试会话中使用的配置  。

以下博客提供有关将 PowerShell 扩展用于 Visual Studio Code 的有用入门帮助：

- [PowerShell 扩展][ps-extension]
- [在 Visual Studio Code 中编写和调试 PowerShell 脚本][debug]
- [Visual Studio Code 调试指南][vscode-guide]
- [在 Visual Studio Code 中调试 PowerShell][ps-vscode]
- [Visual Studio Code 中的 PowerShell 开发入门][getting-started]
- [面向 PowerShell 开发的 Visual Studio Code 编辑功能 - 第 1 部分][editing-part1]
- [面向 PowerShell 开发的 Visual Studio Code 编辑功能 - 第 2 部分][editing-part2]
- [在 Visual Studio Code 中调试 PowerShell 脚本 - 第 1 部分][debugging-part1]
- [在 Visual Studio Code 中调试 PowerShell 脚本 - 第 2 部分][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
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

## <a name="powershell-extension-for-vscode"></a>适用于 VSCode 的 PowerShell 扩展

可以在 [GitHub](https://github.com/PowerShell/vscode-powershell) 上找到 PowerShell 扩展的源代码。

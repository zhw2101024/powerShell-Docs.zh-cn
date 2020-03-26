---
title: 使用 Visual Studio Code 进行 PowerShell 开发
description: 使用 Visual Studio Code 进行 PowerShell 开发
ms.date: 11/07/2019
ms.openlocfilehash: 86739970b58460bef9686a75bf0604d0605d4888
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082440"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>使用 Visual Studio Code 进行 PowerShell 开发

[Visual Studio Code](https://code.visualstudio.com/) 是 Microsoft 开发的跨平台（Windows、macOS 和 Linux）脚本编辑器。 与 [PowerShell 扩展](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) 相结合，它提供了丰富的交互式脚本编辑体验，从而可以更轻松地编写可靠的 PowerShell 脚本。

建议使用带有 PowerShell 扩展的 Visual Studio Code 编辑器来编写 PowerShell 脚本。
它支持以下 PowerShell 版本：

- PowerShell 7 及更高版本
- PowerShell Core 6
- Windows PowerShell 5.1

开始前，请确保系统上安装有 PowerShell。 有关 Windows、macOS 和 Linux 上的新式工作负荷，请参阅以下链接：

- [在 Linux 上安装 PowerShell Core][install-pscore-linux]
- [在 macOS 上安装 PowerShell Core][install-pscore-macos]
- [在 Windows 上安装 PowerShell Core][install-pscore-windows]

有关传统 Windows PowerShell 工作负载，请参阅[安装 Windows PowerShell][install-winps]。

> [!NOTE]
> Visual Studio Code 与 [Visual Studio](https://visualstudio.microsoft.com/) 不同。

> [!IMPORTANT]
> [Windows PowerShell ISE][ise] 仍可用于 Windows，但是，它不再处于活动功能开发状态，并且不适用于 PowerShell 7 及更高版本或 PowerShell Core 6。
> 作为 Windows 的随附组件，它仍会获得安全性和高优先级服务修补程序的官方支持。 目前没有从 Windows 中删除 ISE 的计划。

## <a name="editing-with-visual-studio-code"></a>使用 Visual Studio Code 进行编辑

1. 安装 Visual Studio Code。 有关详细信息，请参阅[设置 Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview) 概述。

    每个平台都有安装说明：

    - **Windows**：按照[在 Windows 上运行 Visual Studio Code](https://code.visualstudio.com/docs/setup/windows) 页面上的安装说明进行操作。
    - **macOS**：请按照[在 macOS 上运行 Visual Studio Code](https://code.visualstudio.com/docs/setup/mac) 页面上的安装说明进行操作。
    - **Linux**：请按照[在 Linux 上运行 Visual Studio Code](https://code.visualstudio.com/docs/setup/linux) 页面上的安装说明进行操作。

1. 安装 PowerShell 扩展。

   1. 通过在控制台中键入 `code` 或键入`code-insiders`（在安装 Visual Studio Code 预览体验成员的情况下）来启动 Visual Studio Code 应用。
   1. 通过按 <kbd>Ctrl</kbd>+<kbd>P</kbd>，在 Windows 或 Linux 上启动“Quick Open”。 在 macOS 上，按 <kbd>Cmd</kbd>+<kbd>P</kbd>。
   1. 在“Quick Open”中，键入 `ext install powershell`，然后按 ENTER。
   1. “扩展”视图随即在侧边栏上打开。 从 Microsoft 中选择 PowerShell 扩展。
      应会看到类似于下图的 Visual Studio Code 屏幕：

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. 在 Microsoft 下单击 PowerShell 扩展上的“安装”按钮。
   1. 安装后，如果看到“安装”按钮变为“重载”，则单击“重载”。
   1. 重载 Visual Studio Code 后即可开始编辑。

例如，若要创建新文件，请单击“文件”>“新建”。 若要保存，请单击“文件”>“保存”，然后提供文件名，例如 `HelloWorld.ps1`。 若要关闭文件，请单击文件名旁的 `X`。 若要退出 Visual Studio Code，请单击“文件”>“退出”。

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>在受限制的系统上安装 PowerShell 扩展

有些系统的设置要求检查所有代码签名，且需要手动批准 PowerShell 编辑器服务才能在系统上运行。 如果已经安装 PowerShell 扩展，但出现以下错误，那么更改执行策略的组策略更新可能是原因之一：

```
Language server startup failed.
```

若要手动批准 PowerShell 编辑器服务和适用于 Visual Studio Code 的 PowerShell 扩展，则打开 PowerShell 提示符并运行以下命令：

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

系统会提示你“是否要运行来自此不可信发布者的软件？”
键入 `A` 以运行该文件。 然后打开 Visual Studio Code，并检查 PowerShell 扩展是否工作正常。 如果在开始使用时仍有问题，请在 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) 上告诉我们。

> [!NOTE]
> 适用于 Visual Studio Code 的 PowerShell 扩展不支持在约束语言模式下运行。 有关详细信息，请参阅[支持的 GitHub 问题跟踪](https://github.com/PowerShell/vscode-powershell/issues/606)。

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>对 Windows PowerShell v3 和 v4 使用旧版 PowerShell 扩展

尽管当前的 PowerShell 扩展[已停止支持 v3 和 v4](https://github.com/PowerShell/vscode-powershell/issues/1310)，但仍可以使用该扩展的最新版本。

> [!NOTE]
> 将不会为此扩展的较旧版本提供其他修补程序。 它“按原样”提供，但如果你仍在使用 Windows PowerShell v3 和 Windows PowerShell v4，则可以使用它。

首先，打开“扩展”窗格并搜索 `PowerShell`。 然后单击齿轮，选择“安装其他版本...”。

![安装其他版本...](media/using-vscode/install-another-version.png)

然后选择“`2020.1.0`”版本。 此版本的扩展是支持 v3 和 v4 的最新版本。

另外，添加以下设置，以便不会自动更新扩展版本：

```json
{
    "extensions.autoUpdate": false
}
```

尽管这在可预见的将来是可行的，但是 Visual Studio Code 可以实现一个中断此扩展版本的更改。
因此，由于缺乏支持，我们强烈建议执行以下操作之一：

- 下载 PowerShell 7 - 这是 Windows PowerShell 的并行安装，与 PowerShell 扩展配合使用效果最佳
- 升级到 Windows PowerShell 5.1

本文中的[使用 Visual Studio Code 编辑](#editing-with-visual-studio-code)部分会链接到安装它们的位置。

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>选择要与扩展一起使用的 PowerShell 版本

将 PowerShell Core 与 Windows PowerShell 并行安装后，现在可以将特定版本的 PowerShell 与 PowerShell 扩展一起使用。 使用以下步骤选择版本：

1. 在 Windows 或 Linux 上，使用 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 打开“命令面板”。 在 macOS 上，使用 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。
1. 搜索“会话”。
1. 单击“PowerShell:显示会话菜单”。
1. 选择要从列表中使用的 PowerShell 版本，例如：PowerShell Core。

> [!IMPORTANT]
> 此功能通过不同操作系统上的几个已知路径来发现 PowerShell 的安装位置。 如果已将 PowerShell 安装到非典型位置，则最初可能不会显示在会话菜单中。 可以按如下所述[添加你自己的自定义路径](#adding-your-own-powershell-paths-to-the-session-menu)来扩展会话菜单。

>[!NOTE]
> 还有一种方法可以获取会话菜单。 当 PowerShell 文件在编辑器中打开时，你会看到右下角的绿色版本号。 单击此版本号将为你提供会话菜单。

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>将你自己的 PowerShell 路径添加到会话菜单

可以通过 [Visual Studio Code 设置](https://code.visualstudio.com/docs/getstarted/settings)将其他 PowerShell 可执行文件路径添加到会话菜单：`powershell.powerShellAdditionalExePaths`。

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

- `exePath`设置用户帐户 ：`pwsh` 或 `powershell` 可执行文件的路径。
- `versionName`设置用户帐户 ：将显示在会话菜单中的文本。

可以将默认 PowerShell 版本设置为使用 `powershell.powerShellDefaultVersion` 设置，方法是将其设置为显示在会话菜单中的文本（也是最后一个设置中的 `versionName`）：

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

配置此设置后，请重启 Visual Studio Code 或从“命令面板”中重载当前 Visual Studio Code 窗口，键入“开发人员:重载窗口”。

如果打开会话菜单，你现在会看到其他 PowerShell 版本！

> [!NOTE]
> 如果从源生成 PowerShell，则这是测试 PowerShell 的本地生成的好办法。

### <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code 的配置设置

首先，如果不熟悉如何更改 Visual Studio Code 中的设置，建议查看 [Visual Studio Code 的设置文档](https://code.visualstudio.com/docs/getstarted/settings)。

按照上一段落中的步骤可在 `settings.json` 中添加配置设置。

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

如果不希望这些设置影响所有文件类型，则 Visual Studio Code 还允许按语言进行配置。 创建在 `[<language-name>]` 字段中放置设置，可以配置特定于语言的设置。 例如：

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> 有关 Visual Studio Code 中文件编码的详细信息，请参阅[了解文件编码](understanding-file-encoding.md)。
>
> 另外，请查看[如何在 Visual Studio Code 中复制 ISE 体验](How-To-Replicate-the-ISE-Experience-In-VSCode.md)，以获取有关如何配置 Visual Studio Code 以进行 PowerShell 编辑的其他提示。

## <a name="debugging-with-visual-studio-code"></a>使用 Visual Studio Code 进行调试

### <a name="no-workspace-debugging"></a>无工作区调试

从 Visual Studio Code 版本 1.9 开始，无需打开包含 PowerShell 脚本的文件夹即可调试 PowerShell 脚本。 单击“文件”>“打开文件...”来打开 PowerShell 脚本文件，在行上设一个断点，按 <kbd>F9</kbd>，然后按 <kbd>F5</kbd> 即可开始调试。 此时应出现“调试”操作窗格，通过该窗格可以中断调试器、执行、继续和停止调试。

### <a name="workspace-debugging"></a>工作区调试

工作区调试是指文件夹上下文中的调试，该文件夹是在 Visual Studio Code 中从“文件”菜单使用“打开文件夹...”打开的。打开的文件夹通常是 PowerShell 项目文件夹和/或 Git 存储库的根文件夹。

即使在此模式下，按 <kbd>F5</kbd> 也可开始调试当前所选的 PowerShell 脚本。 但是，通过工作区调试可以定义多个调试配置，而不是只调试当前打开的文件。 稍后我们将对这些进行介绍。

按照以下步骤创建调试配置文件：

  1. 通过按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>，在 Windows 或 Linux 上打开“调试”视图。 在 macOS 上，按 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。
  1. 单击“创建 launch.json 文件”链接。
  1. Visual Studio Code 将提示“选择环境”。 选择“PowerShell”。
  1. 最后，选择要使用的调试类型：

- **启动当前文件** - 在当前活动的编辑器窗口中启动和调试文件
- **启动脚本** - 启动和调试指定的文件或命令
- **交互式会话** - 从集成控制台执行的调试命令
- **附加** - 将调试器附加到正在运行的 PowerShell 主机进程

结果是，Visual Studio Code 会在工作区文件夹的根目录中创建一个目录和一个 `.vscode\launch.json` 文件。 这是调试配置的存储位置。 如果文件位于 Git 存储库中，则通常需要提交 `launch.json` 文件。 `launch.json` 文件的内容为：

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

此文件表示常见调试方案。 在编辑器中打开此文件时，会显示“添加配置...”按钮。 单击此按钮可添加更多 PowerShell 调试配置。 其中可添加的一个有用配置是“PowerShell:**Launch Script**。 通过此配置，可以使用可选参数指定文件，无论编辑器中哪个文件当前处于活动状态，无论何时按 <kbd>F5</kbd>，此文件都会启动。

建立调试配置后，可以选择要在调试会话期间使用的配置。 从“调试”视图工具栏的调试配置下拉菜单中选择配置。

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
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>适用于 Visual Studio Code 的 PowerShell 扩展

可以在 [GitHub](https://github.com/PowerShell/vscode-powershell) 上找到 PowerShell 扩展的源代码。

如果你有兴趣参与，将极大改进拉取请求。 请遵循 [GitHub 上的开发人员文档](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md)来开始使用。

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>适用于 Visual Studio Code 的 PowerShell 扩展故障排除

如果在使用 Visual Studio Code 进行 PowerShell 脚本开发时遇到任何问题，请查看 [GitHub 上的故障排除指南](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)

---
title: 使用 Visual Studio Code 进行远程编辑和调试
description: 使用 Visual Studio Code 进行远程编辑和调试
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67264002"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>使用 Visual Studio Code 进行远程编辑和调试

对于熟悉 ISE 的你来说，你可能还记得可以从集成控制台运行 `psedit file.ps1` 以在 ISE 中打开本地或远程文件。

该功能在适用于 VSCode 的 PowerShell 扩展中也可用。 本指南将演示如何操作。

## <a name="prerequisites"></a>必备条件

本指南假定你拥有：

- 可访问的远程资源（例如：虚拟机、容器）
- 在其中运行的 PowerShell 和主机计算机
- VSCode 和适用于 VSCode 的 PowerShell 扩展

此功能适用于 Windows PowerShell 和 PowerShell Core。

当通过 WinRM、PowerShell Direct 或 SSH 连接到远程计算机时，此功能也适用。 如果要使用 SSH，但使用的是 Windows，请查看 [Win32 版本的 SSH](https://github.com/PowerShell/Win32-OpenSSH)！

> [!IMPORTANT]
> `Open-EditorFile` 和 `psedit` 命令仅适用于 PowerShell 集成控制台  （由适用于 VSCode 的 PowerShell 扩展创建）。

## <a name="usage-examples"></a>用法示例

这些示例介绍从 MacBook Pro 到在 Azure 中运行的 Ubuntu VM 的远程编辑和调试。 Windows 上的过程相同。

### <a name="local-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 编辑的本地文件

启动适用于 VSCode 的 PowerShell 扩展并打开 PowerShell 集成控制台之后，可以在编辑器中键入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1` 来打开本地 foo.ps1 文件。

![Open-EditorFile foo.ps1 可在本地工作](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> 文件 `foo.ps1` 必须已经存在。

由此，我们可以：

- 将断点添加到装订线

  ![将断点添加到装订线](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- 按 F5 调试 PowerShell 脚本。

  ![调试 PowerShell 本地脚本](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

调试期间，可以与调试控制台进行交互，查看左边范围中的变量，以及所有其他标准调试工具。

### <a name="remote-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 编辑的远程文件

现在让我们进入远程文件编辑和调试。 步骤几乎相同，只需要先完成一个操作 - 将 PowerShell 会话输入到远程服务器。

有一个 cmdlet 可以做到这一点。 它被称为 `Enter-PSSession`。

该 cmdlet 的简化说明是：

- `Enter-PSSession -ComputerName foo` 通过 WinRM 启动会话
- `Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 通过 PowerShell Direct 启动会话
- `Enter-PSSession -HostName foo` 通过 SSH 启动会话

有关详细信息，请参阅 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) 的文档。

由于我们要从 macOS 转到 Azure 中的 Ubuntu VM，因此我们将使用 SSH 进行远程处理。

首先，在集成控制台中，运行 `Enter-PSSession`。 当提示符的左侧显示 `[<hostname>]` 时，即表示已连接到远程会话。

![对 Enter-PSSession 的调用](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

现在，我们可以执行与编辑本地脚本相同的步骤。

1. 运行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 以打开远程 `test.ps1` 文件

  ![Open-EditorFile test.ps1 文件](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. 编辑文件/设置断点

   ![编辑并设置断点](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. 开始调试 (F5) 远程文件

   ![调试远程文件](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

如有任何疑问，可在 [GitHub 存储库](https://github.com/powershell/vscode-powershell)中提问。

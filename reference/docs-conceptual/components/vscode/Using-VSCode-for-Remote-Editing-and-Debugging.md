---
title: 使用 Visual Studio Code 进行远程编辑和调试
description: 使用 Visual Studio Code 进行远程编辑和调试
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086658"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>使用 Visual Studio Code 进行远程编辑和调试

对于熟悉 ISE 的人来说，你可能还记得可以从集成控制台运行 `psedit file.ps1` 以在 ISE 中打开本地或远程文件。

事实证明，该功能在适用于 VSCode 的 PowerShell 扩展中也可用。 本指南将演示如何操作。

## <a name="prerequisites"></a>必备条件

本指南假定你拥有：

- 可访问的远程资源（例如：虚拟机、容器）
- 在其中运行的 PowerShell 和主机计算机
- VSCode 和适用于 VSCode 的 PowerShell 扩展

此功能适用于 Windows PowerShell 和 PowerShell Core。

当通过 WinRM、PowerShell Direct 或 SSH 连接到远程计算机时，此功能也适用。 如果要使用 SSH，但使用的是 Windows，请查看 [Win32 版本的 SSH](https://github.com/PowerShell/Win32-OpenSSH)！

## <a name="lets-go"></a>开始

在本节中，我将介绍从 MacBook Pro 到在 Azure 中运行的 Ubuntu VM 的远程编辑和调试。 我可能不使用 Windows，但过程是相同的。

### <a name="local-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 编辑的本地文件

启动适用于 VSCode 的 PowerShell 扩展并打开 PowerShell 集成控制台之后，可以在编辑器中键入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1` 来打开本地 foo.ps1 文件。

![Open-EditorFile foo.ps1 可在本地工作](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 必须已经存在。

由此，我们可以：

向装订线添加断点![向装订线添加断点](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

并按 F5 调试 PowerShell 脚本。
![调试 PowerShell 本地脚本](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

调试期间，可以与调试控制台进行交互，查看左边范围中的变量，以及所有其他标准调试工具。

### <a name="remote-file-editing-with-open-editorfile"></a>使用 Open-EditorFile 编辑的远程文件

现在让我们进入远程文件编辑和调试。 步骤几乎相同，只需要先完成一个操作 - 将 PowerShell 会话输入到远程服务器。

有一个 cmdlet 可以做到这一点。 它被称为 `Enter-PSSession`。

该 cmdlet 的简化说明是：

- `Enter-PSSession -ComputerName foo` 通过 WinRM 启动会话
- `Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 通过 PowerShell Direct 启动会话
- `Enter-PSSession -HostName foo` 通过 SSH 启动会话

有关 `Enter-PSSession` 的详细信息，请查看[此处](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6)的文档。

我将使用 SSH 进行远程处理，因为我要从 macOS 转到 Azure 中的 Ubuntu VM。

首先，在集成控制台中运行 Enter - PSSsession。 你会知道自己正在参与会话，因为 `[something]` 会显示在提示符左侧。

![对 Enter-PSSession 的调用](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

在这里，我们可以执行与编辑本地脚本完全相同的步骤。

1. 运行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 打开远程 `test.ps1` 文件 ![Open-EditorFile test.ps1 文件](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. 编辑文件/设置断点 ![编辑并设置断点](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. 开始调试 (F5) 远程文件

![调试远程文件](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

一切就是这么简单！ 我们希望本指南有助于解答有关在 VSCode 中远程调试和编辑 PowerShell 的任何问题。

如有任何疑问，欢迎随时[在 GitHub 存储库上](http://github.com/powershell/vscode-powershell)提问。

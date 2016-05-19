---
title: 在早期版本的 Windows 上启动 Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# 在早期版本的 Windows 上启动 Windows PowerShell
本部分介绍如何在 WindowsÂ® 7、Windows ServerÂ® 2008 R2 和 Windows Server 2008 上启动 Windows PowerShell 和 Windows PowerShell 集成脚本环境 (ISE)。 还说明了如何为 Windows ServerÂ® 2008 R2 和 Windows Server 2008 上的 Windows PowerShell 2.0 中的 Windows PowerShell ISE 启用可选功能。

若要在支持的系统上安装 Windows PowerShell 4.0，请下载并安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)。 有关详细信息，请参阅[安装 Windows PowerShell](Installing-Windows-PowerShell.md).

若要在支持的系统上安装 Windows PowerShell 3.0，请下载并安装 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)。 有关详细信息，请参阅[安装 Windows PowerShell](Installing-Windows-PowerShell.md).

## 如何在早期版本的 Windows 上启动 Windows PowerShell
使用以下任一方法来启动已安装的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本（如果适用）。

#### 在“开始”菜单中

-   单击“开始”，键入 **PowerShell**，然后单击“Windows PowerShell”.

-   在“开始”菜单中，依次单击“开始”、“所有程序”、“附件”、“Windows PowerShell”文件夹，然后单击“Windows PowerShell”.

#### 在命令提示符处

-   在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：

    ```
    PowerShell
    ```

    你还可以使用 PowerShell.exe 程序的参数来自定义会话。 有关详细信息，请参阅 [PowerShell.exe 命令行帮助](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### 使用管理权限（“以管理员身份运行”）

1.  单击“开始”，键入 **PowerShell**，右键单击“Windows PowerShell”，然后单击“以管理员身份运行”.

## 如何在早期版本的 Windows 上启动 Windows PowerShell ISE
使用以下任一方法启动 Windows PowerShell ISE。

#### 在“开始”菜单中

-   单击“开始”，键入 **ISE**，然后单击“Windows PowerShell ISE”.

-   在“开始”菜单中，依次单击“开始”、“所有程序”、“附件”、“Windows PowerShell”文件夹，然后单击“Windows PowerShell ISE”.

#### 在命令提示符处

-   在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：

    ```
    PowerShell_ISE
    ```

    或

    ```
    ISE
    ```

#### 使用管理权限（“以管理员身份运行”）

1.  单击“开始”，键入 **ISE**，右键单击“Windows PowerShell ISE”，然后单击“以管理员身份运行”.

## 如何在早期版本的 Windows 上启用 Windows PowerShell ISE
在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，默认情况下，所有版本的 Windows 上都启用 Windows PowerShell ISE。 如果尚未启用，则 Windows Management Framework 4.0 或 Windows Management Framework 3.0 会启用它。

在 Windows PowerShell 2.0 中，默认情况下，在 Windows 7 上启用 Windows PowerShell ISE。 但是，在 Windows Server 2008 R2 和 Windows Server 2008 上，它是一项可选功能。

若要启用 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中的 Windows PowerShell ISE，请使用以下过程。

#### 启用 Windows PowerShell 集成脚本环境 (ISE)

1.  启动“服务器管理器”。

2.  单击“功能”，然后单击“添加功能”.

3.  在“选择功能”中，单击“Windows PowerShell 集成脚本环境 (ISE)”



<!--HONumber=May16_HO2-->



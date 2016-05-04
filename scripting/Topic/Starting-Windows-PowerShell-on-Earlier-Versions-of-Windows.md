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
本部分说明了如何在 [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)]、[!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)] 上启动 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 和 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]。 它还说明了如何在 [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)] 上的 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 中启用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] 的可选功能。

若要在支持的系统上安装 [!INCLUDE[psversion4](../Token/psversion4_md.md)]，请下载并安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)。 有关详细信息，请参阅[安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

若要在支持的系统上安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]，请下载并安装 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)。 有关详细信息，请参阅[安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

## 如何在早期版本的 Windows 上启动 [!INCLUDE[mshshort](../Token/mshshort_md.md)]
使用以下任一方法来启动已安装的 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 版本，或 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 版本（如果适用）。

#### 在“开始”菜单中

-   单击“开始”****，键入 **PowerShell**，然后单击“Windows PowerShell”****。

-   在“开始”****菜单中，依次单击“开始”****、“所有程序”****、“附件”****、“Windows PowerShell”****文件夹，然后单击“Windows PowerShell”****。

#### 在命令提示符处

-   在 Cmd.exe、[!INCLUDE[wps_2](../Token/wps_2_md.md)]，或 [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE 中，若要启动 [!INCLUDE[wps_2](../Token/wps_2_md.md)]，请键入：

    ```
    PowerShell
    ```

    你还可以使用 PowerShell.exe 程序的参数来自定义会话。 有关详细信息，请参阅 [PowerShell.exe 命令行帮助](../Topic/PowerShell.exe-Command-Line-Help.md)。

#### 使用管理权限（“以管理员身份运行”）

1.  单击“开始”****，键入 **PowerShell**，右键单击“Windows PowerShell”****，然后单击“以管理员身份运行”****。

## 如何在早期版本的 Windows 上启动 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]
使用以下任一方法启动 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]。

#### 在“开始”菜单中

-   单击“开始”****，键入 **ISE**，然后单击“Windows PowerShell ISE”****。

-   在“开始”****菜单中，依次单击“开始”****、“所有程序”****、“附件”****、“Windows PowerShell”****文件夹，然后单击“Windows PowerShell ISE”****。

#### 在命令提示符处

-   在 Cmd.exe、[!INCLUDE[wps_2](../Token/wps_2_md.md)]，或 [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE 中，若要启动 [!INCLUDE[wps_2](../Token/wps_2_md.md)]，请键入：

    ```
    PowerShell_ISE
    ```

    或

    ```
    ISE
    ```

#### 使用管理权限（“以管理员身份运行”）

1.  单击“开始”****，键入 **ISE**，右键单击“Windows PowerShell ISE”****，然后单击“以管理员身份运行”****。

## 如何在早期版本的 Windows 上启用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]
在 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 中，所有版本的 Windows 上都将默认启用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]。 如果尚未启用，则 Windows Management Framework 4.0 或 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 会启用它。

在 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 中，[!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] 上将默认启用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]。 但是，在 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)]上，它是一项可选功能。

若要在 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 或 [!INCLUDE[lserver](../Token/lserver_md.md)] 上的 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 中启用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]，请使用以下过程。

#### 启用 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

1.  启动“服务器管理器”。

2.  单击“功能”****，然后单击“添加功能”****。

3.  在“选择功能”中，单击 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]。



<!--HONumber=Apr16_HO1-->



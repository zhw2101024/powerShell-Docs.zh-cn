---
title: 准备好使用 Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
---
# 准备好使用 Windows PowerShell
安装并启动 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 后，请考虑以下设置选项。 随时可以执行这些任务。

-   **安装帮助文件。** [!INCLUDE[psversion3](../Token/psversion3_md.md)] 中包含的 cmdlet 不附带帮助文件。 但是，可以使用 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet 在计算机上下载并安装最新帮助文件。 安装文件后，可以使用 [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet 在命令行右侧显示它们。 有关详细信息，请参阅 [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe)。

    如果决定不安装帮助文件，你仍可以在线阅读帮助主题。 若要打开任何 cmdlet 帮助主题的在线版本，请键入：`Get-Help <CmdletName> -Online`。 若要浏览 TechNet 库中的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 帮助主题，请从 [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116) 开始。

-   **运行脚本。** 为了保证 [!INCLUDE[mshshort](../Token/mshshort_md.md)] 安全，[!INCLUDE[mshshort](../Token/mshshort_md.md)] 上的默认执行策略为 **Restricted**。 此策略允许你运行 cmdlet，但不允许运行脚本。 若要运行脚本，请使用 [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) cmdlet 将执行策略更改为 **AllSigned** 或 **RemoteSigned**。 只有计算机上管理员组的成员才能运行此 cmdlet。 有关详细信息，请参阅 [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6)。

-   **启用远程。** 系统已进行了配置，以便你在其他计算机上运行远程命令。 在 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 上，系统总是配置为接收远程命令，也就是说，允许其他计算机在本地计算机上运行远程命令。 若要允许运行其他版本 Windows 的计算机接收远程命令，请在你想远程管理的计算机上运行 [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/19437c28-33b8-4ac1-9113-8439cc8beffb) cmdlet。 只有计算机上管理员组的成员才能运行此 cmdlet。 有关详细信息，请参阅 [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)。

    注意：如果已在运行 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 的计算机上启用远程，则安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 后仍将启用远程。 但是，在 [!INCLUDE[lserver](../Token/lserver_md.md)]（不是 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)]）上，必须在安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 后重新启用远程。

## 另请参阅
[安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[启动 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->



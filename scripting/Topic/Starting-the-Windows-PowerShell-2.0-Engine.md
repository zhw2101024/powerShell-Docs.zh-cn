---
title: 启动 Windows PowerShell 2.0 引擎
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
---
# 启动 Windows PowerShell 2.0 引擎
本部分说明了如何在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 上以及在安装了 [!INCLUDE[psversion2](../Token/psversion2_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 的其他系统上启动 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎（包括 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎）。

[!INCLUDE[psversion4](../Token/psversion4_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 旨在与 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 向后兼容。 Cmdlet、提供程序、管理单元、模块，以及为 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 编写的脚本照常在 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 中运行。 但是，由于 Microsoft.NET framework 4 中运行时激活策略的更改，为 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 编写并使用公共语言运行时 (CLR) 2.0 编译的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 主机程序无法在不经修改的情况下在 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 或 [!INCLUDE[psversion4](../Token/psversion4_md.md)]（使用 CLR 4.0 进行编译）中运行。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎仅在当前脚本或主机程序无法运行时使用，因为它与 [!INCLUDE[psversion4](../Token/psversion4_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 或 Microsoft .NET Framework 4 不兼容。 这种情况很少见。

许多需要 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的程序将自动启动。 这些说明适用于极少数需要手动启动该引擎的情况。

## 安装和启用必需程序
启动 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎之前，请先启用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎和 Microsoft.NET Framework 3.5 Service Pack 1。 有关说明，请参阅[安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

安装了 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 或 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的系统上具备所有必需组件。 无需进行任何其他配置。 有关安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 或 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的信息，请参阅[安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

## 如何启动 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎
启动 [!INCLUDE[mshshort](../Token/mshshort_md.md)] 时，默认启动最新版本。 若要使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎启动 [!INCLUDE[mshshort](../Token/mshshort_md.md)]，请使用 PowerShell.exe 的 Version 参数。 你可以在任何命令提示符（包括 Windows PowerShell 和 Cmd.exe）处运行该命令。

```
PowerShell.exe -Version 2
```

## 如何使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎启动远程会话
若要在远程会话中运行 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，请在加载 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的远程计算机上创建会话配置（也称为“终结点”）。 会话配置保存在远程计算机上，并且任何已获得授权的用户都可以将其用于创建使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的会话。

这是一项高级任务，通常由系统管理员执行。

以下过程使用 [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet 的 **PSVersion** 参数来创建使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的会话配置。 你还可以使用 [New-PSSessionConfigurationFile](assetId:///5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet 的 **PowerShellVersion** 参数为加载 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的会话创建会话配置文件，此外，你可以使用 [Set-PSSessionConfiguration](assetId:///b21fbad3-1759-4260-b206-dcb8431cd6ea) 参数的 **PSVersion** 参数将会话配置更改为使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。

有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](assetId:///c7217447-1ebf-477b-a8ef-4dbe9a1473b8)。有关会话配置（包括安装和安全性）的信息，请参阅 [about_Session_Configurations [v4]](assetId:///a2fbe12a-350c-4d04-be50-24102824e3ab)。

#### 启动远程 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 会话

1.  若要创建需要 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的会话配置，请使用 [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet 的 **PSVersion** 参数，参数值为“2.0”。 在计算机上的连接的“服务器端”或接收端运行此命令。

    下面的示例命令在 Server01 计算机上创建 PS2 会话配置。 若要运行此命令，请使用“以管理员身份运行”****选项启动 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 或 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。

    ```
    Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
    ```

2.  若要在使用 PS2 会话配置的 Server01 计算机上创建会话，请使用创建远程会话的 cmdlet（例如 [New-PSSession](assetId:///76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet）的 **ConfigurationName** 参数。

    使用会话配置的会话启动时，[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎会自动加载到该会话中。

    下面的命令在使用 PS2 会话配置的 Server01 计算机上启动一个会话。 该命令将该会话保存在 $s 变量中。

    ```
    $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
    ```

## 如何使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎启动后台作业
若要使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎启动后台作业，请使用 [Start-Job](assetId:///2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet 的 **PSVersion** 参数。

下面的命令使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎启动后台作业

```
Start-Job {Get-Process} -PSVersion 2.0
```

有关后台作业的详细信息，请参阅 [about_Jobs [v4]](assetId:///7362512a-8a4e-4575-b2ea-a740e5c4f002)。



<!--HONumber=Apr16_HO1-->



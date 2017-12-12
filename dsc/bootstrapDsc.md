---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "初始启动时使用 DSC 配置虚拟机"
ms.openlocfilehash: c793e36eb9caa194104f9dda2aa1d335b21b676c
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2017
---
>适用于：Windows PowerShell 5.0

>**注意：**本主题所述的 **DSCAutomationHostEnabled** 注册表项在 PowerShell 4.0 中不可用。
有关如何在初始启动时于 PowerShell 4.0 中配置新虚拟机的信息，请参阅[想要在初始启动时使用 DSC 自动配置计算机？](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>初始启动时使用 DSC 配置虚拟机

## <a name="requirements"></a>要求

若要运行这些示例，则需要：

- 要使用的可启动 VHD。 可以在 [TechNet 评估中心](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)下载具有 Windows Server 2016 评估副本的 ISO。 可以在[创建可启动虚拟硬盘](https://technet.microsoft.com/en-us/library/gg318049.aspx)处找到有关如何从 ISO 映像创建 VHD 的说明。
- 已启用 Hyper-V 的主计算机。 有关信息，请参阅 [Hyper-V 概述](https://technet.microsoft.com/library/hh831531.aspx)。

通过使用 DSC，可以在初始启动时对计算机实现软件安装和配置的自动化。
可以通过将配置 MOF 文档或元配置注入可启动媒体（例如 VHD）来执行此操作，以便它们能在初始启动过程中运行。
此行为由 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** 下的 [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) 注册表项指定。
默认情况下，此项的值为 2，这允许 DSC 在启动时运行。

如果不希望 DSC 在启动时运行，将 [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) 注册表项的值设置为 0。

- 将配置 MOF 文档注入 VHD
- 将 DSC 元配置注入 VHD
- 启动时，请禁用 DSC

>**注意：**可以将 `Pending.mof` 和 `MetaConfig.mof` 同时注入计算机。
如果这两个文件都存在，则在 `MetaConfig.mof` 中指定的设置优先。

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>将配置 MOF 文档注入 VHD

若要在初始启动时执行配置，可以将已编译的配置 MOF 文档注入 VHD 作为其 `Pending.mof` 文件。
如果将 **DSCAutomationHostEnabled** 注册表项设置为 2（默认值），则在首次启动计算机时，DSC 将应用由 `Pending.mof` 定义的配置。

对于此示例，我们将使用以下配置，它将在新计算机上安装 IIS：

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>将配置 MOF 文档注入 VHD

1. 通过调用 [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet，将 VHD 装入想要注入配置的位置。 例如：

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. 在运行 PowerShell 5.0 或更高版本的计算机上，将以上配置 (**SampleIISInstall**) 保存为 PowerShell 脚本 (.ps1) 文件。

3. 在 PowerShell 控制台中，导航到保存 .ps1 文件的文件夹。

4. 运行以下 PowerShell 命令来编译 MOF 文档（有关编译 DSC 配置的信息，请参阅 [DSC 配置](configurations.md)：

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. 这将在名为 `SampleIISInstall` 的新文件夹中创建 `localhost.mof` 文件。
通过使用 [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet，重命名该文件并将其移动到 VHD 上的正确位置，作为 `Pending.mof`。 例如：

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. 通过调用 [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet 卸除 VHD。 例如：

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. 通过使用安装了 DSC MOF 文档的 VHD 创建 VM。 初始启动并安装操作系统之后，将安装 IIS。
可以通过调用 [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet 对此进行验证。

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>将 DSC 元配置注入 VHD

还可通过将元配置注入 VHD 作为其 `MetaConfig.mof` 文件，从而在初始启动时配置计算机以拉取配置（请参阅[配置本地配置管理器 (LCM)](metaConfig.md)）。
如果将 **DSCAutomationHostEnabled** 注册表项设置为 2（默认值），则在首次启动计算机时，DSC 会将由 `MetaConfig.mof` 定义的元配置应用到 LCM。
如果元配置指定 LCM 应从请求服务器拉取配置，则计算机将尝试在初始启动时从该请求服务器拉取配置。
有关设置 DSC 请求服务器的信息，请参阅[设置 DSC Web 请求服务器](pullServer.md)。

对于此示例，我们将使用上一节中所述的配置 (**SampleIISInstall**)，以及以下元配置：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>将元配置 MOF 文档注入 VHD

1. 通过调用 [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet，将 VHD 装入想要注入元配置的位置。 例如：

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. [设置 DSC Web 请求服务器](pullServer.md)，并将 **SampleIISInistall** 配置保存到相应的文件夹。

3. 在运行 PowerShell 5.0 或更高版本的计算机上，将以上元配置 (**PullClientBootstrap**) 保存为 PowerShell 脚本 (.ps1) 文件。

4. 在 PowerShell 控制台中，导航到保存 .ps1 文件的文件夹。

5. 运行以下 PowerShell 命令来编译元配置 MOF 文档（有关编译 DSC 配置的信息，请参阅 [DSC 配置](configurations.md)：

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. 这将在名为 `PullClientBootstrap` 的新文件夹中创建 `localhost.meta.mof` 文件。
通过使用 [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet，重命名该文件并将其移动到 VHD 上的正确位置，作为 `MetaConfig.mof`。

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. 通过调用 [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet 卸除 VHD。 例如：

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. 通过使用安装了 DSC MOF 文档的 VHD 创建 VM。
初始启动并安装操作系统之后，DSC 将从请求服务器拉取配置，并安装 IIS。
可以通过调用 [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet 对此进行验证。

## <a name="disable-dsc-at-boot-time"></a>启动时，请禁用 DSC

默认情况下，**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** 项的值设置为 2，这使得当计算机处于挂起或当前状态时 DSC 配置能够运行。 如果不希望配置在初始启动时运行，则需要将此项的值设置为 0：

1. 通过调用 [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet 装载 VHD。 例如：

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. 通过调用 `reg load`，从 VHD 加载注册表 **HKLM\Software** 子项。

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. 通过使用 PowerShell 注册表提供程序导航到 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***。

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. 将 `DSCAutomationHostEnabled` 的值更改为 0。

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. 通过运行以下命令来卸载注册表：

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a>另请参阅

- [DSC 配置](configurations.md)
- [DSCAutomationHostEnabled 注册表项](DSCAutomationHostEnabled.md)
- [配置本地配置管理器 (LCM)](metaConfig.md)
- [设置 DSC Web 请求服务器](pullServer.md)


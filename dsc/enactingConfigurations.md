---
ms.date: 2017-06-12T00:00:00.000Z
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "执行配置"
ms.openlocfilehash: db3a999f3e413ebb88e79f5ec04a7449db543030
ms.sourcegitcommit: 46feddbc753523f464f139b5d272794620072fc8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2017
---
# <a name="enacting-configurations"></a>执行配置

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

有两种执行 PowerShell Desired State Configuration (DSC) 配置的方法：推送模式和请求模式。

## <a name="push-mode"></a>推送模式

![推送模式](images/Push.png "推送模式的工作原理")

推送模式指的是用户通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 主动将配置应用到目标节点。

创建并编译配置后，可通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet，并将 cmdlet 的 -Path 参数设置为配置 MOF 所在的路径，从而在推送模式下执行该配置。 例如，如果配置 MOF 位于 `C:\DSC\Configurations\localhost.mof` 中，则使用以下命令将其应用于本地计算机：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __注意__：默认情况下，DSC 运行配置作为后台作业。 若要以交互方式运行此配置，请使用 __-Wait__ 参数调用 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx)。


## <a name="pull-mode"></a>请求模式

![拉取模式](images/Pull.png "拉取模式的工作原理")

在请求模式下，配置请求客户端以从远程请求服务器中获取所需的状态配置。 同样，已将请求服务器设置为托管 DSC 服务，并提供了请求服务器所需的配置和资源。 每个请求客户端都有计划的任务，在节点的配置上定期执行相容性检查。 首次触发事件时，请求客户端上的本地配置管理器 (LCM) 对请求服务器发出请求，获取 LCM 中指定的配置。 如果请求服务器上存在该配置，并通过了初始验证检查，则配置将传送到请求客户端，然后在其上由 LCM 进行执行。

LCM 会按其 **ConfigurationModeFrequencyMins** 属性指定的时间间隔来定期检查客户端是否符合配置要求。 LCM 会按其 **RefreshModeFrequency** 属性指定的时间间隔来定期检查拉取服务器上的更新配置。 若要了解如何配置 LCM，请参阅[配置本地配置管理器](metaConfig.md)。

若要详细了解如何设置 DSC 拉取服务器，请参阅[设置 DSC Web 拉取服务器](pullServer.md)。

如果想利用联机服务承载请求服务器功能，请参阅 [Azure 自动化 DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) 服务。

以下主题说明了如何设置请求服务器和客户端：

- [设置 Web 请求服务器](pullServer.md)
- [设置 SMB 请求服务器](pullServerSMB.md)
- [配置请求客户端](pullClientConfigID.md)


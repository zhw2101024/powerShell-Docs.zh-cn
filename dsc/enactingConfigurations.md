---
title: "执行配置"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 4c802002c6a03a27d02221dd713677911a77c30b

---

# 执行配置

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

有两种执行 PowerShell Desired State Configuration (DSC) 配置的方法：推送模式和请求模式。

## 推送模式

![推送模式](images/Push.png "How push mode works")

推送模式指的是用户通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 主动将配置应用到目标节点。

创建并编译配置后，可通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet，并将 cmdlet 的 -Path 参数设置为配置 MOF 所在的路径，从而在推送模式下执行该配置。 例如，如果配置 MOF 位于 `C:\DSC\Configurations\localhost.mof` 中，你会使用以下命令将其应用于本地计算机： `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __注意__：默认情况下，DSC 运行配置作为后台作业。 若要以交互方式运行此配置，请使用 __-Wait__ 参数调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)。


## 请求模式

![请求模式](images/Pull.png "How pull mode works")

在请求模式下，配置请求客户端以从远程请求服务器中获取所需的状态配置。 同样，已将请求服务器设置为托管 DSC 服务，并提供了请求服务器所需的配置和资源。 每个请求客户端都有计划的任务，在节点的配置上定期执行相容性检查。 首次触发事件时，将导致请求客户端上的本地配置管理器 (LCM) 验证此配置。 如果将请求客户端配置为所需，则不会进行验证。 否则，LCM 将向请求服务器发出请求以获取给定的配置。 如果请求服务器上存在该配置，并通过了初始验证检查，则配置将传送到请求客户端，然后在其上由 LCM 进行执行。

有关部署本地 DSC 请求服务器的详细信息，请参阅《DSC 请求服务器配置和计划指南》。

如果想利用联机服务承载请求服务器功能，请参阅 [Azure 自动化 DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) 服务。

以下主题说明了如何设置请求服务器和客户端：

- [设置 Web 请求服务器](pullServer.md)
- [设置 SMB 请求服务器](pullServerSMB.md)
- [配置请求客户端](pullClientConfigID.md)




<!--HONumber=Jun16_HO4-->



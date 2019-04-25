---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 设置 DSC请求客户端
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079636"
---
# <a name="setting-up-a-dsc-pull-client"></a>设置 DSC请求客户端

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。

必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置和资源以及应在其中发送报表数据的 URL 或文件位置。

以下主题说明了如何设置请求客户端：

* [使用配置名称设置请求客户端](pullClientConfigNames.md)
* [使用配置 ID 设置请求客户端](pullClientConfigID.md)

> [!NOTE]
> 这些主题适用于 PowerShell 5.0。 有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)。
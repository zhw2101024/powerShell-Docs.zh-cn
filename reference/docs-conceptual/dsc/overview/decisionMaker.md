---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于决策者的 Desired State Configuration 概述
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953684"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>适用于决策者的 Desired State Configuration 概述

本文介绍使用 Windows PowerShell Desired State Configuration (DSC) 给业务带来的好处。 它不是技术指南。

## <a name="what-is-desired-state-configuration"></a>什么是 Desired State Configuration？

PowerShell Desired State Configuration 是基于开放标准的内置于 Windows 中的配置管理平台。 DSC 足够灵活以在部署生命周期的各个阶段（开发、测试、预生产、生产）及扩展期间可靠而一致地运转。

DSC 以[配置](../configurations/configurations.md)为中心。
配置是易读的文档，描述了由具有特定特征的计算机（“节点”）组成的环境。
这些特性可简单可复杂，或如确保特定 Windows 功能已启用般简单，或如部署 SharePoint 般复杂。

DSC 也内置了监视和报告。
如果系统不再相容，DSC 会引发警报，并采取措施更正系统。

## <a name="benefits-of-using-desired-state-configuration"></a>使用 Desired State Configuration 的优点

配置的设计实现了轻松读取、存储并更新。
配置声明目标设备应处于的状态，无需编写如何将其置于该状态的说明。
这样用于 DSC 的学习、使用、实现和配置维护的成本都大大降低。

创建配置意味着，单个位置中的复杂部署步骤将捕获为“单一资料来源”。
这使得重复部署一组特定的计算机不易出错。
反之，使部署更快和更可靠会启用复杂部署上的快速周转。

配置还可通过 [PowerShell 库](https://powershellgallery.com)共享，这意味着需要完成的工作可能已经存在常见方案和最佳做法。


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration 和 DevOps

DSC 设计时考虑到 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)后者结合了人员、流程和工具，方便实现快速部署和迭代，旨在向内外部最终用户传递价值。
使单个配置定义环境意味着，开发人员可将其要求编码到配置中，并将该配置签入源控件，而操作小组可轻松部署代码，无需经历易出错的手动流程。

配置也是[数据驱动](../configurations/configData.md)的，便于操作人员识别和更改环境，无需开发人员介入。

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>本地和非本地 Desired State Configuration
DSC 可用于管理本地和非本地部署。
针对本地解决方案，DSC 拥有[请求服务器](../pull-server/pullServer.md)，可用于集中式管理计算机并报告其状态。
针对云解决方案，只要 Windows 可用 DSC 就可用。
Desired State Configuration 还内置有来自 Azure 的特定产品/服务，例如 [Azure 自动化](https://azure.microsoft.com/en-us/documentation/services/automation/)，它可实现 DSC 报告的集中化。

## <a name="dsc-and-compatibility"></a>DSC 和兼容性

尽管 DSC 在 Windows Server 2012 R2 中引入，但下层操作系统可通过 Windows Management Framework (WMF) 程序包使用它。
有关 WMF 的详细信息，可查看 [PowerShell 主页](/powershell/)。

DSC 还可以用于管理 Linux。 有关详细信息，请参阅[适用于 Linux 的 DSC 入门](../getting-started/lnxGettingStarted.md)。

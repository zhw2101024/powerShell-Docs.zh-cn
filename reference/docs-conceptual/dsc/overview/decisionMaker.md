---
ms.date: 10/11/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于决策者的 Desired State Configuration 概述
ms.openlocfilehash: 271ec04035feb17e932acd0ac80f32213a4e018b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352125"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>适用于决策者的 Desired State Configuration 概述

本文档描述了使用 PowerShell Desired State Configuration (DSC) 的商业利益，而非技术指南。

## <a name="what-is-dsc"></a>什么是 DSC？

PowerShell DSC 是基于开放标准的内置于 Windows 中的配置管理平台。 DSC 足够灵活，能够在部署生命周期的各个阶段（开发、测试、预生产、生产）及扩展期间可靠而一致地运转。

DSC 以[配置](../configurations/configurations.md)为中心。 配置是 PowerShell 脚本，它描述了由具有特定特征的计算机或节点组成的环境。 这些特性可简单可复杂，或如确保特定 Windows 功能已启用般简单，或如部署 SharePoint 般复杂。

DSC 内置了监视和报告。 如果系统不再相容，DSC 会引发警报，并采取措施更正系统。

## <a name="benefits-of-using-dsc"></a>使用 DSC 的好处

配置的设计简化了读取、存储和更新配置的方式。 配置声明目标设备的状态，而非编写如何将设备置于该状态的说明。 这些因素降低了通过 DSC 学习、使用、实现和维护配置的成本。

创建配置意味着，单个位置中的复杂部署步骤将捕获为“单一资料来源”。  配置使得重复部署一组特定的计算机不易出错。 此外，还使部署更快并且更可靠，从而可以快速周转复杂部署。

可通过 [PowerShell 库](https://powershellgallery.com)共享配置。 你需完成的工作可能已存在常见方案和最佳做法。

## <a name="dsc-and-devops"></a>DSC 和 DevOps

DSC 以 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) 为设计理念。 人员、流程和工具的组合，方便实现快速部署和迭代，旨在向内外部最终用户传递价值。 定义环境的单个配置意味着开发人员可以将其要求编码到配置，并将该配置签入源代码管理。 然后操作团队无需完成易出错的手动流程即可部署代码。

配置[由数据驱动](../configurations/configData.md)。 定义的数据便于操作人员识别和更改环境，而无需开发人员介入。

## <a name="dsc-on-premises-and-off-premises"></a>DSC 本地和非本地

DSC 可管理本地和非本地部署。 对于本地解决方案，DSC 拥有[请求服务器](../pull-server/pullServer.md)，可用于集中式管理计算机并报告其状态。 对于非本地云解决方案，Windows 适用的地方即可使用 DSC。
Azure 有基于 DSC 的特定产品/服务，例如将 DSC 报告集中化的 [Azure 自动化](https://azure.microsoft.com/en-us/documentation/services/automation/)。

## <a name="dsc-and-compatibility"></a>DSC 和兼容性

尽管 DSC 在 Windows Server 2012 R2 中引入，但下层操作系统可通过 Windows Management Framework (WMF) 使用它。 有关 WMF 的详细信息，请参阅 [Windows Management Framework](/powershell/scripting/wmf/overview)。

DSC 可以用于管理 Linux。 有关详细信息，请参阅[适用于 Linux 的 DSC 入门](../getting-started/lnxGettingStarted.md)。

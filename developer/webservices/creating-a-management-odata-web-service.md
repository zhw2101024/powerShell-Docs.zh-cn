---
title: 创建管理 OData Web 服务 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080690"
---
# <a name="creating-a-management-odata-web-service"></a>创建管理 OData Web 服务

管理 ODATA IIS 扩展是用于创建公开管理数据，通过 Windows PowerShell cmdlet 和脚本，作为 OData Web 服务的实体访问 ASP.NET web 服务终结点的基础结构。 它通过处理 OData 请求并将其转换的 Windows PowerShell 调用来实现的。 产品团队可以在此基础结构来创建终结点公开特定的管理数据集之上构建。

下载并安装[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例。 按照要部署 web 服务的说明。 此 web 服务公开的服务和进程通过创建、 读取、 更新和删除 (CRUD) 操作。 对 web 服务发出的 CRUD 请求调用执行请求的操作的 Windows PowerShell 命令。 由两个架构文件、 schema.mof 和 schema.xml 实现 CRUD 操作和基础 Windows PowerShell 命令之间的映射。 Schema.mof 文件使用[Distributed Management Task Force](https://www.dmtf.org/) (DMTF) 托管对象 (MOF) 标准。 Schema.xml 文件使用 XML 架构中所述[资源的映射架构](./resource-mapping-schema.md)。

> [!IMPORTANT]
> 启用管理 ODATA IIS 扩展在 Windows Server 2008 R2 SP1 之前，必须启用以下功能。
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>创建管理 OData web 服务的步骤

以下主题介绍如何创建和部署管理 OData web 服务。

- [将资源添加到管理 OData Web 服务](./adding-resources-to-a-management-odata-web-service.md)

- [实现自定义授权管理 OData web 服务](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [管理 OData web 服务实现 SessionConfiguration](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [创作管理 OData web 服务的 MOF 架构文件](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [创作管理 OData web 服务的 XML 架构文件](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [创作管理 OData web 服务的 Web.config 文件](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [管理 OData web 服务部署](./deploying-a-management-odata-web-service.md)

- [将管理 OData 实体相关联](./associating-management-odata-entities.md)

## <a name="see-also"></a>另请参阅

[管理 ODATA IIS 扩展架构文件](./management-odata-iis-extension-schema-files.md)

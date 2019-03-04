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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856623"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="3ea1b-102">创建管理 OData Web 服务</span><span class="sxs-lookup"><span data-stu-id="3ea1b-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="3ea1b-103">管理 ODATA IIS 扩展是用于创建公开管理数据，通过 Windows PowerShell cmdlet 和脚本，作为 OData Web 服务的实体访问 ASP.NET web 服务终结点的基础结构。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="3ea1b-104">它通过处理 OData 请求并将其转换的 Windows PowerShell 调用来实现的。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="3ea1b-105">产品团队可以在此基础结构来创建终结点公开特定的管理数据集之上构建。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="3ea1b-106">下载并安装[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="3ea1b-107">按照要部署 web 服务的说明。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="3ea1b-108">此 web 服务公开的服务和进程通过创建、 读取、 更新和删除 (CRUD) 操作。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="3ea1b-109">对 web 服务发出的 CRUD 请求调用执行请求的操作的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="3ea1b-110">由两个架构文件、 schema.mof 和 schema.xml 实现 CRUD 操作和基础 Windows PowerShell 命令之间的映射。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="3ea1b-111">Schema.mof 文件使用[Distributed Management Task Force](https://www.dmtf.org/) (DMTF) 托管对象 (MOF) 标准。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="3ea1b-112">Schema.xml 文件使用 XML 架构中所述[资源的映射架构](./resource-mapping-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3ea1b-113">启用管理 ODATA IIS 扩展在 Windows Server 2008 R2 SP1 之前，必须启用以下功能。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="3ea1b-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="3ea1b-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="3ea1b-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="3ea1b-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="3ea1b-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="3ea1b-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="3ea1b-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="3ea1b-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="3ea1b-118">创建管理 OData web 服务的步骤</span><span class="sxs-lookup"><span data-stu-id="3ea1b-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="3ea1b-119">以下主题介绍如何创建和部署管理 OData web 服务。</span><span class="sxs-lookup"><span data-stu-id="3ea1b-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="3ea1b-120">将资源添加到管理 OData Web 服务</span><span class="sxs-lookup"><span data-stu-id="3ea1b-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="3ea1b-121">实现自定义授权管理 OData web 服务</span><span class="sxs-lookup"><span data-stu-id="3ea1b-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3ea1b-122">管理 OData web 服务实现 SessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ea1b-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3ea1b-123">创作管理 OData web 服务的 MOF 架构文件</span><span class="sxs-lookup"><span data-stu-id="3ea1b-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3ea1b-124">创作管理 OData web 服务的 XML 架构文件</span><span class="sxs-lookup"><span data-stu-id="3ea1b-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3ea1b-125">创作管理 OData web 服务的 Web.config 文件</span><span class="sxs-lookup"><span data-stu-id="3ea1b-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3ea1b-126">管理 OData web 服务部署</span><span class="sxs-lookup"><span data-stu-id="3ea1b-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="3ea1b-127">将管理 OData 实体相关联</span><span class="sxs-lookup"><span data-stu-id="3ea1b-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="3ea1b-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ea1b-128">See Also</span></span>

[<span data-ttu-id="3ea1b-129">管理 ODATA IIS 扩展架构文件</span><span class="sxs-lookup"><span data-stu-id="3ea1b-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)

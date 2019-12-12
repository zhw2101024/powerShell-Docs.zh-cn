---
title: 创建 Management OData Web 服务 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359716"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="3080d-102">创建管理 OData Web 服务</span><span class="sxs-lookup"><span data-stu-id="3080d-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="3080d-103">管理 ODATA IIS 扩展是一个基础结构，用于创建 ASP.NET web 服务终结点，该终结点公开作为 OData Web 服务实体的 Windows PowerShell cmdlet 和脚本访问的管理数据。</span><span class="sxs-lookup"><span data-stu-id="3080d-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="3080d-104">它通过处理 OData 请求并将其转换为 Windows PowerShell 调用来实现此功能。</span><span class="sxs-lookup"><span data-stu-id="3080d-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="3080d-105">产品团队可以在此基础结构的基础上构建，以创建用于公开特定管理数据集的终结点。</span><span class="sxs-lookup"><span data-stu-id="3080d-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="3080d-106">下载并安装[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例。</span><span class="sxs-lookup"><span data-stu-id="3080d-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="3080d-107">按照说明部署 web 服务。</span><span class="sxs-lookup"><span data-stu-id="3080d-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="3080d-108">此 web 服务通过创建、读取、更新和删除（CRUD）操作公开服务和进程。</span><span class="sxs-lookup"><span data-stu-id="3080d-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="3080d-109">向 web 服务发出的 CRUD 请求调用执行所请求操作的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="3080d-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="3080d-110">CRUD 操作与基础 Windows PowerShell 命令之间的映射是通过两个架构文件（架构）和 schema 来实现的。</span><span class="sxs-lookup"><span data-stu-id="3080d-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="3080d-111">架构的 mof 文件使用[分布式管理任务组](https://www.dmtf.org/)（DMTF）托管对象（mof）标准。</span><span class="sxs-lookup"><span data-stu-id="3080d-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="3080d-112">架构 .xml 文件使用[资源映射架构](./resource-mapping-schema.md)中描述的 xml 架构。</span><span class="sxs-lookup"><span data-stu-id="3080d-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3080d-113">在 Windows Server 2008 R2 SP1 上启用管理 ODATA IIS 扩展之前，必须启用以下功能。</span><span class="sxs-lookup"><span data-stu-id="3080d-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="3080d-114">IIS-Iis-webserverrole was-windowsactivationservice</span><span class="sxs-lookup"><span data-stu-id="3080d-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="3080d-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="3080d-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="3080d-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="3080d-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="3080d-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="3080d-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="3080d-118">创建管理 OData web 服务的步骤</span><span class="sxs-lookup"><span data-stu-id="3080d-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="3080d-119">以下主题介绍了如何创建和部署管理 OData web 服务。</span><span class="sxs-lookup"><span data-stu-id="3080d-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="3080d-120">将资源添加到管理 OData Web 服务</span><span class="sxs-lookup"><span data-stu-id="3080d-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="3080d-121">为管理 OData web 服务实现自定义授权</span><span class="sxs-lookup"><span data-stu-id="3080d-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3080d-122">为 Management OData web 服务实现 SessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3080d-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3080d-123">创作用于管理 OData web 服务的 MOF 架构文件</span><span class="sxs-lookup"><span data-stu-id="3080d-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3080d-124">创作用于管理 OData web 服务的 XML 架构文件</span><span class="sxs-lookup"><span data-stu-id="3080d-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3080d-125">创作用于管理 OData web 服务的 web.config 文件</span><span class="sxs-lookup"><span data-stu-id="3080d-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="3080d-126">部署管理 OData web 服务</span><span class="sxs-lookup"><span data-stu-id="3080d-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="3080d-127">关联管理 OData 实体</span><span class="sxs-lookup"><span data-stu-id="3080d-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="3080d-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3080d-128">See Also</span></span>

[<span data-ttu-id="3080d-129">管理 ODATA IIS 扩展架构文件</span><span class="sxs-lookup"><span data-stu-id="3080d-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)

---
title: 创作管理 OData web 服务的 XML 架构文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080724"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="bdd78-102">创作管理 OData Web 服务的 XML 架构文件</span><span class="sxs-lookup"><span data-stu-id="bdd78-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="bdd78-103">你的 web 服务定义的资源后将公开 (请参阅[创作管理 OData web 服务的 MOF 架构文件](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md))，将这些资源映射到基础实现受支持的 Windows PowerShell cmdlet通过创建 XML 文件符合每个资源的操作[资源的映射架构](./resource-mapping-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="bdd78-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="bdd78-104">XML 文件还指定客户端用于访问资源的 Url。</span><span class="sxs-lookup"><span data-stu-id="bdd78-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="bdd78-105">Mappng 的资源添加到 Url</span><span class="sxs-lookup"><span data-stu-id="bdd78-105">Mappng resources to URLs</span></span>

<span data-ttu-id="bdd78-106">XML 文件的第一部分将映射到用来对其进行访问的 Url 的 MOF 架构文件中定义的资源。</span><span class="sxs-lookup"><span data-stu-id="bdd78-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="bdd78-107">下面的示例显示了该映射。</span><span class="sxs-lookup"><span data-stu-id="bdd78-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="bdd78-108">将 cmdlet 映射到 CRUD 操作</span><span class="sxs-lookup"><span data-stu-id="bdd78-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="bdd78-109">然后指定对应于 CRUD 的 cmdlet （创建、 读取、 更新和删除） 资源支持的操作。</span><span class="sxs-lookup"><span data-stu-id="bdd78-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="bdd78-110">在管理 OData[资源的映射架构](./resource-mapping-schema.md)，按如下所示映射的 CRUD 操作。</span><span class="sxs-lookup"><span data-stu-id="bdd78-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="bdd78-111">CRUD 命令</span><span class="sxs-lookup"><span data-stu-id="bdd78-111">CRUD command</span></span>|<span data-ttu-id="bdd78-112">XML 元素</span><span class="sxs-lookup"><span data-stu-id="bdd78-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="bdd78-113">创建</span><span class="sxs-lookup"><span data-stu-id="bdd78-113">Create</span></span>|<span data-ttu-id="bdd78-114">创建</span><span class="sxs-lookup"><span data-stu-id="bdd78-114">Create</span></span>|
|<span data-ttu-id="bdd78-115">读取</span><span class="sxs-lookup"><span data-stu-id="bdd78-115">Read</span></span>|<span data-ttu-id="bdd78-116">查询</span><span class="sxs-lookup"><span data-stu-id="bdd78-116">Query</span></span>|
|<span data-ttu-id="bdd78-117">更新</span><span class="sxs-lookup"><span data-stu-id="bdd78-117">Update</span></span>|<span data-ttu-id="bdd78-118">更新</span><span class="sxs-lookup"><span data-stu-id="bdd78-118">Update</span></span>|
|<span data-ttu-id="bdd78-119">“删除”</span><span class="sxs-lookup"><span data-stu-id="bdd78-119">Delete</span></span>|<span data-ttu-id="bdd78-120">“删除”</span><span class="sxs-lookup"><span data-stu-id="bdd78-120">Delete</span></span>|

<span data-ttu-id="bdd78-121">下面的示例演示用于创建、 读取和更新操作映射上`Service`资源。</span><span class="sxs-lookup"><span data-stu-id="bdd78-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="bdd78-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdd78-122">See Also</span></span>

[<span data-ttu-id="bdd78-123">创作管理 OData web 服务的 MOF 架构文件</span><span class="sxs-lookup"><span data-stu-id="bdd78-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="bdd78-124">资源映射架构</span><span class="sxs-lookup"><span data-stu-id="bdd78-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="bdd78-125">创建管理 OData Web 服务</span><span class="sxs-lookup"><span data-stu-id="bdd78-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)
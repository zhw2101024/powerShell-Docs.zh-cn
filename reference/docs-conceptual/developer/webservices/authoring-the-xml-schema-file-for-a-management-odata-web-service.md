---
title: 创作用于管理 OData web 服务的 XML 架构文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: b830571418fe75bbfc68df02f20a6012efefd99a
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996073"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="2c7d1-102">创作管理 OData Web 服务的 XML 架构文件</span><span class="sxs-lookup"><span data-stu-id="2c7d1-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="2c7d1-103">定义 web 服务将公开的资源之后（请参阅[创作用于管理 OData web 服务的 MOF 架构文件](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)），通过创建符合[资源映射架构](./resource-mapping-schema.md)的 XML 文件，将这些资源映射到用于实现每个资源支持的操作的基础 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2c7d1-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="2c7d1-104">该 XML 文件还指定客户端用来访问资源的 Url。</span><span class="sxs-lookup"><span data-stu-id="2c7d1-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="2c7d1-105">将资源 Mappng 到 Url</span><span class="sxs-lookup"><span data-stu-id="2c7d1-105">Mappng resources to URLs</span></span>

<span data-ttu-id="2c7d1-106">XML 文件的第一部分将 MOF 架构文件中定义的资源映射到用于访问这些资源的 Url。</span><span class="sxs-lookup"><span data-stu-id="2c7d1-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="2c7d1-107">下面的示例演示了该映射。</span><span class="sxs-lookup"><span data-stu-id="2c7d1-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="https://schemas.microsoft.com/powershell-web-services/2010/09">
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

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="2c7d1-108">将 cmdlet 映射到 CRUD 操作</span><span class="sxs-lookup"><span data-stu-id="2c7d1-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="2c7d1-109">然后指定与资源所支持的 CRUD （创建、读取、更新和删除）操作相对应的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2c7d1-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="2c7d1-110">在管理 OData[资源映射架构](./resource-mapping-schema.md)中，CRUD 操作按如下方式进行映射。</span><span class="sxs-lookup"><span data-stu-id="2c7d1-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="2c7d1-111">CRUD 命令</span><span class="sxs-lookup"><span data-stu-id="2c7d1-111">CRUD command</span></span>|<span data-ttu-id="2c7d1-112">XML 元素</span><span class="sxs-lookup"><span data-stu-id="2c7d1-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="2c7d1-113">创建</span><span class="sxs-lookup"><span data-stu-id="2c7d1-113">Create</span></span>|<span data-ttu-id="2c7d1-114">创建</span><span class="sxs-lookup"><span data-stu-id="2c7d1-114">Create</span></span>|
|<span data-ttu-id="2c7d1-115">读取</span><span class="sxs-lookup"><span data-stu-id="2c7d1-115">Read</span></span>|<span data-ttu-id="2c7d1-116">查询</span><span class="sxs-lookup"><span data-stu-id="2c7d1-116">Query</span></span>|
|<span data-ttu-id="2c7d1-117">更新</span><span class="sxs-lookup"><span data-stu-id="2c7d1-117">Update</span></span>|<span data-ttu-id="2c7d1-118">更新</span><span class="sxs-lookup"><span data-stu-id="2c7d1-118">Update</span></span>|
|<span data-ttu-id="2c7d1-119">“删除”</span><span class="sxs-lookup"><span data-stu-id="2c7d1-119">Delete</span></span>|<span data-ttu-id="2c7d1-120">“删除”</span><span class="sxs-lookup"><span data-stu-id="2c7d1-120">Delete</span></span>|

<span data-ttu-id="2c7d1-121">下面的示例演示 `Service` 资源上的创建、读取和更新操作的映射。</span><span class="sxs-lookup"><span data-stu-id="2c7d1-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2c7d1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c7d1-122">See Also</span></span>

[<span data-ttu-id="2c7d1-123">创作用于管理 OData web 服务的 MOF 架构文件</span><span class="sxs-lookup"><span data-stu-id="2c7d1-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="2c7d1-124">资源映射架构</span><span class="sxs-lookup"><span data-stu-id="2c7d1-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="2c7d1-125">创建 Management OData Web 服务</span><span class="sxs-lookup"><span data-stu-id="2c7d1-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)
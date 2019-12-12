---
title: 创作用于管理 OData web 服务的 web.config 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359786"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a><span data-ttu-id="ef3f7-102">创作管理 OData Web 服务的 Web.config 架构文件</span><span class="sxs-lookup"><span data-stu-id="ef3f7-102">Authoring the Web.config file for a Management OData web service</span></span>

<span data-ttu-id="ef3f7-103">在部署你的管理 OData web 服务之前，必须将 web.config 文件配置为指向 XML 架构文件以及实现[Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)和[Set-pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration)接口的 dll。 "的配置文件的配置文件。</span><span class="sxs-lookup"><span data-stu-id="ef3f7-103">Before you can deploy your Management OData web service, you must configure the web.config file to point to the XML schema files and the DLLs that implement the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) and  [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.</span></span>

## <a name="sample-config-file"></a><span data-ttu-id="ef3f7-104">示例配置文件</span><span class="sxs-lookup"><span data-stu-id="ef3f7-104">Sample config file</span></span>

<span data-ttu-id="ef3f7-105">下面的示例展示了 web 服务的 web.config 文件的外观。</span><span class="sxs-lookup"><span data-stu-id="ef3f7-105">The following is an example of what the web.config file for your web service looks like.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a><span data-ttu-id="ef3f7-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef3f7-106">See Also</span></span>

[<span data-ttu-id="ef3f7-107">为管理 OData web 服务实现自定义授权</span><span class="sxs-lookup"><span data-stu-id="ef3f7-107">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[<span data-ttu-id="ef3f7-108">为 Management OData web 服务实现 SessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef3f7-108">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[<span data-ttu-id="ef3f7-109">创作用于管理 OData web 服务的 MOF 架构文件</span><span class="sxs-lookup"><span data-stu-id="ef3f7-109">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="ef3f7-110">创作用于管理 OData web 服务的 XML 架构文件</span><span class="sxs-lookup"><span data-stu-id="ef3f7-110">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="ef3f7-111">创建 Management OData Web 服务</span><span class="sxs-lookup"><span data-stu-id="ef3f7-111">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)
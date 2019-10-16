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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359786"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>创作管理 OData Web 服务的 Web.config 架构文件

在部署您的管理 OData web 服务之前，您必须将 web.config 文件配置为指向 XML 架构文件和实现[Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)的 dll，然后[Set-pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration)接口进行处理。

## <a name="sample-config-file"></a>示例配置文件

下面的示例展示了 web 服务的 web.config 文件的外观。

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

## <a name="see-also"></a>另请参阅

[为管理 OData web 服务实现自定义授权](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[为 Management OData web 服务实现 SessionConfiguration](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[创作用于管理 OData web 服务的 MOF 架构文件](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[创作用于管理 OData web 服务的 XML 架构文件](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[创建 Management OData Web 服务](./creating-a-management-odata-web-service.md)